# SETUP.md — New Project Quickstart
# For humans. Claude doesn't need to read this.
# Run through this once when starting a new project.

---

## Step 1 — Fill in Project Config
Open `CLAUDE.md` and update the Project block at the top:
```
Name    : Your App Name
Type    : SaaS / Landing Page / Dashboard / etc.
Stack   : Next.js / React / Vue / etc.
Domain  : yourapp.com
```
That's the only file you edit per project. Everything else is pre-wired.

---

## Step 2 — One-Time Machine Setup
Only do this once per machine, not per project.

**UI UX Pro Max (design intelligence)**
```bash
npm install -g uipro-cli
```
Requires Python 3.x — check with `python3 --version`. If missing:
- Mac: `brew install python3`
- Ubuntu: `sudo apt install python3`
- Windows: `winget install Python.Python.3.12`

**Claude SEO**
```bash
# Mac/Linux
curl -fsSL https://raw.githubusercontent.com/AgriciDaniel/claude-seo/main/install.sh | bash

# Windows
irm https://raw.githubusercontent.com/AgriciDaniel/claude-seo/main/install.ps1 | iex
```

**Google Stitch MCP**
```bash
# Install gcloud CLI if you don't have it
# → https://cloud.google.com/sdk/docs/install

gcloud auth login
gcloud config set project YOUR_GCP_PROJECT_ID
gcloud beta services mcp enable stitch.googleapis.com --project=YOUR_GCP_PROJECT_ID
npx @_davideast/stitch-mcp init
```
Your GCP Project ID is in the header dropdown at console.cloud.google.com.

---

## Step 3 — API Keys
Create a `.env` file in your project root (never commit this):
```bash
cp .env.example .env
```
Fill in:
```
GEMINI_API_KEY=       # → https://aistudio.google.com (free tier available)
GOOGLE_CLOUD_PROJECT= # your GCP project ID (Stitch auth is handled by gcloud, no key needed)
```
**Never paste keys into chat.** If you do, revoke immediately at:
→ https://console.cloud.google.com/apis/credentials

---

## Step 4 — Per-Project Setup (run at project start)
```bash
# Install UI UX Pro Max into this project
uipro init --ai claude

# Generate your design system (takes ~10s)
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "[your product type]" \
  --design-system --persist -p "[Your App Name]"
# → Creates design-system/MASTER.md — your source of truth for all UI work

# Install Anthropic official skills (Claude Code only)
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

---

## Step 5 — Start Claude Code
```bash
claude
```
Claude reads `CLAUDE.md` automatically on startup. You're good to go.

---

## Step 6 — Before Launch
Run the SEO audit against your domain:
```bash
# Inside the claude CLI
/seo audit https://yourdomain.com
/seo technical https://yourdomain.com
```
Fix any critical errors before going live.

---

## Quick Reference — Key URLs
| Tool | URL |
|------|-----|
| Gemini API keys | https://aistudio.google.com |
| Google Cloud Console | https://console.cloud.google.com |
| 21st.dev components | https://21st.dev/community/components |
| UI UX Pro Max | https://github.com/nextlevelbuilder/ui-ux-pro-max-skill |
| Claude SEO | https://github.com/AgriciDaniel/claude-seo |
| Stitch MCP | https://github.com/davideast/stitch-mcp |
| Anthropic Skills | https://github.com/anthropics/skills |
