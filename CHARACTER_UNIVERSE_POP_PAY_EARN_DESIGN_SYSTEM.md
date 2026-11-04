# Character Universe — Design System Specification

> **Purpose:** Adapt the visual language and interaction patterns of the supplied “Pop Pay Earn” design specification to Character Universe. This document is the visual and interaction guide for the website. `PROJECT_BLUEPRINT.md` remains the source of truth for product behaviour, routes, Unicode correctness, architecture, SEO, privacy, and technical requirements.

---

## 1. Design Tokens

### 1.1 Color Palette

| Token | Hex Value | Role / Usage |
| :--- | :--- | :--- |
| `--color-bg-primary` | `#0C0E17` | Global page background |
| `--color-surface` | `#181B2B` | Main cards, widgets, panels |
| `--color-surface-raised` | `#20243A` | Elevated cards, dropdowns, hover states |
| `--color-surface-input` | `#121624` | Search bars, text inputs, editors |
| `--color-border` | `#2A3046` | Card borders, separators, input outlines |
| `--color-brand-pop` | `#FF4B72` | Primary buttons, active navigation, selected elements |
| `--color-earn-green` | `#10B981` | Successful copy, save, and completed actions |
| `--color-success-soft` | `#12372F` | Success notifications and subtle highlights |
| `--color-text-main` | `#FFFFFF` | Primary text and character names |
| `--color-text-secondary` | `#C0C4D8` | Supporting descriptions |
| `--color-text-muted` | `#8A8FAD` | Labels, helper text, metadata |
| `--color-error` | `#F87171` | Errors and failed operations |
| `--color-warning` | `#FBBF24` | Warnings and caution states |
| `--color-focus` | `#A5B4FC` | Visible keyboard focus ring |

**Colour rules**
- Pink is the primary brand colour. Use it to draw attention to important actions.
- Green is reserved for genuine successful operations, such as copying or saving a character.
- Avoid using pink and green together excessively.
- Do not introduce unnecessary gradients, neon glows, or decorative colour effects.
- Maintain sufficient contrast between text and background surfaces.
- Preserve the existing light theme if one is already implemented; map semantic tokens to light values rather than hard-coding colours into components.

### 1.2 Typography & Scales

**Font Family:** `Inter, system-ui, sans-serif`

| Token | Size | Weight | Usage |
|---|---:|---:|---|
| `font-size-xl` | 32px | 700 | Main homepage heading |
| `font-size-page` | 28px | 700 | Individual tool page headings |
| `font-size-lg` | 20px | 600 | Section headings |
| `font-size-md` | 16px | 400 | Body text, inputs, descriptions |
| `font-size-card` | 16px | 600 | Tool and category card headings |
| `font-size-sm` | 12px | 500 | Metadata, helper labels |

**Typography rules**
- Use a consistent hierarchy throughout the website.
- Keep descriptions short and readable.
- Use a suitable fallback font stack for Unicode characters that Inter cannot render.
- Character glyphs should be visually prominent and must never be accidentally clipped.
- Use sentence case for headings and buttons.

### 1.3 Layout & Structural Spacing

- **Base Grid:** 8px proportional spacing system.

| Element | Specification |
|---|---|
| Widgets / Cards | 16px radius |
| Interactive Action Buttons | 12px radius |
| Large Feature Panels | 20px radius |
| Modal Overlays | 24px radius |
| Large Panel Padding | 24px |
| Standard Card Padding | 20px |
| Compact List Padding | 16px |
| Desktop Page Gutter | 32px |
| Tablet Page Gutter | 24px |
| Mobile Page Gutter | 16px |
| Maximum Content Width | 1200–1280px |

Use consistent spacing between sections, cards, labels, and controls. Avoid creating a different spacing system for every page.

---

## 2. Component Structures

### 2.1 The Character Universe Home Hub

The homepage acts as the central launchpad for the website's utilities. It should feel like a useful creative workspace, not a financial dashboard.

#### A. Hero Search Widget

Place this prominently at the top of the homepage.

**Content**
- Main heading: **“Find the perfect character.”**
- Short description explaining that users can discover, copy, and use Unicode characters, symbols, and emoji.
- Large search input.
- Search icon and clear action.
- Placeholder: `Search symbols, emoji, names, or Unicode…`
- Search button using `--color-brand-pop`.
- Optional `/` keyboard shortcut hint only if the shortcut is implemented.

**Visual treatment**
- Main panel uses `--color-surface`.
- Search field uses `--color-surface-input`.
- Focused search field uses the pink brand accent.
- Input must be large enough for comfortable desktop and mobile interaction.
- Search suggestions must be keyboard accessible.

Search should support only capabilities actually implemented, such as character names, keywords, symbols, or Unicode values.

#### B. Quick Access Tool Matrix

