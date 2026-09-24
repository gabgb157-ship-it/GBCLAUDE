---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Método de teste de oferta em 15min
Material que o Gabriel mandou em 2026-08-29 (`KG_TRAFEGO_Teste-de-Oferta-em-15-Minutos_v1.pdf`,
31 páginas, @Ooliveira.arthur) e pediu para eu usar nas ofertas novas.

## A tese

O Andrômeda tirou a segmentação da mão do anunciante e colocou **dentro do criativo**.
A Meta lê o Ad Text, transcreve o áudio e interpreta a cena — então o criativo agora
tem duas funções: converter **e** segmentar. Uma imagem com Ad Text de 800 palavras
entrega mais texto interpretável do que a maioria dos vídeos de 60s. Por isso imagem
estática voltou a escalar: 2× funções, 0s de gravação, ~15min por bateria.

> "O criativo não é mais a peça que fala com o público. O criativo **é** o público."

## As duas peças e o diagnóstico

**Hook visual (a imagem):** o trabalho é *parar o polegar*. Não explica, não vende, não
precisa ser bonita. Imagem que informa demais responde a pergunta antes do texto e mata
a leitura.
**Ad Text:** conscientiza e converte. É ele que carrega a densidade semântica que a Meta
usa pra segmentar.

| Métrica ruim | Culpado | O que trocar |
|---|---|---|
| CTR (todos) e CPM | hook visual | a imagem, não o texto |
| % de expansão do "ver mais" | 1ª linha do Ad Text | só o hook do texto |
| CTR de link baixo com CTR total alto | body e CTA | reescrever body e CTA |
| Sem entrega e sem clique | oferta ou ângulo | voltar ao estudo de público |

**Regra de ouro:** nunca trocar imagem e texto ao mesmo tempo. Se os dois mudam e o
resultado muda, não se aprendeu nada.

## Os três avatares (é o que abre três públicos)

1. **Autoridade** — "eu resolvo esse problema". Traz lead qualificado e ticket maior.
2. **Transformado** — "eu tive esse problema". Maior conversão em saúde/estética/dinheiro; traz volume.
3. **Visualizador** — "eu vi acontecer com alguém" (filho, cônjuge, cuidador). Abre o
   público que compra **para outra pessoa**; CPM mais barato.

Três avatares = três transcrições semanticamente distintas = três públicos dentro do
mesmo nicho. **Ordem de trabalho: estudo de público → avatares → Ad Text.** Quem pula o
estudo escreve sobre a dor que imaginou e depois culpa o algoritmo.

## Ad Text: proporção, aberturas e estruturas

Hook 10% (2–4 linhas) · Body 75% · CTA 15% (3–6 linhas).
*O hook compra a leitura, o body compra a crença, o CTA só coleta.*

**Regra das duas linhas:** corte o hook no ponto do "ver mais". Se o que sobrou não gera
curiosidade sozinho, o hook não existe.

12 aberturas testadas: confissão de autoridade · diagnóstico herdado · descoberta
contraintuitiva · erro que todo mundo comete · notícia/estudo · pergunta de sintoma ·
antes-e-depois com número · inimigo externo · carta ao passado · objeção invertida ·
cena concreta · lista com número.

4 estruturas de body: **A** história pessoal (transformado/visualizador, barateia CPM) ·
**B** descoberta clínica (autoridade, sustenta ticket alto) · **C** erro em série (público
frio) · **D** contraste direto (público cético que já tentou tudo).

**Mecanismo é obrigatório.** Ad Text sem mecanismo vira post motivacional: agrada, não
vende. O mecanismo responde "por que isso funcionaria comigo se nada funcionou até agora?"

Extensão por destino: quiz 150–300 palavras · VSL 300–500 · advertorial 300–500 ·
venda direta 700–900.

CTA por nível de consciência: inconsciente → descoberta (quiz/teste; pedir compra queima
o lead) · ciente do problema → diagnóstico e explicação · ciente da solução → comparação
e mecanismo · ciente do produto → direto, com garantia.

## Hook visual: onde garimpar e a regra que decide

Cinco minas: YouTube ordenado por mais vistos · Biblioteca de Anúncios filtrada por
imagem e ordenada por tempo no ar (tempo no ar é a única métrica pública de validação) ·
portais de notícia reais · o próprio estudo de público · orgânico que já viralizou no
nicho (o 1º frame de um viral é um hook visual pronto).

> "Colete a estrutura, não o arquivo. Você identifica **por que** aquela imagem para o
> olho — e recria essa razão com o seu elemento."

8 formatos: notícia · clickbait/curiosidade · quiz/pesquisa · comparação lado a lado ·
receita/lista · documento/print · ilustração científica · objeto isolado.

