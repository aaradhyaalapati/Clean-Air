# Adaptive Product Design & UX Engineering Standard

> A reusable set of decision rules for AI coding agents (Codex, Antigravity, and similar tools). It defines the quality of the decisions and implementation—not a visual theme, brand, layout, component library, or design template. Every product should arrive at its own visual language.

## 0. How to apply this document

Treat the rules as three levels:

- **MUST** — non-negotiable quality, accessibility, reliability, and implementation requirements.
- **SHOULD** — strong defaults. Deviate only for a product-specific reason.
- **WHEN APPLICABLE** — use only when the product, screen, platform, and interaction benefit from it.

Do not blindly implement every principle, effect, animation, component, or checklist item. First inspect the product and the current implementation. Preserve a good existing design. A rule that does not fit the product should be marked not applicable, not forced into the UI.

The goal is not “minimalism” or a particular aesthetic. The goal is a distinctive, coherent, usable, accessible, performant interface that feels intentionally designed for this product.

### 0.1 Rule hierarchy and conflict resolution

When rules compete, resolve them in this order:

1. **User safety, privacy, security, and data integrity.** Never trade these away for visual polish or convenience.
2. **User task success and correctness.** The interface must help people understand, decide, and complete the real task.
3. **Accessibility and platform requirements.** Do not invent custom interactions where a familiar accessible pattern is materially better.
4. **Product identity and established conventions.** Respect the product's domain, brand, users, and existing mental models.
5. **Visual quality and expressive character.** Use distinctive art direction without weakening the higher priorities.
6. **Implementation convenience.** Developer speed is not a reason to ship confusing, fragile, or inaccessible UX.

A lower-level preference must not override a higher-level requirement. If two requirements at the same level conflict, choose the option that best supports the primary user task and document the trade-off.

### 0.2 This is not a design template

- Do not reuse the same palette, font pairing, hero composition, card style, navigation pattern, radius scale, animation language, or page structure across unrelated products merely because it worked previously.
- Do reuse proven interaction conventions when they reduce learning cost—for example, a clearly labelled form field, visible keyboard focus, or a predictable dialog close action. Consistency of behavior is valuable; sameness of appearance is not the goal.
- Treat numeric values in this document as starting points or standards where explicitly stated, not universal aesthetic tokens. Choose the actual scale, density, typography, color, and composition from the product's needs.
- A design system is a set of reusable decisions for one product or product family. It is not a universal theme to impose on every project.
- Do not add every component or state listed here to every screen. First establish whether the feature exists and whether the state can occur.
- Do not force a design direction into a familiar category such as SaaS, fintech, AI, portfolio, or dashboard. Understand the actual product before selecting a visual metaphor.

### 0.3 Evidence and applicability

For each consequential design decision, the agent should be able to answer: **What user need does this serve? What product context makes it appropriate? What happens in other states or on other devices? How can it be verified?**

Use this document as a decision framework, not as a substitute for user research or testing. Apply a rule when its underlying problem exists. Mark it not applicable when it does not. If evidence is uncertain, prefer a reversible, familiar, low-risk approach and validate it rather than presenting an assumption as a proven UX law.

---

## 1. Design philosophy: product first, not template first

### MUST

1. Design for the actual product, audience, content, and tasks. Do not start from a generic SaaS/dashboard/landing-page template.
2. Preserve the product name, real capabilities, real content, information architecture, and important user journeys. Do not invent features, metrics, customers, testimonials, integrations, trust badges, or claims.
3. Use the existing brand identity when it is real and established. Do not replace brand colors or marks merely to make the screen look fashionable.
4. Make every visual element earn its place. Remove elements that add no information, hierarchy, affordance, feedback, or meaningful character.
5. Prioritize task completion and clarity over decoration. The interface must remain understandable with all animation disabled.
6. Do not redesign a screen just to make changes. If it is already well designed, preserve it and report only worthwhile refinements.

### Avoid generic AI-generated patterns unless the product genuinely calls for them

- Unmotivated purple/blue gradients, gradient text, neon borders, colored glows, blurred blobs, and glossy glass cards.
- Generic floating orbs, chrome objects, holograms, glowing brains, robots, rockets, circuit traces, and abstract “AI” imagery.
- Emoji used as navigation or interface icons; excessive sparkles; decorative icons beside every label.
- A centered hero with a giant vague headline, three buttons, a row of badges, and a generic illustration by default.
- Repeated equal-width card grids, bento layouts, nested cards, and panels used without a content or workflow reason.
- Excessive pill badges, uppercase tracked labels, over-bold typography, fake activity, fabricated testimonials, and meaningless status indicators.
- Decorative charts, sparklines, progress bars, dividers, and captions that repeat information already visible.
- Scroll-triggered animation on every section, looping motion on static elements, hover scaling on every card, and `transition-all` everywhere.

These are warning signs, not absolute bans. Keep them only when justified by the product's visual direction or interaction model.

### Product direction before styling

Before a substantial design or redesign, write a compact direction:

- **Product:** what it does and for whom, in one sentence.
- **Character:** 2–3 specific adjectives (e.g. precise, quiet, utilitarian; playful, tactile, energetic). Avoid empty descriptors such as “modern”, “clean”, “premium”, or “sleek” unless made specific.
- **World:** the real context/material/domain the product belongs to. Use it to inform visual choices; it need not become an illustration.
- **Moment:** the one meaningful place where the screen earns visual emphasis (real product output, important data, a distinctive interaction, or a key object).
- **Signature:** one small repeatable detail that belongs to this product.
- **Concept:** one sentence that constrains design decisions and remains true in empty, active, error, and completed states.

