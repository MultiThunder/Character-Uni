---
version: "1.0"
name: "Character Universe — Bento Grid Tech Minimalist"
description: "Apple-inspired, modular bento-grid design for a polished Unicode character utility. Replaces every previous visual direction for Character Universe."
colors:
  primary: "#FFFFFF"
  secondary: "#1D1D1F"
  tertiary: "#9562E3"
  neutral: "#F5F5F7"
  surface: "#86868B"
  accent: "#0071E3"
  text-secondary: "#6E6E73"
  border: "#D2D2D7"
  dark-background: "#111113"
  dark-surface: "#1C1C1E"
  dark-raised: "#2C2C2E"
  dark-text: "#F5F5F7"
  dark-text-secondary: "#A1A1A6"
  dark-border: "#38383A"
  dark-tertiary: "#B99AF4"
  dark-accent: "#5EA2FF"
typography:
  display:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    fontWeight: 700
    letterSpacing: "-0.045em"
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.6
  mono:
    fontFamily: "'SFMono-Regular', Consolas, 'Liberation Mono', monospace"
spacing:
  xs: "8px"
  sm: "20px"
  md: "40px"
  lg: "80px"
radii:
  control: "12px"
  card: "24px"
  hero: "32px"
  pill: "999px"
components:
  button-primary:
    backgroundColor: "{colors.accent}"
    textColor: "#FFFFFF"
    padding: "12px 18px"
    borderRadius: "{radii.pill}"
  card:
    backgroundColor: "{colors.neutral}"
    borderRadius: "{radii.card}"
    border: "1px solid {colors.border}"
---

# Character Universe — Bento Grid Tech Minimalist

## 1. Design direction and authority

Character Universe is a practical workspace for discovering, inspecting, assembling, and copying Unicode characters, emoji, symbols, and text art.

**The visual concept: a character workstation organized as a polished bento grid.** Use the clarity and finish of Apple-style interfaces, the modular organization of modern developer tools, and real character specimens as the product's visual identity.

This document **replaces all previous visual design directions and design-system files** for Character Universe. Do not blend it with the former warm editorial/field-guide concept. Keep `PROJECT_BLUEPRINT.md` as the source of truth for product requirements, data accuracy, routes, and functionality. This file governs the UI and visual design.

### The interface should feel
- Premium, quiet, crisp, useful, and intentionally designed.
- Modern and approachable, but precise enough for writers and developers.
- Modular without becoming a wall of identical cards.
- Distinctive because the content inside the grid is real and useful—not because of decorative effects.

### Avoid completely
- The previous ivory-paper, forest-green, editorial-reference-book visual direction.
- Purple/blue gradient blobs, glassmorphism, glowing backgrounds, floating sparkles, and generic AI illustrations.
- A centered SaaS hero followed by three equal feature cards.
- Using a rounded card for every paragraph, feature, and list item.
- Emoji as interface icons; use one consistent line-icon library.
- Decorative stock images, fake terminal windows, meaningless metrics, or fabricated tool results.
- Too many accent colors. Blue is the functional accent; violet is a restrained secondary accent.
- Animation that delays, distracts from, or obstructs the utility.

If a section looks like a generic AI-generated landing-page template, simplify it and give the actual tool more visual prominence.

## 2. Color tokens

Use CSS variables or the framework's equivalent theme tokens. Do not hardcode colors across individual components.

### Light theme

| Token | Value | Use |
|---|---|---|
| `--background` | `#FFFFFF` | Main page |
| `--foreground` | `#1D1D1F` | Primary text |
| `--surface` | `#F5F5F7` | Bento cards and grouped surfaces |
| `--surface-raised` | `#FFFFFF` | Inputs and active work areas |
| `--surface-strong` | `#E8E8ED` | Selected rows and secondary controls |
| `--text-secondary` | `#6E6E73` | Supporting copy |
| `--text-tertiary` | `#86868B` | Nonessential metadata |
| `--border` | `#D2D2D7` | Card borders and separators |
| `--border-strong` | `#AEAEB2` | Stronger boundaries |
| `--accent` | `#0071E3` | Primary action, links, active state |
| `--accent-hover` | `#0063C7` | Hover state |
| `--accent-soft` | `#E8F2FF` | Selected filters and subtle active surfaces |
| `--accent-violet` | `#9562E3` | Rare secondary emphasis |
| `--success` | `#248A3D` | Success |
| `--danger` | `#D70015` | Error/destructive actions |
| `--focus-ring` | `#0071E3` | Keyboard focus |

