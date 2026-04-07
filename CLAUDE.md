# CLAUDE.md
# =========================================================
# Keep this file SHORT. It loads into EVERY session.
# Detailed docs live in agent_docs/ — read them when relevant.
# =========================================================

## Project
```
Name    : [YOUR APP NAME]
Type    : [SaaS / Landing Page / Dashboard / E-commerce / etc.]
Stack   : [Next.js / React / Vue / HTML+Tailwind / etc.]
Domain  : [yourapp.com]
```

## Agent Docs (read before starting relevant tasks)
- `agent_docs/design_system.md`     — UI styles, colors, typography, component rules
- `agent_docs/tools_setup.md`       — Stitch MCP, Nano Banana 2, SEO skill, UI UX Pro Max
- `agent_docs/seo_rules.md`         — SEO commands, schema requirements, Core Web Vitals targets
- `agent_docs/stack_conventions.md` — Stack patterns, file structure, naming conventions

Read only the docs relevant to your current task. Do not read all of them upfront.

## Always True (every task, no exceptions)
- Mobile-first. Responsive: 375 → 768 → 1024 → 1440px.
- No emojis as icons. Use Lucide or Heroicons SVGs.
- `cursor-pointer` on every clickable element.
- Accessible: WCAG AA contrast, real focus states, aria labels.
- Wrap all animations in `prefers-reduced-motion` media query.
- Annotate code with *why*, not just *what*.
- List what you're changing before editing existing files.

## How to Verify Your Work
```bash
npx tsc --noEmit           # type check
npx biome check --write .  # lint + format (auto-fix)
[your test command here]   # tests
```

## Security
Never ask for or accept API keys in chat. They belong in `.env` only (gitignored).
If a key is accidentally shared, revoke it at console.cloud.google.com/apis/credentials.
