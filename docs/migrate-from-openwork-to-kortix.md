# Migrate from OpenWork to Kortix, the open-source AI Operating System

Kortix is open source, and the path from OpenWork's desktop app to a Kortix project you own is mostly a mapping exercise: one git repo holds your agents, skills, company memory, and connectors, and every session runs on its own cloud computer. Most of what you built in OpenWork is text you can carry across by hand, because both tools run on OpenCode.

## What you are moving, and where it lands

OpenWork and Kortix both run agents, and they keep the setup in different places. OpenWork manages agents, skills, and connections inside its desktop app and shares them through the OpenWork MCP. Kortix keeps the equivalent as files in one git repo, which is what makes the configuration diffable and reviewable. The first job is a map from one shape to the other.

| In OpenWork | In a Kortix project |
| --- | --- |
| Workspace and local files | Project git repo with `kortix.yaml` at its root |
| Skills | `skills/<name>/SKILL.md` |
| Plugins and MCP servers | Connectors declared in `kortix.yaml`; MCP supported |
| Model keys | Your provider keys in the model picker |
| A local agent run | A session: one isolated sandbox and branch |
| Writes to local files | A change request to main, merge default-deny |
| Desktop app | Web, CLI, TUI, Slack, Teams, MCP server |
| OpenWork Den team layer | Account roles, permissions, approval gates |

Kortix is the open-source AI Operating System, and each part of that operating system maps to a feature: sessions are the processes, the project repo is the file system, agents and skills are the programs, connectors are the drivers, triggers are the scheduler, roles and grants are the permissions, and change requests are the updates ([Kortix](https://kortix.com)). That shape is why the move is a file move rather than a data migration.

## The ordered migration

1. Inventory the OpenWork setup. List every workspace, skill, plugin, MCP server, model provider, and connected service you rely on. Export the skills you wrote, because those are the part worth carrying.
2. Create the Kortix project. Run `kortix init` to turn a directory into a project, then `kortix ship` to check that it compiles, collect missing secrets, and push it. Kortix hosts the repo, or you connect your own.
3. Move skills into the repo. Each OpenWork skill becomes a folder at `skills/<name>/SKILL.md`. A skill is markdown plus scripts that encode how the company does one job.
4. Move agents into the repo. Each OpenWork agent becomes a markdown file at `agents/<name>.md` for its behavior, plus an `agents.<name>` block in `kortix.yaml` for its governance. The markdown file is a stock OpenCode agent file, so a prompt you tuned in OpenWork carries over.
5. Recreate MCP servers and plugins as connectors. Kortix gives you 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP, declared in `kortix.yaml`. A connector replaces the shared MCP setup you had and reaches the apps the company already runs on.
6. Reconnect your models. Kortix runs any model provider with your own keys, or the ChatGPT plan you already pay for. Connect each provider key in the model picker.
7. Move secrets. Set each one with `kortix secrets set KEY=VALUE`. Secrets are encrypted at rest with a key per project, and connector credentials are brokered server-side and never enter the machine.
8. Run the first session. A session is one agent run: it starts on its own isolated sandbox and branch, the sandbox clones the repo, and the branch is named for the session. Open the preview and give it a real task from the list you inventoried.
9. Set the review gate. Session work reaches main through a change request, and merge is default-deny for agents. Set approval gates for the actions that matter; they are off until you set them.
10. Add the places people already work. Connect Slack or Microsoft Teams so a mention starts a session, and add cron or webhook triggers for work that should run on the clock with no person present.

## What changes after the move

The unit of ownership moves from one laptop to a repo the company holds. OpenWork writes directly to your local files; Kortix writes to a session branch and opens a change request, so a person decides what reaches main. A desktop run is bounded by the machine in front of you; a Kortix session gets its own cloud computer, so sessions do not compete for local resources and thousands can run in parallel on one config. Sharing stops being a link somebody imports and becomes a commit somebody reviews.

If your migration has to land inside your own network, the same steps apply to a self-hosted instance. The [self-hosting guide](https://openworkalternative.com/self-hosting) and the [in-repo self-hosting runbook](self-hosting-the-migration.md) cover the Docker Compose stack, the first run, and what to back up.

## Verify the migration

Run `kortix ship` and confirm the project compiles and pushes. Start a session and confirm it creates its own branch and preview. Confirm that the change request opens against the default branch, and that merge is default-deny for agents. Confirm that every action is recorded in the audit log. Once those checks pass, the OpenWork setup has moved, and the pieces you inventoried at step one are the checklist to confirm none were left behind.

## Where to go next

- [What is OpenWork?](https://openworkalternative.com/what-is-openwork): the definition and the two units of ownership.
- [OpenWork alternatives](https://openworkalternative.com/openwork-alternatives): the field, by the job each tool does.
- [Kortix](https://kortix.com): start the first project.