### Dark theme

| Token | Value | Use |
|---|---|---|
| `--background` | `#111113` | Main page |
| `--foreground` | `#F5F5F7` | Primary text |
| `--surface` | `#1C1C1E` | Bento cards |
| `--surface-raised` | `#242426` | Inputs and active work areas |
| `--surface-strong` | `#2C2C2E` | Selected rows and controls |
| `--text-secondary` | `#A1A1A6` | Supporting copy |
| `--text-tertiary` | `#8E8E93` | Nonessential metadata |
| `--border` | `#38383A` | Borders and separators |
| `--border-strong` | `#545458` | Strong boundaries |
| `--accent` | `#5EA2FF` | Primary action and links |
| `--accent-hover` | `#82B7FF` | Hover state |
| `--accent-soft` | `#1C304A` | Selected filters |
| `--accent-violet` | `#B99AF4` | Rare secondary emphasis |
| `--success` | `#72D38A` | Success |
| `--danger` | `#FF6961` | Error |
| `--focus-ring` | `#82B7FF` | Keyboard focus |

### Color rules
- Most of the interface should be neutral. Use blue for actions and violet sparingly.
- No full-page gradients, neon glows, or blurred blobs.
- Use borders and surface contrast to define bento modules; shadows are optional and subtle.
- Never use color alone to indicate an error, selection, or success.
- Maintain WCAG AA contrast.
- Dark mode is intentionally designed with its own tokens, not mechanically inverted.

## 3. Typography

Use a system font stack for fast loading and a native feel:
- UI/body: `-apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`
- Code and code points: `"SFMono-Regular", Consolas, "Liberation Mono", monospace`
- Glyphs: `ui-sans-serif, "Segoe UI Symbol", "Noto Sans Symbols 2", "Apple Symbols", sans-serif`

Do not assume any one font supports every Unicode character. Retain fallbacks and show code points when a glyph cannot render.

| Role | Desktop | Mobile | Weight |
|---|---:|---:|---:|
| Homepage hero | `clamp(2.7rem, 5vw, 4.5rem)` | `2.5–3rem` | 700 |
| Page title | `2.5–3rem` | `2rem` | 700 |
| Section title | `1.5–1.75rem` | `1.35rem` | 650–700 |
| Card title | `1.125–1.25rem` | `1.05–1.125rem` | 600 |
| Body | `1rem` | `0.95–1rem` | 400 |
| UI label | `0.8125–0.875rem` | `0.8125rem` | 500–600 |
| Metadata | `0.75–0.8125rem` | `0.75rem` | 500 |
| Character specimen | `3.5–6rem` | `2.75–4rem` | 400–600 |

Use tight negative tracking only on large headings. Keep body copy around 1.6 line-height. Use tabular numerals for code points and counts. Avoid making every heading oversized.

## 4. Layout and bento grid

- Max content width: `1280px`.
- Gutters: `40px` desktop, `28px` tablet, `18–20px` mobile.
- Use CSS Grid; use 12 columns on wide screens.
- Main gaps: `16–24px`; larger section gaps: `40–80px`.
- Card radius: `24px`; hero/workspace radius: `28–32px`; controls: `12px`.
- Card padding: `24–32px` desktop and `18–22px` mobile.
- Borders: `1px solid var(--border)`.
- Avoid deep nesting of cards. Use whitespace and headings to group content inside a card.
- Use varied column spans such as 4, 5, 7, and 8 columns. Do not create an unbroken row of three identical cards.
- The largest modules must contain the most important actions, not decoration.
- Use `min-height: 100dvh`, not `100vh`, for viewport-filling layouts.

### Responsive rules
- Desktop: asymmetrical grid and wider tool workspaces.
- Tablet: reduce spans while preserving hierarchy.
- Below 768px: stack modules in task-first order.
- At 320px width: no horizontal page overflow.
- Never shrink a drawing canvas or text editor excessively just to preserve the desktop grid.
- Sticky navigation must not obscure focused controls or anchor targets.

