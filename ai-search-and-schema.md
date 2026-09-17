# AI Search Readiness — Findings

**Category score: 45 / 100**

Students increasingly ask ChatGPT, Gemini, Perplexity and Google's AI Overviews "what's a good free internship with certificate in India?" rather than typing it into a search box. Being *citable* by those systems is a distinct discipline from ranking, and it rewards different things: unambiguous facts, verifiable claims, clean structure.

## A1 — Contradictory facts make the site uncitable — HIGH

This is the finding that matters most here, and it is the same evidence as content.md C1–C3 viewed through a different lens.

An AI system reading this site to answer "is FreeInternships.in free?" encounters:

- the homepage saying there is no registration fee,
- the homepage FAQ saying there are no hidden charges,
- and a program page saying registration is ₹499,

and it encounters the brand's own domain written as **freeinternsios.in** on that same program page. It will either refuse to state a price, hedge, or state the wrong domain. It will also register the source as internally inconsistent, which suppresses citation.

The same applies to the enrolment figure: 25,000+ on one page, 10,000+ on another. There is no way to extract a confident fact.

**Fix:** Resolve C1, C2 and C3. They are three find-and-replace-scale edits and they are the highest-leverage work in this entire audit, for AI visibility and for human trust alike.

## A2 — The FAQ corpus is a strong, underexploited asset — OPPORTUNITY

The site carries roughly **30 FAQs on the homepage and 27 more** on the Digital Marketing task page, covering exactly the questions students ask: eligibility, cost, duration, how tasks are assigned, why submissions get rejected, how certificates are verified, whether beginners can apply.

This is question-and-answer content in the format AI systems prefer to cite. It is currently trapped inside JavaScript accordions with unverified structured data.

**Fix:** Confirm the answers render in the initial HTML (not injected on click). Mark them up with `FAQPage` schema. Then publish the highest-intent ones as standalone articles so they can be cited independently of the page they sit on.

## A3 — No `llms.txt` — LOW

Not present, or not verifiable in this pass. A simple `/llms.txt` summarising what the site offers, in what domains, at what cost, with links to the key pages, is low effort. It is not a ranking factor and no major system commits to reading it, but on a site whose core problem is ambiguous facts, writing the facts down in one authoritative place has value regardless of who reads it.

## A4 — Verify AI crawler access — OPEN

Confirm `robots.txt` does not block `GPTBot`, `ClaudeBot`, `PerplexityBot`, `Google-Extended` or `CCBot` unless that is a deliberate decision. Blocking them removes the site from AI answers entirely.

---

# Structured Data — Findings

**Category score: not verified** — excluded from the health score.

JSON-LD blocks could not be inspected with the tooling available in this pass, so no claim is made about what schema exists. Verify before acting.

## Day 2 verification procedure

1. Run the homepage, `/digital-marketing-internship.php` and one blog post through the **Rich Results Test** (search.google.com/test/rich-results) and the **Schema Markup Validator** (validator.schema.org).
2. Record which types are detected and any errors or warnings.
3. Cross-check against Google Search Console → Enhancements, which reports schema Google has actually processed.

## Schema this site should have, ranked by value

| Type | Where | Why it matters here |
|---|---|---|
| `Organization` | Sitewide | Ties FreeInternships.in to Data Alcott Systems, with `sameAs` links to LinkedIn and YouTube. Directly addresses the split-identity problem in offpage.md F2. |
| `FAQPage` | Homepage, program pages | ~57 existing FAQs. Highest-value, lowest-effort win available. |
| `Course` | Each program page | `name`, `description`, `provider`, `courseMode: online`, `timeRequired`, `isAccessibleForFree`. **Note:** `isAccessibleForFree` cannot be set honestly until the ₹499 contradiction is resolved. |
| `EducationalOccupationalCredential` | Certificate and verification pages | Describes the certificate as a real credential with a verification URL. Nobody in the competitive tier has this. |
| `BreadcrumbList` | Program pages | Breadcrumbs are already rendered on `/digital-marketing-internship.php` but not marked up. |
| `VideoObject` | Tutorial and project videos | ~15 YouTube embeds on the homepage alone, none described to search engines. |
| `Review` / `AggregateRating` | Testimonials | **Do not implement until content.md C5 is resolved.** Marking up unverifiable testimonials as structured review data converts a credibility problem into a structured-data policy violation. |

## One warning

Structured data describes what is on the page. It does not fix what is on the page. Adding `Course` schema with `isAccessibleForFree: true` to a page that says ₹499 makes the contradiction machine-readable. Fix the content first, then mark it up.