Below the hero search, display the main tools as individual cards.

| Tool | Description |
|---|---|
| **Character Search** | Search and discover characters by name, keyword, or Unicode value. |
| **Emoji & Symbols** | Browse expressive emoji, decorative symbols, and special characters. |
| **Draw & Find** | Draw a shape and discover visually similar existing Unicode characters. |
| **Text Inspector** | Inspect text, Unicode code points, character names, and properties. |
| **Text Art Studio** | Create decorative text and visual compositions using supported characters. |
| **Unicode Lookup** | Look up characters using their Unicode names or code points, if implemented as a separate tool. |

Each card must contain:
- A distinctive, consistent line icon.
- Tool name.
- One short description.
- Subtle hover and focus treatment.
- Whole-card navigation where appropriate.
- A real destination; do not add dead links.

Use a responsive grid rather than a long vertical list on desktop: three columns on wide screens, two on tablet, and one or two on mobile depending on available width.

#### C. Popular Character Categories

Create a compact section containing category cards for useful character groups.

Examples:
- Arrows
- Hearts
- Stars
- Mathematical Symbols
- Currency Symbols
- Decorative Symbols
- Letters & Numbers
- Geometric Shapes

Each category must lead to a real browse page or filtered result view. Do not display fabricated popularity rankings or usage statistics.

#### D. Recently Used / Saved Characters

Display this section only if recent or saved character functionality exists.

Each character item should:
- Display the actual glyph prominently.
- Include a copy action.
- Provide access to character details.
- Clearly indicate whether it is saved or recently used.

If no items exist, show an informative empty state instead of sample data pretending to belong to the user. If storage is local-only, describe it accurately; do not imply cross-device sync.

#### E. Featured Tool

A single featured panel may highlight a useful workflow, such as drawing a symbol and comparing existing Unicode matches. Keep it factual and useful. Do not invent activity, user metrics, or rotating content without a real source.

### 2.2 Character Search & Browse Interface

The character browsing experience is one of the website's most important interfaces.

**Character grid**
- Use a responsive grid of individual character tiles.
- Each tile should have a dark surface and subtle border.
- Display the Unicode glyph prominently in the centre.
- Place its verified name or short description below.
- Provide a copy action and a details action.
- On hover/focus, reveal secondary actions without hiding the glyph.
- Every tile must be keyboard operable and have an accessible name.

**Interaction states**
- Default: `--color-surface`.
- Hover: `--color-surface-raised`.
- Selected: subtle pink border.
- Copied: green success indicator.
- Focused: visible keyboard focus ring.

Avoid oversized tiles that waste screen space. The grid should make it possible to explore many characters efficiently.

**Character details**
- Show the actual character, official Unicode name, code point, and other verified properties available from the data source.
- Provide a prominent copy action.
- Never fabricate a Unicode name, code point, or property.
- Distinguish an official Unicode identity from a descriptive search synonym.

### 2.3 Draw & Find Workspace

This tool should receive a dedicated working interface rather than looking like a generic dashboard widget.

**Drawing canvas**
- Large central drawing area.
- Clear canvas background.
- Drawing controls for undo, redo (if supported), and clear.
- Primary action button: **“Find Characters”**.
- Short instruction explaining that the tool finds similar existing characters.

**Results panel**
- Display visually similar existing characters.
- Each result should contain the glyph, verified character name, and Unicode information where available.
- Provide copy and selection actions.
- Clearly distinguish exact matches from approximate visual matches.
- If confidence or similarity is shown, explain what it means and derive it from the actual matching method.
- Include an honest “No close match found” state.

**Product correctness**
- Do not claim that a drawing creates a new official Unicode character.
- The tool identifies existing characters or suggests clearly labelled approximations.
- Keep exact matches, similar candidates, and creative approximations visually distinct.

### 2.4 Text Inspector Interface

Use a structured two-part layout.

**Input panel**
- Large text editor.
- Paste and clear actions.
- Support multiline input.
- Preserve user-entered text.

**Analysis panel**
- Character count, with the counting rule clearly defined.
- Unicode code points.
- Unicode names.
- Character properties where available.
- Clear distinction between grapheme clusters, code points, UTF-16 code units, and bytes when relevant.
- Expandable information rows so detailed Unicode data does not overwhelm the main interface.

Handle combining marks, variation selectors, emoji modifiers, and joined emoji sequences correctly. Do not silently normalize or alter user-entered text.

### 2.5 Text Art Studio

The studio should feel like a focused creative workspace.

**Input and controls**
- Text input.
- Available style or layout options.
- Generation controls.
- Copy and reset actions.

**Output preview**
- Large preview area.
- Monospaced font where alignment is important.
- Preserve whitespace and line breaks.
- Provide an easy copy action.
- Clearly identify whether output uses ASCII, Braille, block elements, or combinations of existing Unicode characters.

