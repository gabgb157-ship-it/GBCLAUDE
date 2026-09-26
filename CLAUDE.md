# Cérebro do Gabriel

Memória de longo prazo do Gabriel para o Claude. Resume as 25 notas do vault do Obsidian
(cópia integral em `vault/Assuntos/`). Para parâmetros, filtros ffmpeg, endpoints e caminhos exatos,
abrir a nota original: `vault/Assuntos/<nome>.md` (o nome aparece entre crases em cada seção).

---

## 1. Quem é o Gabriel e como trabalhar com ele

- Infoprodutor: vende **e-books em PDF** (receitas, protocolos de saúde natural, renda extra) com **tráfego pago**
  e **venda 1:1 no WhatsApp (X1)**. Mercados **Brasil** e **México**. Começando também no **orgânico do Instagram**.
- Fala português do Brasil, informal. **Dita por voz**: termos técnicos chegam embaralhados
  ("Fish Cliente" = subagentes). Na dúvida, confirmar em vez de adivinhar.
- Descreve o conteúdo + um "prompt de design" e quer o PDF pronto. **Revisa uma peça por vez** antes de seguir.
- Modelo de negócio: MVP primeiro; se vender, compra o conteúdo pago e enriquece **mantendo estrutura e design**.
- PC: Windows 11, usuário `C:\Users\gabgb\`, Ryzen 5600H, **7,5 GB de RAM (~0,5 GB livre)**. Tem outra máquina com 16 GB.
  Operação em `C:\Users\gabgb\SETOR_CRIATIVOS\` (DIRETRIZ, PLANILHAS, OFERTAS, ANALISES, LABORATORIO, TAKES, CONHECIMENTO, ORGANICO).
- Contas: Netlify/Claude = expressgabii@gmail.com · Hotmart = gabgb157@gmail.com.

### Limites que ele definiu (não pedir de novo)
- **Não pedir computer-use no `capcut.exe`** e não mexer no mouse enquanto ele usa o PC.
- Navegador com agente: silenciar e pausar vídeos, fechar abas no fim, confirmar antes de pesquisar enquanto ele usa o PC.
- Instagram/sites: **só leitura** (não curtir, seguir, comentar, postar) sem pedido. Não trocar de conta logada.
- Claude **não digita senha nem chave de API**; ele loga. Pexels: pedir a chave a ele.

### Regras éticas já aplicadas (manter)
- **Antes de anunciar qualquer produto, conferir de quem é o PDF** (capa, página de direitos, metadados).
  Casos: mármore (PDF do Paulo Pintor — ele diz ter autorização; pedir por escrito), apostila "salgados de maria" (recusado traduzir).
- Sem depoimento inventado, sem contador falso que reseta, sem biografia falsa, sem "+X leitores".
- **Não clonar voz de terceiros.** Alternativas: clonar a própria voz dele ou contratar locutor.
- Não escrever "COMO REVERTER" em tarja de saúde. Compliance da Meta (seção 3).
- Ao modelar concorrente, **conferir dados bancários** (a chave Pix do concorrente já foi parar no funil).

### Respostas em áudio — `conversa-em-audio`
- Ele → Claude: .opus/.ogg/.mp3 transcritos com Whisper local (`criativo-audio\scripts\transcrever.ps1`).
- Claude → ele: resumo em mp3 com edge-tts `pt-BR-AntonioNeural --rate="+4%"`, em `SETOR_CRIATIVOS\AUDIOS\`
  (.txt + .mp3 com data). Voz ainda não escolhida (alternativas: FranciscaNeural, ThalitaMultilingualNeural).
- Áudio = resumo e decisão. **Copy, tabelas e planilhas continuam em texto.** Roteiro falado: frases curtas,
  sem siglas, sem tabela, sem travessão. 200 palavras ≈ 1min30.

---

## 2. Sistema de agentes (equipe no lugar de funcionários) — `projeto-equipe-agentes-vturb`

- Montado em 11–12/09/2026. Agentes em `C:\Users\gabgb\.claude\agents\`, rotina na skill `setor-criativos`.
  **Heitor = sessão principal (chefe, despacha)**; subagente não chama subagente.
- Equipe (23): Heitor (chefe) · Paula (pesquisa) · Dora · Sofia · Bia · Marcos · Angela · Gil · Vera · Caio (copy) ·
  Rita (revisão) · Edu (edição) · Otavio · Zeca (x1-conversa) · Dani (x1-diagnóstico-lead) · Olivia (x1-objeções) ·
  Fabio (x1-fechamento) · Rui (x1-followup) · Cris · Teo · Ana (análise) · Lucas (lucro-capital) · Lia/Léo/Luna (lentes copy/edição/cena).
- Base de conhecimento: podcast **VTurb – Segredos da Escala** (P1 Matheus Lorenzo set/2026 = atual; P2 Thiago Filamon
  mar/2025 = antigo, usar só o que vale pós-Andrômeda; P3 Diogo Kobata #059) + livros (Hopkins, Halbert, Hormozi, Kennedy,
  Whitman, Schwartz, Masterson, Sugarman, Cialdini). Arquivos em `SETOR_CRIATIVOS\CONHECIMENTO\` (01 a 06).
  Hierarquia de fontes: podcast > estrutura do nosso X1 > dados das campanhas > livros > outros. Livro nunca apaga método do podcast.
- Prioridade: **X1 com ticket baixo**. VSL, sales page, advertorial, e-mail e backend são "future module".
- Legenda do YouTube é atalho para transcrever: `python -m yt_dlp --skip-download --write-auto-subs --sub-langs pt`.

### Regras supremas do sistema
1. **LUCRO LÍQUIDO manda.** Lucro > ROAS/CPA/margem > conversão no X1 > qualidade do lead > criativo > métricas
   intermediárias (CTR, CPM, hook, hold = diagnóstico, nunca vitória).
2. **Classificação obrigatória:** tudo é FATO, RESULTADO VALIDADO, INFERÊNCIA, HIPÓTESE ou IDEIA PARA TESTE, com origem.
   Dado de terceiro nunca vira fato nosso. Relatório fecha em: o que sabemos / o que acreditamos / o que precisamos testar.
3. **Formato de toda entrega a ele (10 itens):** situação, diagnóstico, fatos, hipóteses, riscos, opções, recomendação,
   próxima ação, responsável, métrica de sucesso/fracasso. O papel dele é direção, decisão, capital, aprovação, escala.
4. Verba (Lucas): entrar com 1 ticket/dia, subir +50% (nunca dobrar), reduzir antes de matar, encerrar com 2 tickets sem venda.
   Retorno futuro nunca é garantia (projeção em faixa, com premissa).

### Realidade da operação
- Atendimento no WhatsApp é **automático** (capacidade não é gargalo). **Gargalo = queda de chip** (campanha religada perde aprendizado).
  Quer migrar para **API oficial**.
- "Compras" no Gerenciador = venda paga (etiqueta do comprovante dispara o evento). Margem fina (~R$3/venda).

### Pane conhecida — `agentes-somem-do-registro`
- "Agent type 'x' not found" com arquivo intacto: **Read do arquivo inteiro + Write com o mesmo conteúdo pela ferramenta Write**.
  Reescrever pelo Bash/python não resolve.

---

## 3. Método de teste de oferta (toda oferta nova) — `metodo-teste-oferta-15min`

- Tese: com o Andrômeda, **o criativo é o público** — a Meta segmenta lendo Ad Text, áudio e cena. Estático voltou a escalar.
- **Hook visual** só para o polegar. **Ad Text** conscientiza, converte e segmenta: hook 10% · body 75% · CTA 15%.
  Regra das duas linhas no "ver mais". **Mecanismo é obrigatório.**
- Diagnóstico: CTR/CPM ruim → imagem · expansão baixa → 1ª linha · CTR de link baixo com CTR total alto → body/CTA ·
  sem entrega nem clique → oferta/ângulo. **Nunca trocar imagem e texto ao mesmo tempo.**
- 3 avatares = 3 públicos: Autoridade · Transformado · Visualizador (compra para outra pessoa, CPM mais barato).
  Ordem: estudo de público → avatares → Ad Text.
- Hook visual: quanto menos parecer anúncio, melhor. Teste do polegar.
- Campanha de teste: **ABO**, 1 criativo por conjunto, verba diária = 1 ticket, público aberto, não mexer por 24h.
  Matriz 10 hooks × 3 textos (mínimo 6 × 2). Nome `[OFERTA]_[DATA]_TESTE_AT[n]-[avatar]_H[n]-[formato]`.
- Régua 24h: ½ ticket sem venda mata · 2 tickets e 1 venda mata · sem venda mas CTR alto → separar e recombinar.
  Ler **por peça**, não por combinação. Vencedor vira 5 variações, uma variável por vez.
- Estático é laboratório: o que vence vira vídeo (hook visual = 3s iniciais, hook do texto = 1ª fala, body = roteiro).
- **Compliance:** tirar o "você" de frase com condição; nunca prometer resultado/prazo/cura; sem antes/depois agressivo;
  promessa do CTA visível no topo da página.
- Teste inteiro sem venda e sem CTR → problema é oferta, preço ou página.

### Aprendizados do Diogo Kobata — `Podcast Kobata`
- Oferta não satura, **fatia de público satura** (trocar a persona reabre o lago).
- Matriz persona × curiosidade × situação do dia a dia; metade da leva recombina o validado, metade nova.
- Gancho segmenta (humor e polêmica); **frase de ligação** após o gancho junta personas no mesmo corpo.
- CTA CVI (curiosidade, valor, indireto) + 2º CTA direto. Julgar criativo pela **receita**, não pelo CPA.
- Lateralizar vencedor barato (texto, título, banner, stop scroll, gancho novo). Upsell ÷ ticket: 20% ruim, 35–40% bom.
- **Nossa regra: no máximo 3 ganchos por corpo, nunca 1.** Polêmica só contra mercado/método/situação, em 1ª pessoa. Nada de corte de vídeo de terceiros.

---

## 4. Ofertas e projetos

### Oferta Pudim — Método Pudim Sem Fogo (ATIVA) — `Oferta Pudim`
- X1 revivida em set/2026. Histórico: 7.123 vendas, R$50.911 gastos, CPA R$7,04, custo/conversa R$1,90, conversa→venda 27%.
  Vende **renda** (fazer e vender pudim), não receita. Personagem **Gabi Silva**. Pasta `SETOR_CRIATIVOS\OFERTAS\pudim\`.
- Números: CPA alvo ~R$5,91; ruína ~R$9,19. Escada R$9,90 · 14,90 · 19,90. Chip R$15, instância Leona R$97, imposto 13% sobre mídia.
- Funil rodando: **Leona 4.0 (flow 124558)** — entrega só receitas + aulas; Precificação, Como Vender e bônus após pagamento;
  remarketing com sorteio; upsell 1 em vídeo (R$12,90) e upsell 2 (R$15,90). 3.0 = flow 124207 (validado, fallback).
- Tráfego (22/09): conta **P 3DOLAR**, **1x1 CBO** — 9 campanhas × 1 conjunto × 1 anúncio, US$4/dia, compra por mensagem,
  Brasil, idade mín. 25 (mulheres 30+). Custo por venda US$0,51–1,81 depois de corrigir o texto (era de "Recheios Sem Fogo").
- Criativos validados: CVP01 (não gastar gás, 1:30) e CVP02 (70 pudins, 1:17); duração que escala 1:20–1:40.
  Leva 02 = V020–V024. Leva 03 = V025–V030 (personas mãe, aposentada, doceira, casada, CLT; 3 ganchos por corpo; 3 ondas).
  **Leva 04 (23/09) = avatar de IA**: V031 podcast, V032 UGC fone, V033 carro (`levas/LEVA_04_PROMPTS_E_COPY.md`).
  Áudio e lip sync ficam com o Gabriel. **V033 carro v1 editado em 24/09** (71,5 s, voz ElevenLabs + lip sync,
  motion "notificação de celular": pedidos chegando, checklist, contador 30→100, chat do WhatsApp, etiqueta R$ 9,90,
  botão "CHAMA NO ZAP"). **v2 com efeitos sonoros sintetizados** (whoosh nas 10 trocas avatar↔b-roll, pop, ding,
  tick, cha-ching no preço, clique no CTA). **v3 com música** (arquivo dele "videoplayback (7).mp3", do YouTube):
  estouro aos 0s, parte calma na tristeza, 2º estouro exatamente na virada (17,3s); música ~14 dB abaixo da voz.
- **V032 UGC fone v1 editado em 25/09** (77,5 s = 71,5 s de fala + 6 s de cartela com 3 setas): mesmo MP3 do V033,
  na pegada da referência que escalou (legenda curta itálica, prova em janela no topo, carimbo ESGOTADO,
  "vai ter de novo?" chegando, botão laranja com cursor clicando, cartela final "CLIQUE NO BOTÃO ABAIXO"). Sem música ainda.
- Música já usada na leva 04: "videoplayback (7).mp3" (V033) — não repetir.
- Pendências: preço do potinho (gancho V027A); narradoras por persona; prêmio do sorteio (microondas vs "super kit com batedeira").

### Orgânico — avatar de finanças Augusto Montenegro — `projeto-organico-avatar-financas`
- Desde 18/09/2026. Avatar de IA (senhor grisalho, cenário de luxo) no Instagram **@_augusto.montenegro**, modelando
  **@emilio.gouvea**. Estrutura de copy: "NUNCA faça X" → o que pensam de você → "ricos não fazem X" → princípio →
  "um entre centenas de códigos" → "reuni num livro, link do perfil" → "comenta [palavra]".
- Produto próprio: **"O Código da Prosperidade 2.0"**, R$37,90 (de R$79,90), PDF 54 págs A5 com 23 regras + extras.
  Hotmart ID **8551221**, checkout `pay.hotmart.com/W107671384G?checkoutMode=10` (o banner só aparece com esse parâmetro).
- Site no ar: **https://augustomontenegro.netlify.app**. Publicar:
  `netlify deploy --prod --dir "C:\Users\gabgb\SETOR_CRIATIVOS\ORGANICO\PAGINA\site" --site b7e09cd0-c209-43ce-9c74-9bc6377b8fcf --no-build`.
  Tudo que muda fica no bloco CONFIG do `index.html`. `?src=CODIGO` segue para a Hotmart (src/sck).
- Página diz que Augusto é personagem (sem citar "IA", a pedido); aviso "não é recomendação de investimento" mantido.
- Pendências: "Autor: Gabriel" no checkout (Perfil Público já como Augusto — reconferir); depoimentos reais
  (proposta: dar o livro a 10–20 seguidores); "bônus da semana" real para justificar contador; foto nova do autor.
- Próximo passo pedido: replicar o sistema de agentes para o orgânico (tendências, algoritmo, copy, edição,
  **postagem automática 3–4/dia**, métricas). **Propor e confirmar com ele antes de construir.**

### Criativo de salgados v6 — `criativo-salgados-v6`
- Reels para a apostila de salgados (R$10,90, bônus congelamento, CTA WhatsApp). Base boa: `Downloads\CRIATIVO_NOVO_v4.mp4`.
- Pendente: som ancorado na transcrição (~14 pontos); trocar planos com `@ArmandoFelipeReceitas`; cena caseira em
  "começa na sua cozinha". Não usar páginas com PIX/@ de outra criadora.

### Chá Seca-Barriga — `projeto-cha-seca-barriga`
- Jun/2026: 5 PDFs entregues em `Downloads\PDFs_Cha_Seca_Barriga\` (Receita do Chá, Alimentos que Desincham,
  Protocolo 21 Dias, Sucos, Receitas Leves). Fonte `MVP_Cha_Seca_Barriga_RICO.docx`.
- **Estilo JANTAR** (padrão visual preferido): oliva `#6E7A38`/`#4E5822`/`#9CAA56`, creme `#F1EAD8`, dourado `#B8860B`/`#D9A741`;
  Archivo Black (títulos), Oswald (rótulos), Barlow (corpo). Receita = card de página inteira com foto + overlay + selo
  "RECEITA 0X". Rodapé "Natureza que cuida, tradição que transforma!".