### Layering
- Base: `0`
- Sticky navigation: `100`
- Dropdowns/popovers: `200`
- Dialogs/modals: `300`
- Toasts/live feedback: `500`

## 5. Brand and site shell

### Wordmark
Use a clear typographic wordmark: **Character Universe**. A small custom mark may derive from paired brackets or contrasting glyph shapes. It must work in one color and at favicon size.

Do not use a planet, galaxy, starburst, brain, robot, or magic wand as the logo.

### Header
- Approximately `64–72px` tall, with a subtle bottom border.
- Wordmark on the left.
- Navigation: `Explore`, `Tools`, `Draw & Find`; include `About` only if implemented.
- Right side: search shortcut, theme toggle, and favorites only if functional.
- Use a straightforward header, not a giant floating navigation pill.
- On mobile, collapse secondary links into an accessible menu.
- Use one icon set (Lucide or an existing equivalent), typically 16–20px.

### Footer
Use a quiet responsive footer with real links: Explore, Character Search, Emoji, Text Inspector, Draw & Find, Text Art, About, Privacy. Remove empty or placeholder link groups. Include a short rendering note where appropriate: “Character appearance can vary by device, app, and font.”

## 6. Homepage — a character-utility bento

### Objective
Visitors should be able to search or open a tool immediately. This is a utility, not a marketing funnel.

### Hero composition
Create an asymmetric split:
- Main hero/search module: roughly 7–8 of 12 columns.
- Character specimen module: roughly 4–5 of 12 columns.

**Main module**
- Eyebrow: `UNICODE · SYMBOLS · TEXT TOOLS`
- Headline: **Find the character. Make it yours.**
- Description: “Search, inspect, draw, and copy characters for the places you write.”
- Large functional search input: `Search by character, name, meaning, or code point`
- Example searches: `infinity`, `em dash`, `heart`, `U+00A9`
- Search is the primary action; do not add a competing CTA.

**Specimen module**
- Arrange real glyphs such as `∞`, `↗`, `§`, `¶`, `※`, and `∴` in a clean, considered composition.
- Use small names/code points only where useful.
- This is a specimen of the product's actual content, not a random glyph collage.
- On mobile, place it below search and reduce its height.

### Below-the-fold modules
Use a purposeful, asymmetric bento grid:

1. **Find a character** — larger module with real search examples and a route into the library.
2. **Draw & Find** — canvas preview or restrained SVG illustration, with a clear link to the functional tool.
3. **Inspect text** — a real example of a hidden character and its code point, only if the inspector supports it.
4. **Make text art** — a small real sample with whitespace preserved.
5. **Explore characters** — a wider module for categories and Unicode blocks.
6. **Learn something useful** — a concise, accurate explainer such as code points versus visible characters.

Homepage order: header → search/specimen hero → primary tools → browse categories → short educational content → footer.

Do not put a signup wall, ad, newsletter prompt, or long intro before the main utility.

## 7. Search, browse, and character detail

### Search field
- Height `52–56px` desktop and at least `48px` mobile.
- Radius `12–16px`, not an exaggerated capsule.
- Search icon on the left and clear action on the right when text exists.
- Accessible label and clear focus ring.
- Preserve the query predictably.

### Results
Use a compact list for text-heavy searches and a grid for visual browsing. Do not make each result a large marketing card.

Each result should contain:
- A glyph in a consistent specimen area.
- Verified character name.
- Code point or sequence.
- Category/block when useful.
- Copy action with local feedback.
- Link to details when available.

Use thin separators in list mode. On mobile, keep Copy visible and move secondary metadata to a second line.

### Library grid
- Compact filters for category and Unicode block only when implemented accurately.
- Consistent specimen-cell dimensions.
- Clear selected/focus outline.
- Character names and code points available to assistive technology.
- Preserve filters and search when navigating to a detail and back.

### Character detail
Show the large glyph, verified name, description, copy action, code point(s), block, available encodings, a text preview, and meaningful related characters. State rendering limitations when relevant. Never invent Unicode metadata; multi-code-point sequences must list all code points in order.

## 8. Draw & Find — signature tool

