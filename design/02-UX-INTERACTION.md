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
