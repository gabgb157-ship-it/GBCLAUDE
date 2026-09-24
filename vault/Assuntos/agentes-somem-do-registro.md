---
tags: [reference, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Agentes somem do registro
Em 12-13/09/2026, 5 agentes do setor (estrategia-visual, ganchos, critico-copy, x1-conversa,
lente-cena) sumiram da lista de subagent_type disponivel, com os arquivos intactos no disco (mesmo
frontmatter, sem BOM, CRLF igual aos que funcionavam).

**Reescrever os bytes pelo Bash/python NAO reinscreve.** O que funcionou: **Read do arquivo inteiro e
Write com o mesmo conteudo pela ferramenta Write** - o registro recarrega na hora ("New agent types
are now available").

**Como aplicar:** se um Agent falhar com "Agent type 'x' not found" e o arquivo existir em
C:/Users/gabgb/.claude/agents/, fazer Read + Write dele antes de relancar. Conferir a lista de
agentes do setor contra [[projeto-equipe-agentes-vturb]].