### Heading
**Draw a shape. Find its character.**

Description: “Sketch a symbol to find similar Unicode characters. For complex scenes, try character combinations or text art.”

Do not imply every drawing can match a single Unicode character.

### Desktop workspace
Use two aligned bento modules:
- Drawing workspace: 7–8 columns.
- Match results: 4–5 columns.
- Avoid a card nested inside another card.

### Canvas
- Height around `420–520px` on desktop, responsive on smaller screens.
- Raised surface, subtle border, `16–20px` radius.
- High-contrast strokes and adjustable stroke width.
- Toolbar: Undo, Redo, Clear, stroke width, optional background/contrast toggle.
- Main action: `Find matches`.
- Hint: “Draw one symbol, letter, or simple shape.”
- Support pointer and touch input. Prevent accidental page scrolling while drawing.
- No decorative grid unless it helps the drawing task.

### Results
- Heading: `Closest matches`.
- Display actual candidates with glyph, verified name, and copy action.
- Similarity percentages are allowed only if the algorithm provides a meaningful calibrated score. Otherwise show ranked results without invented precision.
- Selecting a result opens details or places the character into the output field.
- Empty state offers a clear next step.

### Complex drawing fallback
For a scene such as a person diving into a lake, do not force an unrelated symbol. Offer distinct, honest options:
1. `Find similar characters` — existing Unicode only.
2. `Build a character combination` — existing emoji/symbols.
3. `Make text art` — approximate the scene using text-compatible characters.
4. `Keep as an image` — only if image output is actually supported.

Never claim to create a new universally supported Unicode character. Clearly label approximations.

### Mobile
Canvas first and full width. Results below after submission. Keep Clear and Find accessible. Touch targets should be at least 44 × 44px where practical. Do not shrink the canvas to preserve two columns.

## 9. Text Inspector

Design this as a precision utility, not a statistics dashboard.

- Desktop: large text-input module beside a results module.
- Mobile: input first, results below.
- Show grapheme clusters, Unicode code points, UTF-8 bytes, and other counts only when precisely defined.
- Identify invisible/control characters by visible name and code point, e.g. `ZERO WIDTH SPACE · U+200B`.
- Highlight relevant characters in the preview without changing the original text.
- Explain normalization or transformations before applying them.
- Put copy actions beside the relevant value.
- No giant metric tiles, score gauges, or generic “analysis complete” banners.

Do not equate JavaScript string length with the number of user-perceived characters. Handle combining marks and bidirectional text correctly.

## 10. Text Art and character composition

- The editable output is the main visual surface.
- Use a monospace editor with exact whitespace and line-break preservation.
- Preview the exact content that will be copied.
- Toolbar may include Copy, Clear, font size, width, Undo/Redo, and supported output modes.
- Only show modes such as Text, Braille, or Block characters if implemented correctly.
- Avoid fake terminal chrome unless a terminal-style output is an actual user-selectable feature.
- Never silently trim, normalize, or modify whitespace.
- Provide local copy feedback and explain compatibility limitations where relevant.

## 11. Shared components

### Buttons
- Primary: blue fill, white text, 600 weight, pill radius, `12px 18px` padding.
- Secondary: surface fill, visible border, foreground text.
- Ghost: transparent with clear hover/focus state.
- Destructive: semantic danger color only.
- Hover: subtle color shift; optional 1px lift on major cards/buttons, no glow.
- Active: restrained tactile press effect.

### Cards
- Main bento: `24px` radius.
- Hero/workspace: `28–32px`.
- Background: `--surface`; border: `1px solid var(--border)`.
- Subtle shadow is optional; prefer border and surface contrast.
- Do not put a shadow on every element.
- Avoid nested cards and endless grids of tiny boxes.

### Inputs
- Visible label above the field.
- `12–16px` radius, clear border, 2px focus ring with offset.
- Error text below the relevant field.
- Placeholder is an example, not a label.
- Disabled states remain readable.

### Icons
Use a single consistent line-icon system, normally 16–20px. No emoji as interface icons. Icon-only controls need accessible names and tooltips when useful.

### Feedback
Copy feedback should appear near the action. Every asynchronous feature needs idle, loading, success, and recoverable error states. Never fake progress or report success before the action succeeds.

