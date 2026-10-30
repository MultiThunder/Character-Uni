# The Character Universe --- Project Blueprint

**Document type:** Product and implementation specification\
**Status:** Authoritative project brief\
**Audience:** AI coding agents, frontend developers, product designers
and maintainers\
**Product tagline:** Every character has a story.

------------------------------------------------------------------------

## 0. Instructions to the coding agent

Treat this document as the product contract. Read it before making
changes. Follow it unless the user explicitly changes a requirement.

### Non-negotiable rules

1.  **Inspect before editing.** Examine the existing repository,
    framework, package scripts, routes, design files, assets and
    conventions before changing anything. Do not replace a working stack
    merely because another stack is preferred.
2.  **Preserve working functionality.** Do not remove, rename or
    redesign unrelated working features. Avoid broad rewrites. Make
    focused, reversible changes.
3.  **Follow `DESIGN_SYSTEM.md`.** It is the visual source of truth for
    colors, typography, spacing, layout, responsive behavior,
    components, dark mode and interaction states.
4.  **Implement real behavior.** Never leave a visible button, search
    field, tab, theme switch, drawing tool, copy action or filter inert.
    If a feature is not implemented, mark it clearly as unavailable or
    keep it out of the live navigation.
5.  **Do not fabricate Unicode.** A custom drawing, AI description or
    internal ID is not a Unicode character. Only display a code point,
    official Unicode name, category or encoding when it is grounded in
    verified data or a correct algorithm.
6.  **Distinguish result types.** Label an exact character match,
    approximate match, Unicode text-art result, semantic emoji
    suggestion and image output separately.
7.  **Do not expose secrets.** API keys must never be embedded in
    client-side code. Optional remote AI features must be isolated
    behind a server-side adapter and must degrade gracefully when
    unavailable.
8.  **Privacy by default.** Do not transmit pasted text or drawings to a
    remote service without clear disclosure. Prefer local processing. Do
    not log user content in analytics.
9.  **No fake data presented as real.** Sample data may be used in
    development but must be clearly marked and must not be presented as
    verified search popularity, device compatibility or Unicode
    metadata.
10. **No placeholder polish.** Avoid decorative controls that do
    nothing, empty sections, broken image placeholders, lorem ipsum,
    fake testimonials, invented statistics and "coming soon" links that
    look operational.
11. **Use Git safely.** Inspect status before changes, preserve user
    work, make focused changes and report modified files. Never
    overwrite user work or run destructive Git commands without explicit
    approval.
12. **Verify the result.** Run available lint, type-check, build and
    test scripts. Fix issues introduced by the change. If a command
    cannot be run, say so plainly.

### Required workflow for each task

1.  Read this file and `DESIGN_SYSTEM.md`.
2.  Inspect the relevant implementation and identify the smallest
    coherent change.
3.  State a concise implementation plan before a large multi-file
    change.
4.  Implement the behavior and design together.
5.  Test desktop, mobile and both themes where relevant.
6.  Check keyboard navigation, focus states, loading, empty, success and
    error states.
7.  Run repository checks.
8.  Summarize what changed, what was tested, any limitations and any
    required environment variables.

Do not ask the user to repeat requirements already documented here. Ask
a question only when a missing decision materially blocks
implementation.

------------------------------------------------------------------------

## 1. Product overview

The Character Universe is a free, browser-based character discovery and
text utility website. It helps people find, understand, inspect,
compare, create, copy and reuse Unicode characters, symbols and
text-based representations.

The product should have the immediate utility of a focused online tool
website: open a page, complete a task quickly and copy or download a
usable result. It should not feel like a generic chatbot, a social
network or an unfocused AI directory.

### Primary differentiator

**Draw & Find** lets a visitor sketch a symbol and receive: - possible
existing Unicode character matches; - relevant character details and
code points when verified; - a text-art representation generated from
the drawing; - semantic alternatives such as existing emoji combinations
where appropriate; - an optional image output when preserving the exact
drawing is more useful than text.

