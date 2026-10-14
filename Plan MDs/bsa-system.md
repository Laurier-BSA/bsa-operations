# Laurier BSA Operating System

v0.5, 22 Sep 2026. Single reference. Replaces v0.4, the workspace map and the finish checklist.
The durable copy is the Notion page "Workspace map and roadmap". This file is the copy Claude reads.

---

## 1. The three tests

1. Any question about money, people, events or content is answerable from one place.
2. A new exec finds what they need without asking a president.
3. Next year's team inherits working structure, not a folder of dead links.

## 2. Principles

- **One spine.** Initiatives and Team Directory. Everything relates back to those two.
- **Organised by goal, not by team.** Team pages stay thin.
- **Free plan forever.** Formulas, rollups, views, charts, buttons. No automations, no Notion AI.
- **Thirty seconds on a phone** or it will not happen.
- **Three dashboards. Three views per page. Titles, not sentences.**
- **Archive, never delete.**
- **New: schema freeze until 8 Dec.** Fixes and adoption only, no new databases unless a VP asks for one by name. The system is now ahead of the people using it, so every remaining gain comes from use, not from build. This is also the answer to Farhan's "we are overcomplicating it".

## 3. Rules ratified at the VP meeting, 20 Sep 2026

- Finance approves every purchase **before** it is made. An unapproved purchase may not be reimbursed. (This replaces the threshold idea in v0.2 to v0.4.)
- No form, no deduction. An expense only counts against the $850 once the reimbursement form is in and Finance confirms it.
- Reimbursement filed before the event, or within about 3 days after.
- SU event requests go in **8 weeks** ahead. That date sets every other date.
- Storage Inventory is updated after every event, not when someone remembers.
- Every booth decides its engagement hook in advance. Setup is its own named shift with names on it.
- Each president owns one initiative end to end. For every other initiative, the VP of that team owns momentum.
- Anything not member facing comes out of Generated Budget.
- Cadence: weekly VP standup (15 min, async form), monthly VP planning (60 min, in person, Friday 5 to 7), team meetings at each VP's own cadence.
- Decor spend cut sharply. DIY or none for small events.

## 4. Dashboards: three, and no more

| Page | Question it answers | Why it cannot merge |
|---|---|---|
| **Briefing** | What is on me today | Filters dynamically on the viewer |
| **Club Dashboard** | What is the state of everything | Same for everyone, opened weekly |
| **Team Progress** (VP space) | Who is holding things up | Restricted content must be its own page |

No per team dashboards. A board grouped by Team on Club Dashboard gives every team its slice.

## 5. Sidebar, target shape

```
LAURIER BSA
  daily
├── Home                  what we are running, how this works
├── Briefing              your tasks, your reimbursements, your shifts
├── Club Dashboard        phases, gates, this month
  doing the work
├── Initiatives           the playbook, task packs, every event
├── Money                 budget, log an expense, reimbursements
├── Storage and shifts    inventory, shopping, availability
├── Promote               content calendar, media, assets
├── People and partners   directory, hiring, contacts, sponsors
  reference
├── Meetings
├── Guides                handbooks, SU policy, how to use Notion
├── Forms
└── Archive

PRESIDENTS AND VP
├── Team Progress
├── Run the VP meeting
└── People Record         private: violations, conduct
```

Team handbooks live under Guides. Team pages stop being sidebar items once their content sits on the goal page that matches the job. Verify what has actually been applied before moving anything.

## 6. Databases and IDs, as of 22 Sep

| Database | Data source ID | Role |
|---|---|---|
| Initiatives | `7b98e159-7c4c-466d-98ac-3949ba493719` | Hub. Every event, booth, campaign, project |
| Tasks | `49cca9bc-5dc4-43ea-8d77-4bf6ded244ae` | All work. Scheduling engine lives here |
| Team Directory | `197ac90c-76f1-80e5-b407-000b3e3e841b` | Every exec |
| Budget Lines | `7735c17c-d4c8-421d-bb0e-829469c5286f` | Plan per initiative |
| Transactions | `e197e3c9-1f82-4d7a-9e91-84731da313ca` | Every dollar, 44 rows |
| Budget Categories | `ef519958-ea72-45b8-ad5a-81ebe5ec18bd` | Plan per category per term |
| Availability | `9495ffba-9a2e-451d-b09c-3ce9034febe4` | 68 blocks, 13 execs |
| Role History | `12fba1b6-3fc6-4829-aef8-11b40acd00fc` | Empty. Backfill before term wrap |
| Brainstorm | `177ac90c-76f1-8030-bad1-000bd3a62cbf` | Idea intake, `Became` to Initiatives |
| Executive Team Form | `18dac90c-76f1-8082-917e-000bff2b7bb4` | Applications pipeline |
| Attendee Form | `981a3b91-d7e8-48f3-9635-cc7e3ce634d3` | Signups and check ins |
| Team Meetings | `eca05e7a-8269-4fa4-8b96-7a15bb51d9b0` | Public meetings |
| VP Meetings | `291ac90c-76f1-80d2-98b5-000b535c2e84` | Restricted meetings |
| Semester Onboarding | `87f8a75e-d8cc-4e8c-bc89-be08d3c90e5b` | Start of term form |
| SU Guides and Policies | `28579596-652a-4e0f-912c-adbd532e38d8` | SU rules per team |
| Forms Index | `7dde7f7e-6811-4d69-a696-c2f8f68796ff` | Every form in one list |

