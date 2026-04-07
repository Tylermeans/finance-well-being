# Tools Setup
# Read this when: installing tools, starting a new project, or using Stitch/images/SEO for the first time.

---

## UI UX Pro Max (Design Intelligence)
Generates complete design systems — styles, colors, typography, anti-patterns.
Requires: Node.js + Python 3.x. No API key.

```bash
npm install -g uipro-cli
uipro init --ai claude
# Generates: .claude/skills/ui-ux-pro-max/

# Generate + persist design system for this project (run once per project)
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "[product type]" \
  --design-system --persist -p "[Project Name]"
# Output: design-system/MASTER.md + design-system/pages/
```

When building a page, tell Claude:
> "Read design-system/MASTER.md. Check design-system/pages/[page].md if it exists. Then build."

---

## Nano Banana 2 (Image Generation)
Google's Gemini 3.1 Flash Image model. Fast, 4K output, subject consistency.
Requires: `GEMINI_API_KEY` in `.env`  →  https://aistudio.google.com

```javascript
// Model: "gemini-3.1-flash-image-preview"
const res = await fetch(
  `https://generativelanguage.googleapis.com/v1beta/models/gemini-3.1-flash-image-preview:generateContent?key=${process.env.GEMINI_API_KEY}`,
  {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      contents: [{ parts: [{ text: "PROMPT HERE" }] }],
      generationConfig: { responseModalities: ["IMAGE", "TEXT"] }
    })
  }
);
```

Aspect ratio defaults: heroes → 16:9 | avatars → 1:1 | mobile social → 9:16
Resolution: minimum 1024px, prefer 2048px for landing pages.

---

## Google Stitch MCP (Design-to-Code Bridge)
Connects Stitch AI designs directly to Claude Code. Claude reads design HTML/CSS/tokens.
Requires: Google Cloud project with Stitch API enabled. Free to use.

```bash
# One-time setup (Google Cloud already authorized)
gcloud config set project YOUR_PROJECT_ID
gcloud beta services mcp enable stitch.googleapis.com --project=YOUR_PROJECT_ID
npx @_davideast/stitch-mcp init    # auto-writes MCP config to ~/.claude/mcp.json
```

```bash
# Workflow
npx @_davideast/stitch-mcp view --projects              # browse projects
npx @_davideast/stitch-mcp view --project <id> --screen <id>  # inspect a screen
npx @_davideast/stitch-mcp serve -p <project-id>        # local Vite preview server
```

```bash
# Optional Stitch skills
npx skills add google-labs-code/stitch-skills --skill react:components --global
npx skills add google-labs-code/stitch-skills --skill shadcn-ui --global
```

---

## Claude SEO Skill
Full technical audits, schema generation, Core Web Vitals, AI search optimization.
Requires: Python 3.8+. No API key for core features.

```bash
# Install (run once)
curl -fsSL https://raw.githubusercontent.com/AgriciDaniel/claude-seo/main/install.sh | bash
```

Commands (run inside `claude` CLI):
```
/seo audit https://[domain]        # full parallel audit
/seo technical https://[domain]    # Core Web Vitals + technical
/seo schema https://[domain]       # detect + validate + generate schema
/seo geo https://[domain]          # AI Overviews / GEO optimization
/seo plan [saas|local|ecommerce]   # strategic SEO plan
```

---

## Anthropic Official Skills
```bash
# Register + install via Claude Code (run once)
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

---

## 21st.dev Components
Community UI components, copy-paste ready. No account needed to browse.
→ https://21st.dev/community/components
When building UI: check here first for navigation, pricing tables, hero sections, card grids.

---

## Required .env Keys
```bash
GEMINI_API_KEY=          # Nano Banana 2 — https://aistudio.google.com
GOOGLE_CLOUD_PROJECT=    # Stitch MCP — your GCP Project ID (auth via gcloud, no key in env)
# Optional for live SEO data:
# AHREFS_API_KEY=
# SEMRUSH_API_KEY=
```
