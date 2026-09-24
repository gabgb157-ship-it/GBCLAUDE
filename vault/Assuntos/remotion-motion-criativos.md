---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Remotion: motion dos criativos
Projeto em `C:\Users\gabgb\Downloads\remotion-criativos` (Remotion 4.0.524, instalado em 15/09/2026).
Peças do Pudim V020 em `src/pecas/` (Gancho, ZapPerguntas, Lista, Receitas, Metodo, Preco, Cta);
visual compartilhado em `src/estilo.tsx` (componente Tarja, cores branco/#FFE44A/#E02424, Arial Black
carregada de `public/ariblk.ttf`). A duração e os tempos vêm das props (`duracao` em quadros a 30 fps),
então dá pra casar com a voz passando `--props`.

Render com fundo transparente (pra usar como camada no CapCut/`montar`):
`npx remotion render <Id> out/<Id>.mov --codec=prores --prores-profile=4444 --pixel-format=yuva444p10le --image-format=png`

Conferência: scratchpad `pudim/qa_mg.py [Id]` monta 6 quadros de cada peça sobre um frame de fundo.
Cuidado: tarja de uma linha só com 56px+ passa da borda se tiver mais de ~22 letras — quebre com `\n`
(escreva o `\n` pela ferramenta de edição, não pelo sed, que vira quebra de linha de verdade).

Ver [[capcut-kit-windows]], [[pipeline-video-ffmpeg]].
