# Launch checklist — jujuhung.com

Plain GitHub Pages (`jujuhung/juliahung`, `main` / root). DNS moves from Wix
back to GoDaddy. No server-side redirects: old Wix URLs 404, and `404.html`
forwards visitors on known old paths with JavaScript.

## Done

- [x] Delete `_redirects`, `tools/gen_redirects.py`, `commission/`
- [x] Sitemap: drop `/./`, add `<lastmod>`, percent-encode Chinese URLs
- [x] Favicon + apple-touch-icon on every page
- [x] `404.html` forwards old `/artwork/*`, `/exhibition/*`, `/post/*` and one-offs
- [x] JSON-LD `sameAs`: Instagram `jujuhung` + Artsy

## Prelaunch (no GoDaddy access needed)

- [ ] Merge `prelaunch-cleanup` into `main`
- [ ] Review copy at `https://jujuhung.github.io/juliahung/` — click through
      every section, including the three Chinese `/post/` pages
- [ ] Search Console: export Performance → Pages, last 12 months (baseline)
- [ ] Screenshot the full Wix DNS panel (catch any record not listed below)
- [ ] Logged in as **jujuhung** on GitHub: profile Settings → Pages →
      Add a domain → `jujuhung.com`. Note the `_github-pages-challenge-jujuhung`
      TXT value
- [ ] Decide on analytics (GoatCounter / Plausible) — optional

## Launch day

Do it at a quiet time: the site and inbound email are down from the
nameserver switch until the records below are in.

1. [ ] GoDaddy → jujuhung.com → DNS → Nameservers → **Use default nameservers**
2. [ ] Delete GoDaddy's default Parked `@` A record and `www` CNAME
3. [ ] Add:

   | Type  | Name | Value | Priority |
   |-------|------|-------|----------|
   | A     | @    | 185.199.108.153 | |
   | A     | @    | 185.199.109.153 | |
   | A     | @    | 185.199.110.153 | |
   | A     | @    | 185.199.111.153 | |
   | CNAME | www  | jujuhung.github.io | |
   | MX    | @    | aspmx.l.google.com | 10 |
   | MX    | @    | alt1.aspmx.l.google.com | 20 |
   | MX    | @    | alt2.aspmx.l.google.com | 30 |
   | MX    | @    | alt3.aspmx.l.google.com | 40 |
   | MX    | @    | alt4.aspmx.l.google.com | 50 |
   | TXT   | @    | `v=spf1 include:_spf.google.com ~all` | |
   | TXT   | @    | `google-site-verification=Q58UPR_F6h95WFPE_zPv6-H41359y3UJeD3d9mdrsMs` | |
   | TXT   | _github-pages-challenge-jujuhung | (from GitHub) | |

4. [ ] Add a `CNAME` file to the repo root containing `www.jujuhung.com`, push
5. [ ] Repo Settings → Pages: DNS check passes → tick **Enforce HTTPS**
       (certificate can take up to 24h)
6. [ ] GitHub profile Settings → Pages → **Verify** the domain

## Verify

- [ ] `https://www.jujuhung.com` loads with a valid certificate
- [ ] `http://jujuhung.com` → `https://www.jujuhung.com/`
- [ ] Spot-check ~20 pages, images, the CV and press PDFs
- [ ] `/artwork/21g` forwards to `/artworks/21g/`; `/nope` shows the 404 page
- [ ] Email to `atelier@jujuhung.com` from an outside account arrives; reply goes out
- [ ] GoDaddy: auto-renew on, domain lock on

## SEO — launch day

- [ ] Search Console: add a **Domain** property if only URL-prefix exists
- [ ] Submit `https://www.jujuhung.com/sitemap.xml`
- [ ] URL Inspection → Request indexing: home, about, artworks, exhibitions,
      top ~6 pages from the baseline export
- [ ] Bing Webmaster Tools → Import from Google Search Console
- [ ] Rich Results Test: home, one artwork, one post
- [ ] Share previews: Facebook Sharing Debugger, LinkedIn Post Inspector
- [ ] Update Instagram bio and other profiles to the new URLs
- [ ] Ask galleries / press linking to old `/artwork/` URLs to update (nice to have)

## Weeks 1–8

- [ ] Weekly: Search Console → Pages. 404s on old Wix URLs are expected;
      a 404 on a page that should exist is not
- [ ] Weekly: Performance vs. baseline — 2–4 weeks of wobble is normal
- [ ] Wix plan: disconnect domain, keep plan ~4 weeks as fallback, then cancel
      (images are already archived in `_archive/originals/`)

## Later

- [ ] Lighter Selected Press PDF (currently 42 MB)
- [ ] Recompress the ~12 images over 500 KB (low priority)
