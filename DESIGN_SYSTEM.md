# The Character Universe --- Design System

**Document type:** Authoritative visual and interaction specification\
**Applies to:** Homepage, tool pages, character detail pages, guides,
dialogs, forms, navigation and all future features\
**Brand tagline:** Every character has a story.

------------------------------------------------------------------------

## 0. Instructions to the design/coding agent

This document is the visual source of truth. Follow it before inventing
new colors, spacing, components or page layouts.

1.  Inspect the current repository and reuse existing working components
    where they meet this specification.
2.  Do not redesign the brand independently on each route.
3.  Do not change product functionality merely to match a screenshot.
4.  Build shared tokens and reusable components; do not hardcode a
    different style on every page.
5.  Every page must work in light and dark mode.
6.  All interactive controls need real behavior, accessible names, focus
    states and feedback.
7.  Do not use oversized decorative artwork that pushes the tool below
    the fold.
8.  Avoid generic AI-generated gradients everywhere, excessive
    glassmorphism, random floating icons and inconsistent card styles.
9.  If a visual reference conflicts with accessibility or responsive
    behavior, preserve the intended visual hierarchy while implementing
    accessible, responsive behavior.
10. Before completion, compare all implemented routes against these
    rules and fix inconsistencies.

------------------------------------------------------------------------

## 1. Brand and visual identity

### Personality

-   Curious, clever and welcoming.
-   Technically trustworthy, without looking like a developer-only
    console.
-   Calm, clean and efficient.
-   Slightly playful through character glyphs and small illustrations,
    not through clutter.
-   Professional enough for students, writers, designers and developers.

### Visual concept

Use a clean, modern utility interface with: - a white/light neutral
foundation; - deep navy text; - lavender/indigo as the primary brand
accent; - pale lilac surfaces for featured areas; - restrained borders
and soft shadows; - rounded cards and clear typography; - prominent real
character glyphs as visual content.

The interface should resemble a carefully designed reference/tool
product---not an admin dashboard, game UI, social network or AI chat
page.

### Logo usage

-   Use the actual approved project logo if one exists in the
    repository.
-   If no logo asset exists, create a simple consistent text-and-symbol
    lockup using a small character-inspired mark and the wordmark "The
    Character Universe".
-   Do not repeatedly substitute random icons for the brand mark.
-   Never stretch, recolor unpredictably or add a background box to a
    transparent logo unless the asset was designed for it.
-   Ensure the logo remains legible in both themes.

------------------------------------------------------------------------

## 2. Color tokens

Define tokens centrally using the framework's theme/CSS-variable system.
Components should consume tokens, not repeat hex values.

### Light theme

  -----------------------------------------------------------------------
  Token                   Value                   Usage
  ----------------------- ----------------------- -----------------------
  `--background`          `#F7F8FC`               Overall page background

  `--surface`             `#FFFFFF`               Cards, panels, menus

  `--surface-secondary`   `#F0EEFF`               Featured panels and
                                                  soft emphasis

  `--surface-tertiary`    `#F2F4FA`               Muted controls and
                                                  subtle backgrounds

  `--text-primary`        `#202044`               Main text and headings

  `--text-secondary`      `#666582`               Supporting text

  `--text-muted`          `#817F9B`               Metadata; do not use
                                                  for essential
                                                  low-contrast text

  `--border`              `#E3E6EF`               Default card and field
                                                  borders

  `--border-strong`       `#C9CBE0`               Emphasized borders

  `--primary`             `#5B49D6`               Primary actions and
                                                  active states

  `--primary-hover`       `#4937C1`               Hover state

  `--primary-soft`        `#EAE7FF`               Soft accent background

  `--focus-ring`          `#6B5AE8`               Keyboard focus

  `--success`             `#16834A`               Success state

  `--warning`             `#946200`               Warning state

  `--danger`              `#B42335`               Error/destructive state

  `--info`                `#315BC6`               Informational state
  -----------------------------------------------------------------------

### Dark theme

  -----------------------------------------------------------------------
  Token                   Value                   Usage
  ----------------------- ----------------------- -----------------------
  `--background`          `#0B1020`               Overall page background

  `--surface`             `#111A2C`               Cards, panels, menus

  `--surface-secondary`   `#191A38`               Featured panels and
                                                  soft emphasis

  `--surface-tertiary`    `#172238`               Muted controls

  `--text-primary`        `#F1F0FF`               Main text and headings

  `--text-secondary`      `#B9B8D5`               Supporting text

  `--text-muted`          `#9695B5`               Metadata; not for
                                                  essential text

  `--border`              `#293650`               Default borders

  `--border-strong`       `#3B4967`               Emphasized borders

  `--primary`             `#A99AFF`               Primary actions and
                                                  active states

  `--primary-hover`       `#C0B6FF`               Hover state

  `--primary-soft`        `#29244D`               Soft accent background

  `--focus-ring`          `#B6A9FF`               Keyboard focus

  `--success`             `#63D39A`               Success state

  `--warning`             `#F1C66D`               Warning state

  `--danger`              `#FF8B98`               Error/destructive state

  `--info`                `#91B4FF`               Informational state
  -----------------------------------------------------------------------

