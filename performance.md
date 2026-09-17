# Performance & Core Web Vitals — Findings

**Category score: not measured** — excluded from the health score rather than guessed.

Lab and field measurement (PageSpeed Insights, GTmetrix, CrUX, Lighthouse) could not be executed in this pass. Scoring this category from inference would put a made-up number in an audit report, which is worse than an honest gap. What follows is (a) everything about performance that *is* observable from the delivered markup, and (b) the exact procedure to close the gap.

---

## Observable, from the markup

### P1 — Four third-party counter widgets load on every page — HIGH

The footer of every page carries four links and their associated scripts from `livetrafficfeed.com`:

- Live Maps Visitor
- Website Counter
- Flag Counter
- Live Traffic Stats

These are visitor-counter widgets. They contribute nothing a user came for, they add a third-party origin to the critical path on every page load, and they are render-blocking unless explicitly deferred. On a site whose analytics need is already met by Google Analytics, this is pure cost.

**Fix:** Remove all four. This is the single largest performance win available and it takes minutes. Expect a measurable improvement in LCP and TBT.

### P2 — Per-testimonial requests to an external avatar API — MEDIUM

Each testimonial without a student photo triggers a request to `ui-avatars.com`. The carousel renders on every page with six visible slides. That is up to six extra cross-origin requests sitewide. See images findings I2.

### P3 — Heavy media on the homepage — MEDIUM

The homepage renders roughly **fifteen** YouTube thumbnails (six tutorial videos, three project videos, six testimonial demos) plus two full-size certificate JPEGs, three banner images and a logo. Without `loading="lazy"` and explicit dimensions this is a large above-and-below-fold payload with unreserved layout space.

### P4 — Carousels and accordions are layout-shift risks — MEDIUM

The homepage has a testimonial carousel, a banner rotator, a sticky announcement bar, a lightbox modal and a multi-category FAQ accordion with ~30 items. Each is a CLS source if it initialises after first paint without reserved height. The FAQ accordion in particular expands and collapses large blocks of content.

**Fix:** Reserve explicit `min-height` on the carousel and banner containers. Render FAQ answers collapsed via CSS `max-height` rather than by injecting DOM after load.

### P5 — Mobile usability: positive signals — INFO

`<meta name="viewport" content="width=device-width, initial-scale=1.0">` is correctly set on every page audited, and the markup shows a separate mobile navigation structure. The site is built responsively. Confirm tap-target spacing on the sticky bar, which packs nine links into one row.

---

## How to measure this properly — Day 2 procedure

**1. Field data (what real users experience — this is what Google ranks on).**

- Google Search Console → Experience → Core Web Vitals. This reads from CrUX. If the site has too little traffic, CrUX will report "insufficient data" — record that; it is a finding in itself.
- Run the homepage and `/digital-marketing-internship.php` through PageSpeed Insights. The top panel is field data, the bottom is lab. Report them separately; do not merge them.

**2. Lab data (reproducible, good for diagnosing).**

- PageSpeed Insights, mobile tab, three runs, record the median. Mobile first — the audience is students on phones.
- GTmetrix with the test location set to **Mumbai or Chennai**, not the default Vancouver. The server is in India and the audience is in India; a North American test location will produce misleading TTFB.

**3. Record these for each URL tested.**

| Metric | Good | Needs work | Poor |
|---|---|---|---|
| LCP — Largest Contentful Paint | ≤ 2.5 s | 2.5–4.0 s | > 4.0 s |
| INP — Interaction to Next Paint | ≤ 200 ms | 200–500 ms | > 500 ms |
| CLS — Cumulative Layout Shift | ≤ 0.1 | 0.1–0.25 | > 0.25 |
| TTFB | ≤ 800 ms | 0.8–1.8 s | > 1.8 s |

**Note on FID:** the original task brief asks for FID. Google retired First Input Delay on 12 March 2024 and replaced it with INP. Measure INP. Say so in the report — noticing that the brief is out of date is worth more than reporting a metric that no longer exists.

**4. Pages to test.** Homepage, `/digital-marketing-internship.php`, `/blog/index.php`, one blog post, `/register.php`. Five URLs is enough to characterise the site.

---

## Expected wins, in order of effort-to-impact

1. Remove the four livetrafficfeed widgets — minutes, high impact.
2. Add `width`, `height` and `loading="lazy"` to every image — hours, high CLS impact.
3. Replace `ui-avatars.com` with CSS initials — hours.
4. Convert `/uploads/` images to WebP with `srcset` — a day.
5. Reserve height on carousels and the FAQ accordion — a day.
6. Enable gzip/Brotli, set far-future cache headers on `/assets/`, and put static assets behind a CDN — a day, and it addresses TTFB, which is the metric most likely to be poor on shared PHP hosting.
