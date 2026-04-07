# SEO Rules
# Read this when: adding new pages, optimizing performance, writing meta tags, or running audits.

---

## Every New Page Requires
- `<title>` — unique, under 60 chars
- `<meta name="description">` — 150–160 chars
- Open Graph tags: `og:title`, `og:description`, `og:image`, `og:url`
- `<link rel="canonical">` — always self-referencing
- Schema markup — see below

---

## Schema Markup (Minimum)
Every project needs at minimum:
```json
// WebSite schema (homepage)
{ "@type": "WebSite", "name": "...", "url": "..." }

// Organization schema (site-wide)
{ "@type": "Organization", "name": "...", "url": "...", "logo": "..." }
```

Page-type additions:
- Blog posts → `Article`
- Products → `Product` + `AggregateRating`
- Local biz → `LocalBusiness`
- SaaS → `SoftwareApplication`

Validate at: https://validator.schema.org

---

## Core Web Vitals Targets
```
LCP  < 2.5s   (Largest Contentful Paint)
INP  < 200ms  (Interaction to Next Paint — replaced FID March 2024)
CLS  < 0.1    (Cumulative Layout Shift)
```

---

## SEO Commands (run in `claude` CLI)
```bash
/seo audit https://[domain]          # run before every launch
/seo technical https://[domain]      # Core Web Vitals + technical checks
/seo schema https://[domain]         # validate schema markup
/seo geo https://[domain]            # AI Overviews / GEO (2026)
/seo page https://[domain]/[path]    # single page deep analysis
/seo plan [saas|local|ecommerce]     # strategic plan by business type
```

## MCP Integrations for Live Data (optional)
```bash
# Ahrefs
npx -y @ahrefs/mcp  # needs AHREFS_API_KEY

# Semrush, Google Search Console, PageSpeed
# See: https://github.com/AgriciDaniel/claude-seo/blob/main/docs/MCP-INTEGRATION.md
```
