# BSA photo storage plan

Written 29 Sep 2026 (asked in session). Scope: one place for every BSA photo and video, easy for execs to reach, cheap or free, ready to sit on `photos.laurierbsa.org` (or `.ca`) once the domain is back. The marketing site is a later project; this plan only makes sure photos can feed it.

## 1. What the setup has to do

| Need | Why |
|---|---|
| One library for Drive, phones and laptops | Photos are scattered across Google Drive, personal phones and personal computers today |
| Phone upload in one tap, or automatic for a chosen album | The Photography target is "20 selects and 3 vertical clips in Drive within 48 hours" (term plan). Uploading has to be easy |
| Albums per event, plus a "Selects" album per event | Marketing builds each photo dump and Reel from the selects |
| Share links for attendees, with no account needed | Photo dumps and "tag yourself" posts |
| Accounts owned by the club, not by one person | Execs change every year. A library tied to someone's personal Google or Laurier account leaves with them |
| A backup copy somewhere else | One server or one account is one point of failure |
| Handles video well | Vertical clips are the part that's been missing, and they're the heaviest files |
| Can move to a custom domain later | `photos.laurierbsa.org` and the website pulling selects |

## 2. Step zero: measure the library (do this first, ~30 min)

Every choice below depends on how many GB you have. Before picking anything:

1. **Google Drive:** open the BSA Drive folder(s) → right-click → *Folder information* (or check drive.google.com/settings/storage on the club account). Note GB, and roughly how much of it is video.
2. **Phones and laptops:** send one message to the execs: "Roughly how many BSA photos/videos do you have, and how many GB?" Old execs too, if you can reach them.
3. Add it up and add 50% for duplicates and this year's events (vertical video grows fast: 1 minute of 4K phone video is about 300–400 MB).

| Total | Sizing band |
|---|---|
| Under 100 GB | Small. Every option works |
| 100–150 GB | Medium. Still fits the free Oracle server |
| Over 150 GB | Large. Needs paid storage or a local drive, or you trim video to selects only |

## 3. Options compared

Prices checked 29 Sep 2026 unless marked *(check)*.

| Option | Cost | Ease for execs | Upkeep | Custom domain | Fit |
|---|---|---|---|---|---|
| **A. Immich, self-hosted on Oracle Cloud Always Free** | $0. VM plus 200 GB block storage free for life | Best: Google-Photos-style app, auto-upload, face search, shared albums, public links | Medium: someone updates it every month or two | Yes | **Recommended** (small or medium library) |
| **B. Immich on a local machine** (a Mac or an old laptop plus an external drive) | $0 (a drive if needed, about CA$80–120 for 1–2 TB) | Same app. Only reachable while the machine is on | Medium; tied to one person's hardware | Yes, via tunnel | **Phase 1 stepping stone**, or fallback |
| C. Immich on a paid VPS (Hetzner, or a managed host like PikaPods) | Roughly CA$5–15/month *(check)* | Same app | Low–medium | Yes | If the library is large or Oracle is unreliable |
| D. **Ente** (hosted, open source, encrypted) | 10 GB free; 200 GB US$59.88/yr; 1 TB US$119.88/yr. Family plan shares storage with up to 5 accounts | Very good: apps, shared albums, public links where guests can add photos without an account | None | No custom domain for the gallery; website images need a separate host | **Best no-server option** if no one wants to run Immich |
| E. Google Drive / Google Photos (status quo) | 15 GB free per account; Google One 2 TB is about CA$14/month *(check)* | Everyone knows it | None | No | Keep Drive as a cold backup for selects only |
| F. Laurier OneDrive | Free, 100 GB per student | Fine | None | No | **Not as the main home**: it belongs to a student account that closes at graduation. The SU's OneDrive rule covers SU executives, not clubs |
| G. Raw object storage (Cloudflare R2, Backblaze B2) | R2: 10 GB free, then US$0.015/GB, free egress. B2: 10 GB free, then US$6.95/TB | Not a photo app | Low | Yes | **Backup target** (B2) and **website image host** (R2), not the library |
| Others looked at: PhotoPrism, Nextcloud Memories, LibrePhotos, Lychee | Free, self-hosted | Weaker mobile upload than Immich, or heavier to run | — | — | Not worth it over Immich |

