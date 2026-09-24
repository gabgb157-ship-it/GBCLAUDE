---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Formato de criativo split + avatar
Formato validado em 03/09/2026 no criativo de fígado (BR), depois de quatro versões.
Vale para os próximos criativos com avatar falante.

**As regras que ele deu:**

- **Split 50/50 exato** — 960px em cima, 960px embaixo em canvas 1080x1920. Não dar
  mais espaço pro avatar: ele reclamou que "o avatar ficou muito maior".
- **O hook já abre dividido**, com b-roll em cima e texto na emenda desde o frame 1.
  Nunca abrir com o avatar em tela cheia.
- **Na maioria do tempo split**, mas variando: às vezes avatar sozinho em tela cheia,
  às vezes **take inteiro em tela cheia** (sem split), como nos virais do TikTok.
- **Tarja nunca em cima da boca.** Em trecho de tela cheia ela vai abaixo do queixo
  (y≈1130-1180); em split fica no painel de cima, acima da emenda.
- **Tarjas centralizadas** pela própria largura, não coladas à esquerda.
- **Pouco tempo em tela**: hook ~8s, as demais 3,5 a 5s. Texto se lê em 3s.
- **B-roll rápido**: cortes de ~1,9s. A 2,7s ele achou parado.
- **Hook em texto sempre impactante** e coerente com o que a copy está falando naquele
  momento.

**Parâmetros que funcionaram:**

- crop do b-roll: `scale=1080:-2,crop=1080:960:0:480`
- crop do avatar em split: `scale=1080:1920,crop=1080:960:0:300` (testei 200/300/400,
  300 é o que centra o rosto com respiro)
- zoom: punch `min(1.30,1.0+0.045*on)`, in `min(zoom+0.0016,1.18)`
- legenda ASS: Arial 42, outline 3, shadow 2, MarginV 300 — pequena e discreta, nunca
  legendão. Ver [[pipeline-video-ffmpeg]].
- tarjas: fundo sólido, canto reto, Arial Black, sombra 70,0,0,0 atrás.
  Branca = afirmação, vermelha = alerta, amarela = promessa. Gerador em
  `scratchpad\tarjas.ps1`.

**Overlay de PNG estoura memória** com 9 imagens em loop de uma vez. Fazer em 3 passes
de 3 PNGs, e sempre `-framerate 1 -loop 1 -t <dur>` (sem o framerate 1 são 30x mais
frames em RAM).

**Sempre transcrever o áudio dele e reescrever a legenda à mão** — o Whisper erra
bastante em pt-BR ("diagrama NOSCO NA MÃO", "50 shorts mais", "Biscoita Integral").

Ver [[triagem-broll-anuncio]] para o que reprovar no material bruto.

**Emenda suave (pedido em 03/09/2026).** Ele não quer o corte reto do `vstack` — quer a
fusão em degradê que os criativos escalados usam. Em vez de empilhar, sobrepor com alpha
gradiente sobre um canvas de 1920:

```
color=c=black:s=1080x1920[base];
[broll]setpts=PTS-STARTPTS,scale=1080:-2,crop=1080:1200:0:360[cima];
[avatar]setpts=PTS-STARTPTS,scale=1080:1920,crop=1080:1200:0:0,format=rgba,
  geq=r='r(X,Y)':g='g(X,Y)':b='b(X,Y)':a='if(lt(Y,200),Y*1.275,255)'[bm];
[base][cima]overlay=0:0[a];[a][bm]overlay=0:720[v]
```

**200px de fusão** é o ponto (testei 120/200/300): visível e sem invadir o rosto. O `1.275`
é 255÷200 — recalcular se mudar a largura. **`setpts=PTS-STARTPTS` em ambos é obrigatório**:
com `-ss` diferentes nos dois inputs o overlay não acha correspondência de PTS e o painel
de baixo simplesmente não aparece (perdi três tentativas nisso).

**Avatar com legenda queimada do vídeo-base:** já veio assim uma vez. Em split, cropar
acima da linha da legenda resolve; em tela cheia, montar o crop limpo sobre um fundo
desfocado dele mesmo (`boxblur=40:2,eq=brightness=-0.12`) e sobrepor centralizado.

**Selo de CTA (pedido em 03/09/2026).** Ícone do WhatsApp + seta vermelha lado a lado,
pulsando juntos, no rodapé e centralizados — entram exatamente quando a locução faz a
chamada. Gerador: `scratchpad\cta\` (16 frames, escala 0.94±0.14 por seno, ciclo de 1s).
Vira vídeo com alpha: `-framerate 16 -stream_loop 20 -i c%02d.png -c:v qtrle -pix_fmt argb`,
depois `overlay=290:1628` em 500x268 com `enable='between(...)+between(...)'`.

O ícone é **desenhado** (círculo #25D366, balão branco, handset recortado) em vez de
baixado — nítido em qualquer tamanho e sem marca d'água. A seta leva borda branca de 11px,
senão some no fundo claro da cozinha.

Fica **abaixo da legenda** (que termina em ~1620 com MarginV 300). Sobrepor os dois é o
erro fácil aqui.
