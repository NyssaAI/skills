# Frontmatter Schemas

All maintained Markdown notes require `type`, `created`, and `status`. Frontmatter dates use ISO `YYYY-MM-DD`; filename date prefixes, where applicable, use `YYYY.MM.DD`. Undated filenames still retain `created` in frontmatter. Tags are optional YAML lists without `#`; omit the field or use `tags: []` when none are useful. Preserve native records such as `.ics` invitations in their native format without inserting YAML.

Disposable tool output in `.temp/` and unchanged preserved originals are exempt. Do not retrofit metadata into preserved evidence.

## Field meanings

`type` identifies document form, independently of maturity, authority, location, and tags. For new notes use `note` (including email captures, daily notes, rules, and procedures), `moc` (area or subtopic guide), or `project` (project index). Preserve existing types; use additional types only when an accepted vault schema defines them. A procedure normally uses `type: note` and may use `tags: [procedure]`.

| Status | Meaning |
|---|---|
| `raw` | Captured and unchecked; may already be correctly filed |
| `draft` | Being written; incomplete or provisional |
| `reviewed` | Checked for clarity, completeness, and supporting evidence |
| `established` | Accepted as reliable; protected from casual revision |

Use exactly one `status`. Choose it from actual review and acceptance, not the filename, destination, or document type. `developing` and `refining` are not supported statuses.

`canonical` is an optional boolean, defaulting to false when omitted. Set `canonical: true` for the designated source of truth. This is independent of maturity; do not infer authority from a note being established.

When multiple canonical documents compete to govern the same purpose, the most recently designated canonical document wins. Sharing a subject alone does not make documents competitors: a canonical reconciliation procedure and a canonical monthly reconciliation record can each govern their distinct purpose. Exclude unchanged preserved inbox originals and historical snapshots, even if their embedded metadata says `canonical: true`; use preservation context and companion metadata to identify them. An archived completed project can still be authoritative for its own distinct purpose.

Determine recency from the documented canonical designation date/time in the note body or reliable approval history; record that date/time when making a new authorized designation. If no designation date is available for a candidate, use its `created` date as the fallback. Compare timestamps in a common timezone; do not use filesystem modification times, import times, filename dates, or routine edits to infer a newer designation. If dates tie or the available evidence cannot establish their order, ask which document governs. Never invent a designation date or promote a noncanonical proposal by recency. Resolving which document to follow does not authorize rewriting or archiving the others.

The optional tag vocabulary is closed to the five values below. Extend it only with explicit user authorization. Preserve unrecognized tags in existing notes until their migration is authorized; do not propagate them into new maintained notes or silently remove historical metadata.

Tags describe useful classifications across folders:

| Tag | Meaning |
|---|---|
| `decision` | Recorded decision and rationale |
| `policy` | Rule or governing expectation |
| `procedure` | Instructions for a repeatable activity |
| `reference` | Factual material for later consultation |
| `analysis` | Interpretation, comparison, or evaluation |

Avoid tags that duplicate the folder, `type`, `status`, or canonical designation. Do not use maturity or authority as tags.

## Date meanings and configuration

Explicit current user instructions take precedence over accepted vault conventions, which take precedence over defaults here. For conflicting canonical rules, apply the authority rule above; if the conflict remains unresolved, ask before dependent filing. Do not rename historical records merely to impose a new convention. For new records:

| Date | Meaning |
|---|---|
| `created` | Date this note was first authored. For a new transcription/import note, the capture date; preserve a known original note creation date when moving/importing an existing note. Never reset on editing or filing. |
| Project folder/index prefix | Date the project folder was first created. Folder and index prefixes match, even if the index is authored later. Accounting period belongs in the slug/goal; deadline is separate. |
| Email day folder and filename prefix | Received date for incoming mail; sent date for outgoing mail. If received time is unavailable, use the message's sent timestamp and disclose that fallback in the capture body or the native record's index annotation. If neither is known, ask rather than invent a date. |
| Calendar filename prefix and week | Event start date, not invitation receipt date. Weeks run Monday through Sunday, inclusive; the folder date is Sunday. |
| Daily-note prefix | Day being described, even when the note is written later. |
| Other dated note prefix | Date of the described event/record when known; otherwise note creation date. Explain a differing event date in the body. |
| `deadline` | Actual agreed target date; do not infer month-end from a project name. If unknown, ask before creating a new project; a capture can remain in the inbox meanwhile. |
| `archived` | Date the item entered the archive. |

Locate existing accepted settings using [the vault-rule discovery procedure](../SKILL.md#finding-governing-vault-rules) before creating any settings note. The confirmed calendar convention is Monday-Sunday, with Sunday week-ending folders; do not ask to confirm it again. For filing timezone, use a task-specific timezone explicitly requested by the user; otherwise use the accepted vault setting, then an explicitly supplied user timezone. If none is available, ask when timezone could change the day. Convert timestamped mail and events to that timezone for filing, while retaining original timestamps and zones. All-day event dates remain their stated calendar dates. Do not infer missing source timezones.

When the task calls for persisting settings in the vault, update the existing designated rules note under its protected-revision rules; do not create a competing file. Only if no such note exists, use `3-resources/rules/vault-settings.md` with `type: note`, `created`, and the maturity justified by acceptance. Designation as canonical still requires user authorization. Read settings from clear body text; do not invent configuration schema keys. A skill-only update does not itself require editing vault documents.

Keep a recurring invitation as one native series record filed by its `DTSTART`; do not manufacture occurrence copies. File a separately received occurrence exception by its occurrence start date, retaining its UID and recurrence identity. For reschedules or cancellations, follow record-update handling in the workflow reference.

## Stable note

```yaml
---
type: note
created: YYYY-MM-DD
status: established
tags: []
---
```

## Draft note

```yaml
---
type: note
created: YYYY-MM-DD
status: draft
tags: [analysis]
---
```

## Map of Content (MOC)

Use `type: moc` for an area guide or subtopic guide. See [SKILL.md](../SKILL.md#maps-of-content-guides-to-related-notes) for their purpose, filenames, placement, and creation rules. Project indexes use the separate schema below.

```yaml
---
type: moc
created: YYYY-MM-DD
status: draft
tags: []
---
```

## Project index

Name the index `YYYY.MM.DD-project-slug-index.md` inside its matching `YYYY.MM.DD-project-slug/` folder.

```yaml
---
type: project
created: YYYY-MM-DD
status: draft
tags: []
goal: "concrete outcome"
deadline: YYYY-MM-DD
---
```

## Inbox-only intent fields

While a note is in `0-inbox/`, it may include `filing-hint`, `context`, and `source`. The librarian uses these as signals, then strips these inbox intent fields when filing. Preserve any substantive source attribution in the note body.

## Canonical rules note

```yaml
---
type: note
created: YYYY-MM-DD
status: established
canonical: true
tags: [policy]
---
```

Use this maturity and authority only after acceptance and designation. See the protected-document rules in [filing-logic.md](filing-logic.md).

## Archive fields

For an individually archived Markdown note, add these fields. For a whole project, add them to its index; they apply to the bundle without rewriting every child. For native records or unchanged historical snapshots, put them in the companion metadata note defined in the workflow reference:

```yaml
archived: YYYY-MM-DD
archived-from: 2-areas/area-name/original-note.md
archive-reason: superseded # completed | stale | abandoned
```

`archived-from` is the exact original vault-relative file path, or the original project folder path for a bundle. Archiving alone does not change maturity. Resolve canonical authority as described in the archive workflow.