Also live and not to be rebuilt: Task Pack Templates, Term Funding, Sponsorships, Storage Inventory, Contacts, Content Directory, Media Directory, VP Standup Updates.

Pages: Club Dashboard `3deac90c76f18133b897eec02777be7b`, Finance `18cac90c-76f1-8057-a83e-f831b0abd549`, Finance Report `3daac90c76f18109bfe3fbc7b1a173bc`, Team Progress `3daac90c-76f1-8148-a05a-cec49ca64030`, Workspace map `3daac90c76f18112968ffa1133170686`, Students' Union `3e0ac90c76f181c8be5ceddb7080ca90`, Forms `3e0ac90c76f181a6b2c0d3cfeeca55d2`.

IDs drift. Verify before writing.

## 7. The initiative pipeline

**Types on Initiatives:** Event, Booth, Campaign, Internal, Project, Outreach, Service. Plus `Skills needed` for skill based projects.

**Five phases.**

| Phase | Leads | In parallel | Gate |
|---|---|---|---|
| 1 Lock | Operations | Events, Finance, Outreach | Date, room and SU request in |
| 2 Build | Creative | Technology, Operations, Finance | Poster approved |
| 3 Promote | Marketing | Creative | Announcement posted |
| 4 Run | Events | Operations, Photography | Event happened |
| 5 Wrap | Finance | Events, Photography, Marketing | Recap filed |

**Packs.** The four packs live as rows in **Task Pack Templates** (under Guides, Initiative Playbook): Event, Booth, Campaign, and Social (added this term). That table is the source of truth and is meant to be edited. To spawn one, ask Claude: *"create the event pack for Nobanno Night, date 27 Nov"*. It reads the table and writes the rows with `Project`, `Team`, `Phase` and `Lead`.

**Buttons are shelved.** Thirty one hand built button actions would duplicate a table that is still changing. Revisit in January, once a full term has run and the packs have stopped moving. If it still matters then, a small script that reads the table beats a button.

**Scheduling.** `Event date` (rollup of Project, Date) feeds `Scheduled` (a typed `Due` wins, otherwise event date minus `Lead`). `Is gate`, `Overdue`, `Blocking others`, `Needs an owner` and `Health` are live formulas. Every view sorts on `Scheduled`.

**Late start rule.** If an initiative is created with less runway than its pack's longest `Lead`, the pack lands already overdue. The owner types a real `Due` on every overdue row within 48 hours of spawning it. Otherwise the scoreboard fills with fake lateness and people stop trusting it.

**Gates.** A gate is only the `GATE:` prefix in a task name. Nothing is load bearing. Decide at the 23 Oct planning meeting, after the booth has run start to finish, whether to keep them.

## 8. The outcome loop

On Initiatives: `Turnout`, `Show rate`, `Cost per head`, `Verdict`, `What worked`, `What to change`, `Recap filed`, `Semester`, plus the rollups `Signups`, `Checked in`, `Spent`, `Budget`, `Completion`.

Filled by the initiative owner within three days. The "Recaps outstanding" view on the Events page should be empty at the end of every week. It is the single number that says whether the loop works.

Past event covers must be set as the **page cover**. Notion galleries cannot preview a URL property. The `Cover image` URL property stays for the website to read.

## 9. Meetings

Both meeting databases carry `Expected`, `Attended`, `Apologies` (relations to Team Directory), `Absent`, `Decisions`, `Still open`, and `Action items` into Tasks. Team Directory derives `Meetings missed`, `Attendance rate`, `VP meetings missed`. Four templates: team planning, team execution, VP standup, VP planning. Nothing is decided in a standup, nothing is reported in a planning meeting. Every action item leaves the meeting with an owner and a date.

## 10. Money

**Two funds.** Allocated Budget (the SU grant, $850 for Fall 2026, resets) and Generated Budget (income, booths, sponsorship, merch margin, carries over). Historical rule: every past expense is Allocated, every income row is Generated.

