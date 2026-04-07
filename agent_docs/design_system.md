# Design System
# Read this when: building any UI component, page, or visual element.

---

## Source of Truth
Always check these files first — they override everything in this doc:
- `design-system/MASTER.md`          — global colors, typography, spacing
- `design-system/pages/[page].md`    — page-specific overrides (if exists)

If these files don't exist yet, generate them:
```bash
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "[product type]" \
  --design-system --persist -p "[Project Name]"
```

---

## UI Standards

**Components**
- Build reusable components. No copy-paste blocks between pages.
- Check 21st.dev (https://21st.dev/community/components) before building common patterns.
- Use shadcn/ui as the base component layer where possible.

**Responsive Breakpoints**
```
375px   → mobile base
768px   → tablet
1024px  → desktop
1440px  → wide
```

**Icons**
- Lucide React or Heroicons only. No emojis, no inline SVG blobs.

**Interactions**
- All hover/focus transitions: 150–300ms ease
- `cursor-pointer` on every clickable element — always
- Focus rings must be visible (don't just `outline: none`)

**Animations**
```css
@media (prefers-reduced-motion: reduce) {
  /* wrap all animations here */
}
```

**Accessibility**
- Contrast ratio ≥ 4.5:1 for body text, ≥ 3:1 for large text
- All images need descriptive `alt` text
- Interactive elements need aria labels when text isn't self-describing

---

## Pre-Delivery Check (run mentally before marking any UI task done)
- [ ] Responsive at all 4 breakpoints
- [ ] No emoji icons
- [ ] `cursor-pointer` on all clickables
- [ ] Hover states with transitions
- [ ] `prefers-reduced-motion` respected
- [ ] Contrast passes WCAG AA
- [ ] Focus states visible
- [ ] All images have alt text