Check contrast for every actual text/background pairing. Tokens are
starting values; accessibility must be verified, not assumed.

### Color rules

-   Primary accent is lavender/indigo; do not introduce unrelated accent
    colors for individual tools.
-   Semantic colors are reserved for success, warning, error and
    informational states.
-   Do not use a gradient as the default background for every section.
-   Avoid pure black backgrounds and low-contrast gray text.
-   Never rely on color alone to indicate status.
-   Character glyphs may use the primary accent in previews, but their
    text must remain readable.

------------------------------------------------------------------------

## 3. Typography

Use a clean system sans-serif stack or the project's existing
high-quality sans-serif font. Avoid adding a remote font dependency
without a reason.

Suggested stack:
`Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`

### Type scale

  Role                          Desktop              Mobile Weight
  ----------------- ------------------- ------------------- ----------
  Hero title                   44--52px            32--38px 700
  Page title                   34--40px            28--34px 700
  Section title                22--26px            20--24px 650--700
  Card title                   16--18px            16--18px 600
  Body                         15--17px            15--16px 400
  Supporting text              13--14px            13--14px 400
  Metadata/label               12--13px            12--13px 500
  Character glyph     Context-dependent   Context-dependent Normal

Use a sensible line-height: approximately 1.1--1.2 for large headings
and 1.45--1.65 for body copy. Avoid very long line lengths in
explanatory text.

Character glyphs must use a fallback-capable font stack. The page must
not break if the visitor's system lacks a particular glyph.

------------------------------------------------------------------------

## 4. Spacing, sizing and geometry

Use a consistent spacing scale based on 4px increments.

Suggested tokens: - `space-1`: 4px - `space-2`: 8px - `space-3`: 12px -
`space-4`: 16px - `space-5`: 20px - `space-6`: 24px - `space-8`: 32px -
`space-10`: 40px - `space-12`: 48px - `space-16`: 64px - `space-20`:
80px

### Containers

-   Main desktop content width: approximately 1200--1280px.
-   Use centered content with responsive side padding.
-   Desktop side padding: generally 24--40px.
-   Tablet side padding: 20--28px.
-   Mobile side padding: 16--20px.
-   Keep text columns readable; do not stretch body copy across very
    wide screens.

### Corner radii

-   Small controls: 8px.
-   Inputs and standard cards: 10--12px.
-   Featured panels: 14--18px.
-   Pills: fully rounded.
-   Avoid mixing sharp corners with very rounded cards without a reason.

### Borders and shadows

-   Prefer subtle borders to heavy shadows.
-   Use low-elevation shadows only for floating menus, dialogs or
    featured cards.
-   Cards should remain distinguishable in both themes without large
    shadows.
-   Do not use a visible border around every tiny icon or decorative
    element.

------------------------------------------------------------------------

## 5. Global page shell

### Header

-   Compact, consistent height.
-   Brand lockup at left.
-   Primary navigation in the middle/right on desktop.
-   Search and theme toggle as clear icon buttons with accessible names.
-   Use a restrained divider or subtle border.
-   Sticky behavior is optional; do not make the header consume
    excessive vertical space.
-   Mobile navigation collapses accessibly and closes after navigation.

### Footer

Include: - brand lockup and short tagline; - links to Home, All Tools,
Character Library and Guides; - About, Contact, Privacy, Terms and
Disclaimer; - copyright line if desired.

Keep it visually quieter than the main content. Do not invent social
profiles or external links.

### Page shell

Each route should use the same content container and shared spacing. The
main page content should be easy to locate and should begin with a clear
title and concise description.

------------------------------------------------------------------------

## 6. Homepage design specification

### Section 1: Header

Brand, navigation, global search and theme toggle.

### Section 2: Hero

-   Large clear headline, e.g. "Find, understand and create any
    character."
-   Short supporting description.
-   Prominent Draw & Find action.
-   Optional compact visual of characters or a drawing canvas preview.
-   Avoid oversized hero artwork that pushes the tool cards too far
    down.

### Section 3: Featured tools

Show four to six operational tools in a responsive grid. Each card
has: - consistent icon treatment; - concise title; - one or two lines of
practical description; - one clear interaction/link.

Do not feature tools that do not work.

### Section 4: Browse by category