Do not claim that a generated composition is a single Unicode character unless it genuinely is one.

---

## 3. Character Universe Action Modals

Replace the reference app's reward modals with useful action confirmations. Do not interrupt every small interaction with a modal; use toasts for lightweight feedback.

### 3.1 Copy Character Confirmation

When the user successfully copies a character:
- Display a compact toast or confirmation panel.
- Use `--color-earn-green` for the success indicator.
- Show the copied glyph if useful.
- Display **“Copied to clipboard”**.
- Automatically dismiss after a short duration.
- Announce the confirmation accessibly through an appropriate live region.

If clipboard access fails, show a useful error and an alternative manual-selection method. Confirm success only after the clipboard operation succeeds.

### 3.2 Save Character Modal

If saving and collections are implemented:
- Dim the background using `rgba(12, 14, 23, 0.75)`.
- Modal surface: `--color-surface`.
- Modal radius: `24px`.
- Display the selected character prominently.
- Allow the user to select an existing collection or create a new one, if supported.
- Primary CTA: **“Save Character”**.
- Confirm success only after the save operation completes.

### 3.3 Character Details Modal

When a user opens character details, display:
- Large Unicode character.
- Official Unicode name, when available.
- Code point.
- Other verified character information.
- Copy button.
- Save action, if supported.

The character itself should be the visual focus.

### 3.4 Modal Animation

- Animate upward from the bottom using a subtle `slide-in-up` effect.
- Combine with a short opacity transition.
- Use approximately 180–220ms duration.
- Respect reduced-motion settings.
- On mobile, use a bottom-sheet layout when appropriate.
- Support Escape to close, focus trapping, and focus restoration.

---

## 4. Engineering State Implementations

### 4.1 Initializing / Loading

Use skeleton loading states with neutral dark surfaces.

- Skeleton character tiles should resemble the final grid.
- Search results should preserve their layout while loading.
- Drawing results should display a loading state within the results panel.
- Avoid fake progress percentages.
- Use subtle animation rather than aggressive flashing.
- Prevent layout shifts while content loads.

### 4.2 Success States

Use green feedback only when an action genuinely succeeds.

Examples:
- Character copied successfully.
- Character saved successfully.
- Text art generated successfully.
- Analysis completed successfully.

Use:
- A small checkmark.
- A short green flash or border transition.
- A brief confirmation message.

Avoid large reward animations, artificial counters, or celebratory currency graphics.

### 4.3 Error States

Errors should be informative and actionable.

Examples:
- Clipboard permission denied.
- No matching characters found.
- Invalid Unicode input.
- Drawing could not be processed.

Use the error token for indicators, but retain readable text and offer a recovery action. Preserve user-entered text and drawing data whenever possible.

### 4.4 Empty States

Empty states should guide users towards a useful next action.

Examples:
- “No characters found. Try another keyword.”
- “Draw a simpler shape to find closer matches.”
- “Your saved characters will appear here.”

---

## 5. Responsive Layout Rules

| Screen | Layout |
|---|---|
| Desktop (1024px+) | Full navigation, multi-column grids, spacious tool workspaces |
| Tablet (768–1023px) | Reduced grid columns, compact navigation, stacked panels when needed |
| Mobile (below 768px) | Compact header, one-column tool workspaces, comfortable touch targets |

- Main content should remain centred.
- Search must remain easily accessible.
- Character glyphs must remain large enough to identify.
- Dialogs should become mobile-friendly sheets where appropriate.
- Fixed navigation must never cover important controls or content.
- Prevent horizontal scrolling.
- Keep touch targets comfortably sized.

---

## 6. Accessibility & Unicode Correctness

- Meet WCAG AA contrast for normal text and controls.
- All functionality must be usable by keyboard.
- Provide visible focus indicators.
- Use semantic headings, buttons, links, labels, and landmarks.
- Announce copy success, errors, and dynamic result updates through appropriate live regions.
- Give character tiles accessible labels that include the character and its verified name where possible.
- Do not communicate state through colour alone.
- Support zoom and text resizing without clipping controls.
- Test scripts and emoji across the supported font stack.
- Treat grapheme clusters and multi-code-point emoji sequences correctly.
- Never invent code points or Unicode properties.
- Never silently alter user-entered text.

---

## 7. SEO, Ads, Privacy & Performance

### SEO
- Keep meaningful page headings and crawlable explanatory text.
- Each indexable tool/category page should have a distinct title, description, canonical URL, and useful content.
- Do not render essential page content only after a client-side interaction.
- Use descriptive internal links between related tools and categories.
- Avoid thin doorway pages generated only to target keyword variants.

