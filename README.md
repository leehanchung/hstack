# HStack

Personal agent plugin monorepo — one set of skills, three platforms.

Works as a native plugin on **Claude Code**, **OpenAI Codex**, and **Cursor** without any build step. Each platform reads its own manifest and discovers the shared `plugins/hstack/skills/` directory.

## Skills

| Skill | Description |
|-------|-------------|
| `copy-editing` | Professional copy editing, grammar, style guide, AI writing pattern detection, and verbosity diagnosis |
| `data-ai-tech-strategy` | Tech strategy and engineering principles for Data/AI/ML organizations |
| `executive-coaching` | Executive coaching frameworks: GROW model, NVC, active listening, burnout prevention, co-founder dynamics, CTO transition |
| `manning-tech-book-writing` | Manning Publications style, chapter structure, and writing standards |
| `ml-paper-writing` | Publication-ready ML/AI research papers for NeurIPS, ICML, ICLR, ACL, AAAI, COLM — full writing process, citation verification, LaTeX, conference checklists |
| `tech-writing` | Strategic tech blog posts and industry analysis — short-form (800-1,500 words) and long-form (2,000-4,000 words) with concision rules and AI pattern avoidance |

## Repository Structure

```
hstack/
├── .claude-plugin/
│   └── plugin.json           # Claude Code manifest
├── .cursor-plugin/
│   └── plugin.json           # Cursor manifest
├── .agents/plugins/
│   └── marketplace.json      # OpenAI Codex marketplace catalog
├── plugins/hstack/           # Shared plugin payload
│   ├── .codex-plugin/
│   │   └── plugin.json       # OpenAI Codex manifest
│   ├── skills/               # Shared skills
│   │   └── <skill-name>/
│   │       ├── SKILL.md      # Entry point with frontmatter
│   │       └── references/   # Supporting materials
│   ├── agents/               # Custom agent definitions
│   └── commands/             # Slash commands
├── rules/                    # Cursor .mdc rules (auto-attach by file type)
│   └── <skill-name>.mdc
├── LICENSE
└── README.md
```

## How Each Platform Discovers Skills

| Platform | Manifest | Skills | Extras |
|----------|----------|--------|--------|
| **Claude Code** | `.claude-plugin/plugin.json` | `plugins/hstack/skills/*/SKILL.md` | `plugins/hstack/agents/`, `plugins/hstack/commands/` |
| **OpenAI Codex** | `.agents/plugins/marketplace.json` -> `plugins/hstack/.codex-plugin/plugin.json` | `plugins/hstack/skills/*/SKILL.md` | `plugins/hstack/agents/`, `interface` branding |
| **Cursor** | `.cursor-plugin/plugin.json` | `plugins/hstack/skills/*/SKILL.md` | `rules/*.mdc` with glob triggers |

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
codex marketplace add leehanchung/hstack
```

In the Codex app, add the GitHub marketplace source `leehanchung/hstack`, then enable the HStack plugin.

### Cursor

Symlink or copy into your Cursor plugins directory. Rules in `rules/` auto-attach to matching file types (e.g., `.tex` files trigger `ml-paper-writing`).

## Adding a New Skill

1. Create `plugins/hstack/skills/<skill-name>/SKILL.md` with frontmatter
2. Add reference files in `plugins/hstack/skills/<skill-name>/references/`
3. Create `rules/<skill-name>.mdc` for Cursor glob-based auto-attachment
4. Update the skill table in this README

## License

MIT
