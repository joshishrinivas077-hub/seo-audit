# Technical SEO — Findings

**Target:** https://www.freeinternships.in/
**Audited:** 16 September 2026
**Pages inspected in depth:** homepage, `/blog/index.php`, `/free-online-digital-marketing-internship.php`, `/digital-marketing-internship.php`
**Category score: 45 / 100**

---

## T1 — Canonical tag points the main landing page at a different URL — CRITICAL

`/free-online-digital-marketing-internship.php` — the page linked from the primary navigation on every page of the site — declares:

```html
<link rel="canonical" href="https://www.freeinternships.in/digital-marketing-internship.php">
<meta property="og:url" content="https://www.freeinternships.in/digital-marketing-internship.php">
```

This instructs Google to drop the navigated URL from the index and consolidate all its signals onto a different page. Every internal link in the header and footer is therefore pointing at a URL the site itself has asked Google not to rank.

**Fix:** Decide which of the two URLs is the real Digital Marketing landing page. Set a self-referencing canonical on it, 301 the other to it, and update the navigation. Do not leave both live.

---

## T2 — Three parallel URL families for the same programs — CRITICAL

Three naming conventions for identical program intent are live simultaneously:

| Pattern | Where it is linked from | Example |
|---|---|---|
| `free-online-{topic}-internship.php` | Main header nav | `free-online-web-development-internship.php` |
| `free-{topic}-internship.php` | Footer "Free Internship Programs" | `free-web-development-internship.php` |
| `{topic}-internship.php` | Body cross-links, canonical targets | `video-editing-internship.php` |

Confirmed live and distinct for Digital Marketing: `/free-online-digital-marketing-internship.php` (task-list page, 42 tasks) and `/digital-marketing-internship.php` (curriculum page, 12-week syllabus). Both target the same head query. Same pattern is visible in the markup for Graphics Design, Video Editing, Web Development, Python Full Stack, Java Full Stack and AI & Data Science.

**Fix:** Pick one family. `free-{topic}-internship.php` is the shortest that still carries the primary keyword. 301 the other two families into it and merge the best content from each pair into a single page.

---

## T3 — The canonical target has no canonical tag and no social markup — HIGH

`/digital-marketing-internship.php` receives canonical authority from T1, but it ships with:

- no `rel=canonical` at all
- no `og:title` / `og:description` / `og:image` / `og:url`
- no `twitter:card`

So the consolidation destination is itself unanchored, and any share of that page renders with no card.

**Fix:** Add a self-referencing canonical and the full Open Graph and Twitter set to whichever URL survives T2.

---

## T4 — Header and footer link different URLs for the same program — HIGH

On every page, the header links `free-online-digital-marketing-internship.php` while the footer's "Free Internship Programs" block links `free-graphics-design-internship.php`, `free-video-editing-internship.php`, `free-web-development-internship.php`, etc. Sitewide internal link equity is being divided between two sets of destinations, and users clicking "Digital Marketing" from different parts of the page can land on different content.

**Fix:** One canonical URL per program, used in header, footer, body cross-links and sitemap.

---

## T5 — Inconsistent internal paths, likely 404s — MEDIUM

| Linked as | Linked from | Also seen as |
|---|---|---|
| `/project.php` | Header nav ("Intern Project") | `/projects.php` (homepage body, "View All Projects") |
| `/contact.php` | Homepage FAQ answer | `/contact-us.php` (footer) |

Both pairs cannot be correct. At least two sitewide links are pointing at a URL that either 404s or is an unintended duplicate.

**Fix:** Crawl with Screaming Frog, resolve the correct path for each, update the links, and 301 the loser.

---

## T6 — Blog assets loaded via path traversal — MEDIUM

The blog header loads the logo as `/blog/../assets/logo_1781240375.png`. It resolves, but it creates a second URL for the same asset, defeats cache reuse between the blog and the rest of the site, and is a symptom of hardcoded relative paths that will break if the blog moves.

**Fix:** Use root-relative paths (`/assets/logo_1781240375.png`) sitewide.

---

## T7 — Faceted blog URLs with no canonical — MEDIUM

`/blog/index.php` generates crawlable combinations of `?section=`, `?category=`, `?subcategory=`, `?cert_category=` and `?page=`, and carries no canonical tag. With 203 posts and five filter dimensions this multiplies into a large, low-value crawl surface on a site whose useful page count is in the low hundreds.

**Fix:** Self-referencing canonical on `/blog/index.php` pointing to the unfiltered URL; `rel="next"`/`rel="prev"` or a clean `/blog/page/2/` structure for real pagination; `noindex, follow` on filter combinations.

---

## T8 — robots.txt and XML sitemap not verified — OPEN

Neither `/robots.txt` nor `/sitemap.xml` could be retrieved with the tooling available in this pass, so their contents are unknown. This is a gap in the audit, not a finding against the site.

**Verify on Day 2:**
1. Open `https://www.freeinternships.in/robots.txt` in a browser. Confirm it returns 200, does not `Disallow: /`, and ends with a `Sitemap:` line containing the absolute sitemap URL.
2. Open the sitemap. Confirm every URL in it returns 200, uses the `https://www.` host, and matches the canonical family chosen in T2. Remove login, register, student-portal and filter URLs.
3. In Google Search Console → Indexing → Pages, record the counts for Indexed, "Duplicate, Google chose a different canonical", "Alternate page with proper canonical tag", and "Crawled — currently not indexed". T1 and T2 will show up here.

---

## What works

- The homepage is indexed and being crawled frequently — it surfaced in live search results with a crawl age of roughly one day.
- `https://www.` is used consistently as the host, and the homepage self-canonicalises correctly to `https://www.freeinternships.in/`.
- HTTPS is served across every page inspected.
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` is present on every page.
- `robots` meta on the homepage is well configured, including `max-snippet:-1` and `max-image-preview:large`.
- Geo meta (`geo.placename: Chennai, India`, `geo.region: IN-TN`) is set on the homepage, which is appropriate given the Chennai landing pages.