Use this direction to choose palette, type, layout, components, imagery, and motion. If the product is unknown, state assumptions. Never invent capabilities to make a concept work.

---

## 2. Visual system

### 2.1 Color

- **MUST:** Use semantic design tokens for page, surface, elevated surface, primary text, secondary text, muted text, border, focus, accent, success, warning, and error.
- **MUST:** Maintain readable contrast. Normal text should target at least WCAG AA 4.5:1; large text and meaningful non-text UI components should target at least 3:1.
- **SHOULD:** Use one coherent neutral ramp tinted subtly toward the product's world, plus a restrained accent derived from the real brand or product context.
- **SHOULD:** Reserve the accent for meaningful emphasis: primary action, selected state, key data, or one important visual moment. Do not highlight everything.
- **SHOULD:** Build palettes in perceptually consistent spaces such as OKLCH when the project's tooling supports it. Check actual rendered contrast rather than trusting token names.
- **WHEN APPLICABLE:** A 60/30/10 split may be used as a rough composition check, not a mathematical requirement. The 10% accent is not a quota.
- **WHEN APPLICABLE:** For dark mode, create depth with deliberate surface steps and readable borders; do not simply invert the light theme.

### 2.2 Typography and content density

- **MUST:** Establish a small, consistent type scale with explicit roles for display, page title, section title, body, labels, captions, and metadata.
- **MUST:** Keep body copy comfortably readable. Use around 16px as a general web default; compact data-dense interfaces may use smaller text only when legibility and zoom remain acceptable.
- **SHOULD:** Use one primary interface typeface and, at most, one complementary display/serif/mono family when the direction justifies it.
- **SHOULD:** Prefer weight and size hierarchy over heavy 800–900 weights. Most UI text should sit around 400–500, with 600 used selectively.
- **SHOULD:** Use sentence case for most UI. Reserve uppercase for contexts where it is native to the product or improves scanning.
- **SHOULD:** Use tabular numerals for aligned data, and keep number/date/currency formats consistent within a screen.
- **SHOULD:** Keep line length around 60–75 characters for long-form reading where possible. Use a line-height around 1.4–1.6 for body text.
- **SHOULD:** Use fluid type sizing (e.g. `clamp()`) for responsive display headings rather than abrupt breakpoint jumps.
- **SHOULD:** Avoid orphaned single words/lines where layout control can prevent them without awkward copy changes.
- **COPY:** Use specific product language. Replace generic headlines and hype with what the product actually does. Labels and buttons should be concise; do not add punctuation just for decoration. Never use fake proof or placeholder names/data in a production screen.

### 2.3 Spacing and alignment

- **MUST:** Use a consistent spacing system based on 4px increments (e.g. 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96). Existing established systems may be preserved.
- **MUST:** Align related labels, controls, icons, numbers, and content to consistent axes.
- **SHOULD:** Use tighter spacing within a group and larger spacing between groups. Let proximity create grouping before adding borders or dividers.
- **SHOULD:** Keep sibling rows and components consistent in padding, height, and rhythm.
- **SHOULD:** Use responsive page gutters and a sensible maximum content width. Avoid stretching text and forms across ultra-wide screens.
- **MUST:** Do not fill whitespace with decorative filler. Whitespace is valid when it gives content room and creates hierarchy.

### 2.4 Layout and composition

- **MUST:** Choose layout based on content priority and task sequence, not habit. Avoid centering and equal-card layouts by default.
- **MUST:** Design all key states and breakpoints, including small mobile widths, tablet, and large desktop.
- **SHOULD:** Vary proportions when the content has unequal importance. Let the primary task or product output receive the space it needs.
- **SHOULD:** Use one obvious primary action per decision area and keep secondary actions visually subordinate. Do not make every action look primary.
- **SHOULD:** Keep application screens calm and functional; reserve richer art direction for places where people enter, pause, or complete a meaningful task.
- **WHEN APPLICABLE:** Use a visual hierarchy based on proximity, similarity, common region, connectedness, and serial position. These are tools for grouping and scanning, not reasons to add more containers.
- **WHEN APPLICABLE:** Use progressive disclosure to hide advanced options until needed, while keeping essential actions discoverable.

### 2.5 Surfaces, borders, shadows, and radii

- **MUST:** Give each surface one clear depth treatment. Avoid stacking border + shadow + glow + gradient + ring without a specific reason.
- **SHOULD:** Prefer subtle hairline borders using alpha colors where appropriate over heavy grey outlines.
- **SHOULD:** Use shadows sparingly and with low opacity and broad blur. In dark themes, rely more on surface steps and borders than large shadows.
- **SHOULD:** Choose radii based on the product's character and component scale; not everything should be a pill.
- **MUST:** For nested rounded surfaces, keep the inner radius coherent with the outer radius and padding (a useful starting rule: inner radius = outer radius − padding, with a minimum of 4px).
- **SHOULD:** Avoid unnecessary nested containers. If an image, chart, or map is the content, let it use the available parent surface rather than wrapping it in multiple cards.

### 2.6 Icons and visual assets

- **MUST:** Use one coherent icon family with consistent size, alignment, and stroke weight. Prefer the project's existing icon set.
- **MUST:** Icons must remain understandable without animation. Use accessible labels for icon-only controls.
- **SHOULD:** Use icons only when they improve recognition, scanning, or affordance. Do not decorate every heading or label.
- **EXCEPTION:** Recognizable third-party brand marks should retain their official colors and proportions.
- **MUST:** Do not generate screenshots of fake UI with text/buttons embedded in images. Render actual UI as HTML/components.
- **WHEN APPLICABLE:** Prefer showing the real product, actual output, a meaningful data visualization, or one concrete metaphor over generic decorative artwork.
- **WHEN APPLICABLE:** Texture, grain, halftone, duotone, glyph rendering, and other effects may be used only when they solve a named visual problem and fit the product. Keep them off functional UI unless they add meaning.

