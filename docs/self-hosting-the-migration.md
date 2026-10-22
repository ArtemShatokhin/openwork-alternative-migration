# Self-host the migration: Kortix, the open-source AI Operating System

Kortix is open source, and self-hosting it is free: one Docker Compose stack runs the whole platform on hardware you control, while agent sessions run off the box on a separate sandbox provider. If your migration has to land inside your own network, this is the path from an OpenWork setup to a Kortix instance you run yourself.

## What a self-hosted Kortix instance installs

A self-hosted Kortix instance is one Docker Compose stack. The frontend, the `kortix-api` image, the LLM gateway, and the Supabase Docker distribution all run on the box you choose. When you set a domain, Kortix also renders Caddy for TLS and a small updater that keeps the images current. The same Compose file runs on a laptop, a VPS, or a server in your own cloud account, so a domain is only a value you set.

## The company stays in the repo

Three things land on disk and stay yours. The company itself is one git repo: `kortix.yaml` declares the agents and what each may touch, each agent is a markdown file at `agents/<name>.md`, each skill lives at `skills/<name>/SKILL.md`, and project memory accumulates under `memory/`. The instance data sits under `~/.config/kortix/self-host/<instance>/`: the Postgres database in `volumes/db/data` and file storage in `volumes/storage`. The instance `.env` holds every secret and signing key the stack uses. Connector credentials are brokered server-side and never enter the machine, and secrets are encrypted at rest with a key per project.

## What the first run asks for

The first run asks for a few values and no model key. You point the install at a domain, or use a Cloudflare tunnel for evaluation, and later run `kortix self-host configure` to enter a sandbox provider key. Models are BYOK in the app, so you connect your own provider key in the model picker once the stack is up. GitHub connects in the dashboard under Settings → Git. The stack has no Redis and no separate worker. Plan for memory as well: each API service defaults to a 640 MiB limit, which suits an 8 GiB host.

## Install and start

On a bare Linux box, the one-shot bootstrap installs Docker, installs the Kortix CLI, and starts the whole stack. On macOS, or on any host you would rather configure by hand, install the CLI and run the manual path:

```sh
kortix self-host init      # renders the Compose config and the .env
kortix self-host start     # brings the stack up
kortix self-host doctor    # validates the Docker tooling and the rendered config
```

Create the DNS records for your domain and for `api.<domain>` before you run it, and open ports 80 and 443. To evaluate without a domain, use `kortix self-host init --tunnel cloudflare`; the tunnel URL changes on every restart, so run production on a real domain.

## What it needs, and what it does not

A self-hosted Kortix instance needs outbound network access, so it is not an offline install. It pulls its images from `docker.io/kortix/*`, and agent sessions never run on the box. They run on a separate sandbox provider that `kortix-api` reaches over egress, with Platinum as the default and Daytona as a legacy fallback. The sandbox provider key is the one credential the stack cannot start without, and a domain or a tunnel gives the sandbox a stable URL to call back to.

## What to back up

Copy two directories and one file under `~/.config/kortix/self-host/<instance>/`: the Postgres directory `volumes/db/data`, the storage directory `volumes/storage`, and the instance `.env`. A restore needs all three, so copy them before any destructive command. Every instance updates itself once a day by default; pin an exact version with `kortix self-host update --tag <version> --auto-update off`, and roll back with `kortix self-host rollback --release <version>`.

## How it compares with self-hosting OpenWork

Kortix self-hosts as the whole platform: the frontend, the API, the LLM gateway, and the Supabase distribution in one Docker Compose project, with the agents, memory, connectors, and triggers in the git repo you own, and agent sessions running off the box on a separate sandbox provider. OpenWork's desktop app runs locally, and the OpenWork Den control plane for a team can be self-hosted, free for organizations of up to five users ([pricing](https://openworklabs.com/pricing), [repository](https://github.com/different-ai/openwork)). Both run on hardware you choose. The difference is what each one treats as the unit you own: Kortix ships the whole platform as the unit, and OpenWork ships the desktop app as the unit with a separate control plane above it.

Self-hosting fixes the setting, not the shape of the work. The review gate still applies: session work reaches main through a change request, and merge is default-deny for agents. For the wider picture, see the site's [self-hosting guide](https://openworkalternative.com/self-hosting) and the [migration runbook](migrate-from-openwork-to-kortix.md). When you are ready to run it, [Kortix](https://kortix.com) has the docs.