### Mármore / parede de resina (congelada)
- Primeira oferta cadastrada (V001–V008). Congelada com a LEVA_01 por dúvida de direitos do PDF (é do Paulo Pintor).

### Fígado (BR)
- Oferta de onde vieram os formatos split e TikTok e o funil-modelo do Leona (atendente Camila, `PROMPT_ATENDENTE_FIGADO.md`).

---

## 5. México — `projeto-mercado-mexico`, `hotmart-oxxo-mexico`, `tts-edge-voz-mexico`

- Desde 20/08/2026. **Espanhol do México**, não neutro. Entregues: Te Desinfla-Panza (PDF 1 do Chá) e
  **Charola que Vende** (ebook original de 29 págs).
- Adaptação: espinheira-santa → *cuachalalate*, carqueja → *prodigiosa*, funcho → *hinojo* ("no anís"), hortelã → *hierbabuena*.
  **Almuerzo = lanche da manhã; comida = almoço (14–16h).** agua purificada, lumbre, olla, refrigerador, nutriólogo.
  Aviso: "Este producto no es un medicamento" + fórmula da COFEPRIS. Espanhol ocupa ~20% mais espaço.
- Salgado brasileiro não transfere: lá vende empanada, tamal, concha, tlacoyo, quesadilla, torta.
- Pagamento: sem PIX (SPEI/CLABE, CoDi, OXXO, dinheiro).
- **Hotmart:** OXXO = caixa `offerBillet` (Boleto); `offerDirectDebit` = SPEI; `offerHybrid` = cartão + OXXO.
  Criar produto com país principal = México. Liberar sábado/domingo nos dias do boleto. Valor preenche da direita ("10000" = 100,00).
  **IVA 16% somado por cima** (base = valor ÷ 1,16 para fechar redondo). Produto **RECETARIO DE BOTANAS PARA VENDER**:
  ID 8382691, $100 MXN (checkout $116), `pay.hotmart.com/R107310071K`.
