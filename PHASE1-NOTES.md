# Phase 1 deploy notes

Upload every file in this folder to the site root, overwriting the existing ones (41 files: 7 owner/contact pages, homepage, sitemap, and 32 other pages whose footer link text changed).

## What changed
- Titles, meta descriptions, og/twitter titles and JSON-LD names rewritten for the 6 cluster-owner pages plus contact:
  tax-preparation-jersey-city, tax-accountant-jersey-city, tax-planning-tax-consulting-new-jersey, bookkeeping-services-jersey-city, business-tax-preparation-new-jersey, tax-preparation-cost-jersey-city, contact.
- H1s updated on the accountant, tax-consultant and business-tax pages so each carries its target keyword.
- Footer link (all pages): "Jersey City" -> "Jersey City Tax Accountant" so the accountant page gets a keyword anchor instead of a generic one.
- Homepage: one sentence now links the accountant, tax-consultant and bookkeeping pages with keyword anchors.
- Contact page: new "Choose the service you need" section linking all 6 owner pages, so Google can route to service pages instead of contact.
- sitemap.xml: lastmod set to 2026-11-24 for edited pages.
- Homepage title and meta left unchanged on purpose (it already ranks ~6.4 for "tax services jersey city").

## Not fixable in these files (do at host/DNS level)
1. Redirect www.taxservicesjerseycity.com and http:// to https://taxservicesjerseycity.com with a 301. The _redirects file only works on Netlify; GSC shows www/http URLs getting impressions.
2. Then in Search Console: request indexing for the 7 changed pages, and run URL Inspection on cannabis-tax-accountant-jersey-city.html (zero impressions in 3 months).
3. Re-export GSC (Queries + Pages, plus a query-by-page view) in 4-6 weeks to measure position changes.
