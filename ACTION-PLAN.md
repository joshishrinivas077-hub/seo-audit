# Action Plan — FreeInternships.in

Ordered by impact-per-hour, not by category. Each item names the finding it closes.

**Priority definitions**
- **Critical** — blocks indexing, breaches platform policy, or actively misleads users. Fix now.
- **High** — significantly suppresses rankings or conversions. Fix within a week.
- **Medium** — real optimisation opportunity. Fix within a month.
- **Low** — backlog.

---

## Phase 1 — Critical fixes (Week 1)

| # | Action | Priority | Effort | Closes |
|---|---|---|---|---|
| 1 | Find and replace `freeinternsios.in` → `freeinternships.in` across the codebase. Check every `{topic}-internship.php` page — they share a template. | Critical | 15 min | C1 |
| 2 | **Decide the commercial model and state it identically everywhere.** Either remove every ₹499 reference, or add the fee to the homepage and rewrite the "no hidden charges" FAQ. Update the meta description either way. | Critical | 1 hr + a decision | C2 |
| 3 | Pick one URL family for program pages. Recommend `free-{topic}-internship.php`. 301 the other two families into it. Merge the best content from each pair — the task list from one, the curriculum from the other — into a single page. | Critical | 1 day | T1, T2 |
| 4 | Set a self-referencing canonical on every surviving program page. Add the full Open Graph and Twitter set to `/digital-marketing-internship.php`, which currently has neither. | Critical | 2 hrs | T1, T3 |
| 5 | Update header, footer and body cross-links to point at the single canonical URL per program. | Critical | 2 hrs | T4 |
| 6 | **Uncouple Google reviews from certificate issuance.** Remove the scripted review task and the star-rating instruction. Ask for feedback after the certificate is issued, unscripted. | Critical | 1 hr | F1 |
| 7 | Replace the daily link-posting requirement with a portfolio requirement: interns publish their project write-up on their own blog or LinkedIn. Same educational value, no link-scheme footprint. | Critical | 2 hrs | F1 |
| 8 | Reconcile the enrolment, certificate, domain-count and placement figures. One source of truth, rendered from one include, with an "as of" date. Delete any figure you cannot evidence. | High | 2 hrs | C3 |
| 9 | Remove the three static testimonials on `/digital-marketing-internship.php` naming Razorpay and Swiggy with LPA figures, or replace them with entries from the verified testimonial pipeline. | High | 1 hr | C5 |

**Then verify the gaps, in this order:**

| # | Action | Effort |
|---|---|---|
| 10 | Open `/robots.txt` and `/sitemap.xml`. Confirm 200s, no blanket disallow, `Sitemap:` directive present, every sitemap URL matches the new canonical family. | 30 min |
| 11 | Run PageSpeed Insights (mobile, 3 runs, median) and GTmetrix (location: Chennai or Mumbai) on five URLs. Record LCP, INP, CLS, TTFB. | 1 hr |
| 12 | Run the Rich Results Test and Schema Markup Validator on three URLs. Record what exists. | 30 min |
| 13 | Crawl with Screaming Frog. Confirm whether `/project.php`, `/projects.php`, `/contact.php` and `/contact-us.php` return 200 or 404. Fix the broken ones. | 1 hr |
| 14 | Connect Ahrefs Webmaster Tools or Moz free tier. Record DR/DA, referring domains, anchor distribution, toxic links. **Check specifically for a footprint of bare-URL anchors from social domains** — that would confirm F1 has already materialised. | 1 hr |

---

## Phase 2 — High-impact improvements (Weeks 2–3)

