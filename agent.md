# Codex Project Guide: DigiGovSA Static Landing Page

This file is for future Codex sessions working in this repository. Follow it before editing so changes enhance the site without breaking the current visual system, file structure, or static deployment model.

## Project Purpose

This repository contains a static DigiGovSA landing page built from real HTML, CSS and vanilla JavaScript. The design should continue to feel clean, modern, government-grade, trustworthy and aligned with the supplied screenshots:

- White sticky header with DigiGovSA and National Treasury lockup
- Large photographic hero using `assets/hero-digigov.jpg`
- Pale blue-grey content bands
- Dark navy security and CTA sections
- Rounded white cards with soft borders and shadows
- Green accent icons and buttons
- Strong navy headings and muted grey body text

Do not turn the page into a screenshot-only implementation. Text, sections, cards, buttons and navigation must remain real, accessible HTML.

## File Map

- `index.html`: Semantic page structure, inline SVG icon sprite, all section content.
- `css/styles.css`: Design tokens, layout system, component styles and responsive rules.
- `js/main.js`: Small vanilla JavaScript behaviours only.
- `assets/hero-digigov.jpg`: Active hero image.
- `assets/logos/digigovsa-logo.png`: Active DigiGovSA logo for header, footer and favicon.
- `assets/logos/*.png`: Partner logos used in the collaboration strip.
- `README.md`: User-facing run and editing notes.

Keep this structure unless the user explicitly requests a larger reorganisation.

## Technology Constraints

- Use static HTML5, modern CSS and vanilla JavaScript only.
- Do not add React, Vue, Tailwind, Bootstrap, build tools, package managers or framework dependencies.
- Do not introduce generated bundles, minified files or external runtime dependencies.
- Keep JavaScript small and readable. It should only support behaviour such as smooth scrolling, mobile navigation, keyboard handling and minor progressive enhancement.
- Prefer CSS and semantic HTML over JavaScript for layout or visual presentation.

## Visual System

Use the existing CSS custom properties in `css/styles.css` as the source of truth. If a new colour, radius, shadow, spacing scale or layout constant is genuinely needed, add it to `:root` and reuse it consistently.

Current core tokens:

- `--navy`, `--navy-dark`, `--navy-deep`, `--navy-ink`
- `--green`, `--green-strong`, `--green-soft`
- `--orange`
- `--text`, `--muted`, `--muted-light`
- `--bg-soft`, `--border`, `--white`
- `--shadow-soft`, `--shadow-card`
- `--container`, `--header-height`, `--section-space`
- `--radius-sm`, `--radius-md`, `--radius-lg`

Preserve the restrained palette. Avoid introducing decorative gradients, one-off colours, ornate backgrounds, decorative blobs or marketing-page effects that are not present in the current design language.

## Layout Rules

- Keep `.container` as the central width utility with a max width around the current `1280px`.
- Keep desktop section padding generous and reduce it through the existing media queries.
- Preserve the page flow:
  1. Header / navigation
  2. Hero
  3. Collaboration logo strip
  4. The Case for Change
  5. New Approach
  6. Trust, Identity & Security
  7. Building on Experience
  8. Final CTA
  9. Footer
- Do not wrap whole page sections in extra decorative cards. Cards should remain individual repeated items, comparison panels, the timeline panel and the final CTA.
- Do not nest UI cards inside other UI cards.
- Keep rounded corners close to the existing radii: cards around `18px`, large panels around `24px` to `28px`.
- Preserve responsive behaviour:
  - Four-card grids become two columns on tablet and one column on mobile.
  - Three-card grids become one column below the tablet breakpoint.
  - The navigation collapses below roughly `900px`.
  - The hero must stay readable on mobile with a darker overlay.
  - Avoid horizontal scrolling except the timeline fallback.

## Typography and Copy

- Use the current modern sans-serif stack in `--font-sans`.
- Keep heading type bold, compact and navy on light sections.
- Keep dark-section headings white with muted pale body text.
- Do not use viewport-based font sizing.
- Keep `letter-spacing: 0` unless preserving the existing uppercase eyebrow treatment.
- Use British English spelling: modernise, modernisation, centre, programme, etc.
- Maintain a formal, credible public-sector tone. Avoid casual marketing phrases.

## Assets

- Use the PNG logo at `assets/logos/digigovsa-logo.png` for the DigiGovSA brand mark. Do not replace it with a recreated SVG unless the user explicitly asks.
- Keep partner logos in `assets/logos/` and use `<img>` with meaningful `alt` text.
- The active hero is `assets/hero-digigov.jpg`. CSS references it through `.hero`.
- If adding assets, use clear lowercase kebab-case names and place them in the relevant `assets/` subfolder.
- Do not use screenshots as full-page backgrounds or section images to fake the layout.
- Compress large new assets where practical, but do not degrade the supplied brand assets.

