# NyssaAI — Agent Skills Catalog

The central public repository for AI agent skills across the NyssaAI ecosystem. Built with a universal layout compatible with **Google Antigravity (AGY)**, **Claude Code**, **OpenAI Codex**, **OpenClaw**, and **Hermes Agent**.

---

## Installation & Usage

### 1. Claude Code

#### Via NyssaAI Curated Marketplace (Recommended)
```bash
/plugin marketplace add github.com/NyssaAI/plugin-marketplace
/plugin install skills@nyssaai
```

#### Direct Repository Add
```bash
/plugin add github.com/NyssaAI/skills
```

### 2. OpenAI Codex

Add to your `.codex` configuration or clone into your skills directory:
```bash
git clone https://github.com/NyssaAI/skills.git
```
Codex discovers skills via `.codex-plugin/plugin.json` and `skills/`.

### 3. Google Antigravity (AGY)

Include as a workspace customization in `.agents/` or install globally via `~/.gemini/config/plugins/`. Discovered automatically via `gemini-extension.json` and `.agents/plugins.json`.

### 4. OpenClaw & Hermes Agent

Both runtimes natively read the AgentSkills.io standard directory:
```bash
git clone https://github.com/NyssaAI/skills.git
```
Point your agent runtime or extra skills directory to `./skills/`.

---

## Skills Catalog

| Skill | Description | Supported Agents |
| :--- | :--- | :--- |
| [**`para-vault`**](skills/para-vault/) | Manage a PARA knowledge vault: classify notes, enforce folder depth and naming, track document maturity and authority, maintain indexes, and archive safely. | AGY, Claude, Codex, OpenClaw, Hermes |

---

## Repository Structure

```
.
├── .agents/
│   └── plugins.json                   # Antigravity skill declarations
├── .claude-plugin/
│   └── plugin.json                    # Claude Code plugin manifest
├── .codex-plugin/
│   └── plugin.json                    # Codex plugin manifest
├── gemini-extension.json              # Antigravity extension metadata
├── AGENTS.md                          # Universal agent instruction anchor
├── CLAUDE.md                          # Claude Code reference
├── GEMINI.md                          # Antigravity reference
├── skills/                            # Canonical skills directory
│   └── para-vault/                    # PARA Knowledge System skill
│       ├── SKILL.md                   # Core skill workflow & frontmatter
│       ├── agents/
│       │   └── openai.yaml            # Codex UI metadata
│       └── references/                # Progressive disclosure references
│           ├── filing-logic.md
│           ├── frontmatter-schemas.md
│           └── para-rules.md
├── LICENSE                            # MIT License
└── README.md
```

---

## Adding a New Skill

1. Create a new directory under `skills/<skill-name>/`.
2. Add a `SKILL.md` with standard frontmatter:
   ```yaml
   ---
   name: <skill-name>
   description: >-
     A concise description explaining when the agent should trigger this skill.
   ---

   # Skill Name

   ## Workflow
   Step-by-step guidance.
   ```
3. If the skill has complex rules or schemas, put them into `references/` and link to them using relative paths.
4. Optional: add `agents/openai.yaml` if you want custom prompt starters or titles in OpenAI Codex UI.

---

## License

[MIT](LICENSE) © 2026 NyssaAI
