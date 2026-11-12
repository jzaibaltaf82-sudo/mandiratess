# Deploying MandiRates to Cloudflare Pages (free)

**Goal:** get the site live. The package in this folder is a plain static site
(HTML/CSS/JS, no build step), so it uploads directly to Cloudflare Pages.

**What you need before you start:** a Cloudflare account. Ours exists:
jzaibaltaf82@gmail.com, free plan, mandiratess.com already added, email
verification NOT confirmed complete as of 11 Nov 2026 ~13:14 PKT — the
dashboard still showed "Verify your account" blocking Workers & Pages
after the user clicked a link ~13:04, and a fresh verification email was
resent ~13:14. Click the fresh link in the Gmail inbox first. Sign in at
https://dash.cloudflare.com — do not create a second account.

## Step 1 — Create the Pages project (direct upload, no Git)

1. Sign in to the Cloudflare dashboard (jzaibaltaf82@gmail.com).
2. Left menu: **Workers & Pages** → **Create** → tab **Pages** →
   **Upload assets** (this is the direct-upload option — no Git repository
   and no build step needed).
3. **Project name:** `mandiratess` (exactly this — it becomes
   `mandiratess.pages.dev`).
4. Click **Create project**.
5. Drag the **entire contents of this folder** (`mandiratess-site/`) into the
   upload area — or zip the folder contents and upload the zip. Upload
   everything: all the `index.html` files, `404.html`, `sitemap.xml`,
   `robots.txt`, `og-image.png`, `README.md`, `DEPLOY.md`.
   (README.md / DEPLOY.md are harmless text files; Pages serves them as-is.)
6. **Framework preset:** None. **Build command:** leave empty.
   **Build output directory:** leave empty (the files are already the site).
7. Click **Deploy**.

## Step 2 — Check the live Pages URL

- The site is now live at **https://mandiratess.pages.dev**.
- Open it and check: home page loads, `/wheat-price-pakistan/` loads,
  a city page loads (`/wheat-price-faisalabad/`), a missing page shows the
  custom 404 (`/does-not-exist/`), and `https://mandiratess.pages.dev/sitemap.xml`
  lists 24 URLs.
- This URL works **before** the domain is connected. Use it to show the site
  and to submit to search engines while the domain steps below are pending.

## Step 3 — Connect the custom domain mandiratess.com

**Do this only after the nameserver change at Spaceship is done.**
The domain still points at launch1/launch2.spaceship.net. Until the
nameservers are changed to kayleigh.ns.cloudflare.com and
rene.ns.cloudflare.com (at Spaceship, account jhanzaib — correct login
still pending), Cloudflare cannot serve mandiratess.com and this step will fail.

Once Cloudflare shows the domain status as **Active** (not "Invalid
nameservers"):

1. In the dashboard, open the `mandiratess` Pages project →
   **Custom domains** → **Set up a custom domain**.
2. Enter `mandiratess.com` → **Continue** → **Activate domain**.
   Cloudflare adds the DNS records for the Pages project automatically —
   no manual DNS record is needed.
3. Wait a few minutes, then open **https://mandiratess.com** — it should show
   the home page. Also check **https://www.mandiratess.com**: if it does not
   work, add it as a second custom domain the same way (or set a redirect
   in Cloudflare: Rules → Redirect Rules, `www.mandiratess.com/*` →
   `https://mandiratess.com/$1`, status 301).
4. SSL/TLS: leave the default (Full). Pages issues the certificate
   automatically; if the browser shows a certificate warning, wait 10–15
   minutes and retry.

## Step 4 — Tell Google and Bing the site exists (after the domain is live)

1. **Google Search Console:** https://search.google.com/search-console →
   add property `https://mandiratess.com` → verify by the DNS TXT method
   (Cloudflare DNS tab → Add record, TXT, paste the value Google gives) →
   **Sitemaps** → submit `https://mandiratess.com/sitemap.xml`.
2. **Bing Webmaster Tools:** https://www.bing.com/webmasters → add site →
   verify the same way → submit the same sitemap URL.
3. In Cloudflare, **no extra step is needed** for the sitemap — it is served
   from the uploaded files.

## Step 5 — After launch, before applying for AdSense

- The **real author name** is filled in (byline reads "Checked by Jahanzaib", confirmed by the user 11 Nov 2026). Still to do: the **real monitored contact email** (contact page currently says none is set) — an AdSense blocker.
- Replace the SVG placeholder illustrations with real photos (wheat field,
  atta bags) — the captions say so on each figure.
- Re-check prices on publish day: latest AMIS release is 2 Nov 2026 and
  latest PBS SPI is week ended 5 Nov 2026; the next SPI (week ended 12 Nov)
  is expected Fri 13 Nov 2026.

## What NOT to do

- Do NOT change nameservers or DNS from inside this package — the nameserver
  change happens at Spaceship, and the custom-domain step happens in the
  Cloudflare dashboard.
- Do NOT sign in anywhere on the site's behalf from an agent — the steps
  above are done by the user in the Cloudflare dashboard.
- Do NOT pay for anything: Pages free plan covers this site (static, ~660 KB).
- Do NOT claim the site is live at mandiratess.com until Step 3 succeeds —
  until then it is live only at mandiratess.pages.dev.