---

## 3. Interaction, UX, and motion

### 3.1 Core usability principles

Apply the following as practical heuristics, not as rigid formulas:

- **Jakob's Law:** follow familiar platform conventions unless there is a strong product reason not to.
- **Hick's Law:** reduce unnecessary choices and make the next action clear.
- **Fitts's Law:** make frequent and important targets easy to reach; provide generous hit areas.
- **Recognition over recall:** show available choices and context rather than making users remember hidden information.
- **Proximity / similarity / common region:** visually group related content and controls.
- **Progressive disclosure:** reveal complexity at the point it becomes useful.
- **Tesler's Law:** absorb avoidable complexity in the interface rather than transferring it to the user.
- **Aesthetic-usability effect:** visual quality influences perceived usability; it does not replace actual usability testing.
- **Peak-end rule:** make meaningful completion and recovery states clear and satisfying, without manipulative celebration.
- **Zeigarnik / goal-gradient effects:** show progress when it helps users understand remaining work; never manufacture anxiety or artificial urgency.
- **Default effect:** choose safe, useful defaults, and make the consequences clear for consequential actions.
- **Doherty threshold:** aim for immediate acknowledgement; feedback around 100–400ms generally feels responsive, but do not fake completion while work is pending.

### 3.2 States and feedback

- **MUST:** Every interactive component has designed states: default, hover (where relevant), focus-visible, pressed, disabled, loading, success, and error.
- **MUST:** Every form field has a clear label, sensible input type, and nearby actionable validation/error message. Explain how to fix an error where possible.
- **MUST:** Provide visible keyboard focus. Never remove the focus outline without replacing it with an equally clear focus indicator.
- **MUST:** Empty states explain what is missing and the next useful action. Error states explain what happened and the recovery path.
- **SHOULD:** Put feedback close to the action and affected content. Avoid relying solely on transient toasts for important outcomes.
- **SHOULD:** Use consistent success, warning, and error semantics across the product.
- **WHEN APPLICABLE:** Use a small, meaningful confirmation flourish or pulse after success, but ensure the state itself communicates success.

### 3.3 Motion principles

Motion is optional. Use it to communicate cause, hierarchy, continuity, state change, and spatial relationships—not to prove the interface is animated.

- **MUST:** Respect `prefers-reduced-motion`. Provide an equivalent low-motion or no-motion experience. Avoid essential information being conveyed only by movement.
- **MUST:** Animate primarily `transform` and `opacity`; avoid animating layout-affecting properties such as `top`, `left`, or dimensions every frame when transforms can achieve the result.
- **MUST:** Make interactions interruptible where appropriate. Do not block a user's next action behind decorative animation.
- **SHOULD:** Keep common UI transitions brief: roughly 120–200ms for hover/press/toggles, 150–250ms for menus/popovers, and 200–300ms for simple state transitions. Longer entrances are allowed only when they serve the experience.
- **SHOULD:** Use ease-out for elements entering, ease-in-out for movement between on-screen states, and shorter exits than entrances. Avoid spring bounce for everyday controls.
- **SHOULD:** Scale buttons to approximately 0.97–0.98 while pressed, with a short transition, if it feels appropriate for the product.
- **SHOULD:** Use restrained stagger for meaningful lists or sequences; do not animate every element on every page load.
- **SHOULD:** Prefer state change and subtle surface/color feedback over constant motion. Frequent actions should have less animation, not more.
- **SHOULD:** Avoid `transition: all`; specify properties explicitly.
- **WHEN APPLICABLE:** Use origin-aware popovers, directional steppers, drag resistance, velocity-aware release, arc movement, squash/stretch, anticipation, and follow-through only when they support a physical or spatial interaction model.
- **WHEN APPLICABLE:** Crossfade icons when switching states, but keep the final icon legible and recognizable at rest.
- **WHEN APPLICABLE:** Use skeleton shimmer only for meaningful loading placeholders; static skeleton shapes are sufficient and often preferable.

### 3.4 Micro-details (use only when relevant)

- Reserve tab label width so font-weight changes do not shift neighboring tabs.
- Underline links with sufficient offset and visible hover/focus treatment.
- Keep superscripts from disrupting line height.
- Truncate long filenames in the middle when preserving extensions matters.
- Clamp card titles only where a consistent card layout requires it; do not hide useful content without an accessible way to read it.
- Use `100dvh` for full-height mobile sections when viewport browser chrome would make `100vh` unreliable.
- Use `text-box-trim` / `text-box-edge` only with supported-browser fallbacks and after visual verification.
- Disable transitions during theme changes only if the transition causes distracting intermediate states; restore normal transitions afterwards.
- Delay only the first tooltip in a sequence if doing so improves discoverability; never make tooltip access impossible by keyboard or touch.

---

## 4. UX performance and perceived speed

Perceived performance is part of product quality. Do not optimize only for fast office Wi-Fi. Consider slow networks, cold starts, older devices, and repeat visits.

### MUST

