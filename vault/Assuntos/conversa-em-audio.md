---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Conversa em áudio
Em 11/09/2026 ele perguntou se dava pra falar em áudio e receber resposta em áudio, inclusive
dos agentes. O que funciona:

- **Ele → eu:** ele já dita por voz (daí os erros tipo "Fish Cliente" = subagentes). Áudio
  em arquivo (WhatsApp .opus/.ogg, .mp3) eu transcrevo com o Whisper local
  (`criativo-audio\scripts\transcrever.ps1`).
- **Eu/agentes → ele:** resumo falado em mp3 com edge-tts
  `pt-BR-AntonioNeural --rate="+4%"`, salvo em `C:\Users\gabgb\SETOR_CRIATIVOS\AUDIOS\`
  (texto .txt + .mp3 com a data) e enviado com SendUserFile. Outras vozes pt-BR:
  FranciscaNeural, ThalitaMultilingualNeural. Ele ainda não escolheu a voz.
- **Continua em texto:** copy, tabela, planilha, qualquer coisa que ele precise ler pra
  aprovar. O áudio é o resumo e a decisão; o texto é o material.

Escrever o roteiro do áudio pra ser falado: frases curtas, sem sigla solta, sem tabela, sem
travessão. 200 palavras dão ~1min30.

Ver [[projeto-equipe-agentes-vturb]] e [[tts-edge-voz-mexico]].