The product must explain that these are different output types. An
arbitrary drawing cannot be made into a universally supported new
Unicode character merely by using AI.

### Product goals

-   Make common character tasks quick and accessible.
-   Make copy/paste the primary action wherever text output exists.
-   Support a coherent family of tools sharing one design system.
-   Keep deterministic tools fast and local when possible.
-   Create useful, indexable pages for distinct search intents without
    generating thin duplicate pages.
-   Provide a foundation for compliant advertising after the site is
    useful and ready.
-   Keep operating costs and maintenance reasonable for a solo
    developer.

### Non-goals

-   Do not build a new keyboard application in the initial release.
-   Do not claim custom characters work on every device.
-   Do not invent Unicode code points or official names.
-   Do not make every feature dependent on a paid AI model.
-   Do not require accounts for ordinary tool usage.
-   Do not publish mass-generated low-value character pages merely to
    increase page count.
-   Do not promise exact device/font compatibility when the browser
    cannot verify it.

------------------------------------------------------------------------

## 2. Users and primary jobs

### User groups

1.  **Everyday users:** need a symbol to copy into a chat, post,
    username or document.
2.  **Students and writers:** need mathematical, linguistic, scientific
    or typographic characters.
3.  **Developers and technical users:** need code points, escape forms,
    encoding details and text diagnostics.
4.  **Designers and creators:** need visual alternatives, text art and
    font previews.
5.  **Troubleshooters:** need to identify hidden or confusing characters
    in copied text.

### Core user journeys

**Find and copy a symbol** 1. Open Symbol Finder. 2. Search by name,
category, visible character or supported alias. 3. Review results. 4.
Copy the selected character. 5. Optionally open the detail page.

**Inspect suspicious or broken text** 1. Paste text into Text Inspector.
2. See a readable character-by-character breakdown. 3. Identify
invisible, nonprinting or confusing characters. 4. Select a proposed
cleanup action. 5. Preview changes before copying cleaned text.

**Convert a drawing** 1. Draw or upload an image in Draw & Find. 2.
Preview the normalized drawing. 3. Run local text-art conversion and
available character matching. 4. Review clearly labeled results and
confidence/limitations. 5. Copy a character or text-art output, or
download an image.

**Understand a character** 1. Search by name, glyph or code point. 2.
Open a verified character detail page. 3. Read its official metadata and
encoding information. 4. Copy it or explore related characters.

------------------------------------------------------------------------

## 3. Information architecture

Build a multi-page site with shared navigation and components. Keep the
URL structure readable and stable.

### Main routes

-   `/` --- Homepage
-   `/tools/` --- All tools
-   `/draw-symbol/` --- Draw & Find
-   `/text-art/` --- Unicode Text Art Generator
-   `/symbol-finder/` --- Symbol Finder
-   `/characters/` --- Character Library
-   `/unicode/` --- Unicode Explorer
-   `/text-inspector/` --- Text Inspector
-   `/lookalike-characters/` --- Lookalike Character Detector
-   `/compare-characters/` --- Character Comparison
-   `/unicode-converter/` --- Unicode Converter
-   `/font-preview/` --- Font Preview
-   `/character-compatibility/` --- Character Compatibility Checker
-   `/copy-paste/` --- Copy & Paste Board
-   `/emoji-symbol-finder/` --- Emoji & Symbol Alternative Finder
-   `/guides/` --- Educational guides
-   `/about/`, `/contact/`, `/privacy/`, `/terms/`, `/disclaimer/` ---
    Supporting pages

Character detail routes may use `/characters/<slug>/`. Only create
indexable detail pages when there is accurate, useful data and
meaningful page content.

### Main navigation

-   Home
-   All Tools
-   Character Library
-   Guides
-   Search
-   Theme toggle

On narrow screens, collapse navigation into an accessible menu. Do not
hide the main task behind excessive navigation.

### Homepage section order

