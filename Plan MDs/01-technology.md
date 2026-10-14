# Technology

Owns schema, forms, dashboards, integrations, the site. Section A is the audit and the cleanup, and everything else in the term depends on it running first.

## A. Workspace work

- [ ] `API+` **T1 Audit.** Fetch Home, Briefing, Club Dashboard, Team Progress, Meetings, Finance, and the schemas of Initiatives, Tasks, Team Directory, Transactions, Budget Lines, Budget Categories, Task Pack Templates, Content Directory. Compare against `bsa-system.md` sections 5 to 11. Change nothing in this step. Report: what exists but is not in the file, what the file claims but does not exist, and specifically whether Tasks has **both** an `Owner` relation and an `Assignee (Directory)` relation to Team Directory (if it does, say which one the live views use).
- [ ] `API` **T2 One spelling of Fund.** Transactions, Budget Lines and Budget Categories must use the same two option names. Use whichever spelling the Finance page charts already filter on. Re-check every Finance chart still returns a number afterwards. If the API cannot rename a select option, add it to the UI list in section B instead of leaving a mismatch.
- [ ] `API` **T3 Task Pack Templates edits.** The packs are rows, so this is data not schema.
  - Event pack: the first gate becomes `GATE: Date, room and SU event request confirmed`, Operations, 1 Lock, **Lead 56** (the SU needs eight weeks, 49 was wrong).
  - Add to Event, Booth and Social packs: `Storage Inventory updated, items returned` | Operations | 5 Wrap | -2.
  - Add to Event and Social packs: `Photo dump posted, everyone tagged` | Marketing | 5 Wrap | -2.
  - Add to Event and Booth packs: `Selects and vertical clips in Drive` | Photography | 5 Wrap | -2.
  - Booth pack: add `Engagement hook decided: what people actually do at the table` | Events | 1 Lock | 14. Rename the shift row to `Shift roster from Availability, setup shift named`.
  - New **Social pack**, 6 rows: `GATE: Room or venue confirmed` Operations 1 Lock 21 · `Plan, activity and food agreed, purchase approved by Finance` Events 1 Lock 18 · `Poster and story graphic` Creative 2 Build 12 · `Announcement post and story reminders` Marketing 3 Promote 10 · `GATE: Social run` Events 4 Run 0 · `GATE: Receipts logged and recap filled` Events 5 Wrap -3. Plus the two shared Wrap rows above.
- [ ] `API` **T4 Email on Team Directory.** Add it if missing, fill from Executive Team Form through the `Became` relation where it exists. The digest needs it.
- [ ] `API` **T5 Teams database**, only if decision 2 in `bsa-system.md` is yes. Additive only: Teams database with the eight teams and a VP relation, a `Team (rel)` relation on Tasks and Team Directory backfilled from the existing multi select, rollups for open and overdue tasks. Do not touch existing views or the multi select this term.
- [ ] `API` **T6 People Record**, only after decision 3. Database in the VP teamspace: Person, Violations, Violation reasons, Date, Type (missed commitment, no show, conduct, financial, positive note), What happened, Raised by, Action taken, Resolved, Notes. Copy the existing Violations values across, then rename the Team Directory fields to `Violations (moved)` so nothing is lost. Deleting them is a UI step, later.
- [ ] `API` **T7 Workspace map page** updated to mirror `bsa-system.md` v0.5. Headings and tables, titles not sentences.
- [ ] `API` **T8 Sort on Scheduled.** Every task view on Briefing, Club Dashboard, Team Progress and the team pages sorts on `Scheduled`, not `Due`. Report any that could not be changed.

## B. UI run, Chrome or you

Paste this block into Claude in Chrome on a Notion tab, or work down it yourself. Never delete a page, move it to Archive.

