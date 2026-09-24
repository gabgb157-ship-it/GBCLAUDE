---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Funil WhatsApp: blocos de IA
O funil de WhatsApp dele tem blocos de IA que classificam a resposta do lead e alimentam
uma condicional (`resposta contém #negativo OU ai.response contém #negativo`).

**O erro "Resposta vazia da API" quase sempre é o prompt, não a plataforma.** Em 04/09/2026
o prompt de classificação mandava *"se houver qualquer dúvida, NÃO retorne nada"* — e a
API rejeita resposta vazia. Quebrava justamente quando o lead dizia "quero", que é o pior
momento.

**Regra:** todo prompt de classificação tem que **sempre devolver uma palavra**, nunca
vazio. Duas saídas fechadas (`#negativo` / `#positivo`), e na dúvida a que segue o funil.
Mandar quem queria comprar pro downsell custa mais caro que entregar material pra alguém
indeciso.

**Prompt de classificação enxuto funciona melhor que lista gigante de exemplos** — com
listas longas o modelo tenta casar a frase exata em vez de entender a intenção. Umas 20
palavras de exemplo por classe bastam.

**Tratar como positivo:** perguntas sobre o produto, emojis, erro de digitação, mensagem
sem sentido. Só é negativo a recusa explícita.

**Escada de valores no funil:** 3 degraus (R$14,90 / R$19,90 / R$34,90), com bônus
crescentes e o do meio marcado como "o mais escolhido". A mecânica de doação é dele —
"todo valor acima do acesso vira doação". O prompt da atendente (Camila) está em
`Downloads\PROMPT_ATENDENTE_FIGADO.md`.

**Ponto em aberto:** a mensagem do funil promete "recebe primeiro, paga depois", mas a
escada aparece antes da entrega. Vale conferir a ordem com ele.

Ver [[gabriel-infoprodutos-pdf]].