1.  Compact global header.
2.  Hero introducing the website and its main value.
3.  Prominent Draw & Find call to action.
4.  Featured tools (four to six, all operational).
5.  Browse by category.
6.  Popular or curated characters, only when popularity data is real or
    the section is explicitly curated.
7.  Short "How it works" explanation.
8.  Related tools and useful guides.
9.  Footer with policy and contact links.

Do not show every possible character on the homepage. Optimize for quick
discovery and clear hierarchy.

------------------------------------------------------------------------

## 4. Tool inventory and behavior

Implement tools in phases. The architecture may anticipate the full
suite, but do not expose nonfunctional tools as completed.

### Phase 1 --- MVP

#### 4.1 Draw & Find

**Purpose:** Turn a sketch into useful, clearly labeled text or
character results.

Inputs: - touch/mouse/stylus drawing canvas; - image upload with
validation and size limits; - pen width, eraser, undo/redo and clear; -
example drawings for first-time use.

Processing: - normalize crop, background and scale; - produce a
deterministic text-art conversion locally; - search verified character
data for plausible matches; - optionally call a separately configured
semantic-recognition adapter; - rank candidates without inventing
Unicode metadata.

Outputs: - exact/strong Unicode match, if verified; - approximate
Unicode match; - text-art conversion; - semantic suggestion using
existing characters/emoji; - image download when text cannot preserve
the drawing.

Each result must have a clear label and the appropriate action. Copy
only actual text. Download images as images. Do not call a description
or custom identifier a Unicode character.

States: - idle/instructions; - drawing in progress; - processing; -
results; - no match; - invalid/oversized upload; - unsupported
feature/service unavailable; - error with retry; - copied/downloaded
confirmation.

#### 4.2 Unicode Text Art Generator

-   Accept drawing canvas or image upload.
-   Provide width/resolution, brightness threshold, contrast and invert
    controls.
-   Offer supported palettes such as Braille, block elements and
    ASCII-like characters, with correct output labels.
-   Preserve aspect ratio as reasonably as possible.
-   Preview in a monospaced font.
-   Copy plain text and download `.txt`.
-   Warn that chat apps may collapse spaces or alter monospaced
    alignment.
-   Keep deterministic conversion local.

#### 4.3 Symbol Finder

-   Search by visible character, official name, curated alias and
    category.
-   Category filters for hearts, arrows, stars, math, currency, Greek
    letters, music, decorative symbols, emoji and other verified groups.
-   Responsive character grid.
-   One-click copy with accessible feedback.
-   Character card click opens details; Copy must not unexpectedly
    navigate.
-   Useful empty state with suggested categories or alternative terms.

#### 4.4 Character Library

-   Browse by category, script and Unicode block where data supports it.
-   Character detail pages show the actual glyph, official name, code
    point, block, general category and relevant metadata.
-   Include UTF-8/UTF-16 or HTML representations only when correctly
    computed.
-   Explain when a displayed item is a multi-code-point sequence.
-   Show related characters based on verified relationships.
-   Avoid mass-publishing thin pages.

#### 4.5 Unicode Explorer

-   Search official name, code point and supported aliases.
-   Browse available Unicode blocks.
-   Show verified code point metadata.
-   Distinguish code point, encoded bytes, UTF-16 code units and
    multi-code-point sequences.
-   Handle invalid input without crashing.

#### 4.6 Text Inspector

-   Accept pasted or typed text.
-   Visualize spaces, tabs, line breaks and selected nonprinting
    characters.
-   Show each code point, name when available, and string position with
    clearly defined indexing semantics.
-   Identify zero-width characters, bidirectional controls and other
    potentially relevant formatting characters.
-   Provide proposed cleanup as a preview; never silently mutate the
    input.
-   Keep input local and do not log its content.

### Phase 2 --- Supporting tools

#### 4.7 Lookalike Character Detector

Compare visually similar characters and identify potentially confusing
mixed-script text. Show code points and scripts where verified. Explain
that similarity is contextual and does not prove malicious intent.

