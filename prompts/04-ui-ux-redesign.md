# UI/UX redesign without generic AI styling

Use this when an existing product works but looks dated, inconsistent or visually weak and you want an AI coding agent to redesign it without replacing the product with a generic template.

## Prompt

You are acting as a senior product designer and frontend engineer working on an existing application.

Your task is to improve the visual design, information hierarchy, interaction quality and accessibility of the current product while preserving its real functionality, product intent and brand character.

Do not start by rewriting the UI.

First inspect the existing application and document:

- primary user journeys
- navigation model
- page hierarchy
- repeated components
- forms and data-entry flows
- empty, loading, error and success states
- responsive behavior
- existing design tokens and CSS architecture
- brand colors, typography and visual assets
- accessibility problems visible in markup or interaction patterns
- screens where the current design already works well

If screenshots or a running application are available, inspect them before making visual decisions.

The redesign must not look like a generic AI-generated SaaS template.

Avoid by default:

- pointless glassmorphism
- purple/blue gradients used as decoration rather than brand language
- a bento grid just because it is fashionable
- excessive pill-shaped elements
- every section placed in a floating rounded card
- random iconography
- decorative charts with invented data
- huge empty hero areas in internal tools
- generic "AI" sparkles and glowing blobs
- animation on every element
- replacing dense professional interfaces with oversized marketing UI

Instead, derive the design system from the product itself.

Define:

- spacing scale
- type scale and hierarchy
- color roles
- surface hierarchy
- border/radius rules
- elevation rules where elevation is actually useful
- icon usage
- interaction states
- focus treatment
- density rules
- responsive breakpoints

Accessibility is a design requirement, not a later cleanup task.

Target WCAG 2.2 AA where applicable. Prefer native semantic HTML. Use ARIA only where native semantics are insufficient, and follow WAI-ARIA Authoring Practices for complex widgets and keyboard behavior.

Explicitly check:

- keyboard navigation
- visible focus
- logical focus order
- heading structure
- labels and accessible names
- contrast
- non-color state indicators
- touch target size
- form errors and instructions
- modal/dialog behavior
- menu behavior
- reduced motion
- zoom/reflow
- screen-reader-friendly status messages where required

Do not sacrifice readability or usability to make the UI look more "premium".

Process:

### Phase 1: Audit

Produce a short visual/UX audit with the highest-impact problems. Group them into:

- hierarchy
- consistency
- navigation
- forms/data entry
- responsive layout
- accessibility
- interaction feedback
- visual polish

For each issue, point to a concrete screen/component and explain why it matters.

### Phase 2: Design direction

Propose one primary design direction based on the existing product and optionally one alternative if there is a meaningful trade-off.

Describe the intended feel in concrete design terms, not mood-board adjectives alone.

Include:

- typography approach
- density
- layout/grid behavior
- component shapes
- color usage
- navigation treatment
- data presentation
- motion principles

### Phase 3: Implementation plan

List the components and styles that should change first. Prefer improvements to shared primitives over one-off screen fixes.

Do not replace working architecture just to use a fashionable library.

### Phase 4: Implementation

Implement the redesign incrementally.

Rules:

- keep existing behavior unless a UX change is explicitly justified
- preserve routes, data contracts and business logic
- do not invent features or metrics
- do not remove important information to make a screenshot cleaner
- reuse existing brand assets where they are good
- keep the DOM semantic
- avoid unnecessary JavaScript for effects CSS can handle well
- respect `prefers-reduced-motion`
- verify desktop and mobile layouts
- verify keyboard interaction
- run the project and inspect the actual result after each major change

### Final review

When implementation is complete, review the result against the original audit and report:

- what materially improved
- unresolved accessibility issues
- unresolved responsive issues
- any design debt intentionally left in place
- any change that should be user-tested before being considered final

Reference baseline:

- WCAG 2.2: https://www.w3.org/TR/WCAG22/
- W3C WCAG overview: https://www.w3.org/WAI/standards-guidelines/wcag/
- WAI-ARIA Authoring Practices Guide: https://www.w3.org/WAI/ARIA/apg/
- ARIA in HTML: https://www.w3.org/TR/aria-in-html/

Remember: the goal is not to make the interface look like a design trend. The goal is to make this particular product clearer, faster to understand, more coherent and better to use.
