# Product

<!-- impeccable:product-schema 1 -->

This repo holds two sites for one company, iQagent, Inc. Both are plain static HTML/CSS with no build step, in `main/` (iqagent.com) and `software/` (software.iqagent.com).

**Direction (Bob, 2026-11-24):** iQagent is the flagship product and iqagent.com leads with it. The goal is to add other software solutions and services that support the general automation industry, without competing with the flagship. Services will be offered under iQagent (not iQuest). Archive Data Extractor is reachable by link only, through an "Other tools" link in the nav and footer that goes to software.iqagent.com, and is not featured on iqagent.com. When more tools exist, add a section for them, each with its own page. Its marketing goes straight to `software.iqagent.com`, so the brand site doesn't need to promote it. Other tools and services are not defined yet; do not invent any. Bob confirmed (2026-11-24) that iQagent provides services as well as software and describes itself as delivering "industrial automation solutions" (not only software). The site does not describe those services yet, and nothing should be claimed about them until Bob supplies the facts.

## Platform

web

## Stack

Existing codebase: plain static HTML and CSS, deployed on Cloudflare Pages (`main/` via the Git-connected project `iqagent-site`; `software/` via the separate project `iqagent-software`, a manual upload for now).

## Users

**iQagent (iqagent.com):** industrial plant staff who need machine information at the machine. The audience is mixed: plant and controls engineers who set it up and recommend it, maintenance and operations managers who care about technician productivity and downtime, and system integrators who deploy it for their customers. End users are technicians and operators on phones, tablets and RealWear HMT headsets. Plant IT teams ask about security and hosting first. Confirmed by Bob as a mix of these groups on 2026-11-24.

**Archive Data Extractor (software.iqagent.com):** WinCC engineers, plant engineers and analysts, and integrators who need to get WinCC tag logging archives out into CSV for reports, audits, migrations and recovery. Often under time pressure: a report is due, a regulator wants last year's data, or all that is left of an old project is a folder of `.mdf` backups.

The two audiences overlap but differ. They are separate audiences with a light link between them (Bob, 2026-11-24). On iqagent.com the audience is the flagship's; the Extractor audience arrives directly at the software site.

## Product Purpose

**iQagent** is a mobile plant-floor app, sold since 2011. A QR code, or a barcode asset tag the plant already uses, is attached to each machine, line or area (a point of interest, or POI). Scanning it shows that equipment's live process data, manuals, videos, drawings and forms. Users can fill in forms offline, share annotated photos and video with a remote expert, and get push and email alerts. The aim is less time hunting for information. It is being relaunched after about two years with no sales.

**Archive Data Extractor for WinCC** exports WinCC tag logging archives to CSV. It reads offline `.mdf` archive folders or a running project, and puts timestamps in the plant's time zone. It is read-only. Success is a user who confirms with the free trial that it reads their archives, then buys a license.

## Positioning

- **iQagent:** the headline is "Scan a code. See everything about the machine." It maps onto asset tags a plant already has. It installs on the customer's own server, cloud server or VM, and none of the plant data is sent to iQagent. Setup, including the first POI, takes about 15 minutes.
- **Extractor:** it does what WinCC's own export does not. Tag logging archives are compressed, so plain SQL can't read them. This tool reads them without SQL or OLE DB programming, works offline from archive files, and handles time zones correctly. Bob Meads, the builder, has worked with WinCC since 1996, starting on the original Siemens team that brought it to the American market. The company is a Siemens Solution Partner.

## Operating Context

- iQagent runs on the customer's server (on-premises, cloud or VM). Live data comes from OPC DA, OPC UA and ODBC. Devices are iOS, Android and RealWear HMT. No other smart glasses are supported, and nothing should mention HoloLens.
- The Extractor is a Windows desktop tool (.NET Framework 4.6.1 or later) that needs the WinCC OLE DB provider and a reachable SQL Server. It supports WinCC SCADA V7.4 and later and WinCC Professional. WinCC Unified is not supported.
- Both sites are static. Inquiries for iQagent go through a Calendly 30-minute booking. The Extractor is sold through Paddle checkout, with a free trial installer served from the site and a 14-day refund window.
- Brand site and software site are separate Cloudflare Pages projects from one repo.

## Capabilities and Constraints

