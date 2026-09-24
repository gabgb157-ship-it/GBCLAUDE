---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Hotmart: OXXO no México
Na config de checkout da Hotmart **não existe uma opção chamada "OXXO"**. Quem
procura por esse nome conclui que a plataforma não aceita e vai atrás de outro
gateway. O OXXO é o que a caixa **`offerBillet` ("Boleto Bancário")** vira quando
o comprador é mexicano. O rótulo diz: Brasil (Boleto), Chile (Sencillito),
Colômbia (Efecty), **México (OXXO)**, Peru (PagoEfectivo), Portugal (Multibanco).

Outros mapeamentos do mesmo menu:
- `offerDirectDebit` ("Débito Bancário") = **SPEI** no México
- `offerHybrid` ("Pagamento Híbrido") = cartão + OXXO
- `offerMercadoPago` = exclusivo México e Argentina

Dois detalhes que derrubam OXXO sem aviso:
1. **"Dias em que o boleto estará disponível"** vale pro OXXO também. Se sábado e
   domingo estiverem desmarcados, a opção some do checkout no fim de semana.
2. Definir **"Principal país para vendas" = México** na criação do produto já faz
   a Hotmart nascer com `offerBillet` e `offerBilletMobile` ligados. Se o país
   ficar Brasil, nascem desligados — foi o que aconteceu no MAGNETÍZALOVE.

O campo **Valor** preenche da direita pra esquerda: digitar "100" resulta em
1,00. Para 100,00 tem que digitar "10000".

Ver [[projeto-mercado-mexico]].

## IVA mexicano: 16% POR CIMA, não embutido

Venda pro México leva **+16% de IVA somado ao preço base**, não embutido. Base de
$100 vira **$116,00 no "Total a Pagar"**. A caixa "Incluir impostos no preço" do
cadastro não resolve — ela diz literalmente *"exceto para vendas no México"*.

Para o comprador ver um número redondo, a base tem que ser o valor **dividido por
1,16**: para fechar em $100,00, base = **$86,21**.

Em ago/2026 o Gabriel optou por deixar base $100 (checkout $116) e avisar o valor
na conversa antes de mandar o link, porque o criativo em vídeo e o banner têm
"100 pesos" queimado na imagem.

## Produto RECETARIO DE BOTANAS PARA VENDER

ID 8382691 · base $100 MXN · checkout `pay.hotmart.com/R107310071K`
Métodos ativos no checkout mexicano: Débito/Crédito, OXXO, Mercado Pago, SPEI, PayPal.
O rótulo `payment_data.section_title_v2` que aparece na linha do OXXO é bug de
i18n da Hotmart — o logo renderiza normal, a opção funciona.
