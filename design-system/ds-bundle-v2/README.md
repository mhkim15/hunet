# EDU Design System

A **monotone (grayscale) design system** for Hunet 연수원 (learner-facing LMS) screens.
This sync ships the **design tokens** and a set of **reference component cards** (real HTML/CSS,
the way the team built them). There are no compiled JS/React components — style with the tokens
below and compose layouts to match the reference cards.

## Styling idiom — CSS custom properties

Style everything through `var(--*)` tokens. There are **no utility classes and no component props** —
the system is a token sheet plus reference markup. Always pull color, type, spacing, radius, shadow,
and layout values from the tokens; never hardcode hex/px that a token already names.

The full sheet loads via `styles.css` (`@import "./tokens/_tokens.css"`), so every token below is
available globally.

### Color (monotone — accent is black, not a brand color)
- Scale: `--color-black`, `--color-gray-900|700|500|400|300|200|100|50`, `--color-white`
- Semantic: `--color-bg`, `--color-surface`, `--color-border`, `--color-border-dark`
- Text: `--color-text-primary`, `--color-text-secondary`, `--color-text-disabled`, `--color-text-inverse`
- Accent: `--color-accent` (black), `--color-accent-subtle`, `--color-accent-hover`

### Typography
- `--font-family` (Noto Sans KR stack)
- Size: `--font-size-xs|sm|md|lg|xl|2xl|3xl` (11→24px)
- Weight: `--font-weight-regular|medium|semibold|bold`
- Line height: `--line-height-tight|normal|loose`

### Spacing / radius / shadow
- Space: `--space-1|2|3|4|5|6|8|10|12|16` (4→64px)
- Radius: `--radius-none|sm|md|pill|circle`
- Shadow: `--shadow-sm|md|lg`

### Layout frame
- `--layout-max-width` (1130px), `--layout-gnb-height` (60px), `--layout-sidebar-w` (150px), `--layout-h-padding`

## Where the truth lives
- `tokens/_tokens.css` — the authoritative token sheet (read before styling).
- `components/<Group>/<Name>/<Name>.html` — reference markup for each component
  (Tokens, Components: Buttons / CourseCard / LearningStatus / SectionHeader / DailyInsight,
  Layout: GNB / PageLayout). Read these for the exact class structure and composition.

## Idiomatic snippet
```html
<!-- a CourseCard, styled entirely with tokens -->
<div style="
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  overflow: hidden;
">
  <div style="aspect-ratio: 16/9; background: var(--color-gray-100);"></div>
  <div style="padding: var(--space-3);">
    <div style="font-size: var(--font-size-md); font-weight: var(--font-weight-semibold);
                color: var(--color-text-primary);">금쪽같은 직장인을 위한 실무 용어사전</div>
    <div style="font-size: var(--font-size-xs); color: var(--color-text-disabled);
                margin-top: var(--space-1);">휴넷 · 동영상</div>
  </div>
</div>
```