1. Inspect the current loading sequence and identify serial dependencies, redundant requests, blocking work, and repeated loading states before changing code.
2. Do not block the whole screen on data that is not necessary for the first useful view. Render the stable shell and critical content as soon as possible.
3. Avoid waterfalls: independent requests should run concurrently where dependencies and rate limits allow.
4. Keep expensive work off the critical rendering path. Defer non-critical modules, images, and secondary data when appropriate.
5. Preserve correctness, security, and authorization. Never treat cached client data as authoritative for permissions, access control, billing, or sensitive decisions.
6. Measure before and after where possible. Report actual measured values, test conditions, and any trade-offs. Never claim a speedup without evidence.

### SHOULD

- Use stale-while-revalidate or cached snapshots for non-sensitive, low-risk display data where appropriate. Show cached content immediately, refresh in the background, and reconcile updates safely.
- Persist only what is useful and safe. Choose storage based on size, sensitivity, lifecycle, and consistency needs; a small preference/cache may fit local storage, while larger or relational data may need IndexedDB or a backend cache.
- Use request deduplication, cancellation, timeouts, retries with backoff, and appropriate cache headers where they fit the existing architecture.
- Avoid duplicate loading screens. Keep layout dimensions stable to reduce layout shift.
- Lazy-load below-the-fold media and non-critical features. Give important hero imagery explicit dimensions and suitable loading priority.
- Optimize images with modern formats and responsive sizes. Avoid loading oversized assets.
- Monitor Core Web Vitals and real user performance when analytics are available.

### Loading patterns

- **Skeleton loaders:** Use only when loading is long enough to justify a placeholder (a delay of roughly 300ms is a useful starting point). Match the eventual content geometry so layout does not jump. Prefer reusing the same layout structure/component between loading and loaded states.
- **Optimistic updates:** Use for low-risk, reversible actions such as likes, simple toggles, and renames. Update immediately, then reconcile with the server. On failure, roll back and show a clear recovery message. Do not optimistically grant permissions, mark payments complete, or perform irreversible actions.
- **Progress indicators:** Show determinate progress only when the amount of work is known. Use indeterminate indicators for unknown-duration work. Do not show fake percentages.
- **Cached first paint:** May show a recent snapshot while refreshing, but clearly handle stale or invalid data and never allow stale data to authorize protected actions.
- **Parallel requests:** Parallelize independent calls; preserve order only for genuine dependencies. Avoid unbounded request fan-out.

### Backend boundary

If an improvement requires backend changes, API contract changes, server cache configuration, authentication policy, or infrastructure access unavailable in the current environment, do not fake it in the frontend. Document it as a backend/deployment dependency and implement only the safe client-side portion.

---

## 5. Engineering and implementation standards

### MUST

1. Inspect the repository before editing: framework, package manager, app structure, existing components, design tokens, routing, state management, data fetching, tests, linting, and build scripts.
2. Reuse existing components, dependencies, patterns, and code style wherever they are sound. Do not add a library for something the project already handles well.
3. Avoid introducing a new design system or state-management library for a small visual improvement.
4. Keep changes scoped, accessible, responsive, and maintainable. Do not break existing product behavior to achieve a visual result.
5. Do not rewrite unrelated code or perform broad refactors without necessity.
6. Use semantic HTML and accessible names. Prefer native elements when they provide the right behavior.
7. Keep content and layout resilient to long strings, localization, empty data, errors, and loading states.
8. Test each meaningful change. Run the relevant lint, typecheck, unit/integration tests, and build commands available in the project.
9. Do not claim tests passed unless they were actually run and passed. Report unavailable checks and environment blockers.
10. Never hardcode secrets, credentials, private endpoints, or user-specific sensitive data into the client.

### SHOULD

- Use existing CSS variables/theme tokens rather than scattered one-off values.
- Keep components cohesive and avoid excessive abstraction for one-off UI.
- Use stable keys and predictable state transitions.
- Avoid unnecessary rerenders and expensive work in render paths.
- Use semantic buttons and links; do not use clickable `div` elements when a native control fits.
- Ensure loading, empty, error, disabled, and success states are part of the implementation, not an afterthought.
- Keep motion and visual effects performant on modest hardware and mobile devices.

---

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

## 8. Source and attribution

This standard incorporates and adapts principles from the `charles-unslop` skill by LemonFace0309, which itself credits Damir Sokolovsky's `unslop` and Emil Kowalski's design work. The `charles-unslop` skill and its referenced materials are licensed CC BY 4.0. Source: https://github.com/LemonFace0309/charles-skills/tree/main/skills/design/charles-unslop

Additional principles in this document were synthesized from the UX, interaction, accessibility, and performance notes supplied by the project owner. This document is an adapted working standard, not a verbatim copy of the source skill.

## 10. Product-grade UX: the details that separate a real product from a demo

A convincing interface is not only a polished first screen. It behaves correctly across the full lifecycle: first visit, returning visit, slow network, empty data, partial data, errors, permissions, keyboard use, mobile use, and recovery. Audit the complete journey, not just the hero screenshot.

### 10.1 Navigation, location, and continuity

- **MUST:** Make the current location in the product obvious. Active navigation, page title, breadcrumbs (when useful), and selected filters must agree.
- **MUST:** Use real links for navigation and buttons for actions. Preserve browser behaviors such as open-in-new-tab, copy-link, Back, and Forward.
- **SHOULD:** Put shareable, meaningful view state in the URL: search query, filters, sort, pagination, selected tab, and resource identifiers. Do not encode ephemeral state that should remain private or local.
- **SHOULD:** Preserve user context when navigating back: scroll position, search query, filters, and form progress where appropriate.
- **SHOULD:** Deep-link important resources and meaningful application states. A copied URL should open the same useful view for an authorized user.
- **SHOULD:** Use breadcrumbs for genuinely hierarchical content, not as decoration.
- **WHEN APPLICABLE:** Support command palettes and keyboard shortcuts for frequent expert workflows. Never make shortcuts the only way to perform an action.

