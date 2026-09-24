---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Triagem de b-roll
O Gabriel baixa b-roll do TikTok em lote. Boa parte não pode entrar em anúncio pago.
Triar **antes** de montar, extraindo 4 frames por vídeo e olhando em contact sheet.

**Reprova direto:**

- **Marca d'água de perfil** (`@claudia_receitas`, `@saudemfocofit`, `@olhaeunacozinha`,
  selo "FAZ BEM Dicas", avental com nome de canal). Costuma estar em todos os frames.
- **Legenda queimada** em qualquer idioma — é a que mais aparece e a mais fácil de
  deixar passar.
- **Rosto identificável de terceiro**, principalmente quem se apresenta com credencial
  (médico, nutricionista). Mão e braço podem; rosto não.
- **Corpo em foco** (barriga, silhueta) — em nicho de saúde pesa contra.
- **Produto de marca na mão** (barra Milka, molho Kewpie, garrafa com rótulo).
- **Comida que contradiz a copy** — bacon num criativo de fígado, por exemplo.

**Armadilha de busca:** procurar "fígado" no TikTok devolve **receita de fígado bovino**.
Num anúncio sobre gordura no fígado isso confunde e é visualmente pesado. O mesmo vale
para termos que o algoritmo entende diferente do pretendido.

**A verificação que funciona** é extrair **um frame de cada corte do vídeo já montado**,
não amostrar os clipes de origem. Amostragem por clipe já deixou passar duas vezes:
um vídeo de salgados brasileiro no v2 de saladas, e um publieditorial da Kewpie no v5.
Só o frame do que realmente vai ao ar mostra o que vai ao ar.

**Um frame por corte não basta — a marca anda.** A assinatura do criador fica em
posição diferente a cada instante do mesmo corte (o `zoompan` move o quadro e algumas
marcas já se deslocam sozinhas). Amostrar só o meio do corte deixou passar 2 de 9.
O que pega tudo: **6 frames por corte** (0,1 / 0,5 / 0,9 / 1,3 / 1,7 / 2,1s num corte de
2,2s), recortados na faixa onde as marcas aparecem (`crop=700:940:380:980`), 6 por linha
e 11 linhas por folha — 3 folhas cobrem 33 cortes.

**O zoompan reabre o problema.** Marcar "esse clipe se salva cortando a barra de baixo"
na triagem do bruto não basta: o `zoompan` in/out/punch move o quadro e traz a marca de
volta. No hook C do mármore, 7 dos 33 cortes já renderizados ainda mostravam
`@AlinAlesioo721640427` (assinatura diagonal, cada hora numa altura) e um mostrava o
uniforme "GUILHERME NERY DECORAÇÕES". Conferir depois de renderizar, sempre.

**Como consertar sem material novo:** reenquadrar o corte já pronto com um `crop` 9:16
que joga a marca pra fora, e escalar de volta pra 1080x1920 com `flags=lanczos`.
Ex.: `crop=810:1440:0:240,scale=1080:1920:flags=lanczos`. Preserva a duração exata do
corte (então tarja, flash e legenda continuam batendo) e fica melhor que `delogo`, que
borra e aparece em parede lisa.

Quando falta b-roll pra ilustrar algo (suco de caixinha, óleo, barra de cereal),
**fazer card gráfico numerado em vez de encher com comida genérica** — fica melhor e
entrega o conteúdo.

Ver [[formato-criativo-split-avatar]] e [[pipeline-video-ffmpeg]].
