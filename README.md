# OAuth client metadata

OAuth Client ID Metadata Documents for the Proteos agent service's MCP OAuth connect flow.

Some MCP authorization servers (for example Freckle's, on Clerk) do not offer dynamic client registration and instead accept an https URL as the `client_id`: the authorization server fetches the JSON document at that URL and checks the redirect URI against it. Each document's `client_id` is its own URL, so each environment has its own file:

| Environment | client_id | redirect URI |
|---|---|---|
| prod | `https://proteos-ai.github.io/oauth-clients/proteos-mcp-client.json` | `https://api.proteos.ai/agents/v1/mcp-servers/oauth/callback` |
| staging | `https://proteos-ai.github.io/oauth-clients/proteos-mcp-client-stg.json` | `https://api.stg.proteos.ai/agents/v1/mcp-servers/oauth/callback` |

Use the URL as `auth.oauth.client_id` with `registration_mode: "manual"` on the MCP server row. These are public clients (`token_endpoint_auth_method: none`, PKCE); the documents contain no secrets.