### Advertising
- Reserve ad placements without letting them dominate the interface.
- Do not place ads where they can be mistaken for Copy, Search, or Generate controls.
- Do not insert ads between a character glyph and its copy action.
- Prevent ad containers from causing major layout shifts.
- Preserve a usable experience when an ad is not returned.

### Privacy
- Do not send private text entered into Text Inspector to a server unless the feature explicitly requires it and the user is informed.
- Be transparent about whether saved items are local or account-based.
- Do not invent account, sync, or cloud-storage features in the UI.

### Performance
- Lazy-load non-critical imagery and below-the-fold content.
- Avoid shipping large icon or animation libraries for small effects.
- Keep the initial search and browse experience responsive.
- Prevent layout shifts when fonts or ads load.
- Prefer lightweight CSS transitions over complex animation dependencies.

---

## 8. Global Design Rules

1. Every page must use the same colour tokens, typography, spacing, and radius standards.
2. All cards should share a consistent visual language.
3. Use pink for primary actions and selected states.
4. Use green exclusively for genuine successful actions.
5. Do not introduce fake reward counters, balances, streaks, or gamified task systems.
6. Avoid generic AI-generated dashboard patterns and unnecessary decorative elements.
7. Keep the character or utility workspace as the focal point.
8. Ensure every visible button and control performs a real action.
9. Preserve the existing website's routes, features, and working functionality.
10. Maintain both light and dark theme functionality if already implemented.
11. Do not fabricate Unicode names, code points, character properties, popularity statistics, or user activity.

---

## 9. Implementation Priority

1. Global design tokens and theme integration.
2. Header, navigation, and shared layout.
3. Homepage hero search and quick tool cards.
4. Character browsing and result tiles.
5. Individual utility workspaces.
6. Modals, toast notifications, and state feedback.
7. Responsive refinements.
8. Accessibility, performance, and visual polish.

---

## 10. Visual Acceptance Checklist

### Overall appearance
- [ ] Dark navy is the dominant background, with clearly differentiated panel surfaces.
- [ ] Pink is a deliberate brand/action accent rather than a colour applied to every element.
- [ ] Green appears only for genuine success feedback.
- [ ] Typography and spacing feel consistent across all routes.
- [ ] Cards have consistent radii, borders, and hover behaviour.
- [ ] The interface looks like a polished character utility, not a payment or rewards app.

### Home page
- [ ] Search is the most prominent action.
- [ ] Main tools are discoverable without excessive scrolling.
- [ ] Tool cards have clear names and descriptions.
- [ ] No fake balances, earnings, points, streaks, task queues, or fabricated activity are shown.

### Tool pages
- [ ] The actual working area is visually dominant.
- [ ] Search, drawing, inspection, and text-art workflows are easy to understand.
- [ ] Results and metadata are readable and correctly labelled.
- [ ] Exact matches, similar matches, and approximations are not conflated.

### Interaction
- [ ] Copy success is confirmed only after clipboard success.
- [ ] Loading, empty, error, and success states are implemented.
- [ ] Keyboard focus and reduced-motion behaviour work.
- [ ] Dialogs and mobile sheets are usable and accessible.

### Responsive and technical
- [ ] Desktop, tablet, and mobile layouts are checked.
- [ ] No horizontal overflow occurs at narrow widths.
- [ ] Existing routes and working functionality remain intact.
- [ ] SEO content remains crawlable.
- [ ] Ads do not obstruct core controls.
- [ ] Unicode edge cases are not broken by styling or text handling.

---

## 11. Instructions for the AI Coding Agent

1. Read `PROJECT_BLUEPRINT.md` first. It remains the source of truth for product behaviour, routes, Unicode correctness, architecture, SEO, privacy, and testing.
2. Inspect the existing codebase before editing. Identify the current component system, routing, theme mechanism, and working features.
3. Treat this file as a visual and interaction specification, not permission to rebuild the application from scratch.
4. Preserve all existing working functionality, route names, data sources, and correct Unicode handling.
5. Implement shared design tokens and reusable components before styling every page individually.
6. Apply the system incrementally, beginning with the global shell and home page, then the shared tool-page patterns.
7. Do not create fake dashboard data, reward systems, balances, task completion indicators, or user history.
8. Do not invent new product capabilities. If a referenced feature is not implemented, do not expose a dead control for it.
9. Test the actual UI at desktop, tablet, and mobile widths after each major phase.
10. Keep changes small enough to review and revert through Git. Do not overwrite unrelated files or remove existing functionality to simplify the design.

**Priority order:** visual consistency → search and tool usability → responsive behaviour → accessibility → loading/feedback polish. Product correctness and preservation of existing functionality take priority over visual effects.

---

**Design objective:** Character Universe should feel like a polished, modern, dark-first creative utility platform. It should retain the distinctive pink-and-green visual energy of the supplied Pop Pay Earn reference while making character discovery, copying, inspection, and creation the central experience.