#### 4.8 Character Comparison

Compare two or more characters/sequences by glyph, name, code point
sequence, script, category and normalization behavior. Support
multi-code-point strings.

#### 4.9 Unicode Converter

Support well-defined conversions between literal text, code point
notation, JavaScript-style Unicode escapes, HTML entities, UTF-8 bytes
and UTF-16 code units. Each mode must state its format. Validate
malformed input.

#### 4.10 Copy & Paste Board

Allow users to assemble and reorder a string of characters, copy the
complete string and optionally store favorites locally. Provide
clear/reset and import/export where implemented.

#### 4.11 Font Preview

Preview entered text in fonts available to the page/browser. Do not
claim access to fonts that are not loaded or installed. Warn about
likely missing glyphs only when detection is supported.

#### 4.12 Character Compatibility Checker

Inspect a string for known compatibility concerns and test the current
browser rendering environment where possible. Do not promise universal
device/app compatibility.

#### 4.13 Emoji & Symbol Alternative Finder

Search existing emoji and character data using a short description.
Optional AI may suggest semantic matches, but every returned character
must be validated against a real dataset. Clearly label combinations and
approximations.

### Release policy

-   MVP: Draw & Find, Text Art, Symbol Finder, Character Library,
    Unicode Explorer, Text Inspector.
-   Phase 2: Lookalike Detector, Character Comparison, Unicode
    Converter, Copy & Paste Board.
-   Phase 3: Font Preview, Compatibility Checker, semantic AI
    suggestions and advanced recognition.

The codebase must not display unfinished Phase 2/3 tools as operational.
If a route exists before implementation, either keep it out of the
primary navigation or display an honest, non-deceptive status page.

------------------------------------------------------------------------

## 5. Shared behavior requirements

### Copy actions

-   Use the Clipboard API when available and handle
    permission/secure-context failures.
-   Provide a fallback when feasible.
-   Show accessible success/failure feedback.
-   Never claim copying succeeded before the operation succeeds.
-   Preserve meaningful whitespace and line breaks for text art.
-   Keep Copy separate from card navigation.

### Search

-   Support keyboard submission and clear input.
-   Show loading only when actual asynchronous work occurs.
-   Include empty and no-result states.
-   Do not fabricate result counts or popularity.
-   Debounce remote queries where appropriate; local search should feel
    immediate.

### Theme

-   Support light and dark themes consistently.
-   Persist the user preference locally.
-   Respect system preference on first visit unless a saved preference
    exists.
-   Avoid flashes of the wrong theme where the current framework
    supports early theme initialization.
-   Every component, drawing workspace, tooltip, modal, code panel and
    ad placeholder must remain legible in both themes.

### Forms and uploads

-   Label inputs and errors.
-   Validate file type and size.
-   Explain unsupported inputs.
-   Never execute uploaded files or treat their contents as
    instructions.
-   Avoid uploading user content to external services without clear
    notice.

### Navigation and responsive behavior

-   All links must have real destinations.
-   All buttons must perform their advertised actions.
-   Provide visible focus styles and keyboard support.
-   Use semantic HTML and accessible labels.
-   On mobile, stack workspace panels and keep primary actions
    reachable.

------------------------------------------------------------------------

## 6. Technical architecture

### Preferred approach

Use the repository's existing framework if it is already functional. If
the project is not yet established, a reasonable default is Next.js,
TypeScript, React and Tailwind CSS with reusable accessible components.

Do not migrate frameworks without a specific, documented reason.

### Architectural layers

1.  **Presentation:** shared layout, navigation, cards, inputs, tool
    panels, themes.
2.  **Tool logic:** independent modules for drawing, text inspection,
    conversion and comparison.
3.  **Character data:** versioned, validated Unicode metadata and
    curated aliases.
4.  **Optional AI adapter:** server-side only; disabled cleanly when not
    configured.
5.  **Analytics adapter:** aggregate events without capturing
    user-entered text/drawings.