**Four places.** Budget Categories (plan per category per term, the number spending is measured against), Budget Lines (plan per initiative), Transactions (every dollar), Term Funding (what the SU gave us), Sponsorships (deals and documents).

**The flow.** Ask Finance, get approval, buy, log the expense with a receipt within 3 days, Finance confirms and it is deducted, Rubric submission, paid out.

| Purpose | Fund |
|---|---|
| Event delivery | Allocated first, Generated covers overflow |
| Exec socials, appreciation, merch | Generated only |
| Reusable equipment and decor | Generated preferred, it carries over |
| Emergency buffer, target $200 floor | Generated, never spent without both presidents |
| Sponsorship in kind | Neither, log at $0 against the sponsor in Contacts |

Known inconsistency to fix: the `Fund` options are not spelled the same across Transactions, Budget Lines and Budget Categories. One spelling, everywhere, or the charts lie.

## 11. People

Team Directory is the roster. `Role` holds both role tags and status tags (on co-op, offboarding), so filter on it rather than on Notion user groups. Tasks keep both `Assignee` (person, drives Briefing) and `Assignee (Directory)` (relation, drives the scoreboard).

Role History is one row per person per role per term. Still empty, and it is the only item this term with a hard deadline, because it is the recognition data and the handover data at once.

Executive Team Form is the applications pipeline. Semester Onboarding captures availability, responsibilities and the agreement each term. Contacts holds everyone external and stays separate from Team Directory (decided: a roster and a contact list have nothing in common except having names).

## 12. Private data

Notion permissions are per page. Hiding a column in a view is not privacy.

Currently exposed to every exec: `Violations`, `Violation reasons`, `Student ID` and the attendance formulas on Team Directory, plus the attendance view on Club Dashboard.

Target: a **People Record** database in the VP teamspace holding Person, Violations, Violation reasons, conduct log (Date, Type, What happened, Raised by, Action taken, Resolved) and notes. Three rules so it does not become a grudge list: facts not opinions, the person is told when something is logged about them, positive notes get logged too.

Attendance counts can stay open. Visible to everyone reads as a system; visible only to presidents reads as surveillance. Violations cannot stay open.

Student ID: keep it on Directory, hidden from every view, so the Rubric auto fill keeps working. Moving it to People Record breaks the rollup and buys nothing, since the number is printed on a OneCard anyway.

## 13. Build it ourselves, revised order

1. **Reminder digest. October, not later.** There are no automations on this plan and `Scheduled` already computes every date. A twice weekly message per person, plus a presidents summary, is what makes people open Notion at all. Everything else in this list is a nicety next to it.
2. **Availability overlap finder.** January.
3. **Pack spawner.** January, and only if asking Claude turns out to be a bottleneck for people who are not presidents.
4. **QR check in.** Before Boshontoboron, so `Turnout` and `Show rate` stop being estimates.
5. **Public site.** Figma structure this term, build over the winter break. The outcome fields are already the fields the events archive needs.

## 14. Open decisions

| # | Decision | Recommendation | By |
|---|---|---|---|
| 1 | Keep gates, or drop the `GATE:` prefix | Keep for one full event, then decide on evidence | 23 Oct planning |
| 2 | Teams database | Build it additively: a relation beside the existing multi select, backfilled, no view rewrites this term | 23 Oct |
| 3 | People Record and attendance visibility | Build People Record, move Violations, leave attendance open | 2 Oct |
| 4 | Student ID | Keep, hidden | 2 Oct |
| 5 | Does Farhan want a read only Sheet mirror of the finance numbers | Ask him plainly. A weekly export he actually reads beats a dashboard he does not | 25 Sep |
| 6 | Flagship concept and whether it is ticketed | See term-plan section 3 | 25 Sep |
| 7 | Where the reminder digest sends: exec Discord, email, or WhatsApp | Whichever channel the exec team already reads | 29 Sep |
| 8 | Still unanswered from v0.2: is there a BSA card, what is Rubric's payout turnaround, is the Winter forecast deadline fixed | Ask the new SU contact in one message | 30 Sep |

## 15. What changed since v0.4

- The VP meeting happened. Its rules are section 3 and replace the threshold approval design.
- `Scheduled` and the rest of the scheduling engine are built and work through the API.
- Task Pack Templates replaced the hard coded packs. Buttons shelved.
- Briefing replaced Your Dashboard. Three dashboards, final.
- Budget Categories, Term Funding and Sponsorships exist. Fall allocation is $850.
- Chart views can be created through the API, so the "not built on purpose" list in the old checklist is wrong.
- `Waiting on` stays unbuilt, deliberately. Phases and gates carry sequencing.
- Proposals stay inside Brainstorm. No Proposals database, ever.
