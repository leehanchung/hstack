# HStack — Agent Plugin Monorepo

Personal monorepo of agent skills, commands, and rules for Claude Code, OpenAI Codex, and Cursor.

## Repository Layout

```
hstack/
├── .claude-plugin/plugin.json   # Claude Code manifest
├── .codex-plugin/plugin.json    # OpenAI Codex manifest
├── .cursor-plugin/plugin.json   # Cursor manifest
├── skills/                      # Shared skill definitions (all platforms)
│   └── <name>/
│       ├── SKILL.md             # Entry point (frontmatter + instructions)
│       └── references/          # Supporting materials
├── rules/                       # Cursor .mdc rules (glob-triggered)
├── agents/                      # Agent persona definitions
├── commands/                    # Slash commands
├── LICENSE                      # MIT — Han Lee
└── README.md
```

## Conventions

### Skills

Every skill lives in `skills/<skill-name>/` with a `SKILL.md` at the root. Frontmatter must include:

```yaml
---
name: skill-name            # Must match directory name
description: ...            # Used for discovery and triggering across all platforms
allowed-tools: "..."        # Codex tool scoping (ignored by Claude/Cursor)
---
```

Supporting files go in `references/`. Scripts go in `scripts/`. Keep `SKILL.md` body under 500 lines — use references for overflow.

### Naming

- Directories: `kebab-case`
- Skill names: must match their parent directory name exactly
- References: `kebab-case.md` (prefer hyphens over underscores)

### Adding a New Skill

1. `mkdir -p skills/<name>/references`
2. Create `skills/<name>/SKILL.md` with required frontmatter
3. Create `rules/<name>.mdc` for Cursor auto-attachment (optional but recommended)
4. Update the skill table in `README.md`

### Cursor Rules

Each `.mdc` file in `rules/` mirrors a skill. Include `globs:` for file-type auto-attachment when applicable (e.g., `**/*.tex` for paper-writing skills). Set `alwaysApply: false` unless the rule should load on every prompt.

### Agents

Agent definitions in `agents/` are platform-aware markdown files that define personas or workflows. Use descriptive filenames like `paper-reviewer.md` or `strategy-advisor.md`.

### Commands

Slash commands in `commands/` are markdown files. The filename becomes the command name (e.g., `commands/review.md` → `/hstack:review`).

## Development Workflow

- No build step — all platforms read markdown directly
- Test locally with `claude plugin install .` (Claude Code), `codex plugin install .` (Codex), or symlink into Cursor plugins
- Keep manifests in sync: if you add a new top-level directory, add it to all three `plugin.json` files

## Platform Manifest Locations

| Platform | Manifest | Agent Instructions |
|----------|----------|--------------------|
| Claude Code | `.claude-plugin/plugin.json` | `CLAUDE.md` (this file) |
| OpenAI Codex | `.codex-plugin/plugin.json` | `AGENTS.md` |
| Cursor | `.cursor-plugin/plugin.json` | `.cursor/rules/*.mdc` |

## Do Not

- Put anything other than `plugin.json` inside `.claude-plugin/`, `.codex-plugin/`, or `.cursor-plugin/`
- Duplicate skill content across platforms — write it once in `skills/`, generate platform adapters
- Add secrets, API keys, or `.env` files to this repo
