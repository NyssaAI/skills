# NyssaAI — Agent Skills Catalog

The central public repository for AI agent skills across the NyssaAI ecosystem. Compatible with Claude Code and Antigravity.

---

## Installation

### Via NyssaAI Curated Marketplace (Recommended)

1. Register the NyssaAI marketplace:
   ```bash
   /plugin marketplace add github.com/NyssaAI/plugin-marketplace
   ```

2. Install the skills package:
   ```bash
   /plugin install skills@nyssaai
   ```

### Direct Installation

You can also install this repository directly:

```bash
/plugin add github.com/NyssaAI/skills
```

---

## Repository Structure

```
.
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/                  # Individual skill definitions
│   └── <skill-name>/
│       ├── SKILL.md         # Skill instructions & metadata
│       └── ...
├── LICENSE                  # MIT License
└── README.md
```

---

## Skills Catalog

| Skill | Description | Status |
| :--- | :--- | :--- |
| *(Catalog growing)* | See [skills/](skills/) for upcoming workflow skills. | In development |

---

## Creating a New Skill

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
3. Test the skill locally with your agent.
4. Submit a pull request.

---

## License

[MIT](LICENSE) © 2026 NyssaAI
