---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Pipeline de produção de PDF no Windows
Pipeline que funciona nesta máquina (C:\, Windows 11, sem node/npm/python/pandoc/poppler/imagemagick):

1. **Montar o conteúdo em HTML/CSS** (A4: `.page{width:210mm;height:297mm}`, `@page{size:A4;margin:0}`, `print-color-adjust:exact`). Fontes via Google Fonts (Archivo Black + Oswald + Barlow). Imagens referenciadas por caminho `file:///C:/...` absoluto.
2. **Gerar o PDF de verdade com Chrome headless:**
   `& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless=new --disable-gpu --no-pdf-header-footer --run-all-compositor-stages-before-draw --virtual-time-budget=18000 --print-to-pdf="saida.pdf" "file:///C:/.../arquivo.html"` (os erros de GCM no stderr são inofensivos).
3. **Verificar renderizando o PDF de volta em PNG** via WinRT `Windows.Data.Pdf.PdfDocument` no PowerShell (Add-Type System.Runtime.WindowsRuntime; helpers AsTask para IAsyncOperation e IAsyncAction; `RenderToStreamAsync` com `PdfPageRenderOptions.DestinationHeight`). `$page.Close()` não existe — ignorar esse erro.

**Fotos:** usar a API do **Pexels** (`https://api.pexels.com/v1/search?query=...&orientation=...`, header `Authorization: <chave>`; baixar `src.large2x`). Gabriel tem uma chave pessoal gratuita do Pexels (pedir a ele; não fica salva aqui). Openverse (sem chave) funciona mas é limitado por Cloudflare (429) e qualidade mediana — evitar. Truque útil: montar um "contact sheet" HTML com os candidatos e capturar com `chrome --headless --screenshot` pra escolher rápido.

Ler .docx sem ferramentas: copiar para .zip, `Expand-Archive`, ler `word/document.xml` com `[System.IO.File]::ReadAllText(path,[Text.Encoding]::UTF8)`. Ver [[projeto-cha-seca-barriga]].