**Quanto menos parecer anúncio, melhor.** Passa no filtro: enquadramento de pessoa comum,
luz natural com imperfeição, layout que imita interface conhecida, texto curto ou nenhum,
contexto doméstico. Aciona o filtro: banco de imagens com modelo sorrindo, estúdio de luz
perfeita, moldura e logo, bloco de texto grande, selo de "oferta", paleta de marca
caprichada. Não é só estética — **aparência nativa gera mais interação orgânica e a Meta
cobra CPM menor por isso**.

**Teste do polegar:** ponha a imagem no meio do seu feed e role rápido. Se ela se destaca
*por parecer anúncio*, refaça. Tem que se destacar por ser estranha.

## A matriz e a campanha

**10 hooks × 3 Ad Texts = 30 criativos.** Não se produz 30 — produz 13 peças e combina.

Campanha: **ABO** (nunca CBO — em CBO o algoritmo concentra verba e você perde a leitura
que foi comprar) · **um criativo por conjunto** · **verba diária = um ticket** · público
amplo sem interesse nem lookalike (a segmentação está no criativo) · todos os
posicionamentos · **subir tudo junto e não tocar por 24h**.

Nomenclatura: `[OFERTA]_[DATA]_TESTE_AT[n]-[avatar]_H[n]-[formato]`
(ex.: `POS40_2608_TESTE_AT1-VIS_H01-NOTICIA`).

Reduza **conjuntos**, nunca a verba de cada um — conjunto com verba abaixo do ticket
devolve ruído. 6 hooks × 2 Ad Texts = 12 criativos já dá leitura.

**Régua de corte (24h):** meio ticket sem venda → mata · meio ticket com venda → mantém ·
um ticket e uma venda → mantém · dois tickets e uma venda → mata · sem venda mas CTR muito
alto → **separa** (a imagem funciona, o texto não: recombine) · sem venda e sem entrega →
mata.

**Leia por peça, não por combinação.** Some tudo o que o Ad Text 1 fez em todas as imagens,
e tudo o que o Hook 07 fez em todos os textos. Uma peça só está reprovada quando morre em
*todas* as combinações.

Cada vencedor vira cinco variações — uma variável por vez. Ad Text vencedor: mantém o body,
troca o hook (procura o teto do ângulo, não um ângulo novo). Hook vencedor: mantém o
conceito, muda enquadramento/luz/cor/objeto/formato.

**Atalho barato:** campanha de tráfego só com as imagens, verba baixa, pra separar as dez
em três boas e sete descartáveis antes de gastar ticket.

## Do estático ao vídeo — muda como eu monto criativo

Grava-se vídeo **depois** de saber qual mensagem vende. O estático é o laboratório.

| Validado no estático | Vira, no vídeo |
|---|---|
| hook visual vencedor | os 3 primeiros segundos (primeiro frame + movimento) |
| hook do Ad Text | a primeira fala, praticamente sem reescrita |
| body do Ad Text | o roteiro do miolo, um parágrafo por cena |
| CTA do Ad Text | o fechamento |
| avatar vencedor | quem narra |

Isso valida a ordem que a gente já vinha usando (transcrever primeiro, cortar no sentido
da fala) e acrescenta o passo que faltava: **testar a mensagem em imagem antes de gastar
montagem de vídeo**. Ver [[pipeline-video-ffmpeg]] e [[projeto-mercado-mexico]].

## Compliance (o que derruba conta em saúde/estética/finanças)

1. **Nunca atribuir a condição ao leitor.** Errado: "Você que está na menopausa e
   engordou". Certo: "Depois dos 40 o corpo passa a responder de outro jeito."
2. **Nunca prometer resultado, prazo ou cura.** Errado: "Elimine em 21 dias, garantido."
   Certo: "O protocolo que passei a seguir depois desse diagnóstico."
3. **Nada de antes/depois agressivo** nem imagem gráfica de condição médica.
4. **A promessa do CTA tem que ser a primeira coisa visível na página de destino.**

*A reescrita que quase sempre resolve:* tire o "você" de qualquer frase que carregue a
condição — passe pra terceira pessoa ou pra experiência do narrador. A força da copy
permanece, o risco cai muito. Isso bate com a posição que eu já vinha aplicando nos
criativos do México: falar de comida, não de tratamento.

## Os 12 erros que matam o teste

trocar imagem e texto juntos · empilhar criativos no mesmo conjunto · usar CBO ·
segmentar por interesse · mexer nas primeiras 24h · matar com 3h de rodagem · nomear de
qualquer jeito · ler por combinação · Ad Text sem mecanismo · pular o estudo de público ·
achar vencedor e não variar · parar de testar quando começa a lucrar.

Se o teste inteiro morreu sem venda **e** sem CTR decente, o problema quase nunca é o
criativo — é a oferta, o preço ou a página.