### 10.2 Forms and input quality

- **MUST:** Give every field a persistent visible label. Placeholder text is an example or hint, never the only label.
- **MUST:** Associate help and error text programmatically with the field. Move focus to an error summary or first invalid field after failed submission when appropriate.
- **MUST:** Validate on the server as well as the client. Client validation improves feedback; it is not a security boundary.
- **MUST:** Preserve valid user input after validation errors, network failures, and recoverable interruptions.
- **MUST:** Do not block paste, password managers, browser autofill, or normal keyboard behavior without a compelling security reason.
- **SHOULD:** Validate at a useful moment: lightweight format feedback while typing when it helps, and full validation on blur or submit. Avoid shouting errors before a user has had a chance to enter a value.
- **SHOULD:** Put errors next to the relevant field and explain both what is wrong and how to fix it. Do not rely on red alone.
- **SHOULD:** Mark required and optional fields consistently. If most fields are required, mark optional fields rather than cluttering every label.
- **SHOULD:** Use the correct input type, autocomplete token, input mode, and appropriate mobile keyboard.
- **SHOULD:** Use sensible defaults only when the choice is safe and reversible. Never preselect a consequential choice merely to increase conversion.
- **SHOULD:** Break long forms into logical groups. Use a stepper only when the task genuinely has stages; show progress and allow review/backtracking.
- **WHEN APPLICABLE:** Autosave drafts with a visible saved/saving/failed state. Debounce writes, handle conflicts, and avoid claiming a save before persistence is confirmed.

### 10.3 State completeness: every feature has more than a happy path

For each data-driven feature, inspect and design these states where relevant:

1. Initial / first-use state.
2. Loading state (including slow loading).
3. Loaded state with realistic content.
4. Empty state with a useful next action.
5. Partial state (some data available, some unavailable).
6. Validation state.
7. Recoverable error state with retry or correction.
8. Permission-denied / unauthenticated state.
9. Offline / reconnecting state when network use matters.
10. Success / completed state.
11. Destructive confirmation and undo state.
12. Stale-data state when cached information may be old.

- **MUST:** Do not leave blank screens, dead buttons, raw stack traces, unexplained error codes, or permanent spinners.
- **MUST:** Empty states explain what belongs here and the next useful action. Do not use empty states as marketing banners.
- **MUST:** Distinguish “no results” from “failed to load” and from “no data exists yet”.
- **SHOULD:** Keep the layout stable between loading and loaded states. Reserve image, media, and content dimensions to prevent layout shift.
- **SHOULD:** Use skeletons only when the expected wait justifies them. Keep the skeleton geometry close to the real content; avoid skeletons for tiny waits or simple actions.
- **SHOULD:** Provide retry paths that preserve the user's query and input.
- **SHOULD:** Show stale cached content immediately when safe, then refresh in the background. Label freshness where stale information could affect a decision.

### 10.4 Feedback, actions, and trust

- **MUST:** Every action gives timely, understandable feedback. The user should know whether it happened, is happening, failed, or needs confirmation.
- **MUST:** Prevent accidental duplicate submissions. Disable or safely deduplicate repeated requests while an action is pending.
- **MUST:** Destructive or irreversible actions require clear consequence wording and a deliberate confirmation, or a reliable undo mechanism.
- **SHOULD:** Prefer undo for reversible actions (archive, remove from list) and confirmation for irreversible/high-impact actions (permanent deletion, payment, external send).
- **SHOULD:** Use optimistic updates only when the action is likely to succeed, the change is reversible, and rollback is correct. Reconcile with the server; on failure restore the previous state and explain what happened.
- **SHOULD:** Keep the original action label visible during loading (e.g. “Saving…” rather than an unexplained spinner).
- **SHOULD:** Use inline feedback for local field errors, toasts for brief global confirmations, and persistent banners for issues that need attention. Do not use a toast as the only record of critical information.
- **SHOULD:** Announce async status and validation changes to assistive technology using appropriate live regions without making every update interruptive.
- **WHEN APPLICABLE:** Offer undo, retry, cancel, pause, or resume for long-running tasks. Show meaningful progress only when progress can be measured; do not invent percentages.

### 10.5 Search, filtering, sorting, and tables

- **MUST:** Preserve the query when users open a result and return to the list.
- **SHOULD:** Make active filters visible and removable. Provide a clear-all action when multiple filters can be applied.
- **SHOULD:** Show result counts when useful, and distinguish the total result count from the currently loaded count.
- **SHOULD:** Use filter labels that match users' vocabulary, not internal database field names.
- **SHOULD:** Keep sort order visible and explain what the default sort means when it is not obvious.
- **SHOULD:** Provide useful no-result recovery: suggest removing filters, correcting spelling, broadening the query, or trying a related search when supported.
- **SHOULD:** Use tables for precise comparison and aligned values; use cards only when each item benefits from independent visual grouping.
- **SHOULD:** Align numeric columns consistently, use tabular numerals, and right-align comparable quantities.
- **WHEN APPLICABLE:** Support column visibility, resizing, sticky headers, bulk selection, pagination, and export for genuinely data-heavy workflows. Do not add enterprise controls to a simple list.

### 10.6 Content and microcopy