## 12. Motion

- Default transitions: `180–240ms`, ease-out.
- Small hover lift is allowed on major interactive modules, not every element.
- Optional entry motion: fade and translate `8–12px`; do not animate every card in a staggered cascade.
- Animate transform and opacity where possible.
- No animated gradients, glowing backgrounds, bouncing icons, parallax, or distracting scroll reveals.
- Respect `prefers-reduced-motion`.
- Drawing, typing, searching, and copying must feel immediate.

## 13. Accessibility and Unicode correctness

- Target WCAG 2.2 AA.
- Full keyboard navigation, semantic headings, accessible names, visible focus.
- Touch targets at least 44 × 44px where practical.
- Never use color as the only status indicator.
- Support 200% zoom and 320px-wide screens.
- Test glyph fallback across scripts and symbol ranges.
- Distinguish grapheme clusters, code points, and bytes.
- Invisible characters must have visible labels.
- Copy operations must preserve the exact intended text.
- Respect reduced-motion preferences.

## 14. SEO and ad placement

### SEO
- Unique title, description, H1, and useful explanatory content per real route.
- Put the working tool before long-form content.
- Avoid mass-produced near-duplicate pages.
- Keep URLs stable and shareable.
- Use structured data only when valid.
- Character names and code points must be crawlable text, not only canvas/image content.

### Ads
- Reserve space to prevent layout shifts.
- Never place ads inside the canvas, text editor, search field, result row, or next to Copy.
- Clearly distinguish ads from product controls.
- Prefer below-workspace placement or a carefully considered secondary region on wide screens.
- On mobile, do not insert an ad between the user's input and result.

## 15. Instructions for the coding agent

1. Read `PROJECT_BLUEPRINT.md` and this file fully before editing.
2. This file replaces all previous Character Universe design systems. Do not mix in the old warm editorial/field-guide design.
3. Inspect the repository, framework, routes, existing components, and Git status.
4. Preserve working functionality, data accuracy, URLs, and architecture.
5. Implement theme tokens first, then the shell and responsive grid primitives.
6. Build the homepage and review it before redesigning every tool page.
7. Design each tool around its actual task; do not reuse one generic layout everywhere.
8. Use real Unicode specimens and accurate labels.
9. Never invent scores, metadata, activity, or functionality.
10. Avoid new dependencies for minor visual details.
11. Test light/dark mode, keyboard access, reduced motion, mobile layout, and glyph rendering.
12. Run lint, type checks, tests, and production build after each coherent stage.
13. Use Git commits to keep changes reviewable and reversible.

### Suggested implementation stages
- A: Tokens, theme toggle, header/footer, grid and container primitives.
- B: Homepage hero, search, and asymmetric bento modules.
- C: Search results, character detail, and library.
- D: Draw & Find and honest complex-drawing fallback.
- E: Text Inspector and Text Art.
- F: SEO content, ad placement, and real favorites if supported.
- G: Accessibility, performance, responsive and visual QA.

## 16. Acceptance checklist

- [ ] This Bento Grid Tech Minimalist direction is followed.
- [ ] Previous visual directions have been removed.
- [ ] Homepage uses purposeful asymmetric bento modules, not three equal feature cards.
- [ ] White/light-gray surfaces, dark text, blue interactions, and restrained violet emphasis are consistent.
- [ ] Dark mode uses its own tokens and readable borders.
- [ ] Card radii and spacing are consistent without turning everything into a card.
- [ ] Search and tools are more prominent than marketing copy.
- [ ] Character specimens and metadata are real and accurate.
- [ ] No fake results, scores, activity, or unsupported features.
- [ ] Complex drawings are handled honestly.
- [ ] Copy preserves exact text.
- [ ] No emoji are used as interface icons.
- [ ] No horizontal overflow at 320px.
- [ ] Keyboard focus, accessible labels, and reduced-motion support work.
- [ ] Ads do not interrupt the primary workflow.
- [ ] Existing routes and functionality remain intact.
- [ ] Lint, type checks, tests, and production build pass.

**Final principle:** the bento grid provides structure, the typography provides clarity, and real working character tools provide the personality. The result should feel like a premium character workstation—not a generic AI landing page.
