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
