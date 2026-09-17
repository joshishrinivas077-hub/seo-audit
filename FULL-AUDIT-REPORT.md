# SEO Audit — FreeInternships.in

**Task:** DM-SEO-001 · Complete SEO Audit of FreeInternships.in
**Client:** Data Alcott Systems, Chennai
**Audit date:** 16 September 2026
**Scope:** Technical, on-page, off-page, competitor analysis
**Method:** Live inspection of rendered pages and delivered head markup, plus SERP research. Tool-dependent measurements (Core Web Vitals, backlink metrics, structured-data validation) are documented with procedures rather than estimated.

---

## SEO Health Score: 47 / 100 — Needs Work

Scored on the five categories that could be verified in this pass, reweighted to 100%. Two categories are deliberately unscored rather than guessed.

| Category | Weight | Score | Status |
|---|---|---|---|
| Content Quality & E-E-A-T | 23% | **38** | Critical issues |
| Technical SEO | 22% | **45** | Critical issues |
| On-Page SEO | 20% | **55** | Needs work |
| AI Search Readiness | 10% | **45** | Needs work |
| Images | 5% | **70** | Good |
| Performance (Core Web Vitals) | 10% | *not measured* | Procedure in `findings/performance.md` |
| Structured Data | 10% | *not verified* | Procedure in `findings/ai-search-and-schema.md` |

**Why two categories are unscored.** Lighthouse, CrUX, Ahrefs and the Rich Results Test were not available in this pass. Putting a plausible-looking number against an unmeasured category is the most common way audit reports mislead. Both gaps are closeable in about an hour each, and each finding file contains the exact steps.

---

## The one-paragraph summary

FreeInternships.in is not suffering from a technical SEO problem in the usual sense. It is indexed, it is crawled daily, it is on HTTPS, it is responsive, its keyword targeting is well matched to what students actually search, and it owns a differentiator — QR-verified, publicly checkable certificates — that none of its direct competitors have. What it is suffering from is **self-inflicted ambiguity**: three different URL families for the same pages, a canonical tag that points the main navigation's landing page at a different URL, a program page that calls the brand *freeinternsios.in*, and a "₹499 registration" on a site whose entire proposition and domain name is that it is free. Fix the contradictions and the site gets substantially better without a single line of performance optimisation.

---

## Top 5 critical issues

### 1. The site contradicts itself on price

`/digital-marketing-internship.php` states "One-Time Registration Fee ₹499 only" — in the ribbon, in the stat block, in a testimonial, and in the meta description that appears in search results. The homepage states "100% Free Online Internship – No Registration Fee" and its FAQ states "there are no hidden charges."

On a domain called **freeinternships.in**.

This costs conversions, costs trust, costs AI citability, and is the first thing a Google quality rater would notice. → `findings/content.md` C2

### 2. A live page uses the wrong domain name, eight or more times

`/digital-marketing-internship.php` refers to the brand as **freeinternsios.in** throughout — in headings, body copy, FAQ answers and CTAs. Any brand recognition that page builds accrues to a domain that does not exist. → `findings/content.md` C1

### 3. The main navigation's landing page is canonicalised to a different URL

`/free-online-digital-marketing-internship.php` — linked from the header on every page of the site — carries `rel=canonical` pointing at `/digital-marketing-internship.php`. Every internal link in the header points at a URL the site has asked Google not to index. → `findings/technical.md` T1

### 4. Three URL families compete for the same keywords

`free-online-{topic}-internship.php` (header), `free-{topic}-internship.php` (footer), and `{topic}-internship.php` (cross-links and canonical targets) all exist simultaneously. Header and footer link *different URLs for the same program*. Internal link equity is split three ways across every program. → `findings/technical.md` T2, T4

### 5. The program instructs interns to build links and reviews in ways that breach platform policy

Interns are required, as a condition of receiving their offer letter and certificate, to post a scripted five-star Google Maps review and to post a link to the site across four social platforms six days a week. Incentivised reviews breach Google's review policies; certificate-gated link posting at volume is link-scheme territory. The risk falls partly on the interns' personal accounts. → `findings/offpage.md` F1

---

## Top 5 quick wins

Each of these is hours, not days, and each moves a real metric.

