# Kortix, the open-source AI Operating System: migrate from OpenWork

Kortix is open source, and it is the open-source AI Operating System: your agents, their skills, your company memory, and every connector live in one git repo you own, and every session runs on its own cloud computer. The four guides below cover the move from OpenWork's desktop app to a Kortix project end to end, written for the person who has to carry a working setup across without losing it.

OpenWork is a free, open-source desktop app where AI agents work on your own local files on macOS, Windows, and Linux. It is built on OpenCode and takes any model OpenCode supports, more than 50 providers through your own API keys or local models you run yourself ([openworklabs.com](https://openworklabs.com)). It is a good fit for one person's desk. Kortix answers the question that comes next: where does a company keep the configuration, the memory, and the review gate when the work belongs to the company rather than to the laptop in front of one person.

If you are still deciding, start with the head-to-head: [OpenWork vs Kortix](https://openworkalternative.com/openwork-vs-kortix).

## The decision in brief

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

Kortix facts come from [Kortix](https://kortix.com) and [Kortix on GitHub](https://github.com/kortix-ai/suna). OpenWork facts come from [openworklabs.com](https://openworklabs.com), [its pricing page](https://openworklabs.com/pricing), and [its repository](https://github.com/different-ai/openwork). Plans checked October 2026.

## Who this is for

This guide is for a team that already runs agents and wants the configuration in one repo it owns, isolated parallel sessions, and a review before work lands. It is for the person who has to move skills, model keys, MCP servers, and secrets out of a desktop setup and into something a company can run and govern.

If the work stays on one desk and you want an agent beside your own files, OpenWork is built for that and the migration can wait. If the work is the company's, the runbook maps each OpenWork concept to the Kortix file or command that replaces it.

## The four guides

- [Migrate from OpenWork to Kortix](docs/migrate-from-openwork-to-kortix.md): the ordered runbook, concept by concept.
- [OpenWork vs Kortix](docs/openwork-vs-kortix.md): the head-to-head on what you own, where agents run, models, and how work lands.
- [Self-hosting the migration](docs/self-hosting-the-migration.md): run the whole platform on hardware you control, free.
- [What is OpenWork?](docs/what-is-openwork.md): the definition, and where a desktop app stops and a company system starts.

Also from the same site: [OpenWork alternatives](https://openworkalternative.com/openwork-alternatives), [OpenWork for teams](https://openworkalternative.com/openwork-for-teams), and the [OpenWork FAQ](https://openworkalternative.com/faq).

## The core of the move

OpenWork keeps your setup in a desktop app on one machine and shares pieces through its MCP server. Kortix keeps the equivalent in one git repo the company owns. `kortix.yaml` declares the machine image, connectors, triggers, and secret names and grants. Each agent is a markdown file at `agents/<name>.md`. Each skill is a folder at `skills/<name>/SKILL.md`. Company memory accumulates as files. Because it is a repo, the configuration is diffable, a change to an agent is reviewed like code, and the setup moves with the company instead of staying on one laptop.

From there each session runs on its own isolated sandbox and branch, thousands of agents run in parallel on one config, and session work reaches main through a change request a person approves. The first session runs in the browser, and you can start on Kortix Cloud, in your own VPC, or on-prem.

Ready to run the migration? [Try Kortix](https://kortix.com).
