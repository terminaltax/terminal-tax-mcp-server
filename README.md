# Terminal Tax

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
- Claude.ai and ChatGPT in a web browser add the same address as a custom connector; steps at
  https://terminal.tax/integrations.
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

- One original tax year 2025 US federal Form 1040 or 1040-SR per session (and a narrow Form 1040-SS).
- No state, territory or local return; no amended return (1040-X), extension (4868) or Form 1040-NR.
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

## Client configuration

Claude Code:

```sh
claude mcp add --transport http terminal-tax https://mcp.terminal.tax/v1/hosted-mcp
```

Codex:

```sh
codex mcp add terminal-tax --url https://mcp.terminal.tax/v1/hosted-mcp
```

Cursor, VS Code and other clients that read `.mcp.json`: see [`.mcp.json`](.mcp.json) in this repository.

Gemini CLI:

```sh
gemini extensions install https://github.com/terminaltax/terminal-tax-mcp-server
```

Kiro: Powers > Add Custom Power > Import power from GitHub, with this repository's URL (it reads
[`plugin.json`](plugin.json) and [`mcp.json`](mcp.json)).

Cursor plugin: [`.cursor-plugin/plugin.json`](.cursor-plugin/plugin.json) declares the same remote server.

Cline: add a remote server named `terminal-tax` with the URL above and Streamable HTTP transport, or from the Cline CLI:

```sh
cline mcp add terminal-tax https://mcp.terminal.tax/v1/hosted-mcp --transport streamableHttp --yes
```

## About this repository

This repository holds only this description, the MCP Registry `server.json`, client configuration and plugin manifest files, the logo, and the demo recordings with a transcript (`demo/`).
It contains no code and nothing to run: the server is hosted by Terminal Tax LLC.

## Demo

[demo/terminal-tax-demo-1.1.0.mp4](demo/terminal-tax-demo-1.1.0.mp4): a 3 min 42 s recording on the Terminal Tax test environment (app.terminal.tax) with a fictional taxpayer; nothing is filed or charged. A customer talks with their AI assistant in plain words, answers its questions and shares their W-2 and 1099-INT as files; the assistant prepares the return with Terminal Tax and hands over the filing link; the customer reviews, signs and adds a card on the filing page. Transcript: [demo/terminal-tax-demo-1.1.0.md](demo/terminal-tax-demo-1.1.0.md).

The earlier recording, [demo/terminal-tax-demo.mp4](demo/terminal-tax-demo.mp4), shows the assistant's tool calls in a terminal.