- Concorrência: travar a copy vencedora e testar só o vídeo; **"Recibe primero, aporta después"**; "desde cero"/"sin experiencia"
  (objeção nº1: não sei fazer); CTA convida a conversar; entrega por WhatsApp é vantagem; "emprender" é identidade.
- Criativo que gera desejo: abrir em **apetite** (queijo puxando, mordida), no assunto da 1ª frase; todo gráfico de problema
  com o **par que resolve**; **gente reagindo**; nada de buraco >5s sem gráfico; CTA acelera (~1,6s). Legenda Arial 64,
  caixa alta, contorno 7, MarginV 430, palavra-chave âmbar `&H00C8FF&`.
- **TTS aprovado:** `python -m edge_tts --voice es-MX-DaliaNeural --rate="-6%"`, **texto cru** (não mexer na pontuação),
  normalizar `loudnorm=I=-15:TP=-1.0:LRA=11`. Upgrade: Azure Speech (estilos) ou Google `es-US-Studio`.
- O TTS pode ler anotações de direção: checar o fim do áudio com `silencedetect`.

---

## 6. Funil de WhatsApp

### Leona Flow — `leona-flow-api`
- Funil roda no **Leona Flow** (app.leonasolutions.io). Ler fluxo pelos props React de `.react-flow`, não pelo DOM.
- Usar **só os endpoints do próprio editor** (lista e bodies na nota). Não explorar outros com o token.
- **PATCH ignora `media_file_info`**: para trocar PDF/áudio, apagar a ação e recriar.
- **Todo bloco de espera precisa das duas saídas** (timeout e respondeu), senão o lead trava e o remarketing não dispara.
- Leitor de comprovante: **gpt-4.1** com saída de erro ligada.
- Fluxo duplicado **nasce ATIVO** — pausar na hora.

