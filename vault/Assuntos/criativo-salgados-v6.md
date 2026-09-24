---
tags: [project, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Criativo de salgados — v6
Trabalho em andamento desde 2026-08-08: montar criativo de anúncio (Reels 9:16) para a apostila de salgados do Gabriel, modelando um criativo de referência dele.

## Arquivos de origem
- Referência: `Downloads\TESTE DE CRIATIVOS NOVOS SALGADOS\CRIATIVO NO TESTE.mp4` (123s, 540x960)
- Locução nova: `Downloads\AUDIO DO CRIATIVO SALGADOS\audio 2 salgados teste cv.mp3` (110,37s, já em −14,8 LUFS)
- Transcrição: `..._analise\audio-novo.srt` (40 trechos)
- Material bruto: `Downloads\PASTA CONTEUDO DE EDIÇAO SALGADOS\` (15 vídeos, 576x1024, ~20 min)

## Roteiro da locução nova (blocos)
0–9 gancho invertido ("nunca vendeu = vantagem") · 9–26 o inimigo · 26–38 a regra ("quem briga por preço nunca lucra") · 38–50 promessa · 50–62 quebra de objeção · 62–86 oferta · 86–99 bônus congelamento + preço R$10,90 · 99–110 CTA WhatsApp

## Entregue
`Downloads\CRIATIVO_NOVO_v4.mp4` — **é a base boa**. 110,37s, 1080x1920, 48 cortes, legenda .ass estilo CapCut (caixa alta, palavra de impacto com halo vermelho), zoom lento alternado, CTA com seta + balão do WhatsApp (`scratchpad\cta.png`, desenhado em SVG).

Scripts em `scratchpad\`: `montar3.ps1` (montagem), `legenda.ps1` (SRT→ASS), `sons.ps1`, `montar5.ps1`.

## O que o Gabriel REJEITOU (v5) e por quê
Som em todos os 38 cortes, sempre o mesmo swoosh. Ficou repetitivo e fora de sincronia. **A causa raiz:** os sons foram ancorados nos cortes do vídeo (a cada ~2,4s), não no ritmo da fala. Metade caiu no meio de frase.

## O que falta — v6
Refazer o desenho sonoro ancorado na **transcrição**, não no corte. ~14 pontos no vídeo inteiro, escolhidos pelo sentido da frase: riser antes de revelação, impacto na palavra de peso (vício / nunca lucra / dinheiro), chime no preço, buildup antes do CTA. Banco pronto em `C:\Users\gabgb\sfx-banco` (100 efeitos CC0, 8 categorias, do videoeditingsfx.com).

Também pendente: trocar 4–5 planos com marca d'água `@ArmandoFelipeReceitas` e corrigir "começa na sua cozinha" para cena caseira (vídeos 7 ou 10 da pasta).

**Música: o Gabriel coloca ele mesmo no CapCut** (a biblioteca de lá é licenciada pra ele). Não tentar automatizar a timeline do CapCut — ver [[pipeline-video-ffmpeg]].

Páginas do PDF de congelamento saíram do criativo: tinham PIX e @ de outra criadora visíveis.
