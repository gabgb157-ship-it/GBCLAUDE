---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Pipeline de vídeo com ffmpeg
Instalado em 2026-08-08 nesta máquina (C:\, Windows 11), a pedido do Gabriel, para editar criativos de anúncio.

**ffmpeg 9.0 full build** (via `winget install Gyan.FFmpeg`):
`C:\Users\gabgb\AppData\Local\Microsoft\WinGet\Packages\Gyan.FFmpeg_Microsoft.Winget.Source_8wekyb3d8bbwe\ffmpeg-9.0-full_build\bin\`
Traz libx264/265/AV1, NVENC/AMF/QSV, libass, drawtext, xfade, zoompan — e **whisper embutido** (`--enable-whisper`), sem precisar de whisper.cpp separado.

**Modelo de transcrição:** `C:\Users\gabgb\whisper-models\ggml-small.bin` (465MB, bom p/ português). Upgrade p/ medium/large se precisar de mais precisão.

**Skills criadas em `C:\Users\gabgb\.claude\skills\`** (2026-08-08), todas testadas:
`criativo-analisar` (relatório + frames + folha de contato + mapa de estrutura) · `criativo-audio` (transcrever/normalizar/cortar-silencio + Find-Beats) · `criativo-montar` (vertical/juntar/texto) · `criativo-entregar` (pacote pro CapCut). Todas carregam `scripts\ffmpeg-lib.ps1`, cópia de `_lib\ffmpeg-lib.ps1` — **ao corrigir a lib, redistribuir para as 4**.

**Decisão combinada com o Gabriel:** não automatizar a timeline do CapCut (clique em pixel erra frame). As skills entregam material tratado, ele monta lá.

## Pegadinhas que custaram tempo (todas confirmadas na prática)

1. **Filtro whisper e caminho do Windows:** `:` dentro de string de filtro é separador de opção. `C\:/...` **não** funciona. Solução: caminho **sem letra de drive** — `model=/Users/gabgb/whisper-models/ggml-small.bin` resolve na unidade atual. Use `-WorkingDirectory` + nome relativo pro `destination=`.
2. **`$Args` é variável automática do PowerShell.** Parâmetro de função com esse nome chega sempre vazio. Renomear (ex: `$FFArgs`).
3. **PS 5.1 lê .ps1 como ANSI sem BOM** → acentos viram `DuraÃ§Ã£o`. Salvar como **UTF-8 com BOM** (`New-Object System.Text.UTF8Encoding($true)`).
4. **Nunca usar `2>&1` em exe nativo no PS 5.1** — vira ErrorRecord e mata o script mesmo com exit 0. ffmpeg escreve tudo em stderr. Usar `Start-Process -RedirectStandardError <arquivo>` e ler o arquivo.
5. **`Start-Process -ArgumentList` não cita sozinho** — argumento com espaço vira dois. Citar manualmente.

## Limite real

Claude não escuta áudio, mas **mede e vê**: `ebur128` (LUFS), `astats` (pico/clipping), `silencedetect`, `showwavespic` (batidas visíveis), `showspectrumpic` (chiado), `whisper` (fala com timestamp). O que continua humano: se a trilha combina e se o corte emociona. Ver [[gabriel-infoprodutos-pdf]] e [[pipeline-pdf-windows]].

## PowerShell não distingue maiúscula de minúscula em variável

Mordeu duas vezes no mesmo script de gráficos (25/08/2026) e é sutil porque não
dá erro — o texto sai errado em silêncio:

- `$w = $W-40` **sobrescreve** `$W`. Dentro de um bloco que desenha um card,
  isso muda a largura da tela no meio do desenho.
- `$o = NovoBmp ...` (helper que devolve hashtable) **sobrescreveu** `$O`, que
  era o caractere Ó do acento. O resultado foi `System.Collections.Hashtable`
  impresso dentro do texto do gráfico.

Terceira mordida (28/08/2026), a pior de achar: num script com
`param([string]$Saida = "...\final.mp4")`, um laço que montava filtro usou
`$saida = if (...) { "[vout]" } else { "[v$n]" }`. Isso **sobrescreveu o
parâmetro** — o ffmpeg gravou num arquivo chamado `[vout]` e o erro só apareceu
lá na frente, como `Get-MediaInfo: Arquivo não encontrado: [vout]`, três
passadas depois. O filtro estava certo; o caminho de saída é que tinha virado
rótulo de filtro.

Regra: variável de uma letra só para acento ou constante é armadilha, e
**nome de variável local nunca pode ecoar um parâmetro do `param()`**, nem com
outra caixa. Usar nomes próprios (`$acentoO`, `$cw`, `$ch`, `$bm`, `$rotulo`).

## A vírgula liga mais forte que o + dentro de @( )

```powershell
$itens = @( "CU" + $A + "NTAS", "C" + $O + "MO" )   # ERRADO
```
vira `"CU" + $A + ("NTAS","C") + $O + "MO"` — concatena array e o texto sai
corrompido. Tem que parentizar cada item:
```powershell
$itens = @( ("CU" + $A + "NTAS"), ("C" + $O + "MO") )
```
Mesma família do `+` antes de `-join` e do `-replace` com `+` no argumento.

## `-loop 1` numa PNG sem `-t` faz o encode nunca terminar

Sobrepor um badge com `-loop 1 -i selo.png` gera quadros infinitamente. Nos
criativos anteriores isso não aparecia porque o `-shortest` vinha junto do
mapeamento do áudio. Num vídeo **sem faixa de áudio** eu tirei os dois juntos —
o ffmpeg rodou até estourar o timeout e deixou um .mp4 de 106MB sem `moov atom`,
que o ffprobe recusa. Sempre `-loop 1 -t <duração> -i img.png` **e** `-shortest`.

## Expressão de filtro com `/` pode ser lida como caminho

`overlay=y='if(lt(t,47.35),1230-(t-47.0)/0.35*40,1190)'` fez o hook de segurança
tratar `/0.35*40,1190` como caminho de arquivo e bloquear a chamada. Escrever a
mesma conta só com multiplicação resolve: `(t-47.0)*114.28`.

## drawtext sem fontfile dá segfault

`ffmpeg -vf "drawtext=text='...'"` sem `fontfile=` derruba o processo com
Segmentation fault nesta máquina. Para carimbar tempo em quadro de contato,
melhor não usar drawtext — gerar os quadros na ordem e confiar na sequência.

## Conferir o frame do corte, não amostras do clipe

Em material de receita estrangeiro (TikTok/Reels em inglês), a legenda queimada aparece
e some ao longo do clipe. Amostrar 3 pontos por vídeo **não pega**: no criativo de
ensaladas (29/08/2026) essa varredura deu tudo limpo e dez cortes entraram com
`Shred up cooked`, `Cube up an avocado`, `Soy sauce`, `1/2 cup onion`,
`mozzarella cheese`, `1/4 cup mayonnaise`.

O que funciona: montar o corte mudo, extrair **um frame do meio de cada corte** (o tempo
acumulado do plano dá a posição), e olhar todos numa folha de contato. É a única
verificação que mostra exatamente o que vai ao ar.

Alguns clipes têm legenda de receita do início ao fim — nesses não adianta procurar
janela limpa, vão para a lista de proibidas.

**Nome de arquivo tambem e case-insensitive no Windows (04/09/2026).** Os planos de corte
`k_1.txt` e as listas de concat `K_1.txt` sao **o mesmo arquivo** — o `: > "$SP/K_$n.txt"`
truncou o plano antes do `while read` conseguir le-lo, e todos os blocos sairam vazios com
"Invalid data found when processing input". Usar nomes claramente distintos
(`plano01.txt` / `lista01.txt`), nunca so a caixa. E o primo do bug de `$Saida` vs
`$saida` no PowerShell, ja anotado acima.

## Página de PDF como b-roll

`pdftoppm` não existe nessa máquina. `pip install pymupdf` e renderizar direto:
`pymupdf.open(pdf)[i].get_pixmap(dpi=300).save(png)` — 300 dpi dá 2482x3510 numa A4.

**A armadilha:** A4 é 0,707 de proporção e o quadro é 0,5625. Encher a altura de 1920
estoura a largura em ~280px, e o corte centralizado **come as laterais do título**.
Não dá pra ter largura inteira e altura cheia ao mesmo tempo.

O que funciona: página inteira em ~1040 de largura por cima de um fundo feito dela mesma
com `boxblur=32:2,eq=brightness=-0.14`, mais um `zoompan` lento. Fica nítido, o título
aparece completo e o fundo não distrai.

Legenda amarela por cima cobre o terço de baixo da página — tudo bem, o que importa é
o leitor reconhecer que é documento estruturado, não ler o passo a passo.

## PNG em loop no overlay: sempre `-framerate 30`

`-framerate 1 -loop 1 -t N -i tarja.png` funciona no **primeiro** overlay da cadeia e
**falha silenciosamente do segundo em diante** — a tarja aparece uns 2 segundos depois do
`enable` e some cedo. Não dá erro, só não aparece. Passou batido em dois criativos
entregues antes de eu conferir quadro a quadro.

Usar `-framerate 30 -loop 1 -t N` em todos. E **conferir cada tarja no arquivo final**,
com `ffmpeg -i final.mp4 -ss T -vframes 1` (o `-ss` depois do `-i`, que é o preciso),
recortando a faixa onde ela deveria estar.