Immich is now stable. It reached v2.0 in Oct 2025, v3.0 in Jun 2026, and v3.1 in Jul 2026. The "don't use it for anything important" warning from its early days no longer applies.

### Why Immich on Oracle Free, with a local start

- $0 a month, and it matches the house rule "tooling must be free forever".
- The same Docker setup runs on a laptop today and on the Oracle server later. Moving it means copying one folder and one database dump, not re-uploading.
- Immich's mobile app can back up **one chosen phone album** (e.g. "BSA"), not the whole camera roll. That's the privacy line for execs using personal phones.
- Immich public links can allow uploads, so attendees can add their own photos without an account.

### Known risks and what we do about each

| Risk | Mitigation |
|---|---|
| Oracle reclaims Always Free VMs that sit idle, and has cut the free ARM size in some regions (4 CPU/24 GB → 2 CPU/12 GB) | Immich's background jobs keep it busy enough. Even 2 CPU/12 GB is above Immich's minimum (2 cores, 6 GB). Nightly off-site backup (Phase 4) means losing the VM costs only a rebuild |
| Oracle signup needs a credit card for identity checks | Use the SU credit card if the SU allows it (ask; see §8), not a personal card that leaves with an exec |
| 200 GB storage cap (about 150 GB left after the OS disk) | If the library is over ~150 GB: move to option C, or keep original videos only in the B2 backup and keep compressed copies in Immich |
| Cloudflare's free plan caps each upload at 100 MB, so long videos fail through a Cloudflare Tunnel | Execs upload over **Tailscale** (no limit). The public Cloudflare address is only for viewing share links |
| One person knows how it works | Handover doc plus two admins (see §7) |

## 4. The build, phase by phase

### Phase 1: Local Immich and pulling everything in (week of 5 Oct, free)

**Status (29 Sep 2026):** Compose file and scripts are in `photo-storage/` (Immich v3.2.4). The server has not been started. This Mac has no Docker, about 9 GB free, and no external drive. Phase 1 waits on a host (a spare laptop, or this Mac after about 20 GB is free) and a drive mounted at `/Volumes/BSA-Photos`.

**Machine:** Safdar's Mac, or better an old laptop or mini PC that can stay plugged in, plus an external SSD/HDD if the library won't fit.

1. Install Docker Desktop (Mac) or Docker Engine (Linux).
2. Follow the official Docker Compose install at `docs.immich.app/install/docker-compose`. Download `docker-compose.yml` and `example.env` for the current release, rename it `.env`, set:
   - `UPLOAD_LOCATION=/Volumes/BSA-Photos/immich` (the external drive), or a folder on the internal disk
   - `DB_DATA_LOCATION=./postgres` (keep it on the **internal** disk; Postgres on network drives or exFAT is unsafe)
   - `DB_PASSWORD=` a long random string, saved in the club password manager, not in Notion
3. `docker compose up -d`, open `http://localhost:2283`, create the admin account with a **club email** (the BSA Outlook/Gmail), not a personal one.
4. **Settings to set once** (Administration → Settings):
   - Storage template: on, pattern `{{y}}/{{y}}-{{MM}}-{{dd}}/{{filename}}`, so the folders on disk are readable without Immich.
   - Machine learning: keep on (face and "find the food table" search). If the machine has under 8 GB RAM, turn it off.
   - Video transcoding: default. Originals are always kept.
5. **User accounts:** one per exec who shoots or needs access. Roles:
   - Admin: Safdar plus the Technology VP (two admins, always)
   - Everyone else: normal users, storage quota none
6. **Import Google Drive:**
   - On the club Google account, use Google Takeout → Drive → only the BSA photo folders → .zip 50 GB parts. (If the photos are in Google Photos rather than Drive, pick Google Photos in Takeout.)
   - Import with **immich-go** (`github.com/simulot/immich-go`). It reads Takeout zips directly, keeps dates, and turns Drive folders into albums:
     `immich-go upload from-folder --server=http://localhost:2283 --api-key=<key from Account Settings → API Keys> --folder-as-album=FOLDER /path/to/unzipped/Drive/BSA`
     For Google Photos takeouts: `immich-go upload from-google-photos --server=... --api-key=... takeout-*.zip`
   - Immich skips exact duplicates on its own.