Pill or compact card links for common groups such as hearts, arrows,
stars, math, currency, Greek letters, music, decorative symbols and
emoji. Only link to real category pages.

### Section 5: Popular/curated characters

Use real usage data if available. Otherwise label it as a curated
selection rather than claiming popularity.

### Section 6: How it works

Explain the distinction between Unicode characters, text-art
approximations and image outputs.

### Section 7: Related tools/guides

Useful internal links, not keyword-stuffed lists.

### Section 8: Footer

Policy and contact links.

------------------------------------------------------------------------

## 7. Tool page template

Every tool page follows a common structure while allowing the tool
itself to determine the workspace layout.

1.  Breadcrumbs, if useful.
2.  Page title and concise purpose statement.
3.  Main tool workspace early in the page.
4.  Tool controls and output with clear visual grouping.
5.  Status, errors and feedback adjacent to the relevant control.
6.  Short instructions or examples.
7.  Useful explanation of formats/limitations.
8.  Related tools.
9.  Relevant guide links.
10. Footer.

Do not force a huge hero on every tool page. Utility visitors should
reach the tool immediately.

### Workspace layout

-   Desktop: two columns where appropriate; inputs on the left and
    results on the right.
-   Mobile: stack input first, results second.
-   Keep the primary action close to the input.
-   Use sticky side panels only if they do not impair mobile or keyboard
    behavior.
-   Do not add decorative cards that make a simple task feel
    complicated.

------------------------------------------------------------------------

## 8. Draw & Find page design

This is the flagship tool and should feel like a focused creative
workspace.

### Page introduction

Title: "Draw a character. Find its text equivalent." Description:
explain that the site can find existing Unicode matches or create a
text-art approximation.

Include a compact note explaining that custom drawings cannot become
universally supported new Unicode characters.

### Desktop workspace

Two principal panels: - **Left --- Your drawing:** canvas, pen, eraser,
undo, redo, stroke width, clear, upload. - **Right --- Results:**
candidate Unicode matches, text-art preview, semantic suggestions when
available, and image download when relevant.

### Canvas

-   Large enough for finger/stylus input.
-   Neutral high-contrast canvas surface in both themes.
-   Subtle grid is optional; if used, keep it unobtrusive.
-   Drawing strokes should remain visible in light and dark mode.
-   Controls must have labels/tooltips and keyboard focus.
-   Use pointer events to unify mouse, touch and stylus behavior.
-   Support undo/redo and clear.
-   Validate image uploads and display a preview before processing.

### Results

Separate result types into clearly labeled cards: 1. Unicode match ---
show glyph, official name, code point and Copy. 2. Approximate match ---
explain that it is similar, not exact. 3. Text art --- monospaced
preview, density/resolution controls and Copy Text. 4. Semantic
suggestion --- label emoji/text combinations as approximations. 5.
Custom image --- preview, Download and Share where supported.

Do not show an invented code point for a custom result. Do not claim
that an image is copyable as ordinary text.

### Interaction states

-   Idle: concise instructions and optional examples.
-   Drawing: responsive controls.
-   Processing: honest progress indication only when processing is
    occurring.
-   Results: grouped and clearly labeled.
-   No match: suggest text art or semantic alternatives.
-   Error: explain the problem and provide retry/reset.
-   Copied: concise accessible feedback.
-   Upload rejected: explain accepted file types/size.

### Mobile

-   Canvas first.
-   Toolbar directly above or below the canvas.
-   Results below the canvas.
-   Full-width primary action.
-   No horizontally overflowing controls.
-   Preserve text-art line breaks and show a warning if the target app
    may alter spacing.

------------------------------------------------------------------------

## 9. Component specifications

Build reusable components with consistent variants and states.

### Buttons

Variants: - Primary: filled brand color. - Secondary: neutral surface
with border. - Ghost: low-emphasis action. - Destructive: reserved for
destructive operations.

Requirements: - clear hover/active/focus/disabled states; - visible
labels for primary actions; - accessible labels for icon-only buttons; -
adequate hit targets on touch devices; - no fake loading state unless an
operation is actually in progress.

### Inputs

-   Visible label or equivalent accessible name.
-   Clear focus border/ring.
-   Error/help text associated with the field.
-   Consistent height and padding.
-   Placeholder is not a substitute for a label.
-   Dark theme must use readable input and placeholder colors.

### Cards

-   White/surface background.
-   Subtle border.
-   Consistent padding and radius.
-   Clear title, supporting text and action.
-   Hover state only when the card is interactive.
-   Do not make an entire card clickable if it contains a conflicting
    copy button; use distinct actions.

### Character cards

