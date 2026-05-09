# rpiv-advisor

> [!CAUTION]
> ## This repository has moved to [`juicesharp/rpiv-mono`](https://github.com/juicesharp/rpiv-mono)
>
> This package now lives at **[`packages/rpiv-advisor`](https://github.com/juicesharp/rpiv-mono/tree/main/packages/rpiv-advisor)** inside the monorepo.
>
> - **npm:** still published as `@juicesharp/rpiv-advisor` — no install change.
> - **Issues / PRs:** open them on [`rpiv-mono`](https://github.com/juicesharp/rpiv-mono/issues).
> - **This repo is read-only / archived.**

Pi extension that registers the `advisor` tool and `/advisor` slash command,
implementing the advisor-strategy pattern: the executor model can escalate
decisions to a stronger reviewer model (e.g. Opus), receive guidance, and
resume.

![Advisor model selector](https://raw.githubusercontent.com/juicesharp/rpiv-advisor/main/docs/advisor.jpg)

## Installation

    pi install npm:@juicesharp/rpiv-advisor

Then restart your Pi session.

## Usage

Configure an advisor model with `/advisor` — the command opens a selector for
any model registered with Pi's model registry, plus a reasoning-effort picker
for reasoning-capable models. Selection persists across sessions at
`~/.config/rpiv-advisor/advisor.json` (chmod 0600).

The `advisor` tool is registered at load but excluded from active tools by
default; selecting a model via `/advisor` enables it. Choose "No advisor" to
disable.

`advisor` takes zero parameters — calling it forwards the full serialized
conversation branch to the advisor model, which returns guidance (plan,
correction, or stop signal) that the executor consumes.

## License

MIT