7. **Import laptops:** same `immich-go upload from-folder ...` from each person's folder, or have them drag folders into the web UI (fine for a few GB).
8. **Import phones:** each exec installs the Immich app, logs in, and backs up **only** their BSA album(s). While Immich is local, this works on the same Wi-Fi or over Tailscale (Phase 2).
9. **Organize:** one album per event, named `YYYY-MM-DD Event name` (e.g. `2026-10-30 Adda Night`), plus `YYYY-MM-DD Event name – Selects`. Older stuff goes into year albums (`2024-25 misc`) if dates are unclear.

**Done when:** everything from Drive and every exec's BSA photos is in Immich, with event albums for 2025-26 and 2026-27.

### Phase 2: Remote access without a domain (same week, free)

- **Tailscale** (free Personal plan: 6 users, unlimited devices). Install it on the Immich machine and on the phones of the people who upload most: Photography lead, Marketing lead, the two admins. In the Immich app, set the server URL to the machine's Tailscale address (`http://<machine-name>:2283`).
- More than 6 people need to upload? Share the Immich machine to them with Tailscale device sharing. They join with their own free Tailscale account, and it doesn't count against BSA's 6 users *(check the current device-sharing terms)*.
- **Public share links before the domain exists:** Tailscale Funnel publishes the Immich machine at `https://<machine>.<tailnet>.ts.net` for free. In Immich set Administration → Settings → Server → External domain to that URL, so share links use it. Turn Funnel off when it isn't needed.

### Phase 3: Move to Oracle Cloud Always Free (Oct–Nov, free)

1. Create an Oracle Cloud account with the **club email**. Home region: Toronto (`ca-toronto-1`), or Montreal if Toronto has no ARM capacity. The home region can't be changed later.
2. Create an Ampere A1 VM: Ubuntu 24.04 (or the current LTS), the most OCPU/RAM the free tier gives your account (4/24 or 2/12), 50 GB boot volume. Attach a second block volume of about 150 GB (total stays within the 200 GB free allowance) and mount it at `/srv/immich`.
3. Upgrade the account to "Pay As You Go". **Only** do this if the SU approves a card on it (see §8): it stops idle-reclaim and still bills $0 while you stay inside Always Free limits. Set a **budget alert at $1** in Billing so any charge is caught the same day.
4. Install Docker and Tailscale on the VM. Don't open ports 22 or 2283 to the internet in the Oracle security list; reach the VM through Tailscale only.
5. **Move the library:**
   - On the local machine: `docker compose stop`, dump the database per Immich's backup docs (`docker exec -t immich_postgres pg_dumpall --clean --if-exists --username=postgres | gzip > immich-db.sql.gz`), then `rsync -avh --progress` the `UPLOAD_LOCATION` folder to `/srv/immich/library` on the VM over Tailscale.
   - On the VM: same Immich version, restore the dump per Immich's "Backup and Restore" doc, `docker compose up -d`.
   - Check a few albums, faces and videos, then change the server URL in everyone's app.
6. Keep the local copy for 30 days as a fallback, then keep the external drive as an offline backup (Phase 4).

### Phase 4: Backups, the 3-2-1 rule (with Phase 3)

| Copy | Where | How | Cost |
|---|---|---|---|
| 1. Live | Oracle VM | Immich | $0 |
| 2. Off-site nightly | Backblaze B2 bucket `bsa-photos-backup` | `restic` or `rclone sync` on a cron job at 03:00. Back up the library folder **and** Immich's automatic DB dumps (Immich writes them to `UPLOAD_LOCATION/backups` every day) | First 10 GB free, then US$6.95/TB/month. 100 GB ≈ US$0.63/month |
| 3. Offline | External drive, kept by a president | Plug in once per term, `rsync` from the VM | One-time drive cost |