- **MUST:** Use the user's vocabulary. Explain product-specific terms at the point of use.
- **MUST:** Make button labels describe the outcome (“Create project”, “Save changes”), not vague mechanics (“Continue”, “Submit”) unless the context is clear.
- **SHOULD:** Keep labels stable across the product. Do not call the same concept “workspace”, “team”, and “organization” interchangeably.
- **SHOULD:** Format dates, times, numbers, currency, addresses, and names for the user's locale. Include timezone when scheduling across zones.
- **SHOULD:** Distinguish relative time (“2 hours ago”) from exact time when precision matters; provide exact timestamps in audit/history contexts.
- **SHOULD:** Make links descriptive out of context. Avoid repeated “Learn more” links without accessible context.
- **SHOULD:** Write useful permission explanations before requesting browser/device permissions. Ask only when the feature needs it, not on first launch by default.
- **MUST:** Never fabricate testimonials, user counts, ratings, usage activity, compliance claims, security claims, or customer logos.

## 11. Performance and perceived speed

Performance is part of product quality. A beautiful screen that waits on unnecessary requests, shifts while loading, or freezes during input is not finished.

### 11.1 Loading architecture

- **MUST:** Identify the minimum data required to render a useful first screen. Do not block the entire application on unrelated requests.
- **SHOULD:** Start independent requests in parallel. Avoid sequential waterfalls unless one request truly depends on another.
- **SHOULD:** Render the application shell and useful cached data while revalidating in the background when security and freshness rules permit.
- **SHOULD:** Separate critical-path data from below-the-fold or secondary data. Load secondary panels when needed or when idle.
- **SHOULD:** Use route-level/code splitting for large features and defer non-critical scripts.
- **MUST:** Reserve dimensions for images, embeds, ads, charts, and async content to avoid layout shifts.
- **SHOULD:** Use responsive images, modern formats where supported, and appropriate `srcset`/`sizes`. Lazy-load offscreen media; do not lazy-load the main above-the-fold/LCP image.
- **SHOULD:** Cache according to data volatility and sensitivity. Define invalidation, expiry, and logout behavior; never cache private data in a way that leaks across accounts.
- **MUST:** Treat local cached data as provisional, not authoritative for authorization, payment, subscription entitlements, or other sensitive decisions. Revalidate those with the server before granting access.
- **SHOULD:** Abort obsolete requests, debounce high-frequency search, and avoid state updates from stale responses.

### 11.2 Performance budgets and measurement

- **MUST:** Measure before and after optimization. Do not claim “10x faster” based only on a local impression.
- **SHOULD:** Track Core Web Vitals at the 75th percentile, segmented by mobile and desktop: LCP ≤ 2.5s, INP ≤ 200ms, CLS ≤ 0.1 as good targets.
- **SHOULD:** Use Lighthouse for lab diagnostics and real-user monitoring / field data for production behavior. Lab scores are not a substitute for field experience.
- **SHOULD:** Inspect bundle size, route chunks, long tasks, image weight, font loading, network waterfalls, and third-party scripts.
- **SHOULD:** Test throttled network and CPU, not only a fast developer machine and Wi-Fi.
- **SHOULD:** Prefer `transform` and `opacity` for animation; avoid repeated layout and paint work. Do not optimize blindly at the expense of maintainability.
- **WHEN APPLICABLE:** Set explicit budgets for JavaScript, images, fonts, and route payloads based on the product's device and network audience.

## 12. Accessibility and inclusive interaction

Target WCAG 2.2 AA for web experiences unless the project has a stricter requirement. Automated tools catch only a portion of accessibility issues; manual keyboard and assistive-technology checks remain necessary.

- **MUST:** All functionality works with a keyboard. There are no keyboard traps.
- **MUST:** Use semantic HTML before ARIA. A native button, link, input, select, heading, list, and table is usually more robust than a custom div-based control.
- **MUST:** Every interactive element has an accessible name, role, state, and value where applicable.
- **MUST:** Focus is visible, logically ordered, not removed, and not hidden behind sticky UI or overlays.
- **MUST:** Color is never the only way to communicate status, errors, or selection.
- **MUST:** Text contrast meets WCAG AA: 4.5:1 for normal text and 3:1 for large text. Non-text controls and meaningful graphics need sufficient contrast as required by WCAG.
- **MUST:** Support zoom and text resizing. Do not disable browser zoom.
- **MUST:** Respect `prefers-reduced-motion`. Avoid flashing content and provide pause/stop controls for applicable auto-moving content.
- **SHOULD:** Provide useful alt text for informative images; use empty alt for decorative images. Do not put essential text inside images.
- **SHOULD:** Ensure form labels, instructions, errors, and status messages are announced correctly by screen readers.
- **SHOULD:** Test at 200% zoom and narrow viewport widths; content should reflow without two-dimensional scrolling except where intrinsically required (e.g. some data tables).
- **SHOULD:** Make touch targets comfortably large (typically around 44–48 CSS px where practical) and separate adjacent targets.
- **SHOULD:** Support high-contrast/forced-colors modes and avoid relying on box-shadow alone to communicate boundaries.
- **SHOULD:** Check focus return after dialogs, menus, and popovers close. Manage focus when content is inserted or removed.
- **WHEN APPLICABLE:** Provide captions/transcripts for media, accessible chart summaries or data tables, and alternatives to drag-only interactions.

## 13. Responsive and cross-device quality

- **MUST:** Design for content-driven breakpoints, not only named device widths. Test narrow phones, large phones, tablets, laptops, and wide desktop layouts.
- **MUST:** No accidental horizontal overflow, clipped controls, overlapping text, or inaccessible off-canvas content.
- **SHOULD:** Recompose layout at smaller widths rather than merely shrinking desktop columns. Prioritize content and actions; do not hide essential functionality behind hover.
- **SHOULD:** Test touch, mouse, keyboard, and hybrid input devices. Hover is enhancement, never the only interaction.
- **SHOULD:** Keep mobile navigation, dialogs, sheets, and menus usable with the virtual keyboard open.
- **SHOULD:** Use `100dvh` where viewport-height layouts need to account for dynamic browser chrome; test Safari and Android browser behavior.
- **SHOULD:** Avoid fixed elements that consume too much of a small viewport or cover focused controls.
- **SHOULD:** Test portrait and landscape where the workflow plausibly uses both.

