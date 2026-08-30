# Canonical Domain Setup — taxservicesjerseycity.com (non-www, HTTPS)

Your `CNAME` file (`taxservicesjerseycity.com`) confirms this site is hosted on
**GitHub Pages**. That determines exactly what you need to do.

## 1. HTTP → HTTPS redirect

GitHub Pages handles this automatically once "Enforce HTTPS" is checked.

**Action required:** Go to your repo → **Settings → Pages** → confirm the
"Enforce HTTPS" checkbox is checked. If it's greyed out, wait — it usually
takes a few minutes to a few hours to become available after a custom domain
is verified, then check it.

## 2. www → non-www redirect

GitHub Pages automatically 301-redirects `www.taxservicesjerseycity.com` to
`taxservicesjerseycity.com` **only if**:
- Your CNAME file contains the apex domain (`taxservicesjerseycity.com`) —
  ✅ already correct.
- Your DNS has a `CNAME` record for `www` pointing to
  `<your-github-username>.github.io`, **and** the required `A`/`ALIAS`
  records for the apex domain are set per GitHub's custom domain docs.

**Action required:** In your domain registrar / DNS provider, confirm:
- `www` → CNAME → `<username>.github.io`
- apex (`@`) → A records → GitHub Pages' current IPs (see GitHub's
  "Managing a custom domain" docs for the current list)

Once both are correct and "Enforce HTTPS" is on, GitHub Pages serves the
apex domain and 301-redirects both `http://` and `www` variants into it
automatically — no `.htaccess` needed.

## 3. If you ever move off GitHub Pages

This zip includes two ready-to-use fallback redirect files that do nothing
on GitHub Pages but will work immediately if you migrate:
- `.htaccess` — for Apache-based hosting
- `_redirects` — for Netlify (and Netlify-compatible platforms)

## 4. Google Search Console

GSC no longer has a "preferred domain" setting — it infers the canonical
version from your `<link rel="canonical">` tags, your sitemap, and your
redirects (all of which are now consistently non-www HTTPS across this
site).

**Action required:**
1. In GSC, add/verify a property for `https://taxservicesjerseycity.com`
   (URL-prefix property, not the Domain property, so it stays scoped to the
   exact canonical version).
2. If you previously had a separate GSC property for the `www` version or
   for `http://`, leave it added (don't delete it) — you'll use it once to
   confirm those variants are now redirecting, then you can stop monitoring
   it. Do **not** try to merge properties; GSC doesn't support that.
3. Submit `https://taxservicesjerseycity.com/sitemap.xml` under
   **Sitemaps** in the non-www property.
4. Under **Settings → Crawl stats**, check that Google isn't reporting
   crawl errors on `www` or `http` URLs going forward — a few redirected
   hits are expected and fine; persistent 404s or timeouts are not.
5. Use **URL Inspection** on a few key pages (homepage, the two new money
   pages) to confirm Google sees the correct canonical URL and can index
   them once live.

## 5. Removed from the site during this update

`custom-trade-show-booth-design.html` was deleted. It was an unrelated
page from a different site (canonical pointed to
`tradeshowboothdesigner.com`), not linked from anywhere in your site, and
not in your sitemap — almost certainly a stray file from a template or
another project accidentally included in this export. Off-topic content
like this dilutes topical relevance for a niche local-service site and is
worth keeping out.
