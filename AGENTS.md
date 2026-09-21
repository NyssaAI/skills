# NyssaAI Agent Skills

This repository is the canonical public skills catalog for NyssaAI, engineered for cross-agent compatibility across **Google Antigravity (AGY)**, **Claude Code**, **OpenAI Codex**, **OpenClaw**, and **Hermes Agent**.

## Repository Conventions

- **Skills Directory**: All skills reside under `skills/<skill-name>/`.
- **Primary Instruction**: Each skill must contain a `SKILL.md` with standard YAML frontmatter (`name:`, `description:`).
- **Progressive Disclosure**: Detailed guides, checklists, rules, and schemas belong in `references/` within the skill folder and are loaded on-demand.
- **Relative References**: All internal markdown links within a skill must use relative paths (e.g. `[Rules](references/para-rules.md)`), never host-specific absolute paths.
- **Agent Metadata**: Host-specific metadata stays scoped:
  - Codex / OpenAI UI: `skills/<skill-name>/agents/openai.yaml`
  - Claude Code: `.claude-plugin/plugin.json`
  - Codex Plugin: `.codex-plugin/plugin.json`
  - Antigravity: `gemini-extension.json` and `.agents/plugins.json`

## Available Skills

- **para-vault** (`skills/para-vault/`): Manage a PARA knowledge vault — classify notes, enforce folder depth and naming, track document maturity and authority, maintain indexes, and archive safely.
