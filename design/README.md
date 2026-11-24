# Adaptive Product Design & UX Engineering Toolkit

A modular instruction set for Codex, Antigravity, and other coding agents. It defines quality standards and decision-making rules—not a reusable visual theme or website template.

## Start here

1. Put `AGENTS.md` in the project root, or merge its instructions into the project's existing agent instructions.
2. Keep the specialist Markdown files in a stable location in the repository (for example, `docs/design-standard/`).
3. Ask the agent to read `00-CORE-PRINCIPLES.md` before substantial UI work.
4. Have it load the specialist files relevant to the task rather than treating every rule as mandatory on every screen.

## File map

| File | Purpose |
|---|---|
| `AGENTS.md` | Short entry point and instructions for the coding agent |
| `00-CORE-PRINCIPLES.md` | Rule hierarchy, product-first thinking, anti-template principles |
| `01-VISUAL-DESIGN.md` | Product-specific art direction, visual systems, typography, color, layout |
| `02-UX-INTERACTION.md` | Navigation, forms, states, feedback, interaction patterns, motion |
| `03-PERFORMANCE-ENGINEERING.md` | Performance, implementation, reliability, security, operational quality |
| `04-ACCESSIBILITY-RESPONSIVE.md` | Accessibility and cross-device requirements |
| `05-AGENT-WORKFLOW-AND-AUDITS.md` | Agent workflow, QA process, acceptance checklists |
| `06-REFERENCES-AND-ATTRIBUTION.md` | Source library, research references, credits |
| `DESIGN_STANDARD_FULL.md` | Complete consolidated source document |

## Important principle: consistency without sameness

The toolkit standardizes the quality of decisions, not the appearance of products. Different products should develop different visual languages based on their users, domain, brand, content, and tasks. Reuse proven interaction conventions when they improve usability; do not reuse aesthetics by default.

## Suggested project structure

```text
your-project/
├── AGENTS.md
└── docs/
    └── design-standard/
        ├── 00-CORE-PRINCIPLES.md
        ├── 01-VISUAL-DESIGN.md
        ├── 02-UX-INTERACTION.md
        ├── 03-PERFORMANCE-ENGINEERING.md
        ├── 04-ACCESSIBILITY-RESPONSIVE.md
        ├── 05-AGENT-WORKFLOW-AND-AUDITS.md
        └── 06-REFERENCES-AND-ATTRIBUTION.md
```

The `AGENTS.md` file can be placed at the project root. The specialist files can live under `docs/design-standard/`; update the paths in `AGENTS.md` if you choose another location.

## Usage prompt

> Before implementing this UI change, read the project's `AGENTS.md` and the relevant files in `docs/design-standard/`. Inspect the existing product and rendered interface first. Follow the standards as context-sensitive rules, not as a visual template. Preserve good existing work, explain any meaningful exceptions, implement all relevant states, and verify the result at appropriate viewport sizes.