-   Character glyph is the visual focus.
-   Official name or concise label.
-   Copy action with feedback.
-   Optional code point in expanded/detail context.
-   Handle missing-glyph rendering gracefully.
-   Keep cards aligned despite differing character names.

### Tabs and filters

-   Indicate selected state with more than color alone.
-   Keyboard navigable.
-   Do not reload the page unnecessarily for local filters.
-   On mobile, allow wrapping or horizontal scrolling with clear
    affordance.

### Dialogs and popovers

-   Correct focus management.
-   Escape/close behavior.
-   Return focus to the trigger.
-   Do not trap focus in non-modal popovers.
-   Ensure content is not clipped at mobile viewport edges.

### Alerts and feedback

-   Success, warning, error and info variants.
-   Use icon plus readable text, not color alone.
-   Announce important dynamic feedback to assistive technology.
-   Avoid intrusive alerts for routine copy actions.

------------------------------------------------------------------------

## 10. Responsive breakpoints and behavior

Use the existing framework breakpoints where possible. Suggested
targets: - Small mobile: below 480px. - Mobile/tablet: 480--767px. -
Tablet/small desktop: 768--1023px. - Desktop: 1024px and above. - Wide
desktop: 1280px and above.

These are guidance, not a reason to create layout jumps. Test actual
content at intermediate widths.

### Responsive rules

-   Desktop grids collapse from 3--4 columns to 2, then 1 as space
    requires.
-   Main tool workspaces stack on mobile.
-   Header navigation collapses on narrow screens.
-   Character glyphs remain visible and do not force cards to expand
    unpredictably.
-   Tables should adapt with horizontal scroll or stacked presentation.
-   Avoid fixed heights for text-heavy cards.
-   Prevent page-level horizontal overflow.
-   Maintain comfortable touch targets and spacing.

------------------------------------------------------------------------

## 11. Dark mode requirements

Dark mode is a full theme, not a simple inversion.

-   Use the specified dark tokens.
-   Keep the same layout, hierarchy, content, logos and functionality as
    light mode.
-   Do not swap logos unless a separately approved dark logo exists.
-   Ensure borders remain visible but subtle.
-   Avoid bright white panels against the dark page unless intentionally
    part of a visual preview.
-   Canvas, text-art preview, code examples and character grids need
    explicit dark-mode review.
-   Uploaded images must not be altered just because the theme changes.
-   Preserve contrast for status indicators and focus rings.
-   Save the preference locally and respect system preference on first
    visit.

------------------------------------------------------------------------

## 12. Motion and micro-interactions

-   Use short, restrained transitions (roughly 120--200ms).
-   Animate hover/focus affordances, panel expansion and copy feedback
    only where helpful.
-   Avoid floating decorative animations and continuous movement.
-   Respect `prefers-reduced-motion`.
-   Do not animate character glyphs in ways that make them difficult to
    inspect.
-   Avoid layout shifts during transitions.

------------------------------------------------------------------------

## 13. Advertising placement rules

-   Ads must be visually distinct from tool controls.
-   Never position an ad so close to Copy, Search, Download or
    navigation controls that accidental clicks are likely.
-   Do not cover the drawing canvas or result panels.
-   Prefer placements after the main tool or between substantial
    explanatory sections.
-   Reserve space to reduce layout shift.
-   Keep ad styling separate from brand styling; do not disguise ads as
    character cards or tool buttons.
-   Only add ads after the page meets the provider's requirements.

------------------------------------------------------------------------

## 14. Accessibility and quality checklist

For every route, confirm: - headings form a logical hierarchy; - every
input has an accessible name; - icon-only buttons have labels; - focus
is visible; - all core actions work by keyboard; - contrast is
sufficient in both themes; - errors and success states are announced
appropriately; - no information is conveyed by color alone; - reduced
motion is respected; - zoom and narrow viewports do not break the
layout; - the canvas has instructions and a non-canvas alternative where
practical; - character glyphs are accompanied by names or descriptions
where needed.

------------------------------------------------------------------------

## 15. Visual QA procedure

Before completing any UI task:

1.  Open the affected route in light mode.
2.  Inspect the same route in dark mode.
3.  Test a narrow mobile width and a desktop width.
4.  Compare spacing, alignment, font scale, borders and card hierarchy
    with this document.
5.  Exercise every visible control.
6.  Check empty, loading, error and success states.
7.  Look for overflow, clipped text, broken glyphs and accidental layout
    shifts.
8.  Confirm there are no placeholder images, dead links or decorative
    controls pretending to work.
9.  Check console/build errors if the environment supports it.
10. Fix inconsistencies before reporting completion.

### Final design standard

The finished product should feel like one coherent, polished character
utility website: calm, fast, accessible, precise and immediately usable.
Consistency is more important than adding visual effects or inventing a
new style for each tool.
