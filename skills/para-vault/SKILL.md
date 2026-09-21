---
name: para-vault
description: "Manage a PARA knowledge vault: classify notes, enforce folder depth and naming, track document maturity and authority, maintain indexes, and archive safely."
metadata:
  version: "0.9.1"
---

# PARA Vault Knowledge System

Use this skill for creating, filing, renaming, reviewing, or archiving notes in a PARA-based vault. Preserve user content and make the smallest compliant change. Follow explicit current user instructions, then the applicable accepted vault rules, then this skill's defaults. Resolve competing canonical rules using the schemas' authority rule; ask about unresolved conflicts before dependent changes. Preserve existing folder schemes without silently migrating them; creating root entries still requires the authorization below.

## Finding governing vault rules

For decisions that depend on vault conventions, first check a rules path or configuration supplied for this vault, then rules links in its existing indexes, then make a targeted search in its existing rules location. Use the accepted rules found there; a filename alone does not establish authority. If no applicable rule is found, use this skill's defaults while preserving existing folder schemes. If rules conflict, apply the schemas' authority rule and ask only about unresolved conflicts that affect the task. Do not create settings or reorganize the vault merely to complete discovery.

## Canonical structure

```text
.temp/                         # temporary working files only; nested folders allowed
0-inbox/                       (raw captures; processed originals go in 0-inbox/archive/)
1-projects/{project}/          (active work; one optional subfolder level)
2-areas/{area}/                (ongoing interests; email/calendar date-folder exceptions)
3-resources/{resource-type}/   (reference material; use the approved types below)
4-archives/                    (done, stale, superseded, or abandoned)
```

The vault root is closed by default. The only permitted top-level directories are `.temp/`, `0-inbox/`, `1-projects/`, `2-areas/`, `3-resources/`, and `4-archives/`. Do not create loose root files or any other top-level directory, including convenience folders for scripts, exports, attachments, backups, or new PARA categories, unless the user explicitly authorizes it. Preserve existing root entries; this rule does not authorize deleting or migrating them. Use `.temp/` for temporary and generated working files, then clean them up when the operation is complete.

### Areas

Areas are ongoing domains with no completion date. The standard areas are:

- `email/` — correspondence, follow-ups, and mailbox operating context
- `calendar/` — appointments, routines, scheduling, and planning context
- `daily-notes/` — daily logs, observations, decisions, and journal-like captures

Other areas may be added when they represent a durable part of life or work. Do not create an area for a one-off project or a topic that is better treated as a resource.

Email records go in `2-areas/email/YYYY.MM.DD/`, grouped by the email date defined in the schemas. Calendar invitations go in `2-areas/calendar/we-YYYY.MM.DD/`, grouped by the week containing the event date; `we` means week ending. Weeks run Monday through Sunday, inclusive; name each week folder with its Sunday date. Keep invitations inside the week folder in their native format, such as `.ics`. These date folders allow one additional level only. Other areas remain flat.

Permanent area indexes stay at the area root: `00-email-index.md`, `00-calendar-index.md`, or `00-bookkeeping-index.md`. For example:

```text
2-areas/bookkeeping/00-bookkeeping-index.md
2-areas/email/00-email-index.md
2-areas/email/2026.09.21/2026.09.21-client-question.md
2-areas/calendar/00-calendar-index.md
2-areas/calendar/we-2026.09.27/2026.09.23-project-review.ics
```

The calendar example follows the Monday-Sunday convention: September 23 belongs to the week ending September 27.

### Resources

Resources are reusable reference collections rather than active work. The standard resource types are:

- `company-context/` — durable facts about companies, organizations, products, and operating context
- `people/` — durable context about individuals and professional relationships
- `goals/` — stated objectives, intentions, and goal frameworks used as reference across projects and areas
- `rules/` — canonical vault rules, schemas, tag vocabulary, and filing logic
- `templates/` — note, project, Map of Content (MOC), and other approved content templates

Keep resource types broad and stable; do not create a folder for every topic. New resource types require explicit authorization.

Keep the normal maximum depth at four levels: vault > PARA category > folder > note. Projects may use one additional subfolder level when necessary, for a maximum of five levels, but nesting is discouraged. Email day folders and calendar week-ending folders also permit five levels. All other areas remain flat. Archived project bundles retain their permitted project depth. Nested temporary working folders under `.temp/` are exempt.

## Maps of Content: guides to related notes

A **Map of Content (MOC)** is a Markdown note that helps you understand and navigate a collection of related notes. Think of it as the area's home page: it explains what the area covers, groups links by subject, and briefly explains why each linked note matters. It is a document, not another folder.