## 14. Reliability, security, and operational maturity

A production product must be trustworthy behind the interface too. These checks are part of the agent's audit, but do not attempt backend or infrastructure changes outside the task's scope or permissions.

- **MUST:** Never expose secrets, API keys, private tokens, service credentials, or privileged configuration in client bundles or committed files.
- **MUST:** Enforce authorization and input validation on the server. Hiding a button is not access control.
- **MUST:** Handle authentication expiry, session refresh, logout, and account switching without leaking cached user data.
- **MUST:** Avoid logging passwords, tokens, payment data, or sensitive personal data. Minimize collection and retention.
- **MUST:** Show safe, user-readable errors. Keep diagnostic details in protected logs, not the public interface.
- **SHOULD:** Use error boundaries or equivalent recovery boundaries for major UI regions. One failing widget should not necessarily blank the entire app.
- **SHOULD:** Provide retry behavior with backoff for transient failures; do not retry non-idempotent actions blindly.
- **SHOULD:** Make writes idempotent where possible and handle duplicate requests, race conditions, and stale updates.
- **SHOULD:** Include empty, loading, error, offline, and permission states in tests.
- **SHOULD:** Use structured logs and error monitoring with enough context to diagnose issues, while redacting sensitive fields.
- **SHOULD:** Provide health checks and deployment rollback paths for services where the task includes operations.
- **WHEN APPLICABLE:** Add audit history, export/delete controls, data retention settings, rate limits, abuse prevention, and privacy disclosures according to the product's risk.

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

## 17. Adaptive design decisions: choose the right solution for this product

The agent must select patterns based on the user's task, product type, content, risk, frequency of use, and operating context. The examples below are decision prompts, not prescribed page templates.

### 17.1 Choose the interaction model from the task

- **Frequent, repeatable work:** optimize for speed, keyboard operation, scanning, saved preferences, bulk actions, and low-friction recovery. Do not bury common actions in decorative menus.
- **Occasional or unfamiliar tasks:** prioritize clear language, visible guidance, safe defaults, and progressive disclosure. Avoid assuming users remember previous steps.
- **High-consequence actions:** make consequences explicit, provide a review step when useful, prevent accidental activation, and offer recovery where technically possible. Confirmation dialogs are not a substitute for undo or good safeguards.
- **Exploration and discovery:** make categories, search, filters, previews, and comparison understandable. Preserve the user's query and selection when navigating back.
- **Creation and editing:** protect user work, distinguish saved from unsaved state, preserve drafts on failure, and make the save model predictable.
- **Monitoring and decision-making:** emphasize freshness, provenance, units, thresholds, trends, and actionable exceptions. Never use charts as decoration or imply certainty the data does not support.
- **Transactional flows:** show total cost, commitments, availability, and consequences before confirmation. Minimize unnecessary steps without hiding important information.

### 17.2 Adapt to product context without copying its visual style

Before selecting patterns, identify which contexts apply:

- **Marketing or informational site:** communicate what the organization or product does, who it serves, why it is credible, and what the next step is. Make navigation and calls to action reflect real intent. Avoid vague hero copy and invented proof.
- **SaaS or workflow application:** optimize for repeat usage, information hierarchy, permissions, empty states, data density, keyboard efficiency, and reliable feedback.
- **Commerce or booking:** make product/service details, availability, price, policies, comparison, and checkout consequences clear. Preserve selections and entered information.
- **Developer tool:** prioritize precise terminology, copyable output, code readability, keyboard support, error diagnostics, and useful documentation. Do not hide technical detail from users who need it.
- **Dashboard or analytics product:** make data source, time range, units, update time, filters, and missing data explicit. Choose visualizations that match the question and never distort scales.
- **Community or collaboration product:** make identity, authorship, audience, visibility, notification behavior, and moderation controls understandable.
- **Mobile-first or touch-first product:** prioritize reachability, touch target size, interruption recovery, device constraints, and platform conventions.

Do not apply a context's full pattern set just because the product has one similar feature. A developer tool may contain a checkout-like payment flow; apply transactional safeguards to that flow without turning the entire product into an e-commerce interface.

### 17.3 Choose visual expression deliberately

The visual direction should emerge from the product's purpose and personality, not from a default trend. Consider: domain conventions, audience expectations, content type, emotional tone, brand assets, competitive differentiation, accessibility, and implementation constraints.

The agent should explore at least two meaningfully different directions for a major new product surface when the brief leaves room for interpretation. Compare them against the product's needs, then commit to one coherent direction. Do not produce superficial variants that only change accent color or border radius. For small changes to an established product, preserve its current direction unless there is a clear reason to evolve it.

A coherent direction can be expressive, restrained, editorial, technical, playful, dense, spacious, or something else entirely. No style is inherently more professional. Execution, clarity, consistency, and fit determine quality.

### 17.4 Define tokens after the direction—not before

Create or adapt design tokens only after inspecting the product and choosing its direction. Tokens should encode meaningful roles (for example, text, surface, border, focus, status, spacing, type, elevation, motion), not force a predetermined palette or scale.

