---
name: design
description: >
  Load the design system standards for a specific project and apply them
  when generating or reviewing code. Usage: /design <project>
  Supported projects: mgc, timesync
triggers:
  - /design
---

# Design System Skill

When this skill is invoked with `/design <project>`, do the following:

1. Identify the project name from the argument (e.g. `mgc`, `timesync`).
2. Load the corresponding resource file from this skill's `resources/` folder:
   - `mgc` → `resources/design.mgc.md`
   - `timesync` → `resources/design.timesync.md`
3. Read and internalize all tokens, guidelines, and rules in that file.
4. For the rest of the conversation, enforce those standards when:
   - Generating any component, style, or layout code
   - Reviewing code for design consistency
   - Suggesting colors, spacing, or typography values
   - Recommending PrimeNG components or configurations
5. If the user references a token by name (e.g. `--color-primary`), always resolve
   it against the loaded project's token file — never guess or use generic values.
6. If the project argument is missing or unrecognized, list the available projects
   and ask the user to specify one.

> Always confirm which project's design system is active at the start of your response,
> e.g. "Using **MGC** design system."
