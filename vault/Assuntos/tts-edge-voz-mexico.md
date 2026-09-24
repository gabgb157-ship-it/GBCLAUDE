---
tags: [project, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Voz de TTS aprovada (México)
Instalado em 2026-08-31 nesta máquina como alternativa gratuita ao ElevenLabs, a pedido
do Gabriel. Ele ouviu 9 amostras e escolheu esta:

```bash
python -m edge_tts --voice es-MX-DaliaNeural --rate="-6%" --text "a copy" --write-media saida.mp3
```

**`edge-tts` 7.2.8** (`python -m pip install edge-tts`), grátis e ilimitado, roda local.
Só existem duas vozes es-MX: `DaliaNeural` (feminina, a aprovada) e `JorgeNeural`
(masculina).

**Por que −6%:** medi a referência dele (`AUDIO COPY 3 7.mp3`) em 155 palavras/min; o
edge-tts sem ajuste sai a 164. O −6% iguala.

**Ele preferiu o texto cru.** Testei uma versão com reticências e pontos extras nos
pontos de respiração — ficou a 135 palavras/min e ele não escolheu essa. Não reescrever
a pontuação da copy dele.

**Depois de gerar, normalizar** em `loudnorm=I=-15:TP=-1.0:LRA=11` — é o nível dos áudios
que ele já usava. Na montagem final o `-14 LUFS` de sempre continua valendo.

## Clonagem de voz

Ele pediu para clonar a voz das locuções (as dele e a do criativo escalado da
concorrente). Recusei: não dá para saber de quem é a voz por trás, e clonar voz de pessoa
real sem consentimento é a base de golpe de identidade.

O caminho legítimo que ofereci: clonar a **própria voz dele**, com dois minutos de
gravação limpa — aí o consentimento é dele mesmo. Ou contratar locutor mexicano (Fiverr /
Workana, 20 a 50 dólares por peça de 100s).

Se a qualidade do edge-tts não bastar em algum momento: Azure Speech tem as mesmas vozes
**com controle de estilo** (`cheerful`, `empathetic`, `chat`), 500 mil caracteres grátis
por mês — é onde mora o ganho de naturalidade. Google Cloud TTS (`es-US-Studio`) é o mais
próximo do ElevenLabs, 1 milhão de caracteres grátis/mês.

Ver [[pipeline-video-ffmpeg]] e [[projeto-mercado-mexico]].
