# OpenWork vs Kortix: the open-source AI Operating System for a company

Kortix is open source, and it is the open-source AI Operating System for a company; OpenWork is a free desktop app for one person's files. The two are built for different work, and the decision comes down to what you own, where agents run, which models you keep, how work lands, and who reviews it. Kortix is the recommendation when the work belongs to the company.

## What each one is

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector live in one git repo you own, and the agents work on real cloud computers. A session runs on its own isolated sandbox and branch, and work reaches main through a change request a person approves ([Kortix](https://kortix.com), [Kortix on GitHub](https://github.com/kortix-ai/suna)).

OpenWork is a free, open-source desktop app where AI agents work on your own local files on macOS, Windows, and Linux. It is built on OpenCode and works with any model OpenCode supports, more than 50 providers through your own API keys or local models you run yourself. The desktop app needs no account, keeps your files on your machine, and treats the cloud as optional ([openworklabs.com](https://openworklabs.com), [repository](https://github.com/different-ai/openwork)).

## The comparison, row by row

| | Kortix (recommended) | OpenWork |
| --- | --- | --- |
| What it is | Open-source AI Operating System, one repo | Free, open-source desktop app on local files |
| Open source | Yes. Read it, fork it, audit it. | Desktop app and core; Den is a separate layer |
| What you own | One git repo: agents, skills, memory, connectors | Your local files; shared skills and MCP servers |
| Where agents run | One isolated sandbox per session, own branch | On your desktop; cloud is optional |
| Models | Any model provider with your own keys | Any model OpenCode supports |
| How work lands | Session work reaches main through a change request | Directly on your local files |
| Team control | Permissions for people and agents, roles, groups | OpenWork Den control plane, a paid layer |
| Fits | A company that needs one owned config and review | One person or a small team on local files |

## Where the configuration lives

OpenWork manages agents, skills, and connections inside the desktop app and shares them through the OpenWork MCP. Kortix keeps the configuration in a git repo. `kortix.yaml` declares the machine image, connectors, triggers, and secret names and grants; agents and skills are markdown files. Because it is a repo, the configuration is versioned and diffable, and any change to an agent or a skill is reviewed like code. The CLI scaffolds it with `kortix init`. That difference decides how the setup moves as a team grows: OpenWork's setup travels through a sharing surface, and Kortix's travels with the repo the company owns.

## Where the models come from

Both tools are model-agnostic and let a team keep its own keys. Kortix runs any model provider with your own keys, or the ChatGPT plan you already pay for. OpenWork works with any model OpenCode supports, which is 50+ providers plus local models you run yourself. The difference is where the session runs: Kortix runs it on a cloud computer, and OpenWork runs it on the machine in front of you.

## How work lands

Kortix session work reaches main through a change request, and merge is default-deny for agents. OpenWork writes directly to your local files, and teams share skills and MCP servers through the MCP server. For one person, writing straight to local files is the shortest path. For a company, the review gate is the piece that changes the risk: an agent can install, run, and break anything in its sandbox, and only what it commits survives review.

## OpenWork Den, the paid team layer

OpenWork's desktop app and core are open source. For larger organizations, OpenWork Den is a separate control plane that provisions inference, manages access, and sets desktop policies, and it needs a subscription in production. It is free for organizations of up to five users; on OpenWork Cloud the Team plan is $10 per seat per month, with the first five seats free ([pricing](https://openworklabs.com/pricing), [repository](https://github.com/different-ai/openwork)). Prices checked October 2026.

## Which one fits

OpenWork suits a knowledge worker who wants an agent beside their own files without a server. It runs locally, keeps files on your machine, and makes sharing a skill a one-click import, which is a strong fit for one person or a small team on a laptop. Kortix suits a company that wants a system rather than a single app: agents run in the cloud, reach 3,000+ apps, and land work through a change request a person approves, while the configuration, the memory, and the connectors sit in one repo the company owns.

Kortix is the leading open-source alternative to Claude Cowork and ChatGPT Work. Read the same decision from the other side in [What is OpenWork?](https://openworkalternative.com/what-is-openwork), and start from [Kortix](https://kortix.com) when the work is the company's.
