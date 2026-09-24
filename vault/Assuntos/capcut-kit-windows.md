Kit em `C:\Users\gabgb\Downloads\capcut-kit-main\capcut-kit-main\` (zip veio aninhado).
Original `capcut-bridge.py` é macOS-only. Usar **`python capcut-bridge-win.py <comando>`**.
O script é GERADO: fonte em scratchpad `gerar_bridge_win.py` + `bridge_win_cabecalho.py` +
`bridge_win_comandos.py` (copia os construtores do original por número de linha).
Faixa ao vivo em `capcut_vivo.py` + `capcut_timecode.py` + `ocr.ps1` + `atalhos-capcut.json`.

**CapCut 9.4 no Windows (medido 14/09/2026):**
- rascunhos `%LOCALAPPDATA%\CapCut\User Data\Projects\com.lveditor.draft`, arquivo `draft_content.json`
- lançador `%LOCALAPPDATA%\CapCut\Apps\CapCut.exe`; `Path.read_text` sem encoding quebra acento
- **UI Automation só vê a janela raiz (`HomeWindow`)** — não dá pra achar botão por nome como no Mac
- **PrintWindow(flag 2) captura a janela** (o screenshot comum/computer-use vem preto ou mascarado)
- **OCR do Windows (Windows.Media.Ocr, pt-BR) lê a UI, mas NÃO lê linha só de números** →
  leitor próprio de timecode por forma dos dígitos, treinado na tela: 12/12 certos
- ClearType: haste do "1" vira coluna azul (30,120,177) + verde (3,147,100); dígitos colados ("21") viram um glifo só
- **tabela de atalhos usa os MESMOS nomes internos do kit Mac** (cutoff, del, exportVideo...).
  `Config/keymapSettings` currentKeymapIndex=0 = tabela "Final Cut Pro X" (Ctrl+E exporta, Ctrl+B divide)
- Home=0, Right=1 quadro, Shift+Right=10 quadros — sem perda de passo
- janela de exportar é top-level separada, título `Exportar-<nome>`; tela final tem Compartilhar
  (NUNCA clicar) e **Fechar**; arquivo cai em `Downloads\CRIATIVOS PAREDE DE RESINA ATUALIZADOS\`
- CapCut ignora fechar normal na tela inicial → script força em 30s
- legenda: `y` negativo = baixo (legendas dele em y=-0.56); itálico = `italic_degree: 10`

**RESOLVIDO (15/09/2026): o travamento na exportação era a FONTE.** Texto com a Inter
(instalada em %LOCALAPPDATA%\Microsoft\Windows\Fonts) trava em 30%; texto com
`Apps/<versão>/Resources/Font/SystemFont/en.ttf` do próprio CapCut exporta em 20s. `montar`
usa essa fonte por padrão. Arial Black (C:\Windows\Fonts) ainda não testada.

**Pipeline provado de ponta a ponta:** `montar COPY2_HOOKB_CAPCUT` (18 clipes + voz + 34 legendas +
tarja + card CTA) abriu no CapCut e exportou em 25s pelo `exportar()`.

**Abrir rascunho que não aparece na tela:** com o CapCut FECHADO, mover a entrada pro índice 0 do
`root_meta_info.json` e atualizar `tm_draft_modified`; ao abrir ele vira a 1ª miniatura
(duplo clique em "Projetos".x0+80, cy+90). Roda do mouse e busca pela lupa não funcionaram.

**Pendências achadas no vídeo exportado:**
- saiu em **HEVC** (os dois testes anteriores saíram H.264) — forçar H.264 no diálogo
- voz a **−27 LUFS** — normalizar o áudio pra −14 antes de pôr no rascunho
- legenda de uma linha longa (ex. "NÍVEL DE DIFICULDADE") vaza pelas bordas — ajustar tamanho pelo comprimento
- tarja saiu como texto com contorno, não caixa sólida — usar campos de fundo do texto
- `_nome_no_editor` falha no OCR com underline; o título da janela/painel mostra o nome certo

**Achados no V020 (15/09/2026):**
- **ÁUDIO MUDO:** o modelo `audio-material.json` veio do "Mouse click sound" (effect_id/app_id da
  biblioteca) → o CapCut tocava o clique de 0,2s no lugar do arquivo. `_audio` agora grava como
  `extract_music` / `local_music` (corrigido no bridge e no gerador). O "-27 LUFS" antigo era isso.
- aviso "CapCut Pro" abre como janela separada: PrintWindow NÃO mostra, mas bloqueia clique →
  conferir com `ImageGrab` (tela real) e fechar com Esc/X (`abrir_primeiro.py` faz isso)
- clipe com `escala` + `zoom` juntos: o keyframe de zoom sobrescreve a escala e abre faixa preta
- legenda com Arial Black (C:\Windows\Fonts) → a exportação seguinte não gerou arquivo; suspeita de
  fonte do sistema ser recurso Pro. Gabriel decidiu assinar o Pro (15/09/2026).
- exporta em HEVC → converter pra H.264 no ffmpeg na entrega

**Tela dividida no `montar` (V021, 15/09/2026) — funcionou e exportou em 34s:**
- clipe/camada com `"y"`: unidade = meia tela (0.5 = painel de cima, -0.5 = painel de baixo); clipe
  1080x960 entra "ajustado" e ocupa exatamente o painel
- camada com `"nivel"` (trilha por cima) e `"inicio"`; `"nivel_flash"` no plano; `"musica"` e `"sons"`
  (cada efeito é segmento próprio, com `de`/`duracao` pra pular silêncio do arquivo)
- áudio importado tem que ser `extract_music` + categoria `local` (igual rascunho 0627); `local_music`
  = "Extrair áudio" = recurso Pro que trava a exportação
- baixar música/efeito da biblioteca: `baixar_sons.py` (busca no painel Áudio e anota o arquivo do cache)
- exportação sai 1440x2560 HEVC → converter pra 1080x1920 H.264 na entrega

**V024 (18/09/2026):**
- texto com palavra de outra cor: `"destaques": [[ini, fim], ...]` (índices de caractere) + `"destaque_cor"`
  → o kit parte `styles[]` em faixas; exportou certo (legenda branca com a palavra-chave amarela)
- `line_max_width` NÃO quebra a linha sozinho: legenda longa vaza → medir na Arial Black e dividir antes
- `abrir_primeiro` falha se o app do Claude estiver na frente: repetir o duplo clique até 3x, conferindo `no_editor()`
- lipsync gerado do MP3: o áudio do vídeo é o MP3 adiantado ~38 ms — cortar os dois no mesmo quadro e usar o MP3
- `baixar_sons.py` serve também pra MÚSICA (seção Música do painel Áudio; `consulta@idx`, `@?` só lista)

Gabriel recusou acesso computer-use ao `capcut.exe` — não pedir de novo; e não mexer no mouse com ele usando o PC.

Ver [[pipeline-video-ffmpeg]].
