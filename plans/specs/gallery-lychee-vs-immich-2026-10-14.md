# Gallery: Lychee vs Immich

Written 14 Oct 2026 (asked in session). The 29 Sep plan (`photo-storage-2026-09-29.md`) picked Immich and set Lychee aside. Lychee is what actually went live. This note checks whether to keep it.

## What is running today

| Item | Value |
|---|---|
| App | Lychee v7.1, Docker image `ghcr.io/lycheeorg/lychee:latest` |
| Server | Oracle Cloud Always Free, AMD micro VM: 2 vCPU, **954 MB RAM**, 48 GB disk (41 GB free) |
| Library | 621 MB of photos, SQLite database 1.1 MB |
| Address | https://laurierbsa.duckdns.org (Caddy, free HTTPS) |
| Backups | **None.** No cron job on the server. The only copy is this one VM. |

## What each one does

| | Lychee (current) | Immich |
|---|---|---|
| Built for | Showing albums to other people: a public gallery | Backing up and searching a big library, like Google Photos |
| Face recognition, "search for food table" | No | Yes |
| Phone app with auto-backup of one album | No. Upload on the website (works on phones) | Yes |
| Public album links | Yes, per album: public, hidden, password, download on/off | Yes, share links with a custom name (`/s/meet-the-team`) |
| Guests upload photos without an account | Paid tier (SE) only | Free, on a share link |
| Landing / home page | Built in (we turned it off), plus our own templates | None. Login page or share links only |
| Custom look | Easy. We already add our own CSS, JS, preview card, and error page | Hard. No custom CSS or JS. Changes need a proxy hack and break on updates |
| Video | Plays, makes thumbnails | Better: converts to web-friendly copies |
| RAM needed | Runs in under 1 GB (it does today) | 6 GB minimum, 8 GB recommended |
| Fits this free VM | **Yes** | **No.** Needs the free ARM VM (4 CPU / 24 GB), which Toronto often has no capacity for |
| Database | SQLite: one file, easy to back up | Postgres: needs a dump job, and restores are pickier |
| Updates | Small and occasional | Monthly, and some have needed manual steps |

## Pros and cons for BSA

**Lychee**
- Pros: runs on the free VM we already have; looks like ours (logo, colours, share buttons, error page); has a landing page we can make public later; backups are simple (one folder and one file).
- Cons: no face search; no auto-backup phone app, so execs upload by hand; guest uploads cost money; Lychee is a smaller project than Immich.

**Immich**
- Pros: best for execs dumping hundreds of phone photos; face and object search; free guest uploads; very active project.
- Cons: can't run on our free VM; needs the free ARM VM (hard to get) or a paid server (about CA$5–15/month); can't be branded the same way; no public landing page; more upkeep.

## Recommendation

**Stay on Lychee.** Losing face search is fine for a club gallery whose job is sharing event albums. Immich only wins if execs need phone auto-backup and search across thousands of photos, and getting that means either the hard-to-get ARM VM or a monthly bill.

## Keeping it up and not losing photos

The app choice matters less than these steps. Ranked by risk:

| # | Risk | Fix | Cost |
|---|---|---|---|
| 1 | **No backup.** If the VM or the Oracle account is lost, every photo is gone | Nightly copy of `uploads/` and `sqlite/` to a second provider with `rclone`: Cloudflare R2 (10 GB free, account already exists) or Backblaze B2 (10 GB free). Today's 621 MB fits many times over | $0 |
| 2 | **Oracle reclaims idle free VMs.** A quiet gallery uses little CPU, so it can count as idle and get stopped | Upgrade the Oracle account to Pay As You Go with a $1 budget alert. Free-tier resources still bill $0, and reclaiming stops. Needs a card: ask the SU first | $0 if it stays in limits |
| 3 | **`:latest` image.** Any restart can pull a new Lychee major version that breaks our templates | Pin the image to the version we run now (v7.1.x) and update on purpose | $0 |
| 4 | One admin knows how it works | Second admin account (Technology VP), plus the `photo-storage/` README as the handover | $0 |
| 5 | DuckDNS address | Free and fine. Move to `photos.<club domain>` when the domain is back; only the Caddy file changes | $0 |
| 6 | Free tiers change terms | The backup (step 1) is what protects us: with a copy in R2 or B2, rebuilding on another host takes an hour | — |

## Later

- **Public home page:** turn Lychee's landing page back on, or build our own home template the same way as the error page: logo, a few featured albums, and a link to Instagram. The album list can stay private (`login_required_root_only` is already on).
- If the library grows past about 30 GB or execs ask for phone auto-backup, look at Immich again on the ARM VM, keeping Lychee as the public face.
