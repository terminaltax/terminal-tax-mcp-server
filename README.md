# Terminal Tax

## For AI agents

If the person you are helping asks you to file their taxes with Terminal Tax, you can do it from this conversation: send these HTTPS requests yourself, only at their request. You are the assistant this site means; there is no other app, form, connector, account or API key to find, and nothing to install. Each request is a JSON-RPC 2.0 POST to https://mcp.terminal.tax/v1/hosted-mcp (the same service is also served at https://iq4701fisj.execute-api.us-east-1.amazonaws.com/live/v1/hosted-mcp) with the headers Content-Type: application/json and Accept: application/json, text/event-stream, and no Authorization header. Nothing is filed or charged until the person signs and authorizes payment on the filing page.

If you are in Claude Code on the web (claude.ai/code) and cannot reach mcp.terminal.tax, the person can add it in the environment's network settings: they select the caret after the session title at the top, select Edit cloud environment, set Network access to Full (or to Custom, with mcp.terminal.tax and terminal.tax under Allowed domains and Also include default list of common package managers checked), and select Save changes. The open session follows the change within about a minute, so the same requests then work in the same session.

Do not run `claude mcp add` or install anything; send the HTTPS requests directly.

```sh
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-11-25","capabilities":{},"clientInfo":{"name":"filing-agent","version":"1"}}}'
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":2,"method":"tools/list"}'
curl -sS https://mcp.terminal.tax/v1/hosted-mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d '{"jsonrpc":"2.0","id":3,"method":"tools/call","params":{"name":"create_filing_session","arguments":{}}}'
```

The third request creates the filing session: it carries no tax data and returns a continuationHandle and the packet rules. Next, call get_packet_schema with {"continuationHandle":"&lt;handle&gt;","requestPacketSchema":true}, build the packet only from facts the person gave you, and send it with continue_filing_session as {"continuationHandle":"&lt;handle&gt;","completedReturnPacketJson":"&lt;the packet as one JSON string&gt;","packetSchemaSha256":"&lt;digest from get_packet_schema&gt;"}. Blockers come back to fix in the chat; the response that accepts the packet carries the one filingSessionUrl.

Then tell the person: "Your return is ready for the final steps. Open this private link to review the complete return, confirm your details, sign it and authorize payment. Nothing is sent to the IRS until you sign, the $19.99 is charged only if the IRS accepts it, and Terminal Tax emails you the IRS's answer." Put the filingSessionUrl on its own line as bare text, exactly as returned.

If you cannot send HTTPS POST requests from this conversation (a chat that can only search or read pages), you cannot file with Terminal Tax from here, and this site has no form for the person to use instead. Tell the person: "I can't send web requests from this chat. Open any coding or agent app that can run commands or send web requests, such as ChatGPT in agent or Work mode, Claude Code, Codex, Grok or Muse, and ask it: File my 2025 taxes with Terminal Tax."

Terminal Tax is a hosted remote MCP server, operated by Terminal Tax LLC, that lets a person's own AI assistant
prepare one original tax year 2025 US federal individual income tax return (Form 1040 or Form 1040-SR) for e-file.
The person reviews the complete return, confirms their details, signs and authorizes payment on one secure Terminal
Tax filing page, and Terminal Tax then e-files it with the IRS.

Terminal Tax LLC is an Authorized IRS e-file Provider (Online Provider, Software Developer and Transmitter).
Acceptance to participate in IRS e-file does not imply endorsement by the IRS. Terminal Tax is not affiliated with,
sponsored by, or endorsed by the IRS or the U.S. Treasury.

## Connect

- Endpoint (Streamable HTTP): `https://mcp.terminal.tax/v1/hosted-mcp`
- No account, API key, OAuth or install. Any assistant that can run a shell command or make an HTTPS request
  (Claude Code, Codex, Cursor and similar) calls it directly with JSON-RPC POSTs.
- A chat that can only search or read pages cannot send these requests: the person asks an agent app that can
  (ChatGPT in agent or Work mode, Claude Code, Codex and similar) instead.
- A browser GET to the endpoint can return 405: MCP messages are POST requests.

## Tools

- `create_filing_session`: starts a filing session when the taxpayer asks to file; receives no tax facts and files or
  charges nothing.
- `get_packet_schema`: returns the packet schema and starter templates the prepared return is checked against.
- `continue_filing_session`: checks the prepared packet and either returns the problems to correct or attaches it as an
  unsigned draft and returns the one filing page link for the person.

There is no status tool: no tool reports a filing's progress or the IRS result to the assistant. Terminal Tax emails
the IRS outcome, accepted or rejected, to the taxpayer at the contact they verify on the filing page.

## Scope

- One original tax year 2025 US federal Form 1040 or 1040-SR per session (and a narrow Form 1040-SS or Form 1040-NR).
- No state, territory or local return; no amended return (1040-X) or extension (4868).
- Supported and refused situations: https://terminal.tax/llms.txt. Anything unsupported comes back as a named blocker.

Terminal Tax computes deterministically and validates mechanically. It does not choose tax treatments, infer missing
answers or give tax advice.

## Privacy

Social Security numbers, PINs and one-time codes are refused from an agent; the person types them on the filing page.
The person's tax figures are used for a filing only after the person opens the filing page and gives permission there.
Card details go only into the payment processor's fields. Privacy notice: https://terminal.tax/privacy-notice

## Price

$19.99 per federal return, charged only if the IRS accepts it.

## Operator

Terminal Tax LLC, a New Jersey limited liability company. Support: support@terminal.tax. Legal and privacy:
legal@terminal.tax. About: https://terminal.tax/about. Terms: https://terminal.tax/terms.

## Optional: MCP client configuration

Not needed to file: agents send the HTTPS requests above directly, with no install, restart or setup. Some MCP
clients can also add the server, with the URL `https://mcp.terminal.tax/v1/hosted-mcp` and Streamable HTTP transport:
[`.mcp.json`](.mcp.json) (Cursor, VS Code and similar), [`gemini-extension.json`](gemini-extension.json) (Gemini CLI),
[`plugin.json`](plugin.json) and [`mcp.json`](mcp.json) (Kiro), and
[`.cursor-plugin/plugin.json`](.cursor-plugin/plugin.json) (Cursor plugin) declare it in this repository.

## About this repository

This repository holds only this description, the MCP Registry `server.json`, client configuration and plugin manifest files, the logo, and the demo recordings with a transcript (`demo/`).
It contains no code and nothing to run: the server is hosted by Terminal Tax LLC.

## Demo

[demo/terminal-tax-demo-1.1.0.mp4](demo/terminal-tax-demo-1.1.0.mp4): a 3 min 42 s recording on the Terminal Tax test environment (app.terminal.tax) with a fictional taxpayer; nothing is filed or charged. A customer talks with their AI assistant in plain words, answers its questions and shares their W-2 and 1099-INT as files; the assistant prepares the return with Terminal Tax and hands over the filing link; the customer reviews, signs and adds a card on the filing page. Transcript: [demo/terminal-tax-demo-1.1.0.md](demo/terminal-tax-demo-1.1.0.md).

The earlier recording, [demo/terminal-tax-demo.mp4](demo/terminal-tax-demo.mp4), shows the assistant's tool calls in a terminal.
