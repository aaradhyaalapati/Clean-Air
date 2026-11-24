## 6. Required agent workflow

For a design pass or UX improvement, follow this sequence.

### Step 1 — Inspect

- Read the relevant source files and project instructions.
- Run the app or inspect screenshots at real target sizes when possible.
- Review desktop and mobile states, not only the first viewport.
- Identify existing good decisions that should be preserved.

### Step 2 — Audit

List issues by category: hierarchy, spacing, color, typography, copy, icons, layout, surfaces, responsiveness, accessibility, states, motion, loading/performance.

For each issue, record: location, user impact, severity, and proposed correction. Separate visible evidence from assumptions.

### Step 3 — Define direction and scope

Write the product direction (Product, Character, World, Moment, Signature, Concept). State what will stay unchanged, what will change, and why. Do not invent a new direction if the existing one is working.

### Step 4 — Subtract before adding

Ask of every badge, icon, caption, divider, wrapper, shadow, control, animation, and sentence: “What breaks if this is removed?” If the answer is “nothing”, remove it unless it is the deliberate product signature. Preserve information users need; relocate or simplify it rather than deleting it.

### Step 5 — Implement in sensible passes

A. Information hierarchy and content
B. Spacing and alignment
C. Color and typography
D. Layout and responsive behavior
E. Component/surface details
F. States, interaction, and accessibility
G. Motion and meaningful visual assets
H. Loading/performance optimizations

Do not add motion or artwork to compensate for weak hierarchy or missing content.

### Step 6 — Implement one item at a time and verify

For multi-item UX audits:

- Evaluate each checklist item against the project.
- Mark it **Already done**, **Built**, **Skipped — not applicable**, or **Skipped — requires backend/external access**.
- Implement one item at a time when changes are independent; run the narrowest relevant checks after each item.
- Group checks only when items are tightly coupled and separate runs would be meaningless or prohibitively expensive. Explain that choice.
- Do not invent missing checklist items. If a supplied list is truncated, explicitly say which items were available and audit only those.

### Step 7 — Final verification

- Inspect the rendered result at mobile and desktop sizes.
- Check keyboard navigation, focus visibility, labels, contrast, and reduced-motion behavior.
- Exercise loading, empty, error, success, disabled, and responsive states relevant to the change.
- Check for console errors, broken routes, overflow, layout shifts, and regressions.
- Run the project's available checks.
- Compare the final screen against the original audit and product direction.
- Remove one more unnecessary element, then restore it only if something genuinely breaks.

### Step 8 — Final report

Provide a concise but specific report:

1. **Direction:** Product, Character, World, Moment, Signature, Concept.
2. **What changed:** group by pass and name the files changed.
3. **Checklist:** every supplied item with one status:
   - **Built:** what changed, files, and how to see it.
   - **Already done:** where it exists.
   - **Skipped:** why it does not fit or what dependency blocks it.
4. **Verification:** exact checks run and their results; list checks not run.
5. **Known trade-offs:** cache freshness, latency, accessibility limitations, backend work, or other remaining issues.

Never report an item as Built based only on a plan or intention.

---

## 7. Fast review checklist

Before calling a screen finished, ask:

- [ ] Does this look and behave like this product, rather than a reusable AI template?
- [ ] Is the primary task obvious without reading extra explanatory copy?
- [ ] Is there one clear visual hierarchy and one deliberate focal point?
- [ ] Are all colors, fonts, radii, and spacing choices coherent and tokenized?
- [ ] Are icons consistent, necessary, and aligned?
- [ ] Can any wrapper, badge, divider, caption, decoration, or animation be removed?
- [ ] Are content, loading, empty, error, disabled, focus, and success states handled?
- [ ] Does the interface work with keyboard, touch, zoom, and reduced motion?
- [ ] Does it work at narrow mobile widths and large desktop widths?
- [ ] Are images and network requests appropriate for the critical path?
- [ ] Have actual checks been run, and are performance claims measured?
- [ ] Is there one meaningful detail that could not be pasted unchanged into a competitor's product?

---

## 15. Forms of quality assurance

Do not treat “it compiles” as proof that the product works.

### Before implementation

- Inspect the repository structure, package scripts, framework, existing component library, design tokens, routing, state management, tests, and lint/type-check setup.
- Run the existing checks once to establish a baseline. Record pre-existing failures instead of attributing them to the new work.
- Inspect the actual rendered UI at relevant viewports. If screenshots or browser tooling are available, use them; do not judge only from source code.
- Identify the user journey and states affected by the change.

### During implementation

- Make one coherent change at a time. Avoid broad rewrites when a focused fix is safer.
- Reuse existing components and dependencies. Add a library only when it solves a real need and its cost is justified.
- After each meaningful change, run the narrowest relevant test/check. At the end, run the full available suite.
- Test keyboard navigation, focus, validation, loading, error, empty, success, and responsive behavior relevant to the change.
- Inspect console errors, failed network requests, hydration warnings, and accessibility warnings where tooling allows.

### Before completion

- Verify the actual UI, not just the code diff. Check at least one small and one large viewport.
- Check reduced-motion behavior and keyboard access for changed interactions.
- Confirm no fake data, dead controls, placeholder links, unimplemented menu items, or “coming soon” features were presented as complete.
- Report exactly what was changed, what was tested, what failed, and what remains blocked or requires backend/product-owner input.
- Do not claim a test, screenshot, performance measurement, or accessibility audit was performed unless it actually was.

## 16. Practical acceptance checklist

Use this as a final review, not a reason to add features that the product does not need.

### Visual and interaction

- [ ] Product-specific visual direction exists and is reflected in the screen.
- [ ] Hierarchy is clear; the primary action is obvious.
- [ ] Spacing, typography, color, radii, and icon treatment are consistent.
- [ ] No unexplained decoration, fake proof, redundant labels, or dead controls remain.
- [ ] Hover, focus, active, disabled, loading, success, and error states are designed where relevant.
- [ ] Motion is purposeful, interruptible where appropriate, and reduced-motion safe.

### UX and content

- [ ] Navigation, Back/Forward, deep links, and state persistence work where relevant.
- [ ] Forms have labels, correct input semantics, validation, and recoverable errors.
- [ ] Empty, loading, partial, offline, error, and success states are handled where relevant.
- [ ] Destructive actions are safe; reversible actions support undo where appropriate.
- [ ] Copy is specific, accurate, consistent, and free of fabricated claims.

### Engineering and quality

- [ ] Responsive layouts work without accidental overflow.
- [ ] Keyboard and assistive-technology behavior has been considered and tested.
- [ ] Loading does not block on unrelated requests; layout shifts are controlled.
- [ ] Sensitive data and authorization are handled safely.
- [ ] Tests, lint, type checks, and build checks pass—or failures are documented accurately.
- [ ] The final report names files changed, behavior verified, checks run, and remaining limitations.
