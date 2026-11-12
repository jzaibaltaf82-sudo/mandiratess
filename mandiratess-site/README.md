# MandiRates — mandiratess.com (static site package)

Plain static site (HTML/CSS/JS, no build step). Upload the whole folder to
Cloudflare Pages — see `DEPLOY.md` for the exact steps.

## What is ready (11 Nov 2026)

- **23 pages + 404 + sitemap + robots + OG image** (660 KB total, largest page 45 KB):
  home, wheat hub, Punjab, Lahore, Faisalabad, Multan, Atta, Support Price,
  History, Rice, Sugar, Cotton, Calculators, AI Tools, Alerts, Pricing, About,
  FAQ, Privacy, Terms, Contact, Corrections, Methodology.
- **On-page SEO on every page:** unique title + meta description (24/24 unique),
  one H1, H2/H3 structure, direct-answer intro, dated sourced prices, internal
  links between hub / city / atta / support-price / history / rice / sugar /
  cotton pages, FAQ sections on 7 pages.
- **Technical SEO:** `sitemap.xml` (24 URLs), `robots.txt`, canonical tags
  (24/24), Open Graph + Twitter cards (24/24, real 1200×630 `og-image.png`),
  JSON-LD on every page — Article on the 11 price pages, BreadcrumbList on 22
  pages, FAQPage on the 7 pages that have FAQs. Mobile-friendly, lightweight,
  no external JS.
- **Competitor gaps closed (audit read 9 Nov 2026, 7 sites):** verified-only
  history chart (no invented daily series), 6 calculators (kg↔maund 40kg and
  37.324kg, atta bag, chakki, household stock, revenue, break-even), working
  CSV export (Punjab mandi table + history anchor points), AI Market Brief in
  English + Roman Urdu (hub, dated 11 Nov 2026), Price Checker, Ask MandiRates
  (front-end demo, answers only from this site's figures), front-end watchlist
  (localStorage, labelled front-end only), Free / Farmer Pro / Trader pricing
  page, About / Contact / Privacy / Terms, competitor audit table (hub).
- **Human-made feel:** warm paper palette (Fraunces + Public Sans), SVG
  illustrations (range bar, atta bags, history chart, wheat stalks on home),
  "Last checked: 11 Nov 2026, 12:00 PKT" on all 16 price pages and
  "Last updated: 11 Nov 2026" on the trust pages.
- **Honesty labels everywhere:** site is NOT AdSense-approved; API and price
  alerts have NO live backend; SaaS tier prices are unvalidated proposals;
  alerts/watchlist are front-end only.

## Verified figures used (do not change without re-verifying)

- AMIS Punjab mandi average **Rs 4,546/40kg** on the Punjab page (recomputed
  from 19 Punjab mandis, total Rs 86,373 ÷ 19 = Rs 4,545.95), range
  Rs 3,363–5,640, **2 Nov 2026**. The hub keeps **Rs 4,551** from Zarat Ghar's
  hub page, with a footnote explaining the Rs 5 difference.
- PBS atta **Rs 2,941.34/20kg**, week ended **5 Nov 2026** (~Rs 147.07/kg;
  10kg Rs 1,470.67, 50kg Rs 7,353.35, calculated).
- **Rs 4,500/40kg is an INDICATIVE price** for the 2027 crop, set 23 Oct 2026,
  **not formally notified** — separate from the Sindh release price cut
  Rs 5,000 → Rs 4,500 (3 Nov 2026, government wheat to mills).
- **Lahore and Multan have NO AMIS mandi row** — those pages print no rate.
- **Karachi atta Rs 3,371 is UNVERIFIED** — not published as a 5 Nov figure.
- **Toba Tek Singh Rs 3,600 / Bahawalnagar Rs 4,525 are unverified** — noted
  as reported-but-unverified only, never as table rows.
- Rs 3,900 season label is unverified — deliberately left out of the table.
- Next data point: **PBS SPI, week ended 12 Nov, expected Fri 13 Nov 2026** —
  update the atta national average and the city split together, never one alone.

## What is still blocked

1. **Nameserver change at Spaceship — still pending.** Domain mandiratess.com
   still points at launch1/launch2.spaceship.net. It must be changed to
   kayleigh.ns.cloudflare.com and rene.ns.cloudflare.com. The Spaceship login
   for guestpost793 was rejected twice ("Invalid username or password") —
   the correct username is jhanzaib (from the user's screenshot), and that
   login still needs to be saved via the secure card before retrying.
   No one should change DNS until that login works.
2. **Real author name for the byline — done 11 Nov 2026 ~19:12 PKT.** The user confirmed "Jahanzaib" as the author name, and every price page now says "Checked by Jahanzaib". A real monitored contact email is still a remaining AdSense blocker (the contact page says so plainly; do not use info@example.com).
3. **Hosting choice — decided: Cloudflare Pages (free).** Deploy steps are in
   `DEPLOY.md`. The site will first be live at mandiratess.pages.dev; the
   custom domain mandiratess.com only works after blocker 1 is done.
4. **Cloudflare email verification — NOT confirmed complete as of
   11 Nov ~13:14 PKT.** The user clicked a link ~13:04, but the dashboard
   still showed "Verify your account" blocking Workers & Pages, and a fresh
   verification email was resent ~13:14. Click the fresh link first.

## Regenerating the site

The generator is saved durably at
`~/workspace/your_files/mandiratess-site-generator/gen_site.py`.
Run `python3 ~/workspace/your_files/mandiratess-site-generator/gen_site.py`
— it rewrites this folder (it asserts `og-image.png` exists first; that file
is a real asset in this folder, generated with PIL, 1200×630).

Do NOT edit the generated HTML by hand for content changes — edit the
generator and re-run it, so the next regeneration does not wipe the fix.

## Verification done 11 Nov 2026 (after the SEO build)

- HTML parse: 24 pages, 0 issues. Internal links: 22 hrefs, 0 missing targets.
- OG/Twitter/canonical: 24/24 each. JSON-LD parses on every page (11 Article,
  22 BreadcrumbList, 7 FAQPage — matching the 7 FAQ sections). 24 unique
  titles, 24 unique meta descriptions, H1 on every page.
- JS: `node --check` passes; all 6 calculators + Price Checker (5 mandis incl.
  Lahore/Multan no-rate) + Ask MandiRates (5 questions incl. out-of-scope
  fallback) + watchlist add/render/remove + both CSV downloads exercised in
  Node with a DOM stub — all correct.
- Content scan: no unverified figure published as fact (Karachi atta 3,371
  absent; Toba Tek Singh / Bahawalnagar only as reported-but-unverified;
  Rs 3,900 only in "deliberately left out" notes; Rs 4,500 always "indicative,
  not notified"; no AdSense-approval, live-SaaS, or #1-ranking claim).
- Punjab table arithmetic re-checked: 6 verified rows, per-kg and per-100kg
  columns exact; average row Rs 4,546 / Rs 113.65 / Rs 11,365.00.
