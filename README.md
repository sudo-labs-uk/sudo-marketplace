# sudo-marketplace

The `sudo` plugin marketplace for Claude Code. It lists Sudo Labs plugins; each plugin
lives in its own repository and is fetched from there at install.

```sh
claude plugin marketplace add sudo-labs-uk/sudo-marketplace
claude plugin install sudo-skills@sudo
claude plugin install secretdrop@sudo
claude plugin install cairn@sudo
claude plugin install chief@sudo
```

A plugin's skills run under its name, such as `/sudo-skills:grilling`, `/cairn:sweep` or
`/chief:chief`.

`chief` needs [uv](https://docs.astral.sh/uv/) on `PATH`: its hooks run through
`uv run` at the start, on each prompt and at the end of every Claude Code session.

| Plugin | Repository | Releases |
|---|---|---|
| `sudo-skills` | `sudo-labs-uk/sudo-skills` | Every commit on `main` |
| `secretdrop` | `sudo-labs-uk/secretdrop` | Each `version` bump in its `plugin.json` |
| `cairn` | `Rendiere/cairn` (private) | Each `version` bump in its `plugin.json` |
| `chief` | `sudo-labs-uk/chief` (private) | Each `version` bump in its `plugin.json` |

Installs are cached copies. `claude plugin update <plugin>@sudo` fetches a new release,
and turning on auto-update for this marketplace in `/plugin` does it in the background.
Installing `cairn` needs read access to `Rendiere/cairn`, and installing `chief` needs
read access to `sudo-labs-uk/chief`, through an SSH key or a stored git credential.

To add a plugin, add an entry to `.claude-plugin/marketplace.json` whose `name` matches
the `name` in that plugin's own `plugin.json`, then run `claude plugin validate .`.
