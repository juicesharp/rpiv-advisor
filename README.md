# rpiv-advisor

Pi extension that registers the `advisor` tool and `/advisor` slash command,
implementing the advisor-strategy pattern: the executor model can escalate
decisions to a stronger reviewer model (e.g. Opus), receive guidance, and
resume.

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

## Migration from rpiv-pi ≤ 0.3.0

If you had an advisor configured while rpiv-pi bundled this tool, your previous
selection lived at `~/.config/rpiv-pi/advisor.json`. The new plugin reads
`~/.config/rpiv-advisor/advisor.json` only — run `/advisor` once to re-select
your model.

## License

MIT
