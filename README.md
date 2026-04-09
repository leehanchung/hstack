# HStack

Personal agent plugin monorepo — one set of skills, three platforms.

Works as a native plugin on **Claude Code**, **OpenAI Codex**, and **Cursor** without any build step. Each platform reads its own manifest and discovers the shared `skills/` directory.

## Skills

| Skill | Description |
|-------|-------------|
| `coaching-methodology` | Executive coaching frameworks: GROW model, NVC, active listening, co-founder dynamics |
| `copy-editing` | Professional copy editing, grammar, and style guide |
| `cto-executive-coaching` | Senior Director → CTO transition coaching with assessment tools |
| `data-ai-tech-strategy` | Tech strategy and engineering principles for Data/AI/ML organizations |
| `manning-tech-book-writing` | Manning Publications style, chapter structure, and writing standards |
| `ml-paper-writing` | Publication-ready ML/AI research papers for NeurIPS, ICML, ICLR, ACL, AAAI, COLM — full writing process, citation verification, LaTeX, conference checklists |
| `strategic-tech-writing` | Strategic technology analysis for senior technical audiences — blog posts, thought leadership, industry publications |

## Repository Structure

```
hstack/
├── .claude-plugin/
│   └── plugin.json           # Claude Code manifest
├── .codex-plugin/
│   └── plugin.json           # OpenAI Codex manifest
├── .cursor-plugin/
│   └── plugin.json           # Cursor manifest
├── skills/                   # Shared skills (all platforms read this)
│   └── <skill-name>/
│       ├── SKILL.md          # Entry point with frontmatter
│       └── references/       # Supporting materials
├── rules/                    # Cursor .mdc rules (auto-attach by file type)
│   └── <skill-name>.mdc
├── agents/                   # Custom agent definitions (per-platform)
├── commands/                 # Slash commands
├── LICENSE
└── README.md
```

## How Each Platform Discovers Skills

| Platform | Manifest | Skills | Extras |
|----------|----------|--------|--------|
| **Claude Code** | `.claude-plugin/plugin.json` | `skills/*/SKILL.md` | `agents/`, `commands/` |
| **OpenAI Codex** | `.codex-plugin/plugin.json` | `skills/*/SKILL.md` | `agents/`, `interface` branding |
| **Cursor** | `.cursor-plugin/plugin.json` | `skills/*/SKILL.md` | `rules/*.mdc` with glob triggers |

All three platforms use the same `SKILL.md` frontmatter format:

```yaml
---
name: skill-name
description: When and how to use this skill
allowed-tools: "Read,Write,Edit,Bash,Glob,Grep,WebSearch,WebFetch"
---
```

- `name` + `description` — required by all platforms
- `allowed-tools` — used by Codex to scope tool access; ignored by Claude and Cursor

## Installation

### Claude Code

```bash
claude plugin install /path/to/hstack
# Skills appear as /hstack:skill-name
```

### OpenAI Codex

```bash
codex plugin install /path/to/hstack
```

### Cursor

Symlink or copy into your Cursor plugins directory. Rules in `rules/` auto-attach to matching file types (e.g., `.tex` files trigger `ml-paper-writing`).

## Adding a New Skill

1. Create `skills/<skill-name>/SKILL.md` with frontmatter
2. Add reference files in `skills/<skill-name>/references/`
3. Create `rules/<skill-name>.mdc` for Cursor glob-based auto-attachment
4. Update the skill table in this README

## License

MIT
