# Integrações (MCP comunitários)

Todos os servidores abaixo são **comunitários, não oficiais**. Revise o código e o status de manutenção antes de instalar, e teste primeiro em projetos descartáveis.

| Ferramenta | Servidor sugerido | Uso | Observações |
|---|---|---|---|
| CapCut | [MigueDuque/capcut-mcp-server-extended](https://github.com/MigueDuque/capcut-mcp-server-extended) | Edição de rascunhos, tipografia, animações, Reels/Shorts | Node 18+, CapCut desktop. **Feche o projeto no CapCut antes de editar** (autosave sobrescreve). Alternativa: [JmsLdrn/capcut-mcp](https://images.glama.ai/mcp/servers/JmsLdrn/capcut-mcp). |
| ArtCraft | [theCosmicCrafter/artcraft-mcp](https://github.com/theCosmicCrafter/artcraft-mcp) | Geração de imagem, vídeo e 3D (thumbnails, B-roll) | Consome créditos da assinatura. Alternativa: [smoermeow/artcraft-mcp](https://github.com/smoermeow/artcraft-mcp). MCP oficial ainda em [proposta](https://github.com/storytold/artcraft/issues/2003). |
| YouTube | youtube-studio-mcp ([Glama](https://glama.ai/mcp/servers/o4o0o9tw5i)) | Data API v3 + Analytics API (OAuth2), métricas e edição de metadados; inclui 8 skills | Alternativa só-leitura por padrão: sigvardt/youtube-mcp ([Glama](https://glama.ai/mcp/servers/oz1i7kbfl7)). |
| Instagram | instagram-claude-mcp ([Glama](https://glama.ai/mcp/servers/e5q85izsj9)) | Insights de conta e posts (somente leitura, Graph API oficial) | Requer conta Business/Creator ligada a página do Facebook e app Meta. Para publicar: [aleemhaider/instagram-mcp](https://mcpservers.org/ru/servers/aleemhaider/instagram-mcp). |

## Configuração

Copie `.mcp.json.example` para `.mcp.json` (fica fora do git) e ajuste caminhos e credenciais conforme o README de cada servidor. Os **nomes** dos servidores (`capcut`, `artcraft`, `youtube`, `instagram`) devem ser mantidos, porque o agente `edicao` referencia `mcp__capcut__*` e `mcp__artcraft__*`.

CapCut e ArtCraft rodam **na máquina onde os apps estão instalados** — use esses agentes no Claude Code local (desktop/CLI), não numa sessão em nuvem.

## Como os agentes usam

| Agente / skill | Integrações |
|---|---|
| `briefing-video-horizontal` | youtube (referências e métricas), WebSearch |
| `briefing-video-vertical` | youtube, instagram (Reels/Shorts), WebSearch |
| `briefing-criativo-imagem` | artcraft, WebSearch |
| `edicao` | capcut (16:9 e 9:16), artcraft |
| `buscar-referencias-video` | WebSearch, youtube |
| `buscar-referencias-visuais` | WebSearch, artcraft (prompts) |
