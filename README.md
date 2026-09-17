# SEO Audit — FreeInternships.in

Internship task **DM-SEO-001** · Digital Marketing · Data Alcott Systems
Audited **16 September 2026**

**SEO Health Score: 47 / 100 — Needs Work**

---

## What this is

A full SEO audit of https://www.freeinternships.in/ covering technical SEO, on-page SEO, content quality, off-page and backlink strategy, AI search readiness, and competitor analysis — with a prioritised, costed action plan.

Every finding is evidenced from the live site. Where a measurement could not be taken with the tools available, the category is marked unmeasured and the procedure to take it is documented, rather than a plausible-looking number being invented.

## The headline

The site is indexed, crawled daily, responsive, and targets exactly the queries its students search. Its problem is self-inflicted ambiguity:

1. The homepage says the internship is free. `/digital-marketing-internship.php` says registration is ₹499 — including in its meta description, which renders in the search result.
2. That same page calls the brand **freeinternsios.in**, eight or more times.
3. The Digital Marketing page linked from the header canonicalises to a *different* URL.
4. Three URL families for the same programs are live at once; header and footer link different ones.
5. The program requires interns to post scripted five-star reviews and daily backlinks as a condition of certificate issuance.

Fix the contradictions and the site improves substantially without a single line of performance work.

## Files

| File | What's in it |
|---|---|
| [`FULL-AUDIT-REPORT.md`](FULL-AUDIT-REPORT.md) | Executive summary, health score, top 5 critical issues, top 5 quick wins, method and limitations |
| [`ACTION-PLAN.md`](ACTION-PLAN.md) | 40 prioritised actions across 4 phases, with effort estimates and the finding each closes |
| [`seo-audit-report.html`](seo-audit-report.html) | Visual report — score chart, evidence panels, roadmap |
| [`audit-data.json`](audit-data.json) | Structured findings envelope for downstream tooling |
| [`findings/technical.md`](findings/technical.md) | Canonicals, URL architecture, internal paths, faceted blog URLs |
| [`findings/content.md`](findings/content.md) | Brand misspelling, price contradiction, statistic conflicts, 173 duplicate posts, testimonials |
| [`findings/onpage.md`](findings/onpage.md) | Title/meta inventory, headings, keyword stuffing, internal linking, images |
| [`findings/performance.md`](findings/performance.md) | Observable performance issues + full Core Web Vitals measurement procedure |
| [`findings/offpage.md`](findings/offpage.md) | Link-scheme and review-policy risk, brand entity signals, linkable assets |
| [`findings/competitors.md`](findings/competitors.md) | Three-tier competitive set, differentiator matrix, five keyword gaps |
| [`findings/ai-search-and-schema.md`](findings/ai-search-and-schema.md) | AI citability, schema priority list, validation procedure |

## Scoring

| Category | Weight | Score |
|---|---|---|
| Content Quality & E-E-A-T | 23% | 38 |
| Technical SEO | 22% | 45 |
| On-Page SEO | 20% | 55 |
| AI Search Readiness | 10% | 45 |
| Images | 5% | 70 |
| Performance (Core Web Vitals) | 10% | not measured |
| Structured Data | 10% | not verified |

Score computed on the five verified categories (80% of total weight), reweighted to 100.

## Method

Live inspection of rendered page content and delivered `<head>` markup for the homepage, `/blog/index.php`, `/free-online-digital-marketing-internship.php` and `/digital-marketing-internship.php`, plus live SERP research for the competitive analysis.

**Not performed in this pass, and marked as such throughout:** Lighthouse/CrUX measurement, JSON-LD validation, backlink metrics, and a full-site crawl. Each finding file contains the exact procedure to close its gap.

**A note on the brief:** the task specification asks for FID. Google retired First Input Delay on 12 March 2024 and replaced it with INP. This audit measures against INP.

## Remaining work before submission

- [ ] Run PageSpeed Insights and GTmetrix on 5 URLs; screenshot and add to `screenshots/`
- [ ] Verify `robots.txt` and `sitemap.xml`; screenshot
- [ ] Run the Rich Results Test; record what schema exists
- [ ] Connect Ahrefs Webmaster Tools; export the backlink profile
- [ ] Crawl with Screaming Frog; confirm the suspected 404s
- [ ] Fill the competitor metrics table in `findings/competitors.md`
- [ ] Record the demo video
- [ ] Publish the blog post linking the repo, report and video

---

*Prepared by an intern on the Data Alcott Systems free Digital Marketing internship program.*
