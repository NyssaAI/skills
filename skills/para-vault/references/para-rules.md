# PARA Rules and Workflows

Use [SKILL.md](../SKILL.md) for folder limits, filenames, and MOC/project-index roles; use [frontmatter-schemas.md](frontmatter-schemas.md) for metadata and date meanings. These workflows do not authorize reorganizing existing vault content.

## Index ownership and links

Update the owning area MOC or project index with useful annotated links when adding meaningful work or context. An area's main MOC may reach notes through its subtopic MOC; do not duplicate every link at both levels. Email and calendar records stay in their area date folders and are linked from relevant projects. For resources, inbox, and archives, update an existing relevant index if present; do not invent a MOC or index to satisfy this instruction.

Use note-name wikilinks only when unambiguous. Otherwise use vault-relative wikilinks, for example `[[2-areas/bookkeeping/00-bookkeeping-index|Bookkeeping]]`. Link attachments using the attachment rule below; for other native records, use relative Markdown links with the extension, resolving them from the linking note. For moves and renames, identify affected inbound links, outgoing relative links, attachment references, and links within moved bundles. Repair them for the final paths and verify that they still resolve to their intended targets, including any heading or block references; preserving file bytes alone is insufficient. Retain useful historical links and describe archived or superseded targets accurately. Routine link maintenance does not require a separate proposal unless it changes accepted assertions or policy.

## Attachments

Inside a project, store attachments and other non-note working files in purpose-specific subdirectories by default. Keep related documents and attachments together within their working collection. A project-root note links into that collection; it does not require its attachments to sit at the root. Outside projects, keep attachments beside their owners, including inside email day folders or calendar week folders, without additional attachment subfolders. Use a simple descriptive kebab-case document name with its original extension, such as `bank-statement.pdf`, without requiring a date prefix. Link from the owning Markdown document with `[[bank-statement.pdf]]`; qualify the wikilink with the vault-relative path when the name is ambiguous. For a native owner that cannot contain wikilinks without changing its format, place the attachment link in its existing index annotation or companion Markdown capture. Preserve native attachment contents and apply the collision and source-identity rules below. When moving or archiving an owner, preserve access to its attachments and repair affected links; do not remove an attachment still used by another document.

## Project working collections

Keep project-wide Markdown notes at the root. Put a Markdown note in a subdirectory only when it directly supports that working collection, such as a discovery register or analysis of an agreement. Put non-note files in purpose-specific subdirectories by default, even when referenced by a root note. A root-required configuration file or other tool-dependent artifact may stay where its consumer requires it. Do not create a generic nested `notes/` tree or separate related documents solely by file extension.

For example:

```text
1-projects/2026.09.21-lawsuit/
  2026.09.21-lawsuit-index.md
  strategy.md
  chronology.md
  discovery/
    document-register.md
    requests/
      first-request.pdf
    responses/
      first-response.pdf
  evidence/
    employment/
      agreement.pdf
      agreement-analysis.md
```

This is an illustration, not a required folder template. Create only folders the actual work needs. Keep the main project index useful by linking to key documents, working folders, or their registers with brief descriptions. A local register may guide a large collection, but is not required for every folder; use `type: note` for a maintained register. The project index need not duplicate its file listing. Preserve complete source packages and their useful internal relationships when filing or archiving.

## Collisions and source records

Before writing, check the destination and existing source identity. Never overwrite an unrelated item. For distinct items with the same proposed name, append `-2`, `-3`, and so on before the extension, taking the first unused suffix. Keep the chosen name stable on re-import by matching source identity first. For colliding new project names, append the suffix to the project slug and use that same slug in its index filename; do not suffix the index independently.

For email, retain Message-ID when available, sender, recipients, received/sent timestamps and zones, and source attribution in the body of a Markdown capture or in the native record. For invitations retain UID, recurrence identity, sequence/update metadata, and original timezone data in the native file. Do not add YAML to native formats. Matching titles alone do not prove identity. If no source identifier exists, compare content and provenance; do not discard uncertain matches.

An exact duplicate import needs no second file; link to the existing record. If the same source identity has a changed payload, preserve the earlier record before storing the new version with the next unused suffix and updating relevant index links. A rescheduled invitation goes in the newly applicable week folder; retain a labeled link to the previous version and mark cancellation in index text when applicable. A recurring series and its occurrence exceptions are distinct identities. Do not silently replace a changed source record, and do not move historical versions merely to make all versions share a folder.