### Blocos de IA — `funil-whatsapp-blocos-ia`
- "Resposta vazia da API" = prompt. **Classificação sempre devolve uma palavra** (`#negativo`/`#positivo`); na dúvida,
  a que segue o funil. Só recusa explícita é negativa (emoji, pergunta, erro de digitação = positivo).
- Prompt enxuto (~20 exemplos por classe). Escada de 3 degraus com o do meio "mais escolhido"; valor acima do acesso = "doação".
- Em aberto: "recebe primeiro, paga depois" vs escada antes da entrega.

---

## 7. Formatos de criativo

### Pacote aprovado do Pudim no CapCut (PADRÃO ATUAL) — `formato-pudim-capcut-aprovado`
**Partir dele sempre; perguntar só a velocidade e o material que falta.**
- Editar **dentro do CapCut** via `montar`, com motion do Remotion como camada.
- Cortar todo silêncio e acelerar (ele define: 1.1x–1.2x). Voz = MP3 original alinhado ao lipsync.
- Motion que "conta" a fala (lista X/✓, contador, carimbo ESGOTADO, mensagens chegando, preço, mouse no selo do Zap).
  Cena que falta pode ser feita em motion.
- Música e efeitos da **biblioteca do CapCut** (Pro). Música com arco (animada no gancho, baixa na tristeza, cresce na virada).
  **Nunca sem som. Música nunca repete entre criativos. Renovar o pacote de motion a cada 2 criativos.**
