---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Formato TikTok viral
Validado em 04/09/2026 na copy 5 (fígado BR). É o irmão do
[[formato-criativo-split-avatar]] — sem avatar, tela cheia o tempo todo.

**A regra que mais importa:** ele reprovou a primeira versão dizendo *"não achei algumas
parte casar com a fala"*. **Fazer o mapa bloco a bloco do áudio antes de escolher clipe**
e perguntar, em cada trecho: o que a voz está dizendo aqui, e a tela mostra isso? Comida
bonita genérica não cobre um trecho que fala de celular, de exame ou de dúvida.

O que resolveu na copy 5: quando a voz nega *"não é água com limão"*, a tela mostra um
copo de água com limão. Quando fala *"fui pra internet"*, mãos digitando no celular.

**Legenda amarela estilo CapCut** (ele pediu por nome):

```
Style: CC,Arial Black,88,&H004AE4FF,&H004AE4FF,&H00000000,&HC0000000,0,0,0,0,100,100,1,0,1,8,5,2,70,70,470,1
```

Amarelo `&H004AE4FF`, contorno preto 8, sombra 5, MarginV 470. **Frases curtas em
maiúscula**, 3 a 6 palavras, trocando a cada 3s — não as duas linhas longas do formato
avatar. Na copy 5 deram 43 blocos.

**Tarja de hook com emoji** (ele mandou print de um concorrente e pediu igual): tarja
vermelha `(222,26,32)` + tarja branca empilhadas, cantos retos, Arial Black, emoji à
esquerda do texto. **System.Drawing não renderiza emoji colorido** — a ambulância sai
legível em branco, mas a chama teve que ser desenhada à mão (bezier laranja
`(242,110,20)` + núcleo amarelo `(255,206,40)`).

**Cortes de 1,9s em tela cheia**, zoom mais forte que no split (`punch` a 1.32, `in`/`out`
a 1.20). Dois ou três **takes inteiros de 6s** nos beats que a imagem carrega sozinha.

**Em tela cheia não existe crop de painel pra esconder legenda queimada** — o quadro
inteiro aparece. Clipes que serviam no split (legenda no rodapé) são reprovados aqui.
Quando o clipe é insubstituível, recortar um retângulo 9:16 dentro da faixa limpa e
reescalar: `crop=688:1224:196:560,scale=1080:1920`.

**Animação de anatomia (fígado 3D):** ele pediu explicitamente, para identificação. O
clipe que ele mandou tinha a animação limpa só nos **3 primeiros segundos** — depois vira
split com o rosto de um médico. Sempre mapear onde a parte usável termina, com frames a
cada 0,3s.

**"COMO REVERTER" eu não escrevo.** Ele pediu essa frase na tarja copiando um concorrente;
troquei por *"O QUE COMER AGORA!"* mantendo cores, emojis e estrutura. Ele aceitou. Ver
as demais regras em [[triagem-broll-anuncio]].

**Som — MUDOU em 14/09/2026:** ele pediu música, efeitos sonoros e motion graphics do CapCut na edição
(pacote do editor do pudim), trecho a trecho, com mesmo recurso pra mesma função. Vale a regra nova; o
parágrafo abaixo é o histórico.

**Histórico · só transição visual, sem efeito sonoro (decidido em 04/09/2026).** Testei whoosh,
boom, riser e pop posicionados nos beats — ele aprovou o resultado mas pediu para não usar
mais. Nas próximas: **flash branco nas viradas de bloco** (`eq=brightness` com pulso de
0,09s somado por ponto) e nada de trilha de efeitos. A música de fundo, quando houver,
vem dele.

**Avatar em formato UGC:** ele entra em ~3 momentos (gancho, mecanismo, CTA) e sai no
resto — deu 14s de avatar contra 39s de b-roll numa peça de 53s, e é a proporção que ele
aprovou. Não é o avatar contínuo do formato split.

**Clipe horizontal** (1024x576) quebra o `crop=1080:1920`. Tratar com fundo desfocado:
`split` → `scale=1080:1920:force_original_aspect_ratio=increase,crop,boxblur=45:2` no
fundo e `scale=1080:-2` centralizado na frente.
