---
tags: [project, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Mercado México
Desde 2026-08-20 o Gabriel está levando os infoprodutos dele para o **mercado mexicano** (espanhol do México, não neutro). Ver [[gabriel-infoprodutos-pdf]].

## Entregue
- `Downloads\PDF1_Te_MX.html` → `PDFs_Cha_Seca_Barriga\MX - 1 - Te Desinfla-Panza (ES-MX).pdf` — o PDF 1 do Chá traduzido/adaptado, mesmo layout JANTAR. Faltam os outros 8 do pacote.
- `Downloads\CHAROLA_QUE_VENDE_MX.html` → `PDFs_Cha_Seca_Barriga\MX - CHAROLA QUE VENDE (ES-MX).pdf` — ebook **original** de 29 páginas sobre vender antojitos em charola (padrão mini/mediano, 8 receitas, precificação, empaque, canais de venda). Sem fotos (falta a chave do Pexels); ilustração em SVG.

## Regras de adaptação que já valeram a pena
- **Trocar ingrediente que não existe lá**: espinheira-santa → *cuachalalate*, carqueja → *prodigiosa* (ambas em qualquer herbolaria). Funcho → *hinojo* (avisar "no anís"), hortelã → *hierbabuena*.
- **Armadilha de horário**: no México *almuerzo* = lanche da manhã e *comida* = almoço principal (14–16h). Traduzir "depois do almoço" como "después del almuerzo" quebra o protocolo inteiro.
- **Vocabulário de cozinha**: agua purificada (não filtrada), lumbre (não fogo), olla, refrigerador, nutriólogo (não nutricionista).
- **Aviso legal mexicano**: incluir "Este producto no es un medicamento" + a fórmula da COFEPRIS *"El consumo de este producto es responsabilidad de quien lo recomienda y de quien lo usa."*
- **Pagamento**: PIX não existe. É SPEI/CLABE, CoDi (QR), depósito em OXXO, dinheiro.
- **Espanhol ocupa ~20% mais espaço que português** — página 5 do Chá estourou o rodapé. Sempre renderizar e conferir.

## Decisão importante (2026-08-20)
`Downloads\SALGADOS ASSADOS_PT1 (2).pdf` (92 págs) **não é material do Gabriel** — é a apostila "salgados de maria" / MV Business, com aviso de direito autoral e marca d'água antipirataria (PIX e @ da autora queimados nas páginas). Recusei traduzir por completo (obra derivada) e escrevi no lugar o ebook original acima. Ele pediu duas vezes e não respondeu se tem direito de revenda — **se ele confirmar que tem licença/PLR, dá para fazer o pacote inteiro**.

Além do direito autoral, o conteúdo não transferia: coxinha, risole, empada, esfirra e requeijão não são referência no México. O equivalente que vende em charola lá é empanada, tamal, concha/pan dulce, tlacoyo, quesadilla e torta.

Pipeline técnico igual ao de sempre: [[pipeline-pdf-windows]].

## Espionagem de concorrência (2026-08-21)
Analisei 25 anúncios ativos de 3 operações de infoproduto no México pela Biblioteca de Anúncios. Playbook completo publicado: https://claude.ai/code/artifact/61f4e546-204a-4baf-91f6-8bfdf2c3b756

Páginas: `564424313425179` Entre Hilos y Arte (crochê, campeão 282 dias) · `844952698707092` Academia Saludable ACC (horta, 95 dias) · `460209863838057` Dulc3mprendimiento (confeitaria, 126 dias).

Achados que valem pra qualquer copy dele no México:
- **Academia Saludable roda 7 anúncios com a copy idêntica ao caractere** — só troca o vídeo. Travar a copy vencedora e testar só criativo é o processo certo.
- **Mecanismo "Recibe primero, aporta después"**: entrega o PDF antes, a pessoa paga o que achar justo depois. Roda há 95 dias. É a melhor jogada pro Gabriel porque contorna o atrito de SPEI/OXXO (o pagamento acontece depois da entrega) e o custo de quem não paga é zero em PDF.
- **"Desde cero" e "sin experiencia"** são as expressões mais repetidas dos 25 anúncios — a objeção nº1 do mercado é "eu não sei fazer".
- CTA nunca manda comprar, sempre convida a conversar ("Escríbenos", "Mándanos mensaje") e nomeia o botão fisicamente.
- Entrega por WhatsApp é escrita como **vantagem**, não detalhe operacional.
- "Emprender" é identidade, não jargão — está até no nome da página Dulc3**mprendimiento**.

**Limitação técnica confirmada**: a Biblioteca de Anúncios trunca o destino dos anúncios click-to-WhatsApp (o href é só `api.whatsapp.com/send`, sem `phone=` nem `text=`). Não dá pra extrair o número por scraping — nem logado, nem na página de detalhe. Pra entrar no funil tem que mandar DM no Instagram e deixar eles passarem o contato.

## O que separa um criativo bom de um que gera desejo (25/08/2026)

Três correções que o Gabriel aprovou na v3 do criativo "presentación". Valem
como padrão para os próximos:

1. **Abrir em apetite, não em produção.** Massa crua no gancho contradiz a copy
   quando ela diz "não é a sua comida que está errada". Puxada de queijo, close
   de recheio, mordida — nos primeiros 2s, com zoom que entra rápido e segura.

2. **Todo gráfico que mostra o problema precisa do par que mostra a saída.**
   O gráfico de comparação de preços (a cliente escolhe a mais barata) só ficou
   completo quando entrou o do reframe: `12 PIEZAS SUELTAS $96 / LA MISMA
   CHAROLA $180 / +$84 EL MISMO TRABAJO`. Os números se ligam de propósito —
   o $96 é 12 × o $8 que aparece no gráfico anterior.

3. **Gente reagindo.** Os cortes só de produção não criam vontade. Reservar as
   tomadas de mordida/saboreio para o bloco de payoff e para o fecho.

Padrão de legenda que ficou: Arial 64, caixa alta, contorno 7, MarginV 430,
palavra-chave em âmbar `&H00C8FF&`.

## Receita de criativo que fechou (26/08/2026)

Quatro criativos entregues e aprovados. O que se repetiu nos três últimos:

**Gancho (0-5s)** — abrir no *assunto da primeira frase*, não em b-roll bonito.
Se a copy fala de calcular preço, abre na calculadora. Três cortes rápidos com
zoom `punch` (entra em 0,3s e segura): tese → produto → rosto.

**Todo gráfico de problema precisa do par que resolve.** Espiral do preço caindo
→ ficha com a ganancia. Comparação de preços → reframe do +$84. Os números se
ligam de propósito entre os dois cards.

**Rosto e mordida.** Só produto e mãos não segura. Reação entra no gancho, no
payoff e no fecho.

**Buraco de mais de 5s sem gráfico = queda.** Se dois cards fortes ficam
distantes, um card curto no meio faz a ponte ("¿CUÁNTO GANASTE? ???").

**CTA acelera**: cortes de ~1,6s no lugar de 2,4s no bloco final.

### Duas travas no script de montagem que pegaram erro de verdade
1. **Colisão de takes** contra a lista de intervalos já usados em outro criativo
2. **Corte estourando o fim do clipe** (`t + d > duração`) — pegou dois casos

### Varredura obrigatória antes de entregar
Contact sheet do vídeo inteiro procurando: texto em português, marca d'água de
terceiro, marca comercial em destaque, legenda queimada brigando com a minha,
rosto identificável. Já barrou: `@ArmandoFelipeReceitas`, "Olara Vanilla",
"VIGGIANO", "Narcisa", pote "MIX PIMIENTAS", garrafa Modelo, link do Drive
exposto e capa "SALGADOS FRITOS NA BANDEJA" em português.

### O TTS lê as anotações de direção
Aconteceu no `audio mexico 3.mp3`: os últimos 13,4s eram a narradora lendo
"Prova visual recomendada: mostrar calculadora confusa...". Sempre checar o fim
do áudio com `silencedetect` antes de montar.