If the club won't spend anything at all: copy 2 goes to Oracle's own Object Storage (20 GB free). That only covers the database plus selects, not every original, so ask the SU about the few dollars for B2 instead.

Test a restore once a term (restore a DB dump into a throwaway Immich on a laptop). A backup nobody has restored doesn't count.

### Phase 5: Domain and website hook-up (when the domain is back)

1. **Domain:**
   - `laurierbsa.org`: check availability. If it lapsed and is free, register it at Cloudflare Registrar (at-cost, about US$10–11/yr *(check)*). If a squatter holds it, don't pay a premium; use `.ca`.
   - `laurierbsa.ca`: .ca needs Canadian presence. An unincorporated Canadian association qualifies under CIRA's rules. Cloudflare Registrar doesn't sell .ca, so buy it at a CIRA-certified registrar (about CA$15–20/yr *(check)*) and point its nameservers to Cloudflare's free DNS.
   - Either way the domain is a recurring subscription: SU approval plus the SU credit card (§8).
2. **Photos address:** Cloudflare Tunnel (`cloudflared` container next to Immich) → `photos.laurierbsa.org`. Turn Tailscale Funnel off. Set Immich's External domain to the new address. Uploads still go over Tailscale because of the 100 MB limit.
3. **Website images:** the marketing site (Cloudflare Pages or GitHub Pages, both free) should **not** hotlink the Immich server. Export each event's Selects album, resized to 2000 px, to a Cloudflare R2 bucket on `img.laurierbsa.org` (10 GB free covers years of web-sized selects). The website then keeps working even when Immich is down or being moved.
4. **Notion:** add one row per event album to the existing **Media Directory** (Home › Marketing › Photography: `Name`, `URL`, `Initiative` relation). Name = album name, URL = Immich album or share link, Initiative = the slot. No new database is needed.

## 5. The fallback if no one wants to run a server: Ente

If the Technology team can't commit to about 1 hour a month:

- One Ente account on the club email, Popular plan **200 GB, US$59.88/yr** (1 TB at US$119.88/yr if the library is large). SU-approved subscription on the SU card.
- Family plan: add up to 5 exec accounts to share that storage (Photography lead, Marketing lead, co-presidents).
- Everyone else contributes through **collaborative public links**: guests can add photos to an album without an account.
- Import: Ente's desktop app can import Google Takeout zips and folders.
- Downsides: files are end-to-end encrypted, so the website can't pull from it; export selects to R2 by hand. There's also no custom domain for the gallery.

## 6. Photo consent and takedowns (needed whichever tool you pick)

- Event signage and the RSVP form: "Photos and video are taken at this event and may be posted on BSA channels. Tell a photographer or DM @laurierbsa if you'd rather not be posted."
- A **"Do not post"** album in Immich: move any photo someone asks about there. Marketing never posts from it.
- Takedown request → remove the post within 48 hours, move the photo to "Do not post". Don't keep a record of the person in club files beyond what's needed. Anything touching conduct or wellbeing goes to the SU Reporting Form, not club records.
- Public share links: set an **expiry** (30 days for attendee photo dumps) and turn off "allow download of originals" unless it's needed.

## 7. Roles and handover

| Role | Who | Does |
|---|---|---|
| Owner and admin | Co-president (Safdar) | Holds the club accounts (Oracle, Tailscale, Cloudflare, B2, registrar), approves spend |
| Admin and maintainer | Technology VP | Monthly update (`docker compose pull && docker compose up -d`, after reading the release notes for breaking changes), checks backups ran |
| Uploaders | Photography team, Marketing | Event albums and selects within 48 hours |
| Viewers | All execs | Browse and download |

- **Every account uses the club email.** Passwords go in a password manager shared between the two admins (Bitwarden free supports a 2-person organization *(check)*), never in Notion. The Marketing and Outreach handbooks still have passwords in plain text (flagged 26 Sep); don't repeat that here.
- **Handover doc**: a Notion page under Technology with the VM IP/Tailscale name, where the compose file and `.env` live, the backup schedule and the restore steps. Walk the incoming Technology VP through it in April.

