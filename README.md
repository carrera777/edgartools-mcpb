# EdgarTools for Claude Desktop

Lets Claude Desktop pull SEC EDGAR data (company profiles, financials, filings, filing text, insider trades, 13F holdings, proxy comp, fund data) directly from sec.gov. It runs locally on your machine and uses the open-source [edgartools](https://github.com/dgunning/edgartools) package. No API key or paid service is involved.

## Before you start

- Claude Desktop installed and signed in (Windows or Mac).
- Internet access to sec.gov and pypi.org.
- Your own name and email. The SEC requires every EDGAR client to identify itself, so use your real details, not a shared or made-up value.

You do not need to install Python, uv, or anything else. Claude Desktop runs the extension with its own built-in runtime.

## Install (about 2 minutes)

1. **Download `edgartools.mcpb`** from this repo (click the file, then the download icon).
2. **Open Claude Desktop** and go to **Settings > Extensions**.
3. Click **Advanced settings**, then **Install Extension...**. Select the `edgartools.mcpb` file. (Dragging the file into the Extensions window also works.)
4. Review the prompt and click **Install**.
5. When asked for **SEC EDGAR Identity**, enter your name and email in this format, then save:

   `Firstname Lastname you@yourcompany.com`

6. Make sure the extension toggle shows **Enabled**.
7. **Fully quit and reopen Claude Desktop.** (On Windows, close it from the system tray too, not just the window.)

The first launch downloads dependencies and can take up to a minute. If the tools do not show up immediately, wait a minute and start a new chat.

## Test that it works

Start a new chat and ask:

> Use EdgarTools to show me Apple's company profile.

Claude should call `edgar_company` (you may be asked to allow the tool) and return Apple Inc., CIK 320193, SIC 3571, shares outstanding and public float. If it does, you are done.

## What you can ask for

| Tool | Example prompt |
|---|---|
| `edgar_company` | "Give me an overview and 4 years of financials for MSFT" |
| `edgar_trends` | "Show 10 years of revenue, net income and EPS for JPM" |
| `edgar_compare` | "Compare revenue and margins for AAPL, MSFT, GOOGL" |
| `edgar_filing` | "Pull Tesla's latest 10-K" |
| `edgar_read` | "Read the risk factors section of Nvidia's latest 10-K" |
| `edgar_notes` | "What does Apple's debt footnote say?" |
| `edgar_text_search` | "Find 8-Ks mentioning a cybersecurity incident since January" |
| `edgar_search` | "List Ford's 8-Ks this year" |
| `edgar_screen` | "List Nasdaq-listed software companies incorporated in Delaware" |
| `edgar_ownership` | "Show insider trades at AAPL over the last 90 days" |
| `edgar_proxy` | "What is the CEO's pay at Microsoft?" |
| `edgar_fund` | "Look up fund VFINX and show its holdings" |
| `edgar_monitor` | "What 8-Ks were just filed?" |

## Troubleshooting

| Problem | Fix |
|---|---|
| Tools do not appear | Fully quit and reopen Claude Desktop, then start a new chat. Confirm the extension is toggled on under Settings > Extensions. |
| Extension shows an error on start | Open Settings > Extensions, open EdgarTools, and confirm the identity field is filled in. Check you can reach pypi.org and sec.gov (corporate proxies or VPNs sometimes block them). |
| SEC returns 403 or 429 errors | The SEC limits clients to 10 requests per second and blocks unidentified ones. Check your identity value is a real name and email, and wait a few minutes. |
| Install button is greyed out or blocked | Your organization may restrict extensions. Ask your Claude admin to allow it, or to allow local extension installs. |
| Need to change your identity | Settings > Extensions > EdgarTools > edit the identity field, then restart Claude Desktop. |

## Updating

The extension pins nothing, so it picks up the latest `edgartools` release the next time its environment is rebuilt. To force an update or install a new bundle version, download the new `edgartools.mcpb` and install it over the old one.

## Notes

- Data comes straight from the SEC's public EDGAR system. This is not an SEC product and is not affiliated with the SEC.
- The extension is read only. It cannot file or submit anything.
- Claude Chrome and Claude for Excel cannot use this extension. It needs a local host like Claude Desktop or Claude Code.
- Created and maintained by [carrera777](https://github.com/carrera777/edgartools-mcpb). If you fork or redistribute this, please keep the credit and link back.