For a calendar update or cancellation without a usable event start, first match the original event by UID and recurrence identity. For a cancellation, use the matched event's applicable start date when recoverable. For a reschedule, recover the new start from the update or reliable associated source evidence; do not use the old date as if it were the new date. If identity or the required date remains unresolved, preserve the native payload in `0-inbox/` and ask for the missing information. Use an undated descriptive filename such as `unresolved-calendar-update.ics`, with collision handling, until the event date is known. Explain the missing information in an existing relevant index annotation or a sibling Markdown capture (`type: note`, its own `created`, `status: raw`, `canonical: false`). Do not invent a week, substitute receipt date, or insert YAML into the native record. Once resolved, apply normal source-record filing and link maintenance.

For independently authored notes, overlapping text or subject matter alone does not establish redundancy. Preserve unique content and provenance, identify contradictory claims, and do not merge or archive merely because the notes overlap. When reconciliation is requested, distinguish supported resolutions from unresolved claims and apply protected-revision rules to substantive changes in established notes. Canonical precedence selects the governing document; it does not by itself disprove every differing claim. Ask only when an unresolved conflict prevents the requested reconciliation.

## Resuming interrupted operations

Before retrying a partially completed filing, move, or archive operation, inspect the source, intended destination, any preserved original or companion metadata, and affected indexes. Compare content and provenance to establish whether the destination belongs to that operation; account for expected metadata and link edits rather than requiring byte equality for maintained notes.

If it is the same operation, reuse verified completed work and finish only the missing preservation, metadata, and link updates. Do not allocate another suffix or treat an already-created project destination as an unrelated collision solely because it exists. Verify destination content and the affected links before removing a remaining working source; retain required historical originals. If the source is already gone, verify the destination and finish outstanding links or metadata without recreating the source. Do not reconstruct missing original evidence by guessing.

If the copies diverge beyond the expected changes or identity remains uncertain, preserve both and ask before overwriting, merging, or removing either. For an unrelated destination, use the normal collision rules. Report any unresolved recovery work rather than claiming completion.

## Inbox processing

Known destinations allow direct filing. The inbox workflow applies to unclassified captures and to source records temporarily held because required filing information is unresolved. Once that information is resolved, process the held record using the steps below.

1. Inspect `filing-hint`, `context`, `source`, maturity, authority, and any tags. Apply protected-revision rules before substantive editing.
2. Apply [filing-logic.md](filing-logic.md), including its email/calendar source-record precedence. Inspect nearby notes or semantic-search matches to resolve ambiguity; matches are evidence, not an absolute rule. Leave a capture in the inbox if its destination or usefulness remains unresolved; do not interpret uncertainty as grounds for archiving.
3. Preserve an unchanged original in `0-inbox/archive/`, applying collision handling. These preserved originals are historical evidence, not competing current canonical documents, even if their captured metadata says otherwise.
4. On the working note, correct metadata, remove inbox-only intent fields, and retain substantive attribution in the body. Filing alone promotes neither maturity nor authority. Preserve native formats unchanged.
5. Apply the naming and date rules; move the working note without overwriting another item. Verify destination content before removing the working source, repair affected links, and update indexes according to ownership above.
6. Add `## Related` only when clear, valuable links exist.

If a note is not useful, delete only with explicit user authorization; otherwise archive it with a reason, subject to the archive exclusions below.

## Protected revisions

For a substantive revision to an established note, create a sibling `<original-stem>-proposed-revision.md`, applying collision handling if necessary. This is a proposal, not an additional MOC or project index, so use `type: note`, its own `created` date, `status: draft`, and `canonical: false`. Link to the accepted original in the body and describe the proposed changes and supporting evidence. Preserve the original and its existing canonical links while approval is pending. An explicit instruction approving that specific revision already supplies approval; do not ask again.

After approval:

1. Preserve the accepted version in verified durable version history that can actually restore it. If such history is unavailable, save an unchanged snapshot as `4-archives/YYYY.MM.DD-<original-stem>-prior-version.md`, using the snapshot date and collision rules. Create its companion metadata note as described below. Do not use `.temp/` as the sole durable copy of an accepted version.
2. For the same document purpose, apply the approved content at the original path, preserving its original `created` date, filename, and canonical designation. Editing permission alone is not evidence that every new claim is established: use `established` when the user accepts the revised document as reliable, `reviewed` when it has been checked but not accepted, or `draft` while provisional. Preserve source evidence and useful content.
3. For a changed purpose, retain the original until the user approves a replacement and explicitly identifies which document becomes the source of truth. Transfer authority and redirect current links only as authorized; label the superseded document and preserve its history.
4. Update existing relevant indexes and mark the proposal as applied in its body, with a link to the accepted document. Archive it when authorized under the archive rules; do not leave it apparently pending or delete it without authorization.

