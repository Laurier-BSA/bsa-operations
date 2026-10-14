# Finance

Budget Lines and Transactions are the system of record. Do not create another money database, this has already happened once.

## A. Workspace work

- [ ] `API` **F1 Fund backfill.** Every Transaction and Budget Line without a `Fund`: expenses become Allocated, income becomes Generated. That is the rule agreed on 19 Sep, so no human judgement is needed. Report how many rows were written and how many already had a value. Do T2 in `01-technology.md` first so there is only one spelling.
- [ ] `YOU` + `API` **F2 Budget Categories.** After the finance meeting, read out the agreed percentage split of the $850. Claude fills `Planned %` and `Planned $` on the Fall 2026 rows. Until this is done the Tracking column says "no plan set yet" and the charts cannot mean anything.
- [ ] `API` **F3 Fall 2026 Budget Lines**, one per initiative from the agreed envelope, each with `Fund`, `Budget category` and `Initiative` set.
- [ ] `API` **F4 Finance number cards** (chart views can be created through the API, contrary to the old checklist): Allocated spent of $850, Allocated left, Generated balance, Owed to execs. Verify what already exists before adding. Three on the Finance page, three on Club Dashboard, no more.
- [ ] `API` **F5 Approval inbox** view if it is not already on the Finance page: Transactions where Approval is requested, oldest first. This is the queue the new rule creates.
- [ ] `API` **F6** Check the Sponsorships row for Sultana'r Kitchen ($200, Winter 2026, contact Shabiha Yousuf) has the deliverables recorded: 3 tickets, logo on posters, social shout out, mention at the event. Outreach needs that as the anchor for the packages page.

## B. Term tasks to seed

| Task | Due | P |
|---|---|---|
| Post the money rules in exec chat and in the Finance handbook: approval before purchase, receipts within 3 days, no form no deduction | 29 Sep | High |
| Ask the SU: can the grant fund a resale float, is there a BSA card, Rubric payout turnaround, Winter forecast deadline | 30 Sep | High |
| Resolve Mayisha Momin's $100 claim, no Directory row exists | 2 Oct | Medium |
| Booth: pricing, float and the BSA share agreed before the table is booked | 8 Oct | High |
| Friday finance check, 15 minutes: approval inbox cleared, reimbursement queue to zero | recurring Fri | High |
| Booth income logged as Inflow against the initiative | 24 Oct | High |
| Rubric claims filed within 7 days of each event | 29 Oct, 6 Nov, 4 Dec | High |
| Flagship purchase list approved and ordered | 6 Nov | High |
| Sponsorship ask amounts priced with Outreach | 6 Nov | Medium |
| End of term finance summary: spent vs plan by category, for the wrap meeting | 2 Dec | High |
| Winter 2027 forecast prepared for the SU | 4 Dec | Medium |

## C. Standing rules

The $850 is not reduced by a purchase, it is reduced by a submitted and confirmed reimbursement form. An unapproved purchase may not be reimbursed, and that has to be said once in public before it is ever enforced in private. Anything not member facing comes out of Generated.
