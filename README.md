# AstraEye Labs MCP connector

**AI research on U.S. stocks, ETFs and crypto, inside the assistant you already use.**

[AstraEye Labs](https://astraeyelabs.io) is an AI research lab for U.S. stocks, ETFs and crypto. Specialist AI
scientists compute every figure in code on licensed market data, and SAGE, the research guide, writes one report
from their findings, with the method behind each analysis and the data sources it used.

This repository documents the AstraEye Labs **remote MCP server**. It lets an AI assistant (ChatGPT, Claude,
Gemini, Perplexity, Grok or any MCP client) read a member's finished research reports and their methods, browse
the analysis catalog and research templates, follow a run, and ask SAGE to price and start new research.

[![AstraEye Labs MCP connector](https://glama.ai/mcp/connectors/io.astraeyelabs/research/badges/score.svg)](https://glama.ai/mcp/connectors/io.astraeyelabs/research)

| | |
| --- | --- |
| Server URL | `https://astraeyelabs.io/mcp` |
| Transport | Streamable HTTP (stateless, JSON) |
| Sign-in | OAuth 2.1 with PKCE, to the member's own AstraEye Labs account |
| Official MCP Registry | [`io.astraeyelabs/research`](https://registry.modelcontextprotocol.io/v0/servers?search=io.astraeyelabs) |
| Documentation | [astraeyelabs.io/research-api](https://astraeyelabs.io/research-api) |
| For AI assistants | [astraeyelabs.io/llms.txt](https://astraeyelabs.io/llms.txt) |

## What makes the numbers checkable

- **Computed, not recalled.** Every figure in a report is computed in code from licensed market data and named
  public sources. The language model explains the results; it does not produce the numbers.
- **Method and sources shown.** Each report lists its data sources, and each analysis carries its method: what it
  measures, the rule it applies, and what it cannot support.
- **Stocks, ETFs and crypto in one report**, from desks for technical structure, fundamentals and macro, news and
  sentiment, on-chain and alternative data, derivatives, and discovery screens.
- **Priced in credits.** Ask SAGE what a run costs in Astra Credits before you start it.

Read a published report, no account needed:
[astraeyelabs.io/r/164j4b202j6w3d204l5z2b53422j54530r0e3528](https://astraeyelabs.io/r/164j4b202j6w3d204l5z2b53422j54530r0e3528)

Guides:
[Seven checks before you trust an AI's stock or crypto numbers](https://astraeyelabs.io/guides/check-ai-stock-research)
and
[Stocks, ETFs and crypto in one AI research report](https://astraeyelabs.io/guides/stocks-and-crypto-in-one-report).

## Connect it

Each connection is made from the assistant: you add the server URL, sign in to AstraEye Labs when it asks, and
choose what the assistant may do. A connection is separate from a personal API token and can be disconnected on
its own in AstraEye Labs settings.

- **Claude**: add a custom connector with the server URL `https://astraeyelabs.io/mcp`.
- **ChatGPT**: open Plugins, choose the plus button, name it AstraEye, and enter the server URL under Connection.
  Adding your own plugin can depend on your ChatGPT plan or workspace settings.
- **Gemini** (web): add AstraEye as a custom app and enter the server URL. Custom apps need a Google AI Pro or
  Ultra plan.
- **Perplexity**: open Connectors, choose Custom connector, then Add MCP connector, and enter the server URL. Then
  open the new connector and choose Add connector. Custom connectors need a Perplexity Pro plan or higher.
- **Grok**: open Connectors, add a custom connector and enter the server URL.

**Who can connect.** The connector needs a personal AstraEye Labs account on the Space Analyst plan or above
(personal accounts only, 18+, not available in every jurisdiction). There is a free plan, and new accounts start
with a 7-day trial with no card. Current plans: [astraeyelabs.io/subscribe](https://astraeyelabs.io/subscribe).

**What it returns.** The written prose of the member's own reports: the executive summary, the discussion, the
conclusion, the prepared questions and answers and, where a report has them, its methodology. It never returns
charts, tables or data fields; those stay in AstraEye Labs, and each report links to its page there.

## Tools

Read tools (scope `research:read`):

| Tool | What it does |
| --- | --- |
| `list_research_projects` | The member's own research projects, newest first |
| `list_research_reports` | The member's finished reports, newest first, with each report's page |
| `get_research_report` | The written summary of one finished report, with its disclosures |
| `get_report_methodology` | How each analysis in a report works, in the run's own words |
| `list_analyses` | The analyses AstraEye can run: scientist, asset class, what it does, the plan it is on |
| `get_analysis` | One analysis in full, including its methodology and what it cannot support |
| `list_templates` | Prebuilt research templates and the analyses each combines |
| `get_template` | One template in full: the analyses it runs, in order |
| `get_research_project` | One of the member's projects, as AstraEye will run it |
| `list_research_runs` | The runs of one project, with status and whether results are ready |
| `get_research_run` | One run's status and progress |
| `list_market_slices` | Market slices a project can cover, such as the S&P 500, the Dow 30, a sector or the top 100 coins |

SAGE tools (scope `sage:chat`, off by default and chosen on the consent screen):

| Tool | What it does |
| --- | --- |
| `send_sage_message` | Sends one message to the member's own SAGE chat and returns SAGE's reply. SAGE can price and start research within the daily credit limit the member set for this connection |
| `get_sage_messages` | Reads the member's SAGE chat, including replies that finished later and notices that a run has completed |

## Safety and spending

- Sign-in is to the member's own account, with a consent screen and a step-up confirmation. Nothing is shared
  across accounts.
- By default a connection can only read. With the SAGE chat permission, every reply and every run spends Astra
  Credits only within the daily credit limit the member chose for that connection.
- `send_sage_message` is marked as an action, so assistants that ask before actions will ask the member first.
- One active connection per assistant. Disconnect it any time in AstraEye Labs settings.

## About this repository

This repository holds documentation and the server's registry metadata (`server.json`) only. The server itself
runs at `https://astraeyelabs.io/mcp`; its source is not published here.

Support: support@astraeyelabs.io · [astraeyelabs.io](https://astraeyelabs.io)

---

AstraEye Labs provides AI-generated research for informational and educational purposes only. Research is
impersonal and descriptive, and it is not investment advice. You decide what, if anything, to do. For users 18+;
not available in every jurisdiction. AstraEye Labs LLC, Texas.