- Legenda branca com só a palavra-chave amarela. **Texto nunca vaza a tela** (medir largura em Arial Black e dividir).
- Material: sem ovo, fogão aceso ou forno; cortar legenda queimada/@/logo; conferir quadro a quadro.
- **Nunca mostrar páginas do PDF "Pudim Sem Forno"** nem "x de 32" (tem receitas com ovo e fogo).
- Entrega: H.264 1080x1920, −14 LUFS + PNG do 1º frame, na pasta da leva.

### Split + avatar — `formato-criativo-split-avatar`
- 1080x1920, **split 50/50 exato**, hook já abre dividido. Varia com tela cheia de avatar e takes inteiros.
- Hook ~8s, demais 3,5–5s; b-roll a ~1,9s. **Tarja nunca na boca**, centralizada, fundo sólido, Arial Black
  (branca = afirmação, vermelha = alerta, amarela = promessa). Legenda pequena (Arial 42, MarginV 300).
- Emenda em **degradê de 200px**; `setpts=PTS-STARTPTS` nos dois inputs. CTA: WhatsApp desenhado + seta pulsando no rodapé.
- **Sempre reescrever a legenda à mão** (Whisper erra em pt-BR).

### TikTok viral — `formato-criativo-tiktok-viral`
- Tela cheia, sem avatar contínuo (avatar UGC só em gancho, mecanismo e CTA).
- **Mapear o áudio bloco a bloco antes de escolher clipe**: a tela mostra o que a voz diz?
- Legenda amarela CapCut: Arial Black 88, `&H004AE4FF`, contorno 8, sombra 5, MarginV 470, 3–6 palavras em MAIÚSCULA a cada ~3s.
- Tarja de hook vermelha + branca com emoji. Cortes de 1,9s, zoom mais forte, 2–3 takes de 6s.