Minor corrections and routine index maintenance can be applied directly when they preserve accepted meaning. Before overwriting, retain a recoverable copy in existing version history or `.temp/` until the result is verified; substantive accepted-version preservation follows the durable procedure above. Do not use revision proposals to justify unrelated cleanup.

## Archive workflow

Do not automatically archive area MOCs, active area notes, or resource documents. Saving a prior-version snapshot during an approved revision preserves evidence; it does not move the current resource document. Archiving these requires a specific user instruction. A completed, abandoned, or superseded project can be archived as an intact folder, including its project index, after its lifecycle outcome is known. Preserve its complete working-folder structure, including nested Markdown, native documents, and attachments; do not flatten or ZIP the bundle to meet a depth preference. Do not scatter its notes or create additional archive category/year folders.

- Individual items go directly under `4-archives/` with their existing filenames, disambiguated on collision.
- Project bundles go to `4-archives/<existing-project-folder>/`. If that folder name collides, stop to distinguish the same project from a different bundle rather than merging or silently renaming it. Add archive fields to the project index; those fields describe the bundle, including native children.
- Add `archived`, exact `archived-from`, and `archive-reason` to individually archived Markdown notes. Archiving does not replace maturity. Native records remain unchanged; use a companion metadata note for an individually archived native record or unchanged snapshot.

A companion metadata note is named `<archived-stem>-<extension>-archive-metadata.md` alongside the archived item, with the extension written as a slug without its dot, for example `2026.09.23-project-review-ics-archive-metadata.md`. Reserve both paths before writing; if either collides, disambiguate the archived filename and derive the companion name from it. The companion uses `type: note`, its own `created`, `status: raw`, `canonical: false`, and the archive fields. Its body links to the item and explains why it was preserved. For an unchanged snapshot, explicitly identify it as historical evidence, including any canonical flag captured inside it; that embedded flag does not confer current authority. This companion is metadata, not a new MOC.

Archiving alone does not revoke canonical authority: a completed project's authoritative record may remain canonical. For a superseded source of truth, identify the approved successor and set `canonical: false` on the superseded maintained note. Resolve competing canonical documents using the schemas' most-recent-designation rule. If the successor/authority decision remains unknown, resolve it before archiving a current canonical document as superseded. Selecting the current source of truth does not itself authorize moving or deleting older documents. Unchanged snapshots and preserved inbox originals are historical copies as described above.

Check backlinks and living parent documents before moving. A content-preserving move needs no extra permanent backup: verify destination content and repair links before removing the source. If archive metadata edits would destroy needed original evidence, preserve an unchanged snapshot first. Never overwrite an unrelated archive item.

## Temporary work

Use task-scoped paths such as `.temp/reconciliation-check/check-balances.py` and `.temp/reconciliation-check/balance-check-results.csv`. Nested temporary folders are allowed. Scripts and disposable output, including Markdown output, need no note frontmatter or index entries. Do not put scripts, exports, or backup folders at the vault root.

If output becomes a retained deliverable, file it in its known project/area/resource destination, add metadata if it is a maintained Markdown note, and update the applicable index. Verify the retained copy before cleanup. Remove only the current operation's disposable temporary artifacts when finished, not unrelated `.temp/` contents.

## Dot-folders and ignore rules

- **Dot-folders ignored entirely**: Any dot-folder other than `.temp/` (such as `.obsidian/`, `.git/`, `.stfolder/`, `.trash/`) is an external tool, sync daemon, or version control directory. The agent must ignore them entirely: never scan them for notes, never index them, never move or file content into them, and never delete or alter them.
- **Root ignore files permitted**: Configuration and ignore files (`.gitignore`, `.gitattributes`, `.stignore`) at the root of the vault are permitted exceptions to the closed-root rule.
- **Default .gitignore behavior**: By default, if a `.gitignore` exists at the root of the vault, it should ignore dot-folders (e.g., `.*/` or specifically dot-directories such as `.temp/`, `.obsidian/`, `.stfolder/`) so that internal workspace caches, temporary operational files, and sync metadata are not tracked in version control.
