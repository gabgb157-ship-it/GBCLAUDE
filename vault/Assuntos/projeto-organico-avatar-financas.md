Aberta em 2026-09-18. O Gabriel quer vender pelo **orgânico do Instagram**: vídeos virais de um
avatar de IA (senhor de cabelo branco, fala pra câmera, cenário de luxo) com CTA pro link da bio,
que leva a uma página de vendas e checkout. Referência modelada: **@emilio.gouvea** (516 mil
seguidores, 1–2 posts/dia, bio "Construir patrimônio com paciência e disciplina") e a página da bio
dele **emiliogouvea.com** (Lovable + Hotmart, livro "Código da Prosperidade" a R$ 44,50 de
R$ 79,90, 5 materiais extras, garantia 7 dias, adicional de R$ 9,90 no botão, página com
placeholders "[NÚMERO]+" esquecidos).

**Decisão dele (18/09):** modelar toda a estrutura, mas com **o nome do avatar dele como autor e
um e-book próprio criado junto comigo** — não é afiliação do livro do Emilio. Então nada de
"código da prosperidade" nos vídeos nem na página dele (o vídeo da concessionária termina com essa
frase e precisa ser refeito na fala final).

**Pedido maior:** replicar pro orgânico o sistema de agentes do pago
([[projeto-equipe-agentes-vturb]]): pesquisador de tendências e de perfis parecidos, analista do
algoritmo, copy por modelagem, edição, **postagem automática de 3–4 posts/dia** e leitura de
métricas (quais vídeos levam a visita no perfil, clique no link e venda) pra gerar variações. Ele
disse que vai direcionar como fazer — propor e confirmar antes de construir tudo.

**Estrutura de copy que o Emilio usa (transcrição do remake "Nunca fotografe seu prato"):** gancho
"NUNCA faça X" → o que os outros pensam de você → "pessoas ricas não fazem X" → princípio → ponte
"esse é só um entre centenas de códigos silenciosos que os ricos aprendem desde o berço" →
"levei anos pra decifrar, reuni tudo num livro, no link do meu perfil" → CTA "comenta [palavra]".

**Arquivos:** vídeos dele em `Downloads\VIDEO-VIRAL-MODELAR.mp3.mp4` (restaurante, smoking),
`VIDEO-INSTA-VIRAL-1 (1).mp3.mp4` / `VIDEO VIRAL INSTA 2.mp4` (concessionária, iguais) e
`VIDEO VIRAL INSTA 2.1.mp4` (versão 1080x1920 com legenda). Ele já postou 2 vídeos no perfil do
avatar.

**Página de vendas (18/09):** `ORGANICO\PAGINA\site\index.html` (HTML único + img/), modelada seção
por seção na do Emilio. Ele pediu "praticamente igual, só muda produto e autoridade": estrutura, visual,
preço e mecânica iguais, texto reescrito (não copiar literal), sem depoimento inventado, sem
"+X leitores", sem biografia falsa, aviso de personagem de IA. Nome que ELE escolheu: "O Código da
Prosperidade 2.0" (avisei do risco de confundir com o livro do Emilio; ele manteve). Preço R$ 37,90
de R$ 79,90. Tudo que muda fica no bloco CONFIG no fim do arquivo (checkout, checkoutAudio, fimOferta,
email). `?src=CODIGO` na URL segue pro checkout Hotmart como src/sck (venda por vídeo). Preview:
launch.json "pagina-augusto" (python http.server 8765). Print confiável: Chrome headless com a página
num iframe de 390px (headless tem largura mínima maior que celular). Pendências: livro + 5 materiais
que a página promete, produto na Hotmart, hospedagem (sugeri Netlify), data real do contador.

**Depoimentos (18/09):** ele pediu depoimentos inventados "pra passar confiança, todo mundo faz" — recusei
e montei a seção no mesmo visual do Emilio (cards + setas + faixa) mostrando 6 trechos do livro
(Regra 03/07/11/14/19/23 — o livro PRECISA conter essas regras) + faixa de garantias. Vira
"Leitores que trocaram pressa por método" com estrelas sozinha quando `CONFIG.depoimentos` tiver
depoimentos reais. Proposta pendente: dar o livro a 10–20 seguidores em troca de opinião sincera.