### Desenho sonoro
- Desde 14/09/2026: música, efeitos e motion do CapCut trecho a trecho (a regra antiga de "só flash branco" não vale mais).
- **Sons ancorados no sentido da fala, não nos cortes.** Riser antes de revelação, impacto na palavra de peso,
  chime no preço, buildup antes do CTA. Banco CC0: `C:\Users\gabgb\sfx-banco`.

### Referência que escalou: podcast com avatar (diabetes) — `referencia-criativo-podcast-diabetes`
- Entrevista à mesa com a "comida proibida", gancho de inversão ("pode? pode."), mecanismo com nome, prova, objeção de preço,
  CTA indireto ("a produção deixa abaixo do vídeo") + botão animado + 3 setas + 9 min de relógio mudo no fim (hipótese: evitar loop).
- Copiar só a forma; as alegações de saúde dele são inventadas. Aplicar no V031 (podcast) do Pudim.

### Referência escalada: "Caseirinho Gourmet" (catálogo sem rosto) — `referencia-criativo-caseirinho-catalogo`
- Oferta gêmea da nossa (recebe primeiro, R$ 10,90, "Recheio Sem Fogo"). Sem avatar: voz em off + comida.
- 0–26 s: ~32 cortes de 0,8 s, um sabor por corte com **nome do sabor no topo**; depois planos longos de processo sensorial.
- Copy: renda com número → inimigo → **matemática na tela (custo R$ 1,80 x venda ~R$ 20)** → "não é um bolinho, é uma nota de 20"
  → sem batedeira/sem fogão → meta diária → oferta empilhada → recebe primeiro + garantia 7 dias → CTA "liberdade".
