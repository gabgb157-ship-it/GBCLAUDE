---
tags: [project, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Skills de vídeo instaladas
Em **25/08/2026** instalei duas coleções de skills de vídeo pedidas pelo Gabriel:

- **video-use** (browser-use) — clonada em `C:\Users\gabgb\Developer\video-use`
- **hyperframes** (HeyGen) — clonada em `C:\Users\gabgb\Developer\hyperframes`, CLI via `npx hyperframes` (v0.8.14)

As duas foram registradas em `~/.claude/skills/` por **junção de diretório**
(`New-Item -ItemType Junction` no PowerShell — o `mklink /J` pelo Git Bash mangla
o caminho). Junção em vez de cópia: `git pull` no repo atualiza a skill sozinho.

A máquina **não tinha Python nem Node** — o `python` do PATH era só o atalho da
Microsoft Store. Instalei via winget: `Python.Python.3.12` e `OpenJS.NodeJS.LTS`
(24.19). O ffmpeg 9.0 que já existia atende os dois.

**video-use quer uma chave da ElevenLabs** em `.env` na raiz do repo, pro Scribe.
Eu não digito chave de API — e nem precisa: o Whisper local
(`criativo-audio\scripts\transcrever.ps1`, modelo `ggml-small.bin`) transcreve
espanhol bem o suficiente pra cronometrar corte.

Ver [[pipeline-video-ffmpeg]].

## O render do hyperframes NÃO roda nesta máquina

Testado em 25/08/2026. A composição passa em `lint`, `check` (contraste WCAG AA
inclusive) e `snapshot` — só o **render** falha: trava no meio da captura com
*"Sequential drawElement capture stalled: no frame progress for 60000ms"*.

Causa: a máquina tem **7,5 GB de RAM com ~0,5 GB livre**. O `doctor` avisa
("Low memory — renders may fail"). O modo de baixa memória já entra sozinho
abaixo de 8 GB (1 worker, captura por screenshot) e mesmo assim não segura.

O Gabriel tem **outra máquina com 16 GB** — é lá que o hyperframes deve rodar.

Nesta máquina, overlay animado sai pelo **pipeline ffmpeg + System.Drawing**
(gerar PNG, compor com `overlay` + `fade` de alpha). Foi assim que saíram o
botão de CTA e o selo de preço dos criativos do México.

Flags que valem tentar na máquina de 16 GB se ainda engasgar:
`--format png-sequence`, `--no-browser-gpu`, `--protocol-timeout`.

## Plugin Remotion (14/09/2026)

Instalado a pedido dele: `remotion@remotion` v4.0.524, escopo user, marketplace
`remotion-dev/claude-code-plugin`. Traz 12 skills (remotion-create, -render, -captions,
-studio, -markup, -multimedia etc.). O Node 24.19 já atende.

- O `claude` **não está no PATH**. O binário do app fica em
  `C:\Users\gabgb\AppData\Roaming\Claude\claude-code\<versão>\claude.exe` (achei pelo processo).
- O `plugin install` clona por **SSH** e falha ("Host key verification failed"). Sem mexer no
  git global, rodar com `GIT_CONFIG_COUNT=1 GIT_CONFIG_KEY_0=url.https://github.com/.insteadOf
  GIT_CONFIG_VALUE_0=git@github.com:` na frente. O `marketplace add` já cai sozinho pro HTTPS.
- Render do Remotion também usa Chrome headless: pode engasgar nos 7,5 GB desta máquina,
  igual o hyperframes. Testar aqui, mas a de 16 GB é a aposta segura.
