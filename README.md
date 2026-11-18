# ai-orchestration

The Griffins: a fixed family of AI coding agents that work together in [herdr](https://herdr.dev) panes.

| Agent | Role | Runs on |
|---|---|---|
| lois | runs the family: agent state, clearing screens, chores | Claude (Sonnet) |
| stewie | leads the work: architecture, hard problems, planning | Claude (Opus) |
| brian | implementation | Claude (Opus) |
| peter | stories, fun copy, chores from lois | Claude (Haiku) |
| meg | code review only | GitHub Copilot CLI |

## Layout

- `bin/griffins` - the launcher: starts the family in herdr, and `send`, `status`, `clear`, `move` (see `griffins --help`).
- `agents/<name>.md` - each agent's command, status line, spinner and persona.
- `family.md` - the note every agent gets, with a section per role.
- `settings.json` - Claude settings shared by all agents.
- `state/` - runtime state (ignored).

## Setup

```bash
git clone git@github.com:eddpascoal/ai-orchestration.git ~/family
ln -s ~/family/bin/griffins ~/.local/bin/griffins
npm i -g @github/copilot          # for meg
herdr integration install claude
herdr integration install copilot
griffins ~/code/<repo>            # start the family in the herdr TUI
```

Sidebar colours, icons and the working animation live in `~/.config/herdr/`
(`config.toml`, `tag-spaces.sh`, `working-spinner.py`) and are not part of this repo.
