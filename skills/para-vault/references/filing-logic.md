# Filing Logic

See [SKILL.md](../SKILL.md#maps-of-content-guides-to-related-notes) for MOC and project-index roles.

## Cascade

Apply source-record routing first, then evaluate the cascade in order. If ownership or usefulness remains unknown, leave the capture in `0-inbox/`; failure to classify is not evidence that it should be archived.

Route email and calendar source records to their area date folders as defined in [SKILL.md](../SKILL.md#areas), using the date meanings in [frontmatter-schemas.md](frontmatter-schemas.md#date-meanings-and-configuration). Link these records from related projects rather than relocating them. When required filing information is missing, hold the record in the inbox; follow [source-record handling](para-rules.md#collisions-and-source-records) before assigning a folder. Apply the cascade below to other notes, including analysis or work derived from those records.

1. **Project** — the note directly advances an active project with a stated goal and deadline. File under `1-projects/YYYY.MM.DD-project-slug/`.
2. **Area** — the note belongs to an ongoing responsibility or interest with no end date. File under `2-areas/{area}/`.
3. **Resource** — the note is reference material rather than work or an ongoing commitment. File under `3-resources/{resource-type}/`.
4. **Archive/delete** — its lack of a useful current role is established. Prefer `4-archives/`, subject to the archive exclusions in [para-rules.md](para-rules.md#archive-workflow); delete only when explicitly authorized.

When the project, area, or resource destination is clear, create or file directly there. Update the project index when adding meaningful work or context. Use `0-inbox/` for raw or unclassified captures when the destination is unclear. Maturity and authority do not determine the destination.

## Area and resource choices

Use existing areas before creating new ones. Apply the [area criteria](../SKILL.md#areas) and [approved resource types](../SKILL.md#resources) in the entrypoint; do not invent categories outside those rules.

## Decision questions

- What concrete active outcome or deadline does this support?
- If none, what ongoing area owns it?
- If neither, is it reference material that may be useful later?
- If none, is it redundant, stale, or intentionally disposable?

When two destinations seem plausible, inspect neighboring notes and semantic-search matches. Prefer the destination whose MOC or project index can explain why the note belongs there. Do not create a new project or area merely to avoid choosing an existing one.

## Structure, metadata, and protection

Use [SKILL.md](../SKILL.md#canonical-structure) for permitted folders, depth, and filenames, and its MOC section for index roles and when a subtopic map is useful. Do not create folders to represent tags, maturity, or canonical authority.

Use [frontmatter-schemas.md](frontmatter-schemas.md) for document types, dates, maturity, authority, and optional tags. Filing or renaming a note does not establish reliability or authority.

Follow [the protected-revision workflow](para-rules.md#protected-revisions) before revising established documents or changing a canonical document's purpose.
