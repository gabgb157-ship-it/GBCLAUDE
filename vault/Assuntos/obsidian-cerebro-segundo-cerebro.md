---
tags: [feedback, memoria-claude]
fonte: "Claude Code (migrado em 2026-09-17)"
---

# Obsidian como segundo cérebro
O Gabriel conectou um servidor MCP chamado **"obsidian"** ao Claude Code (registrado em `~/.claude.json`, escopo *user*, disponível em todos os projetos) em 2026-09-17. Ele usa o plugin do Obsidian **"Local REST API with MCP"** (Adam Coddington), servidor HTTP local na porta `27123`, autenticado por Bearer token. Quando esse servidor aparecer na lista de ferramentas MCP deferidas de uma sessão (buscar via ToolSearch por "obsidian" caso ainda não tenha carregado), ele deve ser usado como memória de longo prazo externa — o "cérebro" do Gabriel.

**Regras de uso, conforme ele pediu:**
- Salvar **automaticamente**, sem precisar que ele diga "guarda isso" toda vez — julgar o que vale a pena guardar (decisões, fatos, preferências, contexto de projeto) da mesma forma que já decido o que vai pra minha própria memória interna.
- Organizar em **dois formatos ao mesmo tempo**:
  1. **Diário por data** (uma nota por dia, ex: `2026-09-17`) com o que rolou nas conversas daquele dia.
  2. **Notas por assunto/projeto** (ex: "Chá Seca-Barriga", "Tráfego X1") que vão sendo **atualizadas/expandidas** ao longo do tempo — não recriadas do zero a cada conversa.

**Why:** ele quer parar de perder contexto entre conversas e ter uma base de conhecimento pesquisável e visual (usa o Graph View do Obsidian) além da minha memória interna em texto puro.

**How to apply:** em qualquer sessão nova, ao identificar algo que vale registrar, usar as ferramentas MCP do Obsidian pra (a) fazer append na nota do dia corrente e (b) criar ou atualizar a nota de assunto relevante — sem perguntar antes, só avisando brevemente que salvou. Isso é complementar à minha memória interna (`[[MEMORY.md]]`), não substitui ela: seguir salvando aqui também quando fizer sentido (padrões de comportamento, preferências que valem pra qualquer projeto).

**Nota técnica:** essa integração só entra em vigor em sessões **novas** — sessões já abertas antes do registro do MCP não carregam a ferramenta. Se em algum momento o servidor aparecer como desconectado, o Gabriel provavelmente fechou o Obsidian ou desligou o toggle "Enable non-encrypted (HTTP) server" nas configurações do plugin — ele precisa estar aberto com o plugin ativo pra API responder.
