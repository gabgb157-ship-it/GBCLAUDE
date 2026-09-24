Gabriel aprovou com elogio forte o V020 (carro) e o V021 (tela dividida) em 15/09/2026
("ficou muito bom mesmo, tá de parabéns"). Entregues em `Downloads\TESTE PUDIM FORMATOS NOVOS\`.

O que repetir:
- editar DENTRO do CapCut (ele quer ver o projeto lá) via `montar`, com motion do Remotion como camada
- cortar todo silêncio de voz+boca e acelerar (V020 1.2x, V021 1.1x — ele diz a velocidade por criativo)
- voz final vem do MP3 original alinhado ao lipsync (qualidade melhor que o áudio do avatar)
- motion que "conta" a fala: lista com X/✓, contador 30→100, carimbo ESGOTADO, mensagens chegando,
  etiqueta de preço, setinha de mouse clicando no selo do Zap junto com o som de clique
- efeitos sonoros e música da BIBLIOTECA DO CAPCUT (ele assinou o Pro e pediu isso)
- música com arco: animada no gancho, baixa na parte triste, cresce na virada
- takes "chamativos" e variedade de receitas (coco, maracujá) quando a fala é "100 receitas"
- sem ovo, fogão aceso ou forno; legenda queimada/@/logo cortados; tudo conferido quadro a quadro
- entrega em H.264 1080x1920 −14 LUFS + PNG do primeiro frame, na pasta da leva

- V022 (mudo, cartelas): ele achou que sem som "não converte" e pediu música de fundo + efeito em cada
  animação/cartela; aprovou ("agora sim ficou muito melhor"). Mesmo quando o pacote do editor diz "sem som",
  pôr música animada (batida alinhada aos cortes, abafada na parte triste) e efeitos sincronizados.
- cena que falta no material (ex.: mãos tristes na mesa) ele aceita feita em motion no Remotion

- **Renovar os motions a cada 2 criativos** (pedido dele no V023): não repetir o mesmo pacote de
  animações em todos; a cada dois vídeos, trocar estilo/peças novas, senão "fica tudo a mesma coisa".
  Pares até agora: V020/V021 tarjas Arial Black + lista/contador; V022/V023 cartelas, manchete, tarja ERRO;
  **V024/V025 "caderno e caneta vermelha"** (remotion-criativos `src/pecas/V024.tsx` + `V024Cenas.tsx`:
  risco de canetão, tira de papel pautado rasgado com fita crepe, post-it, caça-níquel no 100, cupom de
  maquininha no preço, seta de canetão no CTA, fontes Ink Free e Consolas). V026 muda de novo.
- **Música nunca repete entre criativos** (ele notou V022 e V023 com a mesma faixa). Já usadas: "Inspiration
  Epic" (V021), "Motivational Inspiring Corporate Upbeat Uplifting" (V022/V023), "Paradise Modern Light Energy
  Positive Dance" (V024, cortada em 3 pedaços: 1ª virada no gancho, parte calma na tristeza, 2ª virada na virada).
- V024 (18/09): legenda branca com SÓ a palavra-chave amarela (kit: "destaques" no texto), cenas que faltam
  feitas em motion (fogão riscado, mesa à noite, portão, porta, WhatsApp) e varredura de todo o estoque atrás de
  trechos ainda não usados. Legenda: medir largura na Arial Black e dividir a frase em pedaços equilibrados.
- O PDF "Pudim Sem Forno – Faça e Venda" tem 32 páginas e receitas com OVOS e calda no FOGO (ex.: Pudim de Coco)
  — contradiz "não leva ovo / sem fogo / 100 receitas". Nunca mostrar página de receita nem o contador "x de 32".
- Texto de tarja nunca pode vazar a tela: calcular o tamanho da fonte pela largura real (PIL + ariblk)
  antes de renderizar — ele reclamou do CTA do V023 estourando as bordas.

**Why:** foi o padrão que ele validou depois de várias rodadas; mudar o estilo sem pedido arrisca retrabalho.
**How to apply:** nos próximos (V022–V024 e outras ofertas) partir desse pacote; perguntar só velocidade e
materiais faltantes. Ver [[capcut-kit-windows]], [[remotion-motion-criativos]], [[triagem-broll-anuncio]].
