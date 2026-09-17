# On-Page SEO — Findings

**Category score: 55 / 100** — targeting is sound, formatting and hygiene are not.

---

## Title tags and meta descriptions, as they exist today

| URL | Title | Length | Verdict |
|---|---|---|---|
| `/` | Free Internship online with Certificate & Job Assistance \| Real-Time Project Based Online Internship in India \| Work From Home | ~137 chars | Truncates at ~60. Three clauses competing. |
| `/free-online-digital-marketing-internship.php` | 100% Free Online Digital Marketing Internship with Certificate \| 11 Domains | ~74 chars | Close. Trim the suffix. |
| `/digital-marketing-internship.php` | Free Digital Marketing Internship with Certificate \| Online Work From Home | ~73 chars | Good. |
| `/blog/index.php` | DATA ALCOTT SYSTEMS - Professional Internship Platform | ~53 chars | Says nothing about the blog. |

| URL | Meta description | Length | Verdict |
|---|---|---|---|
| `/` | "Free internship 2026 — online internship with certificate, 1–6 months, real-time projects, official certificate & job placement. Best free internship for students in India. Python, AI, Data Science, Free Digital Marketing internship" | ~230 chars | Truncates. Ends in a keyword list, not a sentence. |
| `/digital-marketing-internship.php` | "...job assistance. Register ₹499 only." | ~250 chars | Contradicts the homepage — see C2. |
| `/blog/index.php` | "Free task-based online internship program with DATA ALCOTT SYSTEMS" | ~66 chars | Generic; shared across every faceted blog URL. |

---

## O1 — Homepage title is ~137 characters — HIGH

Google will render roughly the first 60. Everything after "Job Assistance" is invisible in the SERP while still diluting the page's topical focus.

**Rewrite to:**
`Free Online Internship with Certificate 2026 | FreeInternships.in` (64 chars)

**And the description to:**
`Free online internship with certificate — 15 days to 6 months, real projects, mentor-evaluated, QR-verified certificate. Apply free from anywhere in India.` (~154 chars)

---

## O2 — The blog has no SEO identity — HIGH

Title and description are the company boilerplate, and because `/blog/index.php` has no canonical, every `?section=` and `?category=` combination inherits the same pair. A 203-post blog with 25 genuinely strong roadmap articles is presenting itself to Google as one undifferentiated page.

**Fix:** Give the blog index its own title and description. Give each category view a templated but distinct pair, e.g. `Career Tips for Interns — Roadmaps & Guides | FreeInternships.in`.

---

## O3 — Keyword stuffing in meta keywords — MEDIUM

Every page carries a `meta keywords` tag. The homepage's contains 21 phrases; `/digital-marketing-internship.php` carries 12, several of which are near-identical restatements ("free digital marketing internship", "free digital marketing internship with certificate", "free digital marketing internship 2026", "digital marketing internship free online 2026").

Google has ignored this tag since 2009. It does nothing for rankings, and it hands any manual reviewer a clear over-optimisation signal.

**Fix:** Remove the tag sitewide. Move the intent it captures into H2s and body copy where it earns something.

---

## O4 — Heading hierarchy skips levels — MEDIUM

The homepage goes `H1` → `H4` ("Instant Offer Letter Within 24 Hours") before its first `H2`, then uses `H4` for feature cards nested under `H2` sections with no intervening `H3`. `/free-online-digital-marketing-internship.php` places an `H4` ("100% Free Online Digital Marketing Internship with Certificate") above its first `H2`.

This degrades the document outline that both screen readers and Google's passage extraction rely on.

**Fix:** One H1. Section headings H2. Cards and sub-blocks H3. No skipping.

---

## O5 — Emoji in H1 and title tags — MEDIUM

`<h1>🎯 100% Free Online Digital Marketing Internship</h1>`. Google strips most emoji from SERP display, so the character is a wasted first token in the most important on-page element. The task-list page also opens headings with 🔍, ✍️, 📱, ✉️, 📊, 💰, 🏷️, 🎬, 🖌️, 🤝, ⭐.

**Fix:** Keep emoji in body UI where they aid scanning. Remove them from `<title>`, `<h1>` and `<h2>`.

---

## O6 — Title and og:title diverge — LOW

On `/free-online-digital-marketing-internship.php` the `<title>` ends "| 11 Domains" and the `og:title` does not. Minor, but it means the shared card and the SERP tell different stories.

---

## Internal linking

- Header and footer link **different URLs for the same program** (see technical.md T4). This is the biggest internal-linking problem on the site.
- The 25 roadmap articles — the best content asset — are reachable only from the blog index and its sidebar. They are not linked from any program page.
- **Opportunity:** link each roadmap article from the matching program page, and each program page from the matching roadmap article. That is ten high-relevance internal links that cost nothing and connect commercial pages to informational ones.
- Duration pages (`15-days-`, `1-month-`, `2-month-`, `3-month-`, `6-month-internship.php`) are linked from the homepage sticky bar but not cross-linked to each other or to program pages.

---

## What works

- Every page audited has exactly **one** H1.
- Program-page H1s use real query language rather than branding: "Free Digital Marketing Internship with Certificate — Online | Work From Home 2026".
- Keyword targeting is well matched to genuine long-tail intent — `free internship with certificate`, `work from home internship`, `internship for CSE students`, `free internship Chennai`. The site understands what its students actually type.
- The footer's "Popular Internship Pages" block is a well-constructed hub of long-tail landing pages.
- `og:image` and `twitter:card` are correctly set on the homepage.

---

# Images — Findings

**Category score: 70 / 100** — the strongest area.

## What works

- Alt text is present and genuinely descriptive on the images that matter: `"Official internship confirmation certificate 2026 with student name and domain"`, `"Official internship completion certificate 2026 showing successful program completion"`, and blog thumbnails that carry the post title.
- The logo is correctly alt-texted and wrapped in a link to the homepage on every page.
- YouTube thumbnails are served from `img.youtube.com` at `mqdefault`/`hqdefault` rather than full resolution — a sensible choice.

## I1 — Empty image source in the homepage lightbox — MEDIUM

The homepage renders a lightbox node as `<img alt="Enlarged image" src="">`. An empty `src` causes the browser to re-request the page URL as an image. Populate it on open or render the node only when a modal is triggered.

## I2 — Testimonial avatars are third-party API calls — MEDIUM

Students without an uploaded photo get an avatar from `ui-avatars.com/api/?name=...`. Every carousel slide without a photo is an additional DNS lookup, TLS handshake and request to an external host, on every page that renders the carousel — which is every page. Generate initials-avatars in CSS instead. Zero requests, no third-party dependency.

## I3 — No image optimisation pipeline — MEDIUM

Student photos are served straight from `/uploads/` as original `.jpeg` / `.png`, and the certificate samples as full-size `.jpg`. There is no evidence of WebP/AVIF, of responsive `srcset`, or of dimension attributes.

**Fix:** Convert to WebP with a JPEG fallback, generate 2–3 widths with `srcset`, set explicit `width`/`height` on every `<img>` to reserve layout space, and add `loading="lazy"` to everything below the fold. The width/height attributes alone will improve CLS.