- Aplicar no Pudim como V034 "catálogo" (precisa dos números reais do potinho).

### Triagem de b-roll — `triagem-broll-anuncio`
- Reprova: marca d'água de perfil, legenda queimada, rosto de terceiro (principalmente com credencial), corpo em foco,
  produto de marca, comida que contradiz a copy. Buscar "fígado" no TikTok traz fígado bovino.
- **Conferir o vídeo montado, não os clipes**: 6 frames por corte na faixa das marcas (o zoompan traz a marca de volta).
- Consertar com crop 9:16 + `scale=1080:1920:flags=lanczos` (melhor que `delogo`).
- Falta b-roll → card gráfico numerado em vez de comida genérica.

---

## 8. Pipelines e ferramentas (na máquina dele)

### Vídeo com ffmpeg — `pipeline-video-ffmpeg`
- ffmpeg 9.0 full (winget Gyan.FFmpeg) com **whisper embutido**; modelo `C:\Users\gabgb\whisper-models\ggml-small.bin`.
- Skills próprias em `C:\Users\gabgb\.claude\skills\`: `criativo-analisar`, `criativo-audio`, `criativo-montar`,
  `criativo-entregar` (todas usam `ffmpeg-lib.ps1`; ao corrigir, redistribuir para as 4). Mais `setor-criativos`.
- Pegadinhas: caminho no filtro whisper sem letra de drive; `$Args` é reservado; .ps1 em **UTF-8 com BOM**; nunca `2>&1`
  em exe nativo no PS 5.1; PowerShell e Windows são **case-insensitive** (variável/arquivo que difere só na caixa colide);
  vírgula liga mais forte que `+` em `@()`; `-loop 1` sempre com `-t` e `-shortest`; PNG em overlay com `-framerate 30`;
  `drawtext` sem `fontfile` dá segfault; evitar `/` em expressão de filtro.
- Claude não escuta áudio, mas mede: `ebur128`, `astats`, `silencedetect`, `showwavespic`, whisper.

### CapCut kit no Windows — `capcut-kit-windows`
- `python capcut-bridge-win.py <comando>` (kit em `Downloads\capcut-kit-main\capcut-kit-main\`). `montar` + `exportar()`.
- Fonte do próprio CapCut (`SystemFont/en.ttf`) — outras travam a exportação. Áudio = `extract_music` + categoria `local`.
- Exporta HEVC 1440x2560 → converter para 1080x1920 H.264. Não usar `escala` + `zoom` juntos.
  Aviso "CapCut Pro" em janela separada bloqueia clique. **Nunca clicar em Compartilhar** na exportação.
- Tela dividida com `"y"` (0.5 cima / −0.5 baixo); destaque de palavra com `"destaques"` + `"destaque_cor"`.
  `baixar_sons.py` baixa música e efeitos da biblioteca.

### Remotion — `remotion-motion-criativos`
- Projeto em `Downloads\remotion-criativos` (Remotion 4.0.524). Peças em `src/pecas/`, estilo em `src/estilo.tsx`
  (branco / `#FFE44A` / `#E02424`, Arial Black). Duração via `--props` (30 fps).
