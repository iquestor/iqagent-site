# iqagent site: project notes

Last updated: 2026-11-24. Written so a new session can pick up without re-deriving anything.

## Update 2026-11-24 (design refresh with Impeccable)

- **Direction:** iQagent is the flagship and iqagent.com leads with it. Bob plans other software and **services** under iQagent (not iQuest). The Extractor is link-only on the brand site ("Other tools" in the nav and footer, plus a "More from iQagent" row on the home page); its marketing goes straight to software.iqagent.com. The home page describes iQagent as delivering "industrial automation solutions". Services are not described on the site yet; do not invent any.
- **Context files at repo root (not published):** `PRODUCT.md` (product truth, audiences, constraints) and `DESIGN.md` (the visual system), plus `.impeccable/design.json` (sidecar). Read them before design work. A saved critique of `main/` is in `.impeccable/critique/` (local, git-ignored).
- **New palette on `main/` only:** steel navy (#13293d) bars, signal amber (#f5a300) buttons with dark ink text, steel-blue links. White text on amber fails contrast, so buttons use dark text. `software/css/style.css` still has the old orange/charcoal palette and the dark-mode button contrast bug; update it together with the Paddle cutover.
- **Home page:** hero and "Less time hunting for information" section zigzag (image right, then image left); all sections share a 1240px container. The old "Two products" cards are gone.
- **Product page:** the "Features" section was removed (it duplicated "What it does for your team"); the 15-minute setup claim moved into the security section.
- **Images:** `main/images/iqagent_poi_list.jpg` (phone photo) and the screenshots on the product page come from the original iqagent.com site; Bob is licensed to use any image from it.
- **YouTube embed error 153** ("Video player configuration error") only appears when a page is opened from disk (`file://`). Preview with `python -m http.server` inside `main/` and it plays.
- **Open decisions:** whether to cut push notifications (Bob is leaning toward cutting them: no one appeared to use it); iQagent pricing and licensing (Bob will supply); the services content.

## Goal

Relaunch iQagent (the mobile plant-floor app, sold since 2011, no sales in about two years) and host all iQagent products on Cloudflare. The old iqagent.com is a GoDaddy Website Builder site. The brand spelling is **iQagent** (lowercase "a").

## Repo layout

- Repo: `C:\Users\bmeads\Documents\Dev\Source\iqagent-site`, private on GitHub at `iquestor/iqagent-site` (account IQUESTOR, personal). Plain static HTML/CSS, no build step.
- `main/` is the brand site for **iqagent.com**: home, `iqagent/` (product page), `contact.html`, `privacy.html`, `eula.html`, `_redirects`, `robots.txt`, `sitemap.xml`, `css/`, `images/`.
- `software/` is the Archive Data Extractor site for **software.iqagent.com** (copied from `WinCCArchiveDataExtractor/site`). It includes the signed 1.0.2.0 installer in `software/downloads/`, served from the site on purpose (1.2 MB, R2 can wait).
- The app repo (`WinCCArchiveDataExtractor`) still has its own `site/` folder and uncommitted changes. Nothing there was touched. Remove its `site/` and update its `CLAUDE.md` only after the swap below.

## Cloudflare and domain state

- Pages project **`iqagent-site`** is Git-connected to this repo, output directory `main`, preview at `https://iqagent-site.pages.dev` (verified current; deploys on every push).
- Existing Pages project **`iqagent-software`** is a manual upload from the app repo's `site/` and serves `software.iqagent.com` (CNAME to `iqagent-software.pages.dev`). Paddle approved that hostname for payments and Apple Pay (Paddle verifies Apple Pay itself, no file needed). **Do not change it until Paddle finishes verifying the owner's ID** (the last pending step; checkout does not work yet).
- iqagent.com: registrar GoDaddy (privacy via Domains By Proxy, expires 2029-12-20, locks incl. `clientUpdateProhibited` may block nameserver changes), DNS at GoDaddy (`ns69/ns70.domaincontrol.com`).

### Current iqagent.com DNS (copy exactly when moving DNS)

- A (root): 76.223.105.230, 13.248.243.5 (GoDaddy builder; this is what changes). `www` CNAME to `iqagent.com` (changes too).
- MX: `iqagent-com.mail.protection.outlook.com` priority 0 (Microsoft 365, handled by the owner's other company).
- CNAME `autodiscover` to `autodiscover.outlook.com`.
- TXT SPF: `v=spf1 include:spf.em.secureserver.net include:spf.protection.outlook.com -all`.
- TXT `_dmarc`: `v=DMARC1; p=none; rua=mailto:dmarc_rua@onsecureserver.net`.
- No DKIM records exist (selector1/2 missing). Fix after cutover as a separate task (Microsoft 365 admin center).
- Not yet seen: the GoDaddy DNS manager's full record list. Get a screenshot before cutover to catch records not queried (verification TXTs, `_domainconnect`, email forwarding).

## Decisions made

- Extractor stays on the **subdomain** `software.iqagent.com`; brand and iQagent live on `iqagent.com` (separate Pages projects, one repo).
- Installer served from the site for now; Cloudflare R2 later only if wanted (needs DNS on Cloudflare for a custom domain).
- Headline: **"Scan a code. See everything about the machine."** QR codes are generated by the configuration software and printed, or mapped to an existing barcode asset tag.
- Devices: iOS, Android, **RealWear HMT**. No other smart glasses. No HoloLens mention anywhere.
- Proof tiles on the home page are facts only: since 2011, about 15 minutes to set up including the first POI, 3 live data sources (OPC DA, OPC UA, ODBC), 0 plant data sent to iQagent. No customer names or numbers were invented (past large customers left; no permission to name any).
- Security wording: TLS between apps and server; each client app has a token registered with the server; nothing is sent back to iQagent; only user-configured push notifications leave the network, sent from the customer's server straight to Apple and Google. No certifications claimed.
- Booking: Calendly `https://calendly.com/bob-meads/30min` (linked directly from the contact page).
- Video: YouTube `3N2Gp5IkyQw` ("A quick look at iQagent App on the Plant Floor"), embedded via `youtube-nocookie.com`. New videos are planned (show setup with a clock, QR code creation in the configuration software).
- Hero image: `main/images/iqagent_demo.jpg` (taken from the old site).
- `_redirects` maps all 13 old GoDaddy pages (from its sitemap) to new pages; tested on the preview.
- Legal: iQagent-specific privacy notice (dated 2026-10-24) and EULA are drafts. Licensing is **per number of users per server; the server needs no license**. Have a lawyer review both before launch.

## Open items

1. **Push notifications:** keep, demote or cut? If cut, update the home card, the iQagent benefits/features/how-it-works lines, FAQ, the privacy notice and the EULA together.
2. **Licensing and pricing model** (perpetual vs subscription vs both, what the fee covers, updates and support, renewal, whether to show prices). Then rewrite EULA sections 2 and 4 and the iQagent Pricing section. The extractor's model (perpetual with an update period, renewals) is one template.
3. **Privacy notice "Purchases" section:** iQagent is sold by invoice today and will move to Paddle; rewrite when that is live (reuse the extractor notice's Paddle wording).
4. **Possible "SSL/TLS" and role/audit wording:** only if the product actually has roles or audit logs; none claimed now.
5. Add an iQagent link to the extractor site's navigation; consider a Resources page (redirects for `/resources` and `/videos` currently point to the product page).
6. Optional: demo request form instead of Calendly-only; confirm the iQagent brochure PDF has no HoloLens or "smart glasses" wording.

## Cutover plan (after Paddle finishes and the open items are settled)

1. Create a second Pages project from this repo with output directory `software`; verify on its `pages.dev` URL against the live extractor site, including the installer download link.
2. Move the `software.iqagent.com` custom domain from `iqagent-software` to the new project (needs GoDaddy CNAME retargeted or DNS on Cloudflare). Keep the old project as a fallback, then delete it later. Check the Paddle checkout and the Apple Pay button afterwards.
3. Add `iqagent.com` to Cloudflare. Compare its imported DNS records to the list above and fix by hand. Keep GoDaddy as registrar; turn off the registry/update lock first if nameservers cannot be changed. Change the two nameservers at GoDaddy. Attach `iqagent.com` and `www` to the `iqagent-site` Pages project.
4. Verify email still works (send and receive), the site, the redirects, and `www`. Keep the GoDaddy site until confirmed.
5. After: add DKIM, tighten DMARC reports to a mailbox the owner reads, update the app's `LicenseRuntime.BuyUrl` if the Buy page address changes, remove `site/` from the app repo and update its `CLAUDE.md`.

## Working notes

- Commit/push from PowerShell with `git -c core.autocrlf=false commit`; the shell reports exit code 255 because of git's line-ending warnings even when the push succeeded. Confirm with `git status -sb` after `git fetch`.
- Edit files with the Edit tool and re-read a file after any script rewrote it. Do not rewrite HTML with PowerShell 5.1 `Get-Content`/`Set-Content` (it mangled UTF-8 en dashes once; fixed).
- Preview locally with `python -m http.server` inside `main/`, in a new browser tab (local file tabs cannot be driven).
- The site pages use yellow `.ph` spans and a DRAFT banner for placeholders; remove the banner when launching.