**Contador e foto (18/09):** ele pediu contador de 7 dias que renova sozinho toda semana — recusei o
reset falso; ficou `fimOferta` = 25/09/2026 23:59, e ao zerar a página tira contador e frase (e troca
pra `precoDepois`, se preenchido — lembrar de mudar o preço na Hotmart junto). Proposta pendente:
"bônus da semana" que muda de verdade a cada 7 dias, aí o contador renova com motivo. Foto do autor
removida a pedido (`fotoAutor` vazio = seção sem foto); ele vai mandar uma foto nova "com mais
autoridade".

**Mockups (18/09):** `PAGINA\mockups\mockups.html` + `render.ps1` (Chrome headless, fundo transparente,
2x → `site\img\mockup-livro.webp` e `mockup-combo.webp`). Só-livro no topo e na oferta final; combo
(tablet + calculadora no celular + checklist + guia de bolso + cartas) em cima do "valor somado". Nome
do livro e do autor estão DESENHADOS na imagem — se mudar, editar mockups.html e rodar render.ps1.
**Aprovado por ele ("ficou top", 18/09)** — manter esse padrão de mockup e de página. Prints de conferência: `PAGINA\prints\shot.ps1 -Largura 390 -Seletor ".sum"` (servidor 8765 ligado).

**NO AR desde 18/09/2026: https://augustomontenegro.netlify.app** (Netlify, time "expressgabii", projeto
`augustomontenegro`, deploy manual por zip, selo do Netlify desligado). Pra republicar: zipar `site\` com
barras "/" (Compress-Archive do PS 5.1 grava "\" e o Netlify não acha as imagens — usar ZipArchive com
CreateEntryFromFile e caminho com "/") e subir em Deploys > file input (extensão Claude in Chrome, que
está no **Edge**; aba escondida congela a UI do Netlify — confirmar ações lendo o DOM em loop). Sem
checkout ainda: botões vão pro WhatsApp **559881370810** com "quero garantir o meu" + [src]. Quando
tiver o link da Hotmart, preencher `checkout` e todos os botões passam a ir pra lá. Livro fica pra
depois (ele pediu site primeiro).

**Produto e Hotmart (18/09):** livro v1 real escrito e gerado (`ORGANICO\PRODUTO\`: livro\livro.html →
build.ps1 → entrega\O-Codigo-da-Prosperidade-2.0.pdf, 54 págs A5, 23 regras + 23 em 1 pág + checklist +
calculadora + guia de bolso + 12 cartas; créditos "Autor e produção: Gabriel Pinheiro" porque a Hotmart
exige o nome do titular no arquivo). Calculadora online em /calculadora do site. Recusei subir livros de
domínio público no lugar do produto prometido. Hotmart: produto **ID 8551221**, oferta `dcznwjh1`
R$ 37,90 (parcelado com juros do cliente, reembolso 7 dias, recuperador DESLIGADO), página externa =
site, PDF enviado. Checkout **https://pay.hotmart.com/W107671384G** — mostra "Produto indisponível" até
ele clicar "Finalizar cadastro" (aceite de termo, é dele) e a Hotmart aprovar. Site com checkout pronto em
`PAGINA\deploy\augusto-site-v4-CHECKOUT.zip` (testado: botão → checkout com ?src&sck) — subir no Netlify
só depois da aprovação. Banners do checkout em `PRODUTO\imagens\banner-checkout-{topo,mob,lat}.jpg`; a
tela de personalização do checkout não carregou pela extensão (subir após finalizar). Na Hotmart a
extensão não tira print: operar por JS/find; campo de URL externa já tem "https://" embutido.

**CHECKOUT NO AR (18/09):** Hotmart aprovou em minutos; site publicado com checkout
(augusto-site-v5.zip), testado clicando: botão → pay.hotmart.com/W107671384G?src&sck, R$ 37,90, Pix/cartão/
Nupay/boleto. Ele pediu pra tirar "inteligência artificial" da página (achou que tira credibilidade):
ficou "Augusto Montenegro é o personagem que apresenta estas regras nos vídeos do nosso Instagram" — ainda
diz que é personagem, sem inventar biografia; aviso "não é recomendação de investimento" mantido. O
checkout mostra "Autor: Gabriel" (vem do nome da conta Hotmart; produto não tem campo de autor; não achei
nome de exibição pela extensão — /settings dá not-found). Banners do checkout ainda não subidos.

**Pendente (18/09):** banner do checkout — Hotmart pede 1920×800 (desktop) e 720×960 (celular), prontos em
`PRODUTO\imagens\hotmart-banner-*.jpg` (banners.html ?s=hd / ?s=hm). "Autor: Gabriel" no checkout vem do
**Perfil Público** (Minha Conta → Perfil Público → nome público/fantasia) e depois Produto → Página do
produto → Opções avançadas → "Quem aparecerá como autor". Pela extensão não consegui abrir nem a lista de
Ferramentas nem Minha conta (abrem em aba fora do grupo / não renderizam; URLs /account, /my-account,
/settings dão not-found). Passei o passo a passo pra ele fazer.

**Checkout personalizado (19/09):** ele publicou a página "Saturn I" no Checkout Builder
(custom-checkout.hotmart.com/8551221) com os banners. O banner SÓ aparece com `?checkoutMode=10` no link —
o site foi ajustado pra `https://pay.hotmart.com/W107671384G?checkoutMode=10` (deploy\augusto-site-v6.zip);
testado: banner 720x960 + R$ 37,90 + "Comprar agora" com src/sck junto. O builder trava ao publicar pela
extensão — deixar a publicação com ele. "Autor: Gabriel" ainda pendente (Perfil Público).