- **Main map (L0, or level zero):** each area has one, named `00-area-slug-index.md`. It introduces the whole area and provides access to its notes, directly or through subtopic maps. Its permanent filename has no date prefix.
- **Subtopic map (L1, or level one):** an optional note named `01-subtopic-slug-index.md`, created when the user requests it or it materially improves navigation through a coherent subtopic. Around 15 related notes is a useful signal, not a minimum. The main map links to it. Both map files remain at the area root, including in email and calendar areas. Subtopic index filenames also have no date prefix.
- **No level-two maps (L2):** do not create maps beneath subtopic maps. Reconsider the topic boundaries if another level seems necessary.
- **Project index:** `YYYY.MM.DD-project-slug-index.md` serves the same guiding role for a project, alongside its goal and deadline. Do not create a separate main MOC for that project.

Start a map with a short explanation of the subject and current understanding, followed by sections of links with brief descriptions, open questions, and links to related areas. For example, `2-areas/bookkeeping/00-bookkeeping-index.md` explains bookkeeping practices and links to procedures and monthly reconciliation projects. Keep the map current as notes are added or changed. The `00-` prefix identifies the main map and `01-` identifies a subtopic map. All subtopic maps share `01-`; these prefixes indicate map level, not a running sequence. Links express the relationships; no additional folders are needed. Email/calendar records and their day/week folders use dates instead of map-level prefixes.

## Operating rules

- Use `0-inbox/` for raw or unclassified captures when the destination is not yet clear. Do not force known project work through the inbox: when the project, area, or resource destination is already clear, create or file the note directly there.
- Route source email and calendar records to their area date folders and link them from relevant projects. If required source dates cannot be resolved, preserve the record in the inbox until resolved; follow the source-record workflow. For other inbox notes, read intent fields, apply the cascade in filing-logic.md, and inspect nearby notes or semantic-search results when ambiguity exists.
- Direct project work must still follow the naming and frontmatter rules and must update the project's index file when it adds meaningful work or context.
- Every maintained Markdown note has YAML frontmatter with `type`, `created`, and `status`. Preserve native record formats such as `.ics`; do not insert YAML into them. Tags are optional; omit `tags` or use `tags: []` when no useful classification applies. Disposable tool output under `.temp/` and unchanged preserved originals are exempt from note schemas; retained notes are not.
- Use lowercase kebab-case slugs for filenames and folder names, with the documented date formats and `.temp/` exception. Use `YYYY.MM.DD-record-slug` plus the appropriate extension when a date identifies the work or record; use `descriptive-slug.md` for enduring undated content. Use the index names specified above. Project folders remain `YYYY.MM.DD-project-slug`, matching their index prefix. Use the date meanings in the schemas; do not change date prefixes merely because a document is edited. Attachments use simple descriptive names and stay beside their owning document; follow the [attachment rules](references/para-rules.md#attachments).
- Use `status` for maturity: `raw`, `draft`, `reviewed`, or `established`. Use the separate boolean `canonical: true` only for a designated source of truth; authority does not imply maturity. For competing canonical documents serving the same purpose, the most recent canonical designation wins; exclude historical copies and use the schemas' recency and tie rules.
- Add tags only when they improve retrieval, using the closed vocabulary and preservation rules in [the schemas](references/frontmatter-schemas.md#field-meanings).
- Protect documents with `status: established`: minor wording or formatting corrections may retain that status; propose substantive revisions separately and preserve the accepted version until the user approves the revision. An explicit instruction approving a specific revision counts as approval. Keep its maturity accurate after revision; do not automatically promote a draft. Preserve useful content and evidence in canonical documents; propose a replacement if their purpose changes rather than silently repurposing the source of truth.
- Maintain maps as readable guides using the structure above. Follow [index ownership and links](references/para-rules.md#index-ownership-and-links), including wikilinks for notes and attachments. Add `## Related` when strong connections exist. Routine link maintenance may retain established status when it does not change accepted assertions or policy.
- Never auto-archive MOCs, active area notes, or Resources. Use the preservation, collision, and archive procedures in the workflow reference before moving or overwriting a file.

Before choosing metadata or dates, read [references/frontmatter-schemas.md](references/frontmatter-schemas.md). For filing, collisions, protected revisions, temporary artifacts, or archiving, read [references/para-rules.md](references/para-rules.md). For destination decisions, read [references/filing-logic.md](references/filing-logic.md).