## 8. SU and house-rule checks

| Rule | Where it comes from | What it means here |
|---|---|---|
| Subscriptions (e.g. a website domain) should go on the SU credit card and **must be approved by Clubs & Associations before payment** | SU Finance training, Module D.2 "Recurring Payments" | Domain, B2 and Ente (if chosen) all need approval first. Ask at the same time whether the SU card can be attached to a $0 Oracle account for verification |
| All money runs through the SU | CLAUDE.md, SU rules | No exec pays personally and gets reimbursed month after month |
| "Tooling must be free forever. No paid integrations." | CLAUDE.md house rule | The recommended path is $0. B2 backup (under US$1/month), the domain and Ente are **exceptions Safdar must approve**; the rule needs an explicit carve-out if you take them |
| SU executives must use OneDrive | SU "Student Executive Digital File Storage" procedure | Applies to SU executives, not clubs. BSA isn't bound by it |

## 9. Cost summary

| Setup | Year 1 | Ongoing |
|---|---|---|
| Recommended: Immich on Oracle Free + B2 backup + domain | Domain about CA$15–20 + B2 about US$8 (100 GB) ≈ **CA$30/yr** | Same |
| Recommended without the domain or B2 | **$0** | $0 |
| Local-only (Phase 1–2 forever) | $0 (+ drive if needed) | $0 |
| Ente 200 GB + domain | ≈ **CA$100/yr** | Same |

## 10. Decisions for Safdar

1. Library size from §2 (decides Oracle vs paid VPS vs Ente).
2. Self-host (Immich) or hosted (Ente)? This depends on whether the Technology VP will own a monthly update.
3. Which machine hosts Phase 1: your Mac or a spare laptop?
4. Approve the small-spend exceptions to "free forever": B2 backup, domain.
5. `.org` or `.ca`, after checking whether laurierbsa.org is actually available.
6. Ask the SU (Clubs & Associations) about the subscription approvals and the SU card on Oracle.

## 11. Tracker items to add (suggested)

| Item | Owner | Due |
|---|---|---|
| Measure photo library size (Drive + exec survey) | You | 3 Oct |
| Decide Immich vs Ente; approve spend exceptions | You | 5 Oct |
| Phase 1: local Immich plus Drive import | Technology VP (Claude Code can write the compose file and scripts) | 12 Oct |
| Phase 2: Tailscale plus phone app setup for uploaders | Technology VP + Photography | 12 Oct, before the 22 Oct booth |
| SU approval request: domain + B2 | You | 16 Oct |
| Phase 3–4: Oracle move plus nightly B2 backup | Technology VP | 15 Nov, before the 27 Nov flagship |
| Consent line on signage and RSVP form | Marketing | Before the 22 Oct booth |
| Media Directory rows for 2026-27 albums | Photography | Rolling, 48 hours after each event |
| Handover page in Notion | Technology VP | 30 Nov |

## Sources

- Immich stable releases and recaps: https://immich.app/blog, https://github.com/immich-app/immich/discussions/22546
- Immich requirements: https://docs.immich.app/install/requirements/
- Immich + Cloudflare Tunnel: https://www.klissner.uk/en/immich-secure-internet-sharing-a-practical-guide/
- Oracle Always Free: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm, https://terminalbytes.com/oracle-cloud-free-tier-changes-2026/
- Cloudflare R2 pricing: https://www.cloudflare.com/products/r2/
- Backblaze B2 pricing: https://www.backblaze.com/cloud-storage/pricing
- Ente plans and family sharing: https://ente.com/, https://ente.com/help/photos/features/account/family-plans
- Tailscale free plan: https://tailscale.com/pricing
- Laurier OneDrive 100 GB: https://students.wlu.ca/campus-services/tech-services/software/microsoft-office-365.html
- SU digital file storage procedure: https://www.yourstudentsunion.ca/policies-and-procedures-22/student-executive-digital-file-storage
- SU subscription rule: `SU Policies 2026-27/Waterloo SU Clubs Training 2026-Finance.pdf`, Module D.2
