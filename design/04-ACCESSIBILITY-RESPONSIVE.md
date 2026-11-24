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
