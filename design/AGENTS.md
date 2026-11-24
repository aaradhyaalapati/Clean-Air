# Agent Instructions — Adaptive Product Design & UX Toolkit

This repository contains product-quality rules, not a visual template. Do not impose a shared aesthetic across unrelated projects.

## Before changing a UI

1. Inspect the existing repository, product purpose, users, brand, framework, routes, and current rendered interface.
2. Read `00-CORE-PRINCIPLES.md` first.
3. Read only the relevant specialist files:
   - Visual direction or styling: `01-VISUAL-DESIGN.md`
   - Components, flows, forms, navigation, feedback, or motion: `02-UX-INTERACTION.md`
   - Loading, rendering, caching, security, reliability, or implementation: `03-PERFORMANCE-ENGINEERING.md`
   - Accessibility or responsive behavior: `04-ACCESSIBILITY-RESPONSIVE.md`
   - Planning, verification, and final review: `05-AGENT-WORKFLOW-AND-AUDITS.md`
   - Need to verify a source or understand attribution: `06-REFERENCES-AND-ATTRIBUTION.md`

## Non-negotiable behavior

- Derive a distinct visual direction from the actual product. Never apply a default palette, typography pairing, hero layout, card grid, or animation style just because it is familiar.
- Preserve good existing work. Do not redesign for the sake of visible code changes.
- Prefer semantic HTML and established accessible interaction patterns over custom widgets.
- Implement complete states: loading, empty, error, success, disabled, validation, and permission states where they can occur.
- Preserve user input and context during errors and navigation wherever possible.
- Treat performance, accessibility, security, and data integrity as product quality—not optional polish.
- Inspect the actual rendered UI at relevant viewport sizes. Do not claim visual verification if you did not perform it.
- Do not claim tests, builds, audits, or browser checks passed unless you ran them.

## Rule interpretation

The specialist documents use three levels:
- **MUST:** required unless technically impossible or in direct conflict with a higher-priority requirement.
- **SHOULD:** strong default; deviations need a product-specific reason.
- **WHEN APPLICABLE:** use only when the product, screen, platform, and interaction justify it.

Do not blindly apply every rule. Explain meaningful exceptions and verify the result against the user's actual task.
