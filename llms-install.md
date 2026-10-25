# Installing Terminal Tax

There is nothing to install. Terminal Tax is a hosted remote MCP server at `https://mcp.terminal.tax/v1/hosted-mcp`
(Streamable HTTP), with no account, API key, OAuth or restart. Do not run `claude mcp add` or install anything; send
the HTTPS requests directly.

Each request is a JSON-RPC 2.0 POST to `https://mcp.terminal.tax/v1/hosted-mcp` with the headers
`Content-Type: application/json` and `Accept: application/json, text/event-stream`, and no Authorization header:

```sh
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-11-25","capabilities":{},"clientInfo":{"name":"filing-agent","version":"1"}}}'
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":2,"method":"tools/list"}'
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":3,"method":"tools/call","params":{"name":"create_filing_session","arguments":{}}}'
```

The third request creates the filing session: it carries no tax data and returns a continuationHandle. Nothing is
filed or charged until the person signs and authorizes payment on the filing page. The full guide for agents is
https://terminal.tax/llms.txt.

Optional, not needed to file: an MCP client that you want to keep the server in (Cline and similar) can add one
remote server named `terminal-tax` with the URL above, Streamable HTTP transport and no authentication.