### Suggested module boundaries

-   `components/layout/` --- header, footer, navigation, page shell.
-   `components/ui/` --- buttons, fields, cards, dialogs, alerts, tabs.
-   `components/characters/` --- character cards, details, metadata
    panels.
-   `components/drawing/` --- canvas, toolbar, upload and preview.
-   `components/tools/` --- shared tool-page building blocks.
-   `lib/unicode/` --- parsing, validation, code point/sequence
    utilities.
-   `lib/text/` --- inspection, escaping, normalization and text-art
    algorithms.
-   `lib/drawing/` --- canvas normalization and deterministic
    conversion.
-   `lib/search/` --- local character search and ranking.
-   `lib/ai/` --- optional server-side recognition adapter.
-   `data/unicode/` --- validated versioned data files.
-   `app/` or the equivalent route directory --- route-specific pages.

Adapt this structure to existing repository conventions rather than
creating duplicate abstractions.

### Unicode data rules

-   Use a documented Unicode version.
-   Preserve source/version attribution.
-   Keep official names separate from curated aliases and descriptions.
-   Validate code points and sequences.
-   Do not infer an official name from a visual description.
-   Distinguish a single code point from a sequence of code points.
-   Treat emoji sequences and variation selectors correctly.
-   Do not assume that every code point has a visible glyph in every
    font.

### AI integration rules

-   AI is optional and not required for deterministic tools.
-   Use an interface such as `recognizeDrawing()` so the provider can
    change.
-   Keep credentials server-side in environment variables.
-   Validate model output against the character dataset.
-   Treat model output as untrusted and potentially incorrect.
-   Provide timeout, error and unavailable states.
-   Never invent code points from model output.
-   Disclose remote processing before sending drawings or images.
-   Do not store submitted images unless the user explicitly requests a
    feature that requires it and the storage behavior is disclosed.

### Performance

-   Keep initial bundles small.
-   Lazy-load expensive drawing/preview code when useful.
-   Load only relevant character data where feasible.
-   Cache static assets.
-   Avoid remote requests for deterministic operations.
-   Reserve layout space for deferred content.
-   Do not sacrifice accessibility or tool correctness for superficial
    speed scores.

------------------------------------------------------------------------

## 7. SEO and content requirements

### Page-level requirements

Every indexable page needs: - a unique, accurate title; - a useful meta
description; - a canonical URL; - one clear primary purpose; -
meaningful visible content; - logical internal links; - correct heading
hierarchy; - responsive and accessible controls.

### Indexation rules

-   Provide an XML sitemap for canonical, indexable pages.
-   Configure `robots.txt` correctly.
-   Do not index empty search result URLs, arbitrary filter combinations
    or low-value parameter URLs.
-   Use server rendering/static generation where suitable for reference
    content.
-   Ensure important content is present in the rendered HTML where
    possible.
-   Only use structured data when it accurately represents the page and
    complies with the applicable specification.
-   Do not generate mass near-duplicate pages simply by swapping a glyph
    into a template.

### Content quality

A character detail page should include verified metadata, a copy action,
relevant encoding information, meaningful usage notes and related
characters where available. A tool page should put the working tool
early in the page and explain input/output formats and limitations.

Do not pad pages with repetitive prose solely to increase word count.

### Analytics

Track aggregate events such as tool opened, search submitted, copy
succeeded/failed, conversion completed and error type. Do not send
actual pasted text, drawings or uploaded images to analytics.

------------------------------------------------------------------------

## 8. Monetization and advertising

The intended initial business model is free access supported by
advertising, subject to approval and policy compliance.

-   Keep core functionality accessible without an account.
-   Do not place ads so close to character cards or copy buttons that
    accidental clicks are likely.
-   Do not cover the canvas, results or main controls with ads.
-   Reserve ad space where appropriate to reduce layout shift.
-   Clearly distinguish ads from tool controls and content.
-   Do not promise a particular income or RPM.
-   Prioritize usefulness, speed, content quality and trust over ad
    density.

