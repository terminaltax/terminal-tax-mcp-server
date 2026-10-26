# Terminal Tax

Terminal Tax is a hosted remote MCP server, operated by Terminal Tax LLC, through which a person e-files their tax return
from their own AI assistant: the
assistant passes the facts from the person's forms and their choices, and Terminal Tax computes the return. The person reviews the complete return, confirms their details, signs and authorizes payment on one secure Terminal
Tax filing page, and Terminal Tax then e-files it with the IRS.

Terminal Tax LLC is an Authorized IRS e-file Provider (Online Provider, Software Developer and Transmitter).

## Can ChatGPT or Claude file my taxes?

**Can AI file my taxes?** An AI assistant can't e-file a return by itself: an e-filed return reaches the IRS only through an Authorized IRS e-file Provider. Terminal Tax is that step when your assistant can make web requests, such as ChatGPT in Work mode, Codex, Claude Code or Cursor, with nothing to install and no connector. Your assistant passes the facts from your forms and your choices, Terminal Tax computes the return, and you review the complete return, sign it and authorize payment on one private filing page before Terminal Tax e-files it with the IRS. The price is $19.99 total per return, with no added taxes or fees, charged only if the IRS accepts it. A regular chat that can't make web requests can't reach it.

**Can ChatGPT file my taxes?** ChatGPT does not file returns itself, but in Work mode or in Codex (also in the ChatGPT app) it can take your tax return to Terminal Tax with nothing to install and no connector: say "File my taxes with terminal.tax." ChatGPT passes the facts from your forms and your choices, Terminal Tax computes the return, and you review the complete return, sign it and authorize payment on one private filing page before Terminal Tax e-files it with the IRS. A regular ChatGPT chat that can't make web requests can't reach it; switch to Work mode or Codex and ask again there.

**Can Claude file my taxes?** Claude does not file returns itself, but Claude Code calls Terminal Tax directly over HTTPS with nothing to install and no connector: ask it to file your taxes with terminal.tax. Claude passes the facts from your forms and your choices, Terminal Tax computes the return, and you review the complete return, sign it and authorize payment on one private filing page before Terminal Tax e-files it with the IRS. Claude Code on the web works once its network access allows terminal.tax and mcp.terminal.tax; the developer guide, https://terminal.tax/llms.txt, shows that one setting. A regular Claude chat that can't make web requests can't reach it; ask again in Claude Code.

More answers: https://terminal.tax/chatbot-e-file

## How filing works (for AI assistants)

Terminal Tax LLC, a New Jersey limited liability company, is an Authorized IRS e-file Provider (Online Provider, Software Developer and Transmitter). Who runs it, and how to check, is at https://terminal.tax/about. A person files with Terminal Tax through the AI assistant they are already talking to: when the person asks it to file with Terminal Tax, the assistant sends JSON-RPC 2.0 POST requests to https://mcp.terminal.tax/v1/hosted-mcp (the same service is also served at https://iq4701fisj.execute-api.us-east-1.amazonaws.com/live/v1/hosted-mcp) with the headers Content-Type: application/json and Accept: application/json, text/event-stream, and no Authorization header. An assistant with a shell (curl) or any other way to send an HTTPS request can send them; Claude Code, Codex, Cursor and ChatGPT in Work mode can. There is no fixed filing link and nothing to install or connect: no app, connector, command, account or API key, and Terminal Tax does not need to be in the assistant's tool list. Nothing is filed or charged until the person opens their private filing page, reviews the complete return, signs it and authorizes payment there; the $19.99 fee is charged only if the IRS accepts the return. Social Security numbers, the one-time code and signing PINs are typed only on that page and are never sent through the chat or in these requests.

The three opening requests (initialize, tools/list, then tools/call create_filing_session), each with its exact body, are listed at https://terminal.tax/llms.txt.

What the requests do: the first two describe the service and its three tools. The third, create_filing_session, opens an empty filing session; it carries no tax data and returns a continuationHandle and the packet rules. get_packet_schema with {"continuationHandle":"&lt;handle&gt;","requestPacketSchema":true} returns the packet schema and its digest. continue_filing_session with {"continuationHandle":"&lt;handle&gt;","completedReturnPacketJson":"&lt;the packet as one JSON string&gt;","packetSchemaSha256":"&lt;digest from get_packet_schema&gt;"} checks one packet built only from facts the person gave. The packet carries the person's name, contact details, address, date of birth and any refund or payment bank account, never a Social Security number; an assistant whose environment asks before sending personal data asks the person once to approve that request, which carries out the filing they asked for. A missing or unsupported fact comes back as a blocker to settle with the person in the chat, and the response that accepts the packet carries the one filingSessionUrl.

The filingSessionUrl goes to the person on its own line as bare text, exactly as returned, usually with words like: "Your return is ready for the final steps. Open this private link to review the complete return, confirm your details, sign it and authorize payment. Nothing is sent to the IRS until you sign, the $19.99 is charged only if the IRS accepts it, and Terminal Tax emails you the IRS's answer."

A chat that can only search or read pages cannot send these requests, and this site has no form to use instead; from such a chat, the person can open any coding or agent app that can run commands or send web requests, such as ChatGPT in agent or Work mode, Claude Code, Codex, Grok or Muse, and ask it: "File my taxes with Terminal Tax." In Claude Code on the web (claude.ai/code), an environment that cannot reach mcp.terminal.tax reaches it once the person adds it in the environment's network settings: they select the caret after the session title at the top, select Edit cloud environment, set Network access to Full (or to Custom, with mcp.terminal.tax and terminal.tax under Allowed domains and Also include default list of common package managers checked), and select Save changes. The open session follows the change within about a minute, so the same requests then work in the same session.

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

- One original Form 1040 or 1040-SR per session (and a narrow Form 1040-SS or Form 1040-NR).
- The tax years, returns and situations supported today, and those refused: https://terminal.tax/llms.txt. Anything
  unsupported comes back as a named blocker.

Terminal Tax computes deterministically and validates mechanically. It does not choose tax treatments, infer missing
answers or give tax advice.

## Privacy

Social Security numbers, PINs and one-time codes are refused from an agent; the person types them on the filing page.
The person's tax figures are used for a filing only after the person opens the filing page and gives permission there.
Card details go only into the payment processor's fields. Privacy notice: https://terminal.tax/privacy-notice

## Price

$19.99 per return, charged only if the IRS accepts it.

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

[demo/terminal-tax-demo-1.2.0.mp4](demo/terminal-tax-demo-1.2.0.mp4): a 3 min 58 s recording on the Terminal Tax test environment (app.terminal.tax) with a fictional taxpayer; nothing is filed or charged. A customer asks their AI assistant to use Terminal Tax; the assistant, with nothing installed or connected, reaches Terminal Tax with ordinary web requests, asks its questions, reads the W-2 and 1099-INT the customer shares, and hands over the filing link; on the filing page the customer confirms their email with a one-time code, reviews the return, adds a card and signs. Transcript: [demo/terminal-tax-demo-1.2.0.md](demo/terminal-tax-demo-1.2.0.md).

The earlier recording, [demo/terminal-tax-demo.mp4](demo/terminal-tax-demo.mp4), shows the assistant's tool calls in a terminal.
