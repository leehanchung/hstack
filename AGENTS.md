# HStack — Agent Plugin Monorepo

Personal monorepo of agent skills, commands, and rules for Claude Code, OpenAI Codex, and Cursor.

## Repository Layout

```
hstack/
├── .claude-plugin/plugin.json   # Claude Code manifest
├── .cursor-plugin/plugin.json   # Cursor manifest
├── .agents/plugins/marketplace.json # OpenAI Codex marketplace catalog
├── plugins/hstack/              # Shared plugin payload
│   ├── .codex-plugin/plugin.json # OpenAI Codex manifest
│   ├── skills/                  # Shared skill definitions
│   │   └── <name>/
│   │       ├── SKILL.md         # Entry point (frontmatter + instructions)
│   │       └── references/      # Supporting materials
│   ├── agents/                  # Agent persona definitions
│   └── commands/                # Slash commands
├── rules/                       # Cursor .mdc rules (glob-triggered)
├── LICENSE                      # MIT — Han Lee
└── README.md
```

## Conventions

### Skills

Every skill lives in `plugins/hstack/skills/<skill-name>/` with a `SKILL.md` at the root. Frontmatter must include:

```yaml
---
name: skill-name            # Must match directory name
description: ...            # Used for discovery and triggering across all platforms
allowed-tools: "..."        # Codex tool scoping
---
```

Supporting files go in `references/`. Scripts go in `scripts/`. Keep `SKILL.md` body under 500 lines.

### Naming

- Directories: `kebab-case`
- Skill names: must match their parent directory name exactly
- References: `kebab-case.md`

### Adding a New Skill

1. `mkdir -p plugins/hstack/skills/<name>/references`
2. Create `plugins/hstack/skills/<name>/SKILL.md` with required frontmatter
3. Create `rules/<name>.mdc` for Cursor auto-attachment (optional)
4. Update the skill table in `README.md`

### Agents

Agent definitions in `plugins/hstack/agents/` are markdown files that define personas or workflows. Use descriptive filenames.

### Commands

Slash commands in `plugins/hstack/commands/` are markdown files. The filename becomes the command name.

## Do Not

- Put anything other than `plugin.json` inside manifest directories
- Duplicate skill content across platforms — write once in `plugins/hstack/skills/`
- Add secrets, API keys, or `.env` files to this repo