- **Brand spelling is "iQagent"** (lowercase "a").
- **Facts only.** Proof tiles on the home page are facts: since 2011, about 15 minutes to set up, 3 live data sources, 0 plant data sent to iQagent. No customer names, numbers or certifications are claimed (past large customers left and there is no permission to name any). Don't invent any.
- **Security wording:** TLS between apps and server. Each client app has a token registered with the server. Nothing is sent back to iQagent. Only user-configured push notifications leave the network, sent from the customer's server straight to Apple and Google. No certifications claimed.
- **Extractor pricing (live on the site):** free trial (24 hours of data per run), Project Pass $129 for 30 days, Single User $349 with 1 year of updates and $99/year to renew, Integrator Pack $1,199 for 5 seats and $299/year to renew. Licenses belong to a person, not a computer.
- **Siemens trademark disclaimer** must remain: Siemens, SIMATIC and WinCC are trademarks of Siemens AG, and iQagent is not affiliated with or endorsed by Siemens AG.
- **Download tracking** on the Extractor installer records file name, country and referrer host only (see `DOWNLOAD-TRACKING.md`). The privacy notice must stay in sync.
- **Deployment constraints:** every push deploys `main/` to the `iqagent-site` preview. `iqagent-software` must not change until Paddle finishes verifying the owner's ID. After that, `software/` moves to a new Pages project from this repo.
- **Draft state:** the `main/` pages carry a DRAFT banner and yellow `.ph` placeholder spans that must be removed or replaced before launch. The legal pages (privacy notice, EULA) are drafts awaiting lawyer review.
- **Undecided product facts (do not resolve in design work):** whether iQagent keeps, demotes or cuts push notifications; the iQagent licensing and pricing model (EULA sections 2 and 4 and the Pricing section depend on it); the iQagent "Purchases" privacy wording once it moves to Paddle; whether to claim roles or audit logging (none claimed now).
- **Out of scope:** the Ignition-to-WinCC migration research and partner notes in `reports/` and `research_notes/` are unrelated to these sites (Bob, 2026-11-24).

## Brand Commitments

- The name is iQagent, from iQuest. The company is iQagent, Inc., 5174 McGinnis Ferry Road, #143, Alpharetta, GA 30005.
- Voice (existing): practical and direct, written for the people who run and maintain equipment, "not for a boardroom slide." The Extractor page speaks in the first person as Bob Meads, the builder.
- The brand site headline is "Software that puts plant data in the hands of the people who need it."
- Existing assets: the hero image `main/images/iqagent_demo.jpg`, favicons, the Extractor screenshots in `software/images/`, and the YouTube walkthrough videos. These are inherited, not endorsed as a final look.

## Evidence on Hand

- Real product screenshots of the Extractor (`software/images/`), a four-minute YouTube walkthrough (`3N2Gp5IkyQw` for iQagent), a benchmark on the Extractor page (815 tags: 8 min at Parallel 1, 3 min at Parallel 4, on one WinCC 7.4 project), and a step-by-step guide at `software/guides/`.
- A signed 1.0.2.0 installer in `software/downloads/`.
- Builder credibility: WinCC since 1996, Siemens Solution Partner.
- **Absent, so do not fabricate:** customer names, testimonials, case studies, press, awards, certifications, and user counts for either product. iQagent has no pricing yet.

## Product Principles

1. **Facts over claims.** If it can't be shown or truthfully stated, it doesn't go on the site.
2. **Show the real product.** Real screenshots and real numbers beat illustration.
3. **Flagship first, catalog behind it.** iqagent.com leads with iQagent. Other software and services sit lower, with their own call to action (demo for the flagship, trial or download for tools, "talk to us" for services). The Extractor is a link, not a feature, on the brand site.
4. **Name products as "[Product] by iQagent".** Plain "iQagent" means the flagship, so copy never leaves a reader unsure which one is meant.
5. **Plant-floor plain.** Direct language and fast answers. Plant IT and engineers should find what they need without a sales call.
6. **Privacy as a feature.** Plant data stays with the customer, and the sites say so exactly as far as the facts go.

## Accessibility & Inclusion

No product-specific standard was set. Brand site visitors may arrive on phones. Reasonable baseline: WCAG 2.1 AA.
