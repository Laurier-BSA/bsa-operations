# BSA changelog

## 2026-09-25 · Direction: light on facilities (no tracker id; asked in chat)
What changed:
- SU Guides & Policies: added "BSA: 2026-27 direction: light on facilities" (https://app.notion.com/p/3e6ac90c76f18129ad3cd3d0cd53f3dd) and "BSA: Awareness posts on world news" (https://app.notion.com/p/3e6ac90c76f18186b1abc8c974476abc).
- Effort Factors: 6 new factors: Virtual host setup, Speaker details on the SU form, Off-campus waivers, Park or field booking, Sports gear and first aid, Awareness post: research and fact check.
- Brainstorm: 6 ideas, Status Submitted, factors ticked: Virtual speaker meet, Monthly virtual workshop, Picnic in the park, BSA pickup soccer, World news awareness series, Campus advocacy week.
- Kit installed: .claude/agents, .claude/commands, .mcp.json, plans/README-kit.md; tracker copied to plans/TRACKER.md.
Check by hand:
- The awareness-post rule is Claude's proposal. Confirm or edit it.
- Lead days on "Park or field booking" (28) is an estimate. Check the city's park permit time.
- Ask the AVP once whether advocacy posts need anything beyond the poster rules.
- Add this direction as an item on the build board so the next TRACKER.md export carries it.

## 2026-09-25 · #i33 Winter roadmap page per team → [b]
What changed:
- Draft for all nine teams in plans/drafts/i33.md. Each team has a Winter outcome, 3 to 5 milestones by month, a rhythm and one measure. It follows the light-on-facilities direction.
- Audited twice. Audit 1 had 18 fixes and Audit 2 had 7; both sets are applied. The delegator checked the Audit 2 fixes line by line.
- Not yet in Notion. Once you approve the text, it goes onto the team pages through a builder spec.
Check by hand (full list under "Audit 2" in the draft):
- Exec social money: Generated only (BSA rule) or $15 per person / $150 a year from Budgeted (SU). Then make #i05 and #i30 match.
- Ramadan (about 8 Feb to 9 Mar): soccer after Eid. Check the April picnic against exam dates.
- January speaker meets: one guest each, or file the form 8 weeks ahead (mid-November).
- Boshontoboron: MOU with every co-host before SU approval.

## 2026-09-25 · #i26 Alumni Features desk → [b]
What changed:
- Content Directory: 14 desk properties, covering Series, Desk stage, Pitch, Writer, Checked by, Featured person, Source 1 and 2, Consent, Money ask, Stamped, Invite to speak, Desk notes and the Desk check formula. New views: Desk pipeline, Check queue, Pitch a piece (form). The Marketing tabs By Content and By Initiative keep their old columns.
- The pipeline carries three series: Features (South Asian voices in Canada), World news, and Advocacy week.
- Contacts: Type options Speaker and Featured added; new Represents field; new "Speakers and featured" view.
- Team Directory: Delegation option "3.5 Features desk" added. Nobody has it yet.
- New page: Features Desk Handbook (https://app.notion.com/p/3e6ac90c76f181059574c514f86e00ac). Alumni Handbook got one bullet linking to it.
- SU Guides: new row "Speakers must be named on the event form". The "Marketing posts without a second approval" row now notes the desk exception.
- Audited: first pass FAIL on 4 points. All four were fixed. The delegator checked the Alumni Handbook page is intact and added the no-GoFundMe line to the handbook.
- Full spec, Built, Audit and Fixes: plans/specs/i26.md.
Check by hand:
- Make one test row (Series = Features, nothing else) and confirm Desk check lists what's missing. Then rename it "[OLD] desk test" and archive it. The API can't show formula output.
- Name the alumna. Set her Delegation to "3.5 Features desk" and give her edit access to Content Directory; permissions are yours to change.
- Confirm the second-exec check overrides "Marketing posts without a second approval" for desk pieces.
- Confirm or edit the "BSA: Awareness posts on world news" row, and decide on donation links after you ask the AVP.
- Cowork (UI-only): create the Desk piece template, lay out the form questions, add property descriptions.

## 2026-09-26 · Initiatives cleanup, pass 1 (no tracker item; Safdar asked in session)
What changed:
- Semester filled on 15 past rows, taken from Date (Fall = Sep to Dec, Winter = Jan to Apr). Exec Hiring (24 Aug 2024) was set to Fall 2024. Movie / Paint Event and Mock Wedding have no Date, so they were left blank.
- View "All": sorted by Date, newest first. Semester column added.
- View "Active": now shows In progress and For Review, sorted by Date, soonest first.
Check by hand:
- All and Active still show three empty filter chips (Status, Assigned to (legacy), Date) from an old template. The API can't remove them. Click each chip and choose Delete filter.

## 2026-09-26 · Finance page: Reimbursements section (no tracker item; Safdar asked in session)
What changed:
- Finance page (https://app.notion.com/p/18cac90c76f18057a83ef831b0abd549): new "Reimbursements" section at the top, under the money rules.
  - New number card "Owed to execs": sum of Amount on Expense rows where Reimbursement is Not submitted or Submitted to SU.
  - "Awaiting forms" card moved next to it. Funding row now shows Allocated spent and Generated balance only.
  - New table "Approval inbox": Approval = Requested, oldest first (F5 in 04-finance.md).
  - "Submit to SU" and "Owed" moved into this section as steps 2 and 3.
- View "Owed to execs": filter changed from personal-card only to any Expense with Reimbursement Not submitted or Submitted to SU, so cash claims show too. Semester, Method and Rubric Ref columns added.
- No properties or databases added.
Check by hand:
- The owed card shows about $483.71. $458.62 of that is 9 Winter 2025 claims still marked Submitted to SU, with no receipt and no Rubric ref. Confirm with Farhan whether they were paid, then set them to Paid out.
- Get Involved Fair snacks ($25.09, 11 Sep): Approval still Requested and the form is not in. Approve it and file it.
- Transactions: the Winter 2025 claims have no Fund set (F1 backfill still open).

## 2026-09-26 · Finance page, pass 2 (no tracker item; Safdar asked in session)
What changed:
- Transactions: 9 Winter 2025 claims set to Reimbursement = Paid out (Safdar: everything before this year counts as paid).
- Every pending view now also filters Date on or after 2026-05-01: Owed to execs (card and table), Ready to submit to Rubric, Approval inbox.
- "Awaiting forms" card turned into "Owed, by person": bar chart of unpaid claims, grouped by Paid By.
- "Ready to submit to Rubric": Paid By column added.
- Approval inbox: now also catches rows with a blank Approval, so expense-form submissions land in it. The inbox shows Type, Fund, Semester and Reimbursement so Finance can fill them in place.
- Budget Lines block ("Budget lines: projected vs actual"): tabs This year (Fall 2026 + Winter 2027), This term (Fall 2026), Last term (Winter 2026), All time (grouped by Semester). Replaces the "Budget by event" tab.
Check by hand:
- API can't filter on formulas. In the UI, change each term filter to "This year is checked" (Transactions and Budget Lines both have it) so nothing needs editing each term. Until then: update the Semester filters in January, and the 2026-05-01 date guard next May.
- There are no Fall 2026 Budget Lines yet (F3), so This year and This term are empty.
- Expense form questions are UI-only: set them up in the Transactions "Expenditure form" view.

## 2026-09-26 · Finance page, pass 3 (no tracker item; Safdar asked in session)
What changed:
- Transactions: new row "Exec merch: T-shirts and crewnecks (waiting on quote)". Type Expense, Fund Generated Budget, Approval Requested, Semester Fall 2026, Budget category Exec merch, Handled by Syed. Amount blank until the quote comes in.
- Finance page, Reimbursements: new step "1. To buy and quotes" (Type Expense, Reimbursement empty, Approval not Rejected, Semester Fall 2026 or Winter 2027, grouped by Approval). Old steps renumbered 2 to 4. The inbox view is renamed "New receipts to check".
- Safdar was editing the page at the same time. Only the Reimbursements section and the stray view block at the bottom were touched.
Check by hand:
- The query quota ran out this session, so the new view's row count was not verified through the API. Confirm the merch row shows under Requested.

## 2026-09-26 · Finance page, pass 4 (no tracker item; Safdar asked in session)
What changed:
- Owed number card renamed "Expenditures pending". It now counts claims instead of summing dollars. Caption: "Expenditures pending · 0 = all clear". Notion charts can't show conditional text, so the caption carries the meaning.
- Budget Lines: new formula property "Term". It returns "This term", "Last term" or "Older" from Semester and today's date. Fall = Aug to Dec; Winter covers Jan to Jul, so summer counts as the Winter term.
  lets(m, toNumber(formatDate(now(), "M")), y, toNumber(formatDate(now(), "YYYY")), cur, if(m >= 8, "Fall " + format(y), "Winter " + format(y)), prev, if(m >= 8, "Winter " + format(y), "Fall " + format(y - 1)), s, format(prop("Semester")), if(s == cur, "This term", if(s == prev, "Last term", "Older")))
Check by hand:
- Open any Budget Lines row. Winter 2026 must read "Last term" and Fall 2026 "This term". The API can't show formula output.
- Swap the fixed Semester and date filters for formula filters (list in chat, 26 Sep).
- Archived Expenditure Forms: check for submissions after 1 Sep that aren't in Transactions yet. The query quota was used up.

## 2026-09-26 · Finance headline card (no tracker item; Safdar asked in session)
What changed:
- Card "Expenditures pending" is now "Not submitted to SU": counts Expense rows with Reimbursement = Not submitted, dated on or after 1 May 2026. Caption: "Claims not yet submitted to the SU · 0 = all clear". This filter was reset by the API, so re-apply the "This year is checked" swap on this card.
Check by hand:
- Proposed money goals for socials (reusing the #i30 unlock rows). Waiting on Safdar's go-ahead; nothing built.

## 2026-09-26 · Finance build: shopping catalog, points and money goals, Finance bands (asked in session; extends #i30)
What changed (full detail: plans/specs/finance-2026-09-26.md):
- Effort Factors: `Shopping` group + `Est. cost` + `Spend type`; 12 common purchases with typical costs. Headcount sits in the name, e.g. "(per 50 people)".
- Cost chain: Brainstorm `Est. cost` → Initiatives `Idea est. cost` → Budget Lines `Estimate`. Ticked shopping items on the booth, flagship and social candidates (Chai $80, Henna $65, Pitha Night $470, Victory Day $565, Adda Night $55).
- "Credit" renamed "Points" everywhere (Tasks, Initiatives, Brainstorm, Team Directory, Club Dashboard view).
- Money goals: Initiatives `Money goal`, `Goal funds` ↔ Transactions `Toward goal`, `Raised`; `Unlock` shows ⭐ points and 💰 money bars. Team dinner gets a $150 placeholder goal.
- Club Dashboard: `🏆 Team goals` section and callout; `Goals in progress` + new `Reached` tab; `Points this term`; `Not submitted to SU` card in the finance section.
- Finance page: `Do: reimbursements` (monthly check), `Plan: edit here` (3-step how-to), `History` toggle. Your top `Expenditures` layout was kept.
- Tasks: 7 finance tasks for Syed and Jara (monthly checks, $850 split by 2 Oct, Rubric claims after each event).
Check by hand:
- Open one idea (Chai and snacks booth) and read Est. cost; open Unlock 4 and read the 💰 bar. The API can't show formula output.
- Budget Lines `Actual` now sums `Deducted`, not `Amount` (changed outside this session). Keep it or switch it back.
- The $150 dinner goal is a placeholder until the team votes.
- Syed has two Notion accounts; tasks use azad7392@mylaurier.ca.
- UI-only: property descriptions on the new fields; gallery card size on the goal views.

## 2026-09-26 · Finance build: audit fixes
Auditor verdict FAIL (4 must-fix). All four are fixed, plus most of the should-fix list; detail is in plans/specs/finance-2026-09-26.md under "Audit".
- Chai row now means Food Services or Wilf's, not brewing our own. Re-price it from a Food Services quote. The Pizza row now means Food Services or Wilf's unless exempted. The Snacks row says individually pre-packaged only. Decor and Ride carry the $30 To-buy line.
- Initiatives `Spent` now rolls up `Deducted`, so quotes and inflows no longer count as spent. `Raised` now rolls up the new Transactions formula `Goal amount` (Generated inflows only). `Unlock` has zero and empty guards.
- New receipts excludes Inflow and Allocation rows. The two Owed views show only Personal card and Cash rows. Goals in progress hides Archived rows and sorts by Date.
- The Finance page states the 48-hour Rubric and 3-day receipt rules. The copy now asks for Semester and Date, and says to type Planned $ and Planned %.
- The Club Dashboard callout adds that money in goes through the SU and that some goals need both points and money.
- Claim tasks are now due 2 days after each event (24 Oct, 1 Nov, 29 Nov), with notes on the 48-hour rule and SU Desk.
Safdar decides:
- Exec socials: Generated only (callout) or the Team Social 15% bucket of the grant. Pick one; then #i05, the callout and Budget Lines Bucket should match.
Check by hand:
- Set the Shopping option colour to green. Add property descriptions (Est. cost, Spend type, Money goal, Goal funds, Toward goal, Goal amount).
- Test row: a To buy row with $10, an Initiative and Fund Allocated. Deducted and Spent should stay 0. Then rename it `[OLD] test` and archive it.
- Make Date required on the expense form, or a claim can fall out of every Do view.

## 2026-09-26 · Exec social money rule + Chrome checks
What changed:
- Rule (Safdar): exec socials may use the Allocated Budget up to $15/member and $150/yr (Team Social bucket); the rest comes from Generated. Updated: the SU Guides row (renamed "BSA: Exec social money"), the Club Dashboard Team goals callout, all four Unlock page bodies, and the Budget Categories "Exec socials and appreciation" note.
- New views: Brainstorm "Compare costs" (candidate ideas grouped by slot, with Est. cost, lead days, slot fit and votes) and Effort Factors "Shopping list".
Checked in Chrome:
- Est. cost correct on all five candidates: Chai $80, Henna $65, Victory Day $565, Pitha Night $470, Adda $55. The first load showed $40 on the flagships; the correct values appeared after a reload.
- Goals in progress cards render ⭐ bars (0 points so far). The team dinner shows ⭐ and 💰.
Flag for Safdar (not changed; sharing is his call):
- The Club Dashboard is published to the web ("This page is live on laurierbsa.notion.site"). It includes the finance cards and the "VP only" section.
Still UI-only:
- Shopping colour; property descriptions; Date required on the expense form; "This year" filter swaps; widen the gallery cards so the dinner's two bars fit.

## 2026-09-26 · Slot types: fixed initiative types each semester (asked in session)
What changed:
- New `Slot type` select, with the same options on Initiatives and Brainstorm: Large event, Member social, Fundraiser / booth, Club fair, Collaboration, Impact outreach, Team social, Tradition. Minimums come from the team handbooks: Finance ≥2 fundraisers; Outreach ≥2 collaborations and ≥1 impact outreach; Events (term plan) 1 large event + 1 member social.
- Backfilled 25 Initiatives. Not tagged: খেলা হবে (Nov 2025), Exec Hiring, Mock Wedding (archived). Ummah Bazaar was tagged Fundraiser / booth; check that.
- New Initiatives row "Food Justice Garden volunteer day" (2 Jun 2026, Impact outreach, Done), with its 4 garden-form signups linked. Semester left blank because there is no Summer option.
- Brainstorm: the five current candidates are tagged. The six ideas from the direction note (virtual workshop, world news, picnic, advocacy week, speaker meet, soccer) are untagged.
- New views: Initiatives "Semester plan" (board by Slot type, Fall 2026) and Brainstorm "Ideas by slot type" (board).
Check by hand:
- Fall 2026 is short of the handbook minimums: 1 more Fundraiser / booth, 2 Collaboration, 1 Impact outreach. There are no slots yet.
- Marketing Handbook has the Instagram, Outlook and Linktree passwords in plain text, like the Outreach Handbook. Remove them and rotate the passwords.

## 2026-09-29 · Photo storage: Farhan's PC, then Oracle (asked in session)
What changed:
- `photo-storage/README.md` now says this Mac is not the host. Farhan's PC is a temporary shelf. Oracle Cloud Always Free is the host that does not sit on a laptop.
- Windows setup goes through https://immich.app/docker-compose-builder: pin `v3.2.4`, timezone Toronto, CPU only, and **Use a named volume** on, because Postgres cannot live on NTFS. The compose file already in `photo-storage/` stays the Mac/Linux one.
- Admin account is the club mailbox `laurier.bsa@outlook.com`.
Check by hand:
- Farhan's free disk and RAM (16 GB preferred, 8 GB ok) before Docker goes on his PC.
- Stopping Immich does not free the photos. His disk stays full until the library is copied to Oracle and then deleted.
- Oracle still runs Docker. It runs on their VM. Signup needs a card and often waits on free ARM capacity in Toronto.

## 2026-09-29 · Photo storage Phase 1 files (asked in session)
What changed:
- New folder `photo-storage/`: official Immich v3.2.4 `docker-compose.yml`, `.env.example` (library on `/Volumes/BSA-Photos/immich`, Postgres in `./postgres`, timezone Toronto, version pinned), and scripts to write `.env`, check the host, and import Drive folders or a Google Photos takeout with immich-go.
- Immich was not started. `scripts/check-host.sh` stops on three facts: no Docker, about 9 GB free on the internal disk, no external drive.
- No password was generated. `scripts/init-env.sh` does that once, on the host machine. It does not go in Notion.
Check by hand:
- Pick the host: this Mac after freeing about 20 GB, or a spare machine that can stay on. Plug in a drive named BSA-Photos.
- Run `photo-storage/scripts/init-env.sh` and put the database password in the club password manager.
- Library size is still unmeasured (§2 of the plan). That decides whether this drive is big enough.

## 2026-09-29 · Photo storage plan (asked in session)
What changed:
- New plan `plans/specs/photo-storage-2026-09-29.md`. Recommends Immich, run locally first, then moved to Oracle Cloud Always Free, with Tailscale for uploads, a nightly Backblaze B2 backup, and Cloudflare Tunnel on photos.laurierbsa.org once the domain is back. Ente is the no-server fallback. Also covers the Google Drive/phone import steps, the consent rule and handover.
- No Notion changes. The plan reuses the existing Media Directory (Name, URL, Initiative) for album links.
Check by hand:
- Library size (§2) decides which option to use.
- SU rule: subscriptions (domain, B2, Ente) need Clubs & Associations approval and the SU card. The B2 and domain spend is an exception to the "free forever" house rule.
- Prices marked "(check)" weren't confirmed: Hetzner/PikaPods, Google One, domain prices, Bitwarden 2-person org.
- No tracker item exists yet. The suggested items are in §11.

## 2026-09-30 · Tasks views tidy + Growth hub rework plan (asked in session)
What changed:
- Tasks DB views: `By Assigned To` (it was really open tasks grouped by team, a duplicate) is now **My tasks** (Assignee = me, open only, sorted by Scheduled, shows Health). `All tasks` renamed **Open by team**, now sorted by Scheduled with Health shown. `By assignee` now shows open tasks only, sorted by Scheduled. New view **Needs an owner**: open tasks with no Assignee, grouped by initiative. Board and Chart are unchanged.
- New plan `plans/specs/i25-simplify.md`: Growth hub becomes a plain "Training & resources" directory. Completion tracking goes to [OLD] + Archive. Not built.
Check by hand:
- 23 of 37 open tasks have no owner: the booth (22 Oct) and member social (30 Oct) packs, plus the Saima $25.09 reimbursement. Assign them from the Needs an owner view. Their dates come from Scheduled (event date minus Lead), so the booth GATE tasks are already late.
- My tasks: the old view had empty quick-filter chips (Due, Project) left over; they don't filter anything.

## 2026-10-04 · Saima claim submitted + Rubric copy fields + Student ID (asked in session)
What changed:
- Saima's $25.09 Get Involved Fair snacks row: Approval = Approved, Reimbursement = Submitted to SU. Task "Review + reimburse Saima" set to Done.
- Transactions: new text property **Student ID** (the payer's Laurier number). The old `Claimant ID` rollup stays, but it was empty for Saima because her Directory Student ID is blank.
- Transactions page layout: every row now shows the Rubric fields under the title, in form order: Paid By, Student ID, Claimant email, Transaction type, Fund, Amount, Vendor, Date, Rubric category, Initiative, Receipt. Each one can be copied on its own. This replaces copying out of the one-line `Rubric form` formula, which is still there, unchanged.
- Reimbursements page: the "Ready to submit to Rubric" table now uses the same column order and includes Student ID and Claimant ID, with Item frozen. The "Form cards" gallery shows the separate fields instead of the `Rubric form` formula. The "How it works" Submit to SU step now names the fields and club number 1074.
Check by hand:
- Expenditure form (Transactions → "Expenditure form" view): the API can't add form questions. Add **Student ID** as a required question after "Full name of person who paid". It takes about 30 seconds in the form editor.
- A real database *template* can only be made in the UI, so the page layout does that job. Every expense page opens with the fields already set out.
- Paste Saima's Rubric reference into `Rubric Ref`, and add her Student ID to the row (and to her Directory entry if you want the rollup to fill in).
- Pinned fields also show on Inflow/Allocation rows (empty there). Say if you want them moved to a section instead.

## 2026-10-14 · Gallery: share buttons, error page, slideshow, Lychee vs Immich note (asked in session)
What changed:
- Lychee (https://laurierbsa.duckdns.org): white "Share" copy-link button on album headers and in the photo viewer, plus a faded link chip on each thumbnail (`photo-storage/oracle/branding/custom.js`, `user.css`).
- Dead or private links now show a branded error card with "Back to album" (if the album still exists) and "Home" (`branding/error.blade.php`, mounted in the server's `docker-compose.yml`; backup at `docker-compose.yml.bak-errorpage`). `apply-login-look.sh` now uploads it.
- Slideshow speed set to 3 s per photo (Settings → Gallery).
- New note `plans/specs/gallery-lychee-vs-immich-2026-10-14.md`: stay on Lychee; Immich needs 6 GB+ RAM and the VM has under 1 GB.
Check by hand:
- **No backup exists.** All photos live only on the Oracle VM. See the note's risk table.
- Lychee image is `:latest`; pin it before the next restart.
- Lychee restarted once (about 30 s down) to add the error-page mount.

## 2026-10-14 · GitHub: ops folder repo, gallery pushed, pipeline doc (asked in session)
What changed:
- New private repo https://github.com/Laurier-BSA/bsa-operations for this whole folder (plans, Plan MDs, SU Policies, CLAUDE.md, helper agents). `photo-storage/`, `.DS_Store`, `.cursor/` and `.claude/settings.local.json` are ignored. Added `README.md`.
- https://github.com/Laurier-BSA/photo-storage pushed: Share buttons, error page, Albums menu link (logged-in users), sidebar logo alignment, `PIPELINE.md`, `LYCHEE-PERMISSIONS.md`, and copies of the server's compose and Caddy files in `oracle/server/`.
- CLAUDE.md: new GitHub section. Commit and push after each finished item.
Check by hand:
- Open the sidebar logged in, on phone and laptop: Albums link at the top, logo lined up with the icons.
- On GitHub, click Watch → All Activity on both repos if you want emails.
- Plans mention a few member emails (e.g. Syed's mylaurier). Fine in a private repo; keep the repos private.

## 2026-10-30 · Public website, Phase 1 (no tracker id; asked in session)
What changed:
- New site in `bsa-website/` (its own repo, ignored here like `photo-storage/`): Next.js static export for Cloudflare Pages. Home, Events, About, Join, Contact, 404, per-event calendar files, share card. Headline: "A little Bangladesh at Laurier."
- Content from Notion (Initiatives rows with Status Done, Team Directory current execs), the Rubric club page and the club Linktree. Paint & Chai (18 Nov) is the only upcoming event; the flagship and Boshontoboron 2027 are in the data but hidden (`publish: false`).
- Exec cards show roles only. No names until each person agrees (`consentGiven`).
- The Gemini brief had wrong facts, now corrected: email is laurier.bsa@outlook.com (not Gmail), Rubric link is campus.hellorubric.com/?s=13650 (not rubric.ca), and its venues and event details were made up.
- Research, decisions and the full self-audit: plans/specs/website-2026-10-30.md. Lint, types, build and axe (0 violations) pass.
- No Notion changes.
Check by hand:
- Create the empty private repo Laurier-BSA/bsa-website on GitHub (the Claude app got a 403 creating it), then push `bsa-website/`.
- Connect it in Cloudflare Pages (bsa-website/README.md, "Deploy").
- Ask each exec about their name on the site; flip `consentGiven` in `src/data/team.ts`.
- Check the Bangla (বসন্ত বরণ, খেলা হবে) and the line "Open to every Laurier student".
- Notion: Paint & Chai has no Date; Rubric says 18 Nov, 6 PM.
- Ask the AVP if the poster logo rule covers a website.

## 2026-10-30 · Website pushed + Lychee photos (asked in session)
What changed:
- Site is on GitHub: https://github.com/Laurier-BSA/bsa-website (`main`).
- Photos from the Lychee gallery (laurierbsa.duckdns.org) on Home (one per "What we do" row), About (Soco Hoco group) and Events (Soco Hoco, Food Justice Garden). Resized to WebP, location metadata stripped, copied into the repo so the site doesn't depend on the Oracle VM.
- Social Mixer (23 Sep 2025) added to past events, from the welcome slide in the Lychee photos. It isn't in Notion Initiatives.
- Exec titles now match the Meet the Team · Fall 2026 posters (Co-President, VP, Director; Media team).
- Not deployed until people say yes: the 14 Meet the Team posters and the exec dinner group photo (15 Oct), kept in the repo's `assets/`.
Check by hand:
- Connect the repo in Cloudflare Pages (bsa-website/README.md, "Deploy").
- Are the Meet the Team posters already public on Instagram? If yes, ask each exec about the website too, then switch them on per person.
- The flower-wall photo has no date or album. Which event was it? It sits under "Culture & heritage" with no event name.
- Add Social Mixer (23 Sep 2025) to Notion Initiatives so the records match.
- laurierbsa.org: renew at IONOS before about 23 Nov (plans/specs/website-2026-10-30.md §9).

## 2026-10-30 · Paint & Chai date on the website (asked in session)
What changed:
- Website: Paint & Chai is now Sat 14 Nov 2026 (Safdar confirmed). Shown with no start time until the room is booked; the calendar file is all-day.
- Notion was not changed (the write was declined): the Initiatives row still has no Date.
Check by hand:
- SU 21-day rule: a gathering on 14 Nov needed its Rubric event form in by Fri 24 Oct (the Notion page lists that due date). Confirm it went in.
- Rubric still lists Paint & Chai on Wed 18 Nov, 6 PM. Change it there, then send me the start time.
- Set the Date on the Notion Initiatives row.