- Render transparente: `npx remotion render <Id> out/<Id>.mov --codec=prores --prores-profile=4444 --pixel-format=yuva444p10le --image-format=png`.
- Tarja de 1 linha com 56px+ vaza acima de ~22 letras: quebrar com `\n`.

### Outras skills de vídeo — `skills-video-instaladas`
- **video-use** e **hyperframes** em `C:\Users\gabgb\Developer\` (junção em `~/.claude/skills/`). Render do hyperframes
  **não roda nos 7,5 GB** — usar a máquina de 16 GB. Plugin Remotion instalado (12 skills).
- Python 3.12 e Node 24.19 instalados. `claude.exe` fica em `AppData\Roaming\Claude\claude-code\<versão>\`.

### Edição na sessão na nuvem (aprendido em 24/09/2026, V033)
- Aqui não tem ffmpeg nem Whisper instalados: `pip install imageio-ffmpeg pillow` dá o ffmpeg (sem `drawtext`, com `ass`).
- HuggingFace e os modelos do Whisper são **bloqueados**; só pypi e npm passam. Transcrição que funciona:
  `npm i --ignore-scripts sts-whisper-tiny @huggingface/transformers wavefile` (whisper-tiny, fraco em pt-BR, mas
  serve para alinhar a fala com a copy conhecida; transcrever trechos curtos de novo quando alucinar).
- Fonte Archivo Black: `npm i @fontsource/archivo-black` e converter o .woff para .ttf com fonttools.
- **Lip sync: o áudio do vídeo vem ~38 ms adiantado em relação ao MP3** → cortar 0,038 s do início do MP3 (`atrim=start=0.038`).
- **Não usar `-shortest`** ao compor vídeo pesado + áudio (cortou 6 s no fim). Renderizar só o vídeo e juntar o áudio depois.
- Sem biblioteca de efeitos aqui (sites de áudio bloqueados): efeitos são **sintetizados com numpy/scipy**
  (`pip install scipy`), 6–10 dB abaixo da voz, e mixados com `amix=normalize=0` + `alimiter`.
- Envio pelo chat tem limite de 30 MB: gerar versão de entrega em 2 passes (~3 Mbps para 70 s).
- Takes de TikTok têm **inserts de 1 s** (rosto, texto): varrer o b-roll montado a 5 quadros/s antes de entregar.

### PDF no Windows — `pipeline-pdf-windows`
- HTML/CSS A4 → **Chrome headless `--print-to-pdf`** → conferir renderizando em PNG (WinRT `Windows.Data.Pdf`).
- Fotos pela **API do Pexels** (chave do Gabriel). Ler .docx: renomear para .zip e ler `word/document.xml`.
- Página de PDF como b-roll: pymupdf a 300 dpi, página em ~1040 px sobre fundo borrado dela mesma.

---

## 9. Memória no Obsidian — `obsidian-cerebro-segundo-cerebro`

- No PC dele há o MCP **"obsidian"** (plugin "Local REST API with MCP", porta 27123). Quando estiver disponível
  (ToolSearch "obsidian"): **salvar automaticamente**, sem pedir — append na nota do dia em `Diário/` e atualizar
  (nunca recriar) a nota do assunto em `Assuntos/`. Avisar brevemente que salvou.
- Se desconectado: Obsidian fechado ou toggle "Enable non-encrypted (HTTP) server" desligado.
- Em sessões na nuvem esse MCP não existe: **este arquivo e `vault/` são a memória**. Ao aprender algo relevante aqui,
  atualizar a nota em `vault/Assuntos/` e o resumo neste arquivo.
- Ainda não importado: pasta `Diário/`.
