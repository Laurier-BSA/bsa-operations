# i25 rework: Growth hub becomes a plain resources directory

Asked 30 Sep 2026. Safdar: the training tracker is too complicated. Keep one well-laid-out list of the resources with all the important info. Drop completion tracking entirely. **Plan only. Nothing is built yet.**

## What exists now (built 25 Sep from `i25.md`)

- Page `Growth hub` (🌱) under Handbooks, `3e6ac90c76f181a4bfdfc02afbac063c`.
- `Resources` DB `collection://b0fdd9b7-b2c0-4ce1-bf2c-20d805119e8a`: 14 rows (SU modules A–H, OHRCM deck, Intercultural Certificate, LER, LER Student Life, CSEDI, OHRCM office).
- `Completions` DB `collection://9a53e688-a5c6-438d-95e8-1c951196a111`: one row per exec per required resource.
- Team Directory: `Training records`, `Training required`, `Training done`, `Training overdue`, `Training open codes`, `Training`, `Certs missing`.
- Resources: `Completions`, `Assigned`, `Done`, `Completion`.

## Target

One page, **Training & resources**, containing one database, **Resources**, shown as a clean list. Every row carries what someone needs at a glance: what it is, who it's for, the link, how long it takes, and any key date. No per-person rows, no statuses, no proof.

### Resources: fields kept (shown in this order)

| Field | Type | Change |
|---|---|---|
| `Name` | title | none |
| `Kind` | select | none (SU training, Certificate, Recorded workshop, Course, Support office, Guide) |
| `For` | multi_select | rename from `Required for`. Description: "Roles this is most useful for. Empty means everyone." |
| `Link` | url | none |
| `File` | files | none |
| `Time needed` | text | none |
| `Key date` | date | rename from `Due by`. Description: "Session date or SU deadline, if there is one." |
| `Provider` | select | none |
| `Summary` | text | none |
| `Contact` | email | **new**, for the support offices (humanrights@wlu.ca, diversity@wlu.ca) |
| `Status` | select | none (Active / Retired). Views show Active only |

### Resources: fields retired (renamed, hidden, never deleted)

`Code` → `[OLD] Code`, `Proof` → `[OLD] Proof`, `Format` → `[OLD] Format`, `Year` → `[OLD] Year`, `Last checked` → `[OLD] Last checked`, `Completions` → `[OLD] Completions`, `Assigned` → `[OLD] Assigned`, `Done` → `[OLD] Done`, `Completion` → `[OLD] Completion`. `SU guide`, `Initiative` and `Presenter` stay but are hidden from the default view.

### Completions and Team Directory

- `Completions` DB → rename `[OLD] Completions`, move to Archive. Rows untouched.
- Team Directory: rename the 7 training properties to `[OLD] Training records`, `[OLD] Training required`, and so on. Hide them from every Team Directory view (UI-only, so log it for Cowork).

### Views on Resources

1. **Directory** (default): list view, Active only, grouped by `Kind`, sorted by Name. Shows For, Time needed, Key date, Link.
2. **By role**: board grouped by `For`, Active only. An exec opens their role column and sees their set.
3. **Dates**: table, `Key date` not empty, sorted ascending. Shows the SU deadline and the ICC Winter sessions.

### Page content (replaces the current Growth hub body; fetch first)

- Title: `Training & resources`, icon 📚.
- One-line callout: "Everything useful for your role in one list: SU training, certificates, and support offices. Open a row for the link and details."
- The Resources database (Directory view first).
- A short "Add something" line: "Found a good course, talk or guide? Add a row. Official links only. Set old ones to Retired instead of deleting."
- Remove the My training / For presidents / How this works headings.

### Row pages

Replace the "How to complete… Growth hub → My training…" line on all 14 rows with nothing. The Summary field carries the content. Fetch each row before editing.

### Links elsewhere

- Handbooks `## Everyone`: update the link text to the new title. Fetch first.
- Search for any other mention of `My training` or `Completions` (Briefing, VP Handbook, onboarding) and remove it.

## Hard-rule check

- No page, row or property is deleted. Everything goes to `[OLD]` + Archive.
- No new database. One new property (`Contact`).
- No permissions touched. Free-plan only.

## For Cowork (UI-only)

- Hide the `[OLD] Training …` properties on Team Directory views and pages.
- Hide the `[OLD]` Resources properties on the row page layout.

## Size

Small build: 1 page rewrite, ~13 property renames, 1 new property, 3 views, 14 row-body edits, 1 DB archive. No auditor subagent needed.