## HTML Guidelines

- Preserve semantic landmarks: `header`, `nav`, `main`, `section`, `article`, `footer`.
- Keep major section comments in `index.html`; add similar comments for new major sections.
- Use headings in a logical order. Do not skip heading levels for visual reasons.
- Reuse existing component structures:
  - `.feature-card` for light-section cards
  - `.comparison-card` for approach comparisons
  - `.security-card` for dark-section feature cards
  - `.highlight-panel` for the security highlight
  - `.timeline-card` and `.timeline-step` for the timeline
  - `.cta-card` for the final call to action
- Keep the inline SVG sprite if adding icons; add new symbols there and reference them with `<use>`.
- Decorative icons should be `aria-hidden="true"`.
- Links and buttons must have clear accessible names.

## CSS Guidelines

- Edit `css/styles.css`; do not add inline styles.
- Keep component styles grouped near related existing selectors.
- Prefer extending existing classes over creating near-duplicates.
- Use grid and flexbox consistently with the current implementation.
- Keep selectors straightforward and maintainable. Avoid over-specific selectors that make future changes brittle.
- Use fixed dimensions or min-heights for repeated cards where needed to avoid layout shift.
- Ensure text does not overflow buttons, cards or narrow mobile containers.
- If a new section repeats an existing pattern, use existing spacing, cards, icons and heading classes first.

## JavaScript Guidelines

- Keep `js/main.js` dependency-free.
- Preserve current behaviours:
  - Header shadow after scroll
  - Mobile menu toggle with `aria-expanded`
  - Escape key closes mobile menu
  - Smooth scrolling for same-page anchors
  - Mobile menu closes after selecting a link
- Do not use JavaScript to render core content that should be present in HTML.
- If adding behaviour, make it progressive and safe when JavaScript fails.
- Respect `prefers-reduced-motion`.

## Accessibility Requirements

- Keep visible focus states.
- Maintain good colour contrast, especially on dark navy sections and green buttons.
- Keep all image `alt` text meaningful unless an image is purely decorative.
- Ensure the hamburger menu remains keyboard accessible.
- Do not remove the skip link.
- Do not rely on colour alone to communicate important states.
- Verify that internal links scroll to meaningful section starts and are not hidden behind the sticky header.

## Responsive QA Checklist

Before finishing meaningful visual changes, verify:

- Desktop at roughly `1440px` and `1920px` wide.
- Tablet around `768px` to `900px`.
- Mobile around `375px` to `430px`.
- No unexpected horizontal scroll.
- Header logo and CTA fit without overlap.
- Mobile menu opens, closes, and updates `aria-expanded`.
- Hero copy remains readable.
- Cards align and stack cleanly.
- Timeline is usable on narrow screens.
- Footer links wrap without collision.

## Browser Verification

For local QA, serve the folder:

```sh
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

Check the browser console for warnings or errors after changing HTML, CSS, JavaScript, images or links.

## Editing Workflow for Future Codex Sessions

1. Read this file, `README.md`, and the relevant parts of `index.html`, `css/styles.css` and `js/main.js`.
2. Identify whether the request is a content change, asset swap, visual adjustment, responsive fix or behaviour change.
3. Make the smallest scoped edit that satisfies the request.
4. Preserve existing class names and section structure unless changing them is necessary.
5. Run a quick static check with `rg` for broken references after asset or filename changes.
6. Verify in the browser for visual or interactive changes.
7. Report the changed files and any verification performed.

## Common Safe Changes

- Editing card copy inside existing `<article>` blocks.
- Adding a new card by duplicating the matching existing card structure.
- Adjusting section spacing through existing tokens or media queries.
- Swapping logos or hero images while keeping the same file paths or updating all references.
- Adding one or two new icon symbols to the inline sprite and reusing `.icon` styles.
- Improving responsive behaviour without changing desktop layout.

## Changes to Avoid Unless Explicitly Requested

- Replacing the static site with a framework app.
- Moving CSS into inline styles.
- Removing the sticky header or mobile navigation.
- Replacing real text sections with image screenshots.
- Changing the DigiGovSA logo away from `assets/logos/digigovsa-logo.png`.
- Introducing heavy animation, decorative blobs, stock imagery or unrelated visual motifs.
- Renaming established section IDs used by navigation: `#top`, `#why-digigov`, `#approach`, `#trust-security`, `#get-connected`.
- Removing accessibility attributes, focus states or the skip link.
- Reformatting the whole codebase when only a targeted edit is needed.

## Final Quality Bar

The site should remain pixel-close to the supplied DigiGovSA screenshots, easy to maintain, static-hosting friendly, accessible, responsive and free of console errors. Future enhancements should feel like they were part of the original design system, not bolted on.
