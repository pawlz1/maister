# Maister for Codex

This variant is generated from `plugins/maister/`. Never edit generated files.
Full functional parity is the acceptance requirement; see `docs/codex-parity.md`.
This is currently a development port, not a verified parity release.

## Build and test

```bash
make build-codex
make test-codex
```

Requires Python 3.9 or newer for generation, hooks and persistent task tracking.
The existing HTML preview requires Node.js 20 or newer; ASCII fallback is retained.
Codex must support plugins, subagents and lifecycle hooks. Hook execution also
requires explicit trust review; installing a plugin does not trust its hooks.

## Local installation

The repo marketplace at `.agents/plugins/marketplace.json` exposes this variant.
From the repository root:

```bash
codex plugin marketplace add .
codex plugin add maister-codex@maister-codex-plugins
```

Review and trust the bundled hooks using your Codex client's hook trust controls
before running workflows. Do not disable sandboxing or bypass hook trust as an
installation workaround. Restart/reload Codex after refreshing the generated
package. Installed packages are cached; rebuilding the source is not by itself
proof that the installed copy was refreshed.

Installed plugin entry points use namespaced skill syntax, for example
`$maister-codex:maister-init`, `$maister-codex:maister-work`,
`$maister-codex:maister-development`, `$maister-codex:maister-reviews-code` and
`$maister-codex:maister-quick-bugfix`. Supply the same task descriptions and flags as the
original workflows. Public workflows include their execution adapter; internal
skills are loaded in the parent context. Source agent roles dispatch through
native subagents with complete role instructions; their TOML files are optional
custom-agent configurations, not automatically registered by the plugin.

For parser/installation tests, use a temporary CODEX_HOME, never the user's
personal configuration. Actual workflow acceptance requires model-driven tests
with interactive decisions; non-interactive execution must stop at gates.

## Development limitations

Coverage and adapter unit tests do not establish functional parity. Outstanding
work includes model-driven validation of all workflows, task/phase resumption,
parallel dispatch, decisions, hook trust and visual/E2E functionality. The lexical
command guard is defense-in-depth, not a complete shell security boundary.