| # | Action | Priority | Effort | Closes |
|---|---|---|---|---|
| 15 | Rewrite the homepage title to ~60 chars and the description to ~155 chars. Suggested: *Free Online Internship with Certificate 2026 \| FreeInternships.in* | High | 30 min | O1 |
| 16 | Give the blog its own title and description. Add a self-referencing canonical to `/blog/index.php`. `noindex, follow` the filter combinations. | High | 2 hrs | O2, T7 |
| 17 | `noindex, follow` the 173 task-submission posts. Keep them live for students and the public portfolio; stop asking Google to index 173 variants of one sentence. | High | 1 hr | C4 |
| 18 | Delete the four `livetrafficfeed.com` footer widgets. Removes four third-party requests and four sitewide outbound links. | High | 15 min | P1, F3 |
| 19 | Remove `meta keywords` sitewide. It does nothing for rankings and signals over-optimisation. | Medium | 30 min | O3 |
| 20 | Add `width`, `height` and `loading="lazy"` to every image. Fixes the largest CLS source and defers ~15 homepage thumbnails. | High | 4 hrs | I3, P3 |
| 21 | Add `Organization` schema sitewide with `sameAs` for LinkedIn and YouTube. Add `FAQPage` to the homepage and program pages — ~57 FAQs already written. Add `BreadcrumbList` where breadcrumbs already render. | High | 1 day | Schema |
| 22 | Fix heading hierarchy: H1 → H2 → H3, no skipping. Remove emoji from `<title>`, `<h1>` and `<h2>`. | Medium | 4 hrs | O4, O5 |
| 23 | Filter the testimonial carousel by the page's domain. Digital Marketing pages currently show only Web Development testimonials. | Medium | 2 hrs | C6 |
| 24 | Replace `ui-avatars.com` calls with CSS-generated initials. | Medium | 2 hrs | I2 |
| 25 | Fix the empty `<img src="">` in the homepage lightbox. Suppress the zero-count blog category. De-duplicate featured and recent post queries. Restore the missing item 05. | Medium | 2 hrs | I1, C7, C8 |

---

## Phase 3 — Content and authority (Month 2)

| # | Action | Priority | Effort | Closes |
|---|---|---|---|---|
| 26 | **Build a roadmap hub.** Create `/roadmaps/`, link it from the main nav, cross-link each of the 25 roadmap articles to its program page and back. This activates the site's best existing content for half a day of work. | High | 1 day | Gap 4 |
| 27 | **Get listed in the roundup articles that already rank.** Outreach to theinternship.in, traffictail.com, thevistaacademy.com, internshipgate.com and internshipuncle.in. These sites publish "free internship with certificate" listicles that rank for your buyers' queries and do not mention you. Cheapest, highest-relevance traffic available. | High | 1 week | Tier 3 gap |
| 28 | Write the comparison content nobody in the tier has: *How to Verify an Internship Certificate*, *Are Online Internship Certificates Recognised by Employers?*, *Free Internship vs Paid Internship*. These turn the verification tool into a linkable asset. | High | 2 weeks | Gap 1, F4 |
| 29 | Build branch landing pages beyond CSE: ECE, IT, MCA, BCA, MBA, Mechanical. Only where there is genuinely distinct content. | Medium | 2 weeks | Gap 2 |
| 30 | Pitch the certificate verification tool to college placement cells (`.ac.in` domains) and HR blogs. High-relevance, high-trust links, reachable through students you already have. | Medium | Ongoing | F4 |
| 31 | Create and link Instagram, Facebook and X profiles. Add all `sameAs` links to `Organization` schema. State the FreeInternships.in / Data Alcott Systems relationship explicitly on the About page. | Medium | 1 day | F2 |
| 32 | Add `Course` and `EducationalOccupationalCredential` schema. **Only after item 2** — `isAccessibleForFree` cannot be set honestly until the price question is settled. | Medium | 1 day | Schema |
| 33 | City pages beyond Chennai — Pune, Bangalore, Hyderabad, Delhi. Only with genuinely local substance. Near-identical city pages are doorway pages and will be penalised. | Low | 3 weeks | Gap 3 |
| 34 | Add seasonal content: summer internship 2026, winter internship, final-year internship. Publish ahead of each cycle. | Low | Ongoing | Gap 5 |

---

## Phase 4 — Monitoring (Ongoing)

| # | Action | Cadence |
|---|---|---|
| 35 | GSC → Indexing → Pages. Watch "Duplicate, Google chose a different canonical" fall as Phase 1 lands. This is the primary success metric for items 3–5. | Weekly for 8 weeks |
| 36 | GSC → Performance. Track impressions, clicks and average position for `free internship with certificate`, `free digital marketing internship`, `online internship with certificate`. | Weekly |
| 37 | Core Web Vitals in GSC. Confirm the Phase 2 image and third-party fixes moved field LCP and CLS. | Monthly |
| 38 | Google Business Profile review count and rating. **Watch for bulk removals** — that would confirm the incentivised-review risk materialised. | Monthly |
| 39 | Referring domains and anchor-text distribution in Ahrefs. Confirm the bare-URL social footprint stops growing after item 7. | Monthly |
| 40 | Re-run this full audit. | Quarterly |

---

## If only one day is available

Items **1, 2, 6, 15 and 18**. Under three hours of work plus one commercial decision, and they close two of the five critical findings and the biggest performance drag. Everything else can wait; those cannot.
