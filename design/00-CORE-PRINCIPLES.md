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
