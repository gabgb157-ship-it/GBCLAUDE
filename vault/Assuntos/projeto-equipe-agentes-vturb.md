Em 2026-09-11 o Gabriel pediu para montar uma **equipe de agentes e subagentes** (Claude Code)
para tocar a operação de ofertas dele — **no lugar de contratar pessoas**. Primeiro o X1
(venda 1:1 no WhatsApp), depois venda direta.

A base de conhecimento são os episódios do podcast **VTurb – Segredos da Escala** que ele
baixa do YouTube para `Downloads\videoplayback (N).mp4` (640x360, sem título no arquivo —
identificar pelo cenário e pela transcrição). Fluxo: transcrever tudo, extrair o que o
convidado ensina e transformar cada ensinamento em regra de trabalho de um agente.

Quando ele ditou por voz, "subagentes" chegou escrito como **"Fish Cliente"**. O ditado dele
embaralha termos técnicos — na dúvida, confirmar em vez de adivinhar.

Transcrição de 4h30: whisper small do ffmpeg roda a ~2× o tempo real nesta máquina (Ryzen
5600H, só ~0,8 GB de RAM livre). Cortar em blocos de 15 min e rodar 2 em paralelo; mais que
isso começa a usar o arquivo de paginação.

**Onde a equipe mora (montada em 11/09/2026):** agentes em `C:\Users\gabgb\.claude\agents\`
(copy-criativo, revisor-copy, pesquisador-mercado, editor-criativo, analista-trafego,
lente-copy, lente-edicao, lente-cena), rotina na skill `setor-criativos`, e a operação em
`C:\Users\gabgb\SETOR_CRIATIVOS\` (DIRETRIZ, PLANILHAS em CSV com `;` e BOM, OFERTAS,
ANALISES, LABORATORIO, TAKES). A sessão principal é o "head" que despacha; subagente não chama
subagente.

Podcasts estudados: P1 Matheus Lorenzo, P2 Thiago Filamon, **P3 Diogo Kobata #059 (21/09/2026,
fatias de público / CTA CVI / lateralização / upsell ÷ ticket)**. Atalho que funcionou no P3: a
legenda automática do YouTube via `python -m yt_dlp --skip-download --write-auto-subs --sub-langs pt`
(segundos, em vez de 1h+ de Whisper; o 2º pedido deu 429, o `pt-orig.vtt` já basta).
O que cada podcast ensina está em `SETOR_CRIATIVOS\CONHECIMENTO\` (notas bloco a bloco +
transcrições). O playbook foi publicado em
https://claude.ai/code/artifact/67df7d9d-c478-4548-a0e2-392fea8c6c96 (republicar do mesmo
arquivo do scratchpad ou passando a `url`).

**Estado em 11/09/2026:** a oferta do mármore foi a primeira cadastrada (`OFERTAS\marmore\
estudo.md`). Os 8 vídeos da pasta `Downloads\CRIATIVOS PAREDE DE RESINA` viraram V001–V008 na
esteira, com status de tráfego "A CONFIRMAR". Faltam: o Gabriel dizer quais estão no ar e mandar
o export do Gerenciador pra primeira call de segunda. V001–V003 têm 71–75 s, contra a faixa de
44–53 s dos 76 anúncios do concorrente (Paulo Pintor).

**O produto do mármore é do concorrente (achado em 11/09/2026).** O PDF
`Downloads\30 Efeitos Marmorizados - Guia Completo de Modelos.pdf` traz na capa "POR PAULO
VICTOR SAMPAIO GOMES" (o Paulo Pintor, o concorrente modelado), o autor nos metadados é
"Victor Sampaio" (Canva, 02/07/2026), e a pág. 2 diz "uso pessoal e intransferível… proibida a
revenda… sem autorização prévia do autor", com a chave PIX dele. Bloqueei a LEVA_01 e **em 11/09 ele afirmou que TEM autorização do Paulo pra revender**, então
liberei. Pedir a autorização por escrito e uma versão do PDF sem a página com a chave PIX do
autor antes de escalar. Mesmo padrão do caso da apostila "salgados de maria" em
[[projeto-mercado-mexico]]. **Antes de fazer anúncio pra qualquer produto, conferir de quem é o
PDF (capa, página de direitos, metadados).**

**Agente com navegador toca vídeo no PC dele (11/09/2026).** A pesquisadora abriu 4 abas da
Biblioteca de Anúncios e 1 do TikTok no navegador interno do app, e os vídeos tocaram com
som. Ele pediu pra parar, então parei o agente e fechei as abas. Agora o
`pesquisador-mercado` só usa navegador quando liberado, silencia e pausa os vídeos e fecha as
abas no fim. Confirmar com ele antes de rodar pesquisa com navegador enquanto ele usa o PC.

**Nomes da equipe (aprovados por ele em 11/09/2026, já gravados nos agentes e na skill):** Heitor (chefe = a sessão principal),
Paula (pesquisa), Caio (copy), Rita (revisão), Edu (edição), Ana (análise), Lia/Léo/Luna
(lentes copy/edição/cena). A inicial é a da função.

**Conteúdo de épocas diferentes: o recente manda.** Ele avisou que o episódio do Thiago
Filamon (videoplayback (1), gravado em mar/2025) é antigo e o do Matheus Lorenzo (set/2026)
é atual — do antigo, usar só o que ainda vale depois do Andromeda e marcar onde os dois
discordam (ex.: empilhamento de ganchos e muitos ganchos por corpo).

**Sistema maior pedido em 11/09/2026 (11 fases).** Ele quer transformar o conhecimento num
COPY INTELLIGENCE SYSTEM: base do podcast, depois livros (só fontes legais e autorizadas,
separando obra de material secundário), mapa de convergências entre autores, frameworks por
etapa (mercado, persona, consciencia, big idea, mecanismo, angulo, hook, lead, oferta, prova,
criativo, teste), 15 agentes especializados com criterios de aprovacao e rejeicao, sistemas de
score, banco de hipoteses separando fato de hipotese, e loop de aprendizado com metricas.
Ordem obrigatoria: podcast, livros, principios, comparacao, sistema, e so entao agentes.
A Fase 1 ficou em SETOR_CRIATIVOS\CONHECIMENTO\01_PODCAST_KNOWLEDGE_BASE.md.
Pendencia que fecha metade das lacunas: baixar o episodio de VSL do Matheus Lorenzo.

**Prioridade X1 (definida em 11/09/2026).** O modelo atual e oferta de ticket baixo no X1,
entao a arquitetura foi construida pra: anuncio Meta/TikTok, criativo, conversa no Zap,
diagnostico do lead, objecao, fechamento, pagamento, follow-up e metricas. VSL, sales page,
advertorial, e-mail, upsell e backend ficam como FUTURE MODULE: previstos na arquitetura,
nao ativos. Hierarquia de fontes que ele definiu: 1) podcast, 2) estrutura do nosso X1,
3) dados das campanhas, 4) livros, 5) outras fontes. Livro nunca apaga metodo do podcast; em
conflito, vira hipotese de teste. Arquitetura: CONHECIMENTO/02_ARQUITETURA_X1.md. Agentes do
lado da conversa criados: Zeca (x1-conversa), Dani (x1-diagnostico-lead), Olivia (x1-objecoes),
Fabio (x1-fechamento), Rui (x1-followup). Faltam: Dora, Sofia, Bia, Marcos, Angela, Gil, Vera,
Otavio, Cris e Teo.

**Sistema de copy concluido em 12/09/2026.** Fases 1 a 6 feitas: base do podcast (01), arquitetura X1 (02), tres blocos de livros em CONHECIMENTO/livros (A Hopkins/Halbert, B Hormozi/Kennedy/Whitman, C Schwartz/Masterson/Sugarman/Cialdini, so fontes legais, marcando obra x secundario), mapa de convergencias (03) e banco de hipoteses (04, H1 a H33 priorizadas). A equipe tem 22 agentes: Paula, Dora, Sofia, Bia, Marcos, Angela, Gil, Vera, Caio, Rita, Edu, Otavio, Zeca, Dani, Olivia, Fabio, Rui, Cris, Teo, Ana, as 3 lentes e o Heitor (sessao principal). Regras novas que entraram sem teste: codigo da peca no link do wa.me (cupom do Hopkins), Folha de Fatos antes da leva, adjetivo sem numero e REFAZER, CPA fecha no degrau 1, teto de verba = capacidade de atendimento dividida pelo custo por conversa, receita por conversa como metrica-resumo, e uma pergunta depois da entrega (conseguiu abrir?) pra medir consumo.

**Regra critica do orquestrador (12/09/2026).** Nenhum agente transforma hipotese, inferencia ou
opiniao em fato. Tudo que o sistema produz e classificado como FATO, RESULTADO VALIDADO, INFERENCIA,
HIPOTESE ou IDEIA PARA TESTE, com origem. A sessao principal (Heitor) fiscaliza: rebaixa o que veio
promovido, revisa o trabalho construido em cima de hipotese tratada como fato, e registra a
reclassificacao no banco. Dado de terceiro (livro, concorrente, podcast) nunca vira fato nosso.
Todo relatorio pra ele fecha em tres blocos: o que sabemos, o que acreditamos, o que precisamos
testar. Regra em CONHECIMENTO/05_REGRA_DE_CLASSIFICACAO.md e gravada nos 23 agentes.

**Regra suprema (12/09/2026): LUCRO LIQUIDO.** O objetivo do sistema nao e produzir criativo, e
melhorar decisao. Hierarquia: lucro liquido > ROAS/CPA/margem > conversao no X1 > qualidade do lead >
criativo > metricas intermediarias (CTR, CPM, hook, hold, retencao = diagnostico, nunca vitoria).
Principio de teste: errar barato, aprender rapido, identificar sinal, aprofundar vencedor, escalar com
controle, maximizar lucro. Entrou o agente **Lucas** (lucro-capital): CPA real, margem, lucro liquido,
teto de verba por capacidade, arvore de gargalo, escada de decisao de verba (1 ticket/dia pra entrar,
+50% nunca dobrar, reduzir antes de matar, encerrar com 2 tickets sem venda, congelar se a fila de
atendimento encher) e o Offer Selection Score (17 fatores 0-5 com eliminatorias: sem direito de
vender, margem negativa, promessa contra politica, impossivel demonstrar, atendimento acima da
capacidade). Toda recomendacao financeira separa FATO / HIPOTESE / RISCO / EVIDENCIA / DECISAO
PROPOSTA, e **retorno futuro nunca e garantia** (projecao em faixa, com premissa escrita). Planilhas
novas: PLANILHAS/lucro.csv e PLANILHAS/ofertas_score.csv. **Formato obrigatorio de toda entrega a
ele: 10 itens** (situacao, diagnostico, fatos, hipoteses, riscos, opcoes, recomendacao, proxima acao,
responsavel, metrica que define sucesso ou fracasso) — o papel dele e direcao, decisao, capital,
aprovacao, escala. Regra em CONHECIMENTO/06_REGRA_SUPREMA_LUCRO.md.

**Oferta ativa desde 12/09/2026: PUDIM** (nao mais marmore, que ficou congelado com a LEVA_01 na
gaveta e a duvida de direitos em aberto). Pudim ja faturou: 7.123 vendas pagas e R$ 50.911 gastos em
2 contas, CPA R$ 7,04, custo por conversa R$ 1,90, conversa->venda 27%, hook 42,74%, CTR 2,57%.
Vende RENDA (fazer e vender pudim sem fogo), nao receita. Ticket R$ 9,90-19,90 com escada
pague-quanto-quiser e upsell de R$ 9,90 a 5%. Personagem Gabi Silva, historia de virada. Criativos
vencedores tem 1:30 e 1:17 (video longo e a norma no nicho) e estao em
SETOR_CRIATIVOS/OFERTAS/pudim/criativos_validados/. Tudo em OFERTAS/pudim/METRICAS_HISTORICO.md.

**O que importa saber da operacao dele (nao esta em codigo nenhum):** o atendimento do WhatsApp e
**automatico**, nao humano - capacidade nao e gargalo. **O gargalo de escala e queda de chip**: chip
que cai desliga campanha, e campanha religada perde o aprendizado. Instancia de automacao custa
R$ 97 cada, chips ~30/mes a R$ 15, imposto 13% sobre o investido. A solucao que ele quer e **API
oficial** pra estabilizar. "Compras" no Gerenciador = **venda paga** (etiqueta do comprovante dispara
o evento). A margem e fina: ~R$ 3 por venda, e foi isso que matou a operacao quando clonaram os
criativos e o CPM subiu - nao foi a oferta.

**Funil do pudim no Leona (19/09/2026):** fluxo "FUNIL PUDIM SEM FOGO 3.0" (id 124207), duplicado da estrutura do
fígado (remarketing + atendente IA), com as mensagens do "fluxo pudim atualizado 2.0" (id 99187) e a escada V2
(19,90 / 14,90 / 9,90). Atendente IA virou "Gabi". Produto "RECEITAS PUDIM SEM FOGO" criado; pixel é o "PIXEL PUDIM X1".
Ele aprovou e ativou o 3.0 em 19/09. **4.0 (id 124558, pausado):** duplicado do 3.0 so com esta mudanca - na entrega vao so as receitas (Pudim Sem Fogo 1 e 2) + aulas + mensagem do que ela ganha ao pagar; Precificacao, Como Vender e bonus so no pos-pagamento; Gabi sabe disso. Pedido dele: testar sem desmontar o 3.0 validado ("se nao converter, volta pro 3.0"). Ele tira os materiais pagos da pasta do Drive. Ver [[leona-flow-api]].

Ver [[funil-whatsapp-blocos-ia]], [[metodo-teste-oferta-15min]], [[pipeline-video-ffmpeg]].