Only integrate the ad provider after the site is sufficiently complete
and complies with applicable policies.

------------------------------------------------------------------------

## 9. Privacy, security and accessibility

### Privacy

-   Prefer local processing for text and drawing tools.
-   Disclose any external AI processing before upload/transmission.
-   Do not log user content.
-   Keep local favorites optional and allow clearing them.
-   Make the privacy policy reflect actual analytics, hosting,
    advertising and third-party integrations.

### Security

-   Keep secrets server-side.
-   Validate and limit uploads.
-   Sanitize any user-controlled text rendered as HTML.
-   Do not execute content from uploaded files.
-   Use secure headers and safe dependencies appropriate to the existing
    stack.
-   Rate-limit remote AI endpoints if implemented.

### Accessibility

-   Keyboard navigation and visible focus.
-   Semantic headings and form labels.
-   Screen-reader labels for icon-only buttons.
-   Appropriate contrast in both themes.
-   Reduced-motion support.
-   Accessible error and copy feedback.
-   Text alternatives for drawing interactions.
-   Do not communicate status by color alone.

------------------------------------------------------------------------

## 10. Testing and acceptance criteria

Before calling a feature complete, verify:

### Functional

-   Search returns the expected results for representative inputs.
-   Copy actions copy the correct character/string and handle failures.
-   Invalid code points and malformed encodings do not crash the page.
-   Text Inspector handles newlines, tabs, combining marks, surrogate
    pairs and multi-code-point sequences correctly.
-   Text Art output is actual copyable text and its preview reflects the
    output.
-   Draw & Find labels exact matches, approximations, text art and
    images accurately.
-   Upload validation, undo/redo, clear and retry behavior work.
-   No visible control is inert.

### Visual

-   Compare implementation with `DESIGN_SYSTEM.md`.
-   Test common desktop, tablet and mobile widths.
-   Test light and dark themes.
-   Check spacing, alignment, clipping, overflow and loading states.
-   Confirm the main tool is visible early on the page.
-   Check that the design remains coherent across all tool routes.

### Quality

-   Run the repository's lint, type-check, test and build scripts when
    available.
-   Fix errors introduced by the change.
-   Check console errors and broken links.
-   Verify metadata and canonical URLs on important pages.
-   Report tests that could not be run rather than claiming success.

### Completion report

At the end of a task, report: 1. What changed. 2. Files added/modified.
3. Functionality implemented. 4. Tests/commands run and results. 5.
Known limitations or follow-up work.

------------------------------------------------------------------------

## 11. Development order

1.  Inspect repository and establish a baseline.
2.  Implement shared design tokens and responsive shell.
3.  Implement homepage and navigation.
4.  Add validated Unicode data and common character components.
5.  Implement Symbol Finder and Character Library.
6.  Implement Unicode Explorer and Text Inspector.
7.  Implement deterministic Text Art Generator.
8.  Implement Draw & Find using local matching first.
9.  Add remaining Phase 2 tools.
10. Add optional AI recognition only after the deterministic flow is
    stable.
11. Complete SEO, accessibility, performance and privacy checks.
12. Prepare launch and advertising integration when eligible.

Do not attempt every tool in one unreviewed giant change. Build, test
and checkpoint in coherent stages.

------------------------------------------------------------------------

## 12. Definition of done

The project is ready for its first public release when: - the core
routes work; - all advertised MVP tools are functional; - the design
system is consistent across light/dark and mobile/desktop; - no code
point or official metadata is fabricated; - copy/paste behavior has been
tested; - privacy and policy pages reflect actual behavior; - canonical
metadata and sitemap are configured; - no critical build/lint/test
errors remain unresolved; - known limitations are documented; - the user
can revert changes using Git.

**Final instruction:** Favor correctness, clarity, maintainability and
visual consistency over adding more features quickly. The result should
feel like one professionally designed utility product, not a collection
of unrelated AI-generated pages.