1. **Find and replace `freeinternsios.in` → `freeinternships.in`.** Minutes. Removes a critical E-E-A-T failure.
2. **Rewrite the homepage title from 137 characters to ~60.** Minutes. Everything after "Job Assistance" is currently invisible in the SERP.
3. **Delete the four `livetrafficfeed.com` widgets from the footer.** Minutes. Removes four third-party requests and four sitewide outbound links from every page. Biggest single performance win available.
4. **Add `noindex, follow` to the 173 templated task-submission blog posts.** One template edit. Removes 85% of the blog's near-duplicate footprint while keeping the pages useful to students.
5. **Add `FAQPage` schema to the ~57 existing FAQs.** A few hours. The content is already written and genuinely good; it just isn't marked up.

---

## Findings by category

Full evidence, reasoning and fixes are in the `findings/` directory.

| File | Covers |
|---|---|
| `findings/technical.md` | Canonicals, URL architecture, internal paths, faceted blog URLs, robots/sitemap verification procedure |
| `findings/content.md` | Brand misspelling, price contradiction, statistic conflicts, 173 duplicate blog posts, unverifiable testimonials |
| `findings/onpage.md` | Title and meta inventory, heading hierarchy, keyword stuffing, internal linking, image optimisation |
| `findings/performance.md` | Observable performance issues plus the full Core Web Vitals measurement procedure |
| `findings/offpage.md` | Link scheme and review policy risk, brand entity signals, linkable assets, backlink audit procedure |
| `findings/competitors.md` | Three-tier competitive set, differentiator matrix, five keyword gaps |
| `findings/ai-search-and-schema.md` | AI citability, schema priority list, validation procedure |

---

## What is genuinely working

An audit that only lists problems is not an audit. These are real strengths and the recommendations are built to protect them.

- **Indexation and crawl health are fine.** The homepage appeared in live search results with a crawl age of roughly one day. Whatever else is wrong, Google is paying attention.
- **Keyword targeting reflects real student language.** `free internship with certificate`, `work from home internship`, `internship for CSE students`, `free internship Chennai`. Somebody understood the audience.
- **The FAQ corpus is exceptional** — roughly 57 questions across two pages, covering exactly what students ask, including uncomfortable ones like why submissions get rejected.
- **The certificate verification mechanism is a genuine competitive moat.** A public, QR-verified registry where recruiters can check a certificate ID is something no direct competitor offers. It is currently mentioned in passing.
- **Alt text is descriptive** where it matters, which is unusual on a site of this type.
- **One H1 per page**, every page audited, with H1s written in query language rather than branding.
- **The 25 roadmap articles are real content** — differentiated, useful, and entirely orphaned in a blog sidebar.
- **HTTPS, correct viewport, correct host canonicalisation, well-configured robots meta** on the homepage.

---

## Method and limitations — read this before relying on the numbers

**What was verified directly:** rendered page content, `<head>` markup (titles, meta descriptions, canonicals, Open Graph, robots directives, keywords), heading structure, internal link targets, image sources and alt attributes, third-party resource origins, and blog post counts as reported by the site's own index — for the homepage, `/blog/index.php`, `/free-online-digital-marketing-internship.php` and `/digital-marketing-internship.php`. Competitive landscape verified via live SERP research.

**What was not verified, and why it is marked as such rather than estimated:**

| Gap | Reason | How to close it |
|---|---|---|
| `robots.txt`, `sitemap.xml` contents | Not retrievable with the tooling in this pass | Open both in a browser; check GSC → Sitemaps |
| Core Web Vitals, field and lab | No Lighthouse or CrUX access | PageSpeed Insights + GTmetrix (set location to Chennai/Mumbai) |
| JSON-LD structured data | Script blocks not inspectable | Rich Results Test + Schema Markup Validator |
| Backlinks, DR/DA, anchor text | No Ahrefs or Moz access | Ahrefs Webmaster Tools (free) or Moz free tier |
| 404 confirmation for `/project.php` vs `/projects.php`, `/contact.php` vs `/contact-us.php` | Status codes not retrievable | Screaming Frog crawl, 500-URL free tier is sufficient |
| Full-site crawl beyond four pages | Tooling constraint | Screaming Frog, then re-run this audit's checks at scale |

**On FID:** the task brief asks for First Input Delay. Google retired FID on 12 March 2024 and replaced it with Interaction to Next Paint (INP). Measure INP.

---

*Prepared as internship task DM-SEO-001 for Data Alcott Systems. Findings are based on the site as delivered on 16 September 2026 and will drift as the site changes.*