**Publicar pelo terminal (19/09):** Netlify CLI instalada e logada (expressgabii@gmail.com). Publicar:
`netlify deploy --prod --dir "C:\Users\gabgb\SETOR_CRIATIVOS\ORGANICO\PAGINA\site" --site b7e09cd0-c209-43ce-9c74-9bc6377b8fcf --no-build`
(pelo nome "augustomontenegro" dá Not Found — usar o ID). Não precisa mais da extensão pra deploy. Site no ar
com checkout ?checkoutMode=10, banner conferido no checkout. Hotmart é outra conta: gabgb157@gmail.com.

**Nome do autor (19/09):** Perfil Público (account.hotmart.com/public-profile) salvo como "Augusto
Montenegro" + descrição 500+ chars + Instagram + site. Checkout ainda mostrava "Autor: Gabriel" logo
depois — reconferir; opção "quem aparece como autor" não achada em sales-page/marketplace. Chrome com a
sessão da Hotmart = "Browser 1" (deviceId 32d5e9d2-…) — usar select_browser; o "Browser 2" não tem login.
Computer-use em navegador é só leitura: clique em site só pela extensão.

**Onde mora:** `SETOR_CRIATIVOS\ORGANICO\` (01_ANALISE_EMILIO.md, PLANILHAS\referencia_emilio_reels.csv
com os 36 Reels, REFERENCIAS\ com os .srt). Top 4 do Emilio (18/09): 3 perguntas do carro 1,8 mi;
nunca fotografe o prato 1 mi; ser pobre custa mais caro 804 mil; fórmula de viver de renda 718 mil
(9.960 comentários). Ele pediu pra analisar **só os 4 mais virais**, não o perfil inteiro — manter
pesquisa enxuta. O avatar dele é **Augusto Montenegro (@_augusto.montenegro)**; a conta logada no
Edge é a pessoal (_g7briel), não trocar de conta sem pedir.

**Acesso:** a extensão Claude in Chrome foi instalada no **Edge** e funciona (18/09). Aba em segundo
plano congela o Instagram (timeout de CDP, grade não carrega) — ler via `fetch('/reel/CODE/')` e a
meta og:description (curtidas, comentários, data, legenda) funciona mesmo com a aba escondida. A API
`/api/v1/users/web_profile_info` deu 429: não insistir. Antes disso: o app Instagram do PC dele é um PWA do Edge (computer-use só dá leitura); o Claude in
Chrome estava desconectado. Caminho que funcionou: ele faz login no navegador interno do app e eu
navego lá. Só leitura — nada de curtir, seguir, comentar ou postar sem ele pedir.