```
1. FULL WIDTH (••• > Full width): Briefing, Club Dashboard, Team Progress,
   Meetings, Run the VP meeting, Finance, Operations
2. DRAG: "Run the VP meeting" and "Team Progress" to the VP teamspace root.
   "Briefing" to the Laurier BSA root, under Home. Then set sidebar order per
   bsa-system.md section 5.
3. MERGE DASHBOARDS: copy the two buttons from "Your Dashboard" into the top of
   "Briefing", move "Your Dashboard" to Archive, change the Home mentions to Briefing.
4. TEMPLATE PREFILL: open each meeting template, fill Expected, save.
   Team Meetings templates: full exec roster. VP Meetings templates: Farhan, Safdar,
   Saima, Joyita, Syed, Jara, Aryan, Niema. Archive any unused leftover template.
5. FILTERS on Team Progress: the blocking view and the everyone's-open-work view get
   Filter > Overdue > is checked. Sixty seconds, and without it the page shows all work
   instead of late work.
6. CLEANUP:
   - Tasks: delete the "Outreach Tracker" relation (its target is in the trash)
   - VP Meetings Format: delete Presentation, Customer call, Retro
   - VP Meetings: merge the duplicate Monthly Stand-up rows, archive the Untitled row
   - Guides, by-team table: link the Finance and Photography handbooks
   - Transactions: delete the tab level Expenditure form view, keep the one on Finance
   - Transactions: delete the $0 henna summary row
   - Initiatives: compare "Assigned to (legacy)" against Owner, then delete it
   - Budget Lines: delete "Funding source (legacy)" once Fund is backfilled
   - Initiatives: set Recap to Always hide, the recaps database is archived
   - Events page: drag "Recaps outstanding" under the gallery, give it a heading
   - Merge the two VP teamspaces if there are still two
7. CUSTOMIZE PAGE (open a row > ••• > Customize page), once per database:
   Initiatives  show: Date, Type, Phase, Status, Owner, Team, Priority
                when empty: Turnout, Show rate, Cost per head, Spent, Budget, Signups,
                Verdict, Recap filed, Semester, Partners, Skills needed
                hide: everything else, the page body already shows the relations
   Tasks        show: Status, Scheduled, Team, Phase, Assignee, Assignee (Directory), Project
                when empty: Due, Priority, Lead, Notes, From team meeting, From VP meeting
                hide: Event date, Is gate, Overdue, Blocking others, Needs an owner, Health
   Directory    show: Role, Team, Years active, Delegation, Email
                when empty: Terms served, Tasks done, Overdue tasks, Blocking other teams,
                Meetings missed, Attendance rate
                hide: the rest
   Transactions show: Amount, Date, Fund, Item, Paid By, Initiative, Budget category,
                Approval, Reimbursement · hide the rest
   Budget Lines show: Initiative, Budget category, Fund, Projected, Actual, Remaining, Health
   Exec Form    show: Status, Applied for, Email, Year and Program, Academic year
                when empty: Review note, Decision date, Became · hide: Responses, Email link
8. PAGE COVERS on past events, from the images Creative supplies. The gallery previews
   the page cover, never the Cover image URL.
```

## C. Code

- [ ] `CODE` **Reminder digest v1.** Repo `bsa-notion-tools`, MIT, public, so other clubs can use it.
  - Runtime: GitHub Actions cron, `0 13 * * 1,4`, one Notion integration token.
  - Reads Tasks where `Status != Done` and `Scheduled` is on or before today plus 3. Groups by `Assignee (Directory)`, falls back to the team's VP for unassigned rows.
  - Per person message: overdue first, then due in 3 days, then anything where `Blocking others` is true, each with its Notion link.
  - Presidents summary in the same run: overdue count by team, open gates, owed to execs (Transactions, personal card, not paid out), Allocated remaining.
  - Delivery: Discord webhook or Gmail SMTP with an app password, per decision 7. Dry run mode prints to the Actions log.
  - Done when: it matches what Briefing shows, two runs in a row, sent to Safdar only for the first week.
- [ ] `CODE` Availability overlap finder, pack spawner, QR check in: January. Not this term.

## D. Term tasks to seed

| Task | Due | P |
|---|---|---|
| Workspace audit and cleanup complete | 29 Sep | High |
| Phone walkthrough recording posted in exec chat | 30 Sep | High |
| Workspace map page updated to v0.5 | 2 Oct | Medium |
| Reminder digest live | 9 Oct | High |
| Digest extended to the whole exec team after a week of testing | 16 Oct | High |
| Check with the team: is anyone on Android, before standardising any phone app | 16 Oct | Low |
| Website sitemap and events archive structure in Figma | 20 Nov | Low |
| QR check in prototype for Boshontoboron | 4 Dec | Low |
| Systems handbook written | 4 Dec | Medium |
