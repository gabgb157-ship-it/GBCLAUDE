O funil de WhatsApp do Gabriel roda no **Leona Flow** (app.leonasolutions.io; API em apiaws.leonasolutions.io).
Ele loga; eu nunca entro com senha. O token fica no localStorage da página e só é usado dentro dela.

**Ler um fluxo inteiro:** no editor (`/flows/<id>/edit`), a fibra React de `.react-flow` tem `memoizedProps.nodes`
e `.edges` com todas as ações (`data.actions`, com `action_type` + `config`). Blocos fora da tela não ficam no DOM:
usar os props, não `querySelectorAll`. Pra tirar texto grande da página: jogar num `<pre>` dentro de `<main>` e usar
get_page_text (o retorno do javascript_tool corta em ~1000 caracteres).

**Endpoints que o editor usa** (descobertos espiando o fetch ao salvar):
- `GET  /api/v1/flows/<flow>/flow_nodes/<node>` → ações do bloco
- `PATCH /api/v1/flows/<flow>/flow_nodes/<node>/actions/<id>` body `{flow_node_action:{action_type,config,order}}`
- `POST /api/v1/flows/<flow>/flow_nodes/<node>/add_action` (mesmo body)
- `DELETE /api/v1/flows/<flow>/flow_nodes/<node>/actions/<id>`
- `POST /api/v1/flows/<flow>/flow_connections` body `{flow_connection:{from_node_id,to_node_id,condition_type:"timeout_or_unknown",condition_config:{type:"timeout_or_unknown",value:null,response_type:"timeout",source_handle:"timeout"}}}` (ligação da saída "passou o tempo"; no UI é arrastar do ponto de baixo do bloco de espera até o ponto de entrada do destino)
- `GET/POST /api/v1/products` (produto do bloco "venda aprovada"), `GET /api/v1/pixel_configs`

**Armadilha:** o PATCH faz merge do config e **ignora `media_file_info`** — trocar um PDF/áudio por PATCH muda o
nome mas mantém o arquivo antigo. Pra trocar mídia: apagar a ação e criar de novo (add_action). Texto por PATCH é ok.

**Não sair testando endpoints** com o token: o classificador do auto mode bloqueia ("Credential Exploration").
Usar só os endpoints acima, que são os do próprio editor.

**Bug que já aconteceu (21/09):** bloco de espera sem saída de timeout = lead que não responde fica parado pra sempre
e o remarketing (entrada TAG CHAMADA1) nunca dispara. Ao montar/duplicar funil, conferir se toda espera tem as duas saídas.

**Suspeita das vendas sem marcar (21/09):** o bloco de IA principal que lê o comprovante (3.0: 4637537; 4.0: 4654362)
veio do modelo do fígado com `gpt-5.4-pro` e sem saída de erro; os outros leitores de comprovante usam gpt-4.1.
Uma lead (4.0) mandou o comprovante, recebeu o ✅ e o funil parou. Também: a espera de 2 h depois do
"Combinamos que o Pix…" (3.0 4637532 / 4.0 4654357) não tem saída "respondeu". Corrigido nos dois em 21/09
(modelo → gpt-4.1, saída ligada, remarketing V2 30min/30min/1h com foto do microondas). O auto mode bloqueava;
ele passou a sessão pra ignorar permissões e deu acesso total pra editar sites que ele pedir.
Ligação "respondeu": condition_type "always", condition_config {type:"always",value:null,response_type:"client-response",source_handle:"client-response"}.

Duplicar fluxo: menu "Mais opções" da lista → Duplicar. **O duplicado nasce ATIVO** — pausar na hora.
Ver [[funil-whatsapp-blocos-ia]] e [[projeto-equipe-agentes-vturb]].