- Keep tokens semantic so themes and states can change without rewriting components.
- Avoid creating dozens of near-identical values without a demonstrated need.
- Do not hard-code one-off values repeatedly; promote repeated, meaningful decisions into tokens.
- Do not force every surface into a card or every control into a pill.
- Keep component variants limited to real product needs.
- Document exceptions when they are intentional and meaningful.

### 17.5 Make the decision testable

For important choices, define a lightweight acceptance statement. Examples:

- “A first-time user can identify the primary action without reading every paragraph.”
- “A keyboard user can open the dialog, complete the task, close it, and return to the triggering control.”
- “A failed save does not erase the user's edits.”
- “A mobile user can complete the primary flow without horizontal scrolling.”
- “The chart communicates its units, date range, and source.”

Prefer observable outcomes over subjective claims such as “feels premium” or “looks modern.” Visual judgment still matters, but it must be paired with interaction and task verification.

---

## 18. Reference library: standards, research, and maintained implementations

Use these as reference material, not as a mandate to copy their visual identity. Prefer official documentation and maintained repositories. Re-check current guidance when adopting a specific API or standard.

### High-value GitHub repositories

- [Vercel — Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines): practical micro-level rules for keyboard use, focus, links, forms, loading, optimistic updates, URL state, animation, and layout. A strong companion checklist.
- [Charles Liu — charles-unslop](https://github.com/LemonFace0309/charles-skills/tree/main/skills/design/charles-unslop): product-specific art direction, subtract-before-restyling workflow, AI-generated UI warning signs, and visual craft. Licensed CC BY 4.0; retain attribution when adapting.
- [GitHub — Primer Design](https://github.com/primer/design): a mature product design system with foundations, components, and patterns.
- [IBM — Carbon Design System](https://github.com/carbon-design-system/carbon): tokens, grid, typography, icons, components, motion, and enterprise interaction patterns.
- [GOV.UK — Frontend](https://github.com/alphagov/govuk-frontend): accessible production components, browser support, progressive enhancement, and service-oriented UX.
- [Radix UI Primitives](https://github.com/radix-ui/primitives): accessible behavior and interaction primitives for complex controls. Use as a behavior reference; do not assume every project should install it.
- [WAI-ARIA Authoring Practices Guide](https://github.com/w3c/aria-practices): keyboard interaction patterns and semantics for menus, dialogs, tabs, comboboxes, and other widgets.

### Primary standards and documentation

- [Microsoft Fluent 2 — Accessibility](https://fluent2.microsoft.design/accessibility): focus management, contrast, semantic structure, zoom, and responsive reflow.
- [Microsoft Fluent 2 — Layout](https://fluent2.microsoft.design/layout): proximity, whitespace, grids, and alignment.
- [GitHub Primer — Saving](https://primer.github.io/design/ui-patterns/saving/): explicit versus automatic saving, unsaved changes, feedback, and error forgiveness.
- [Atlassian — Writing error messages](https://atlassian.design/content/designing-messages/writing-error-messages): accurate, actionable, concise error communication.
- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/): purpose, agency, familiarity, feedback, simplicity, craft, delight, and platform-specific interaction.
- [Apple — Design principles](https://developer.apple.com/design/human-interface-guidelines/design-principles): explicit guidance that principles are tools for weighing priorities, not a single correct design recipe.
- [Apple — Motion](https://developer.apple.com/design/human-interface-guidelines/motion): purposeful, optional, brief motion that communicates feedback.
- [Material Design 3](https://m3.material.io/): foundations, components, layout, accessibility, color, typography, and motion patterns.
- [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/): normative accessibility success criteria; use WCAG AA as the baseline target for web products.
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/): semantic roles, keyboard behavior, and accessible widget patterns.
- [web.dev — Core Web Vitals](https://web.dev/articles/vitals): field metrics for loading, responsiveness, and visual stability.
- [web.dev — Learn Performance](https://web.dev/learn/performance): practical browser performance fundamentals.
- [MDN — Web Performance](https://developer.mozilla.org/en-US/docs/Web/Performance): browser APIs, rendering, and performance techniques.

### UX research and heuristics

- [Nielsen Norman Group — 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/): system status, real-world language, user control, consistency, error prevention/recovery, recognition, efficiency, minimalism, and help.
- [Baymard Institute — E-commerce UX Research](https://baymard.com/research): deep research on search, navigation, product lists, filters, forms, checkout, and error recovery. Apply relevant findings only to matching product types.
- [Laws of UX](https://lawsofux.com/): a useful index of cognitive and perceptual principles. Treat laws as heuristics, not scientific guarantees or rigid pixel rules.

### How to use references responsibly

1. Prefer normative standards (W3C) for accessibility requirements, official platform docs for platform behavior, and maintained design systems for implementation patterns.
2. Treat blog posts, social posts, and “magic number” rules as hypotheses until validated in the product context.
3. Do not copy a design system wholesale. Extract the principle and adapt it to the product's users, domain, brand, and constraints.
4. Record the source for unusual or consequential rules so future maintainers can revisit them.
5. Recheck links and version-sensitive guidance before applying them to a new project.

---

## 19. Credits and adaptation notes

This standard incorporates and adapts ideas from the following sources:

- Charles Liu's [charles-unslop](https://github.com/LemonFace0309/charles-skills/tree/main/skills/design/charles-unslop), adapted from Damir Sokolovsky's [unslop](https://github.com/heydamir/unslop), licensed CC BY 4.0. Preserve attribution when redistributing adapted portions.
- Vercel Labs' [Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines).
- Public design-system and standards documentation listed in Section 17.

This is a living checklist, not a universal visual theme. Update it when standards change, new evidence emerges, or repeated project audits reveal a useful missing rule.
