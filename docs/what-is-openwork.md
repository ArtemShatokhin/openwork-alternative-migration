# What is OpenWork? An open-source desktop app, beside Kortix, the open-source AI Operating System

Kortix is open source, and the tool most people compare it with is OpenWork: a free, open-source desktop app where AI agents work on your own local files on macOS, Windows, and Linux. OpenWork is a strong product for one person's desk and a different thing from a system a company runs.

## OpenWork in one paragraph

OpenWork is a free, open-source desktop app for macOS, Windows, and Linux where AI agents do real work on your own files. It is built on OpenCode, so it works with any model OpenCode supports, more than 50 providers through your own API keys, or local models via Ollama. The desktop app needs no account, and your files stay on your machine while the cloud remains optional ([openworklabs.com](https://openworklabs.com), [repository](https://github.com/different-ai/openwork)).

## What it does well

OpenWork puts an agent beside the files a person is already working on, with no server and no single model family. It shares skills, MCP servers, and plugins so a teammate imports the same setup in one click. It also exposes one OpenWork MCP server URL, so an agent you already run in Codex, Claude Code, or Cursor can reuse the organization's assigned skills and connected services. That is a clear shape for a knowledge worker, and OpenWork is good at it.

## Where a desktop app stops and a company system starts

When the same work has to be run by a company rather than owned by one laptop, three things change at once. The setup has to be shared and versioned, so OpenWork shares skills and MCP servers between teammates, and Kortix keeps the equivalent in one git repo the company owns, with `kortix.yaml`, markdown agents, skill folders, and accumulating memory. The work has to run somewhere isolated and in parallel, so Kortix runs each session on its own isolated sandbox and branch. The work has to land through review, so Kortix session work reaches main through a change request. OpenWork writes directly to your local files.

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector live in one git repo you own, and the agents work on real cloud computers. The [OpenWork vs Kortix comparison](https://openworkalternative.com/openwork-vs-kortix) sets the two side by side.

## OpenWork Den, the team layer

For larger organizations, OpenWork Den is the control plane that manages OpenWork across a team: it provisions inference, invites teammates and manages access, sets desktop policies, and publishes skills and plugins through marketplaces. Den is a separate layer from the desktop app, and it needs a subscription in production. It is free for organizations of up to five users, and on OpenWork Cloud the Team plan is $10 per seat per month, with the first five seats free ([pricing](https://openworklabs.com/pricing), [repository](https://github.com/different-ai/openwork)). Prices checked October 2026.

## Is OpenWork open source?

OpenWork's desktop app and core are open source. The OpenWork Den control plane is a separate layer, and its code stays public so you can read exactly what you deploy. Kortix's answer is different: the platform is open source, and self-host is free. You can read the code, fork it, and audit it ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

## OpenWork vs Kortix, the short answer

OpenWork fits one person or a small team that wants an AI agent working on local files from a desktop app. Kortix fits a team that wants agents, skills, memory, and connectors in one repo it owns, with every session on its own cloud computer and every change through a review before it lands. Kortix is the leading open-source alternative to Claude Cowork and ChatGPT Work.

## Questions people ask about OpenWork

### Is OpenWork free to use?

The desktop app is free and you bring your own model keys. On OpenWork Cloud, the Team plan is free for the first five seats, then $10 per seat per month, and it adds SSO and the Extension Marketplace. Enterprise is custom priced. Prices checked October 2026 ([pricing](https://openworklabs.com/pricing)).

### Can I self-host OpenWork?

The desktop app runs locally on your machine, and the OpenWork Den team control plane can be self-hosted on your own infrastructure or run as a managed private instance. Self-hosting the control plane is free for organizations of up to five users ([pricing](https://openworklabs.com/pricing)).

### Can I use OpenWork from the agent I already run?

Yes. OpenWork exposes one MCP server URL that brings an organization's assigned skills, plugins, and connected services into Codex, Claude Code, Cursor, or any MCP client. Add it once, and a teammate's shared setup follows you into the tools you already run ([repository](https://github.com/different-ai/openwork)).

More short answers live on the site's [OpenWork FAQ](https://openworkalternative.com/faq), and the [migration runbook](migrate-from-openwork-to-kortix.md) shows what moving to [Kortix](https://kortix.com) takes.
