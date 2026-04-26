# office-design-plugin

A VS Code Agent Plugin that loads project-specific design system tokens and standards
into GitHub Copilot chat, so the AI always uses the correct colors, typography,
spacing, PrimeNG guidelines, and layout rules for each project.

---

## Usage

In any VS Code chat session, type:

```
/design mgc
```
or
```
/design timesync
```

The agent will load that project's design tokens and apply them for the rest of the
conversation — code generation, reviews, and suggestions will all follow those standards.

---

## Supported Projects

| Command         | Project       | File                              |
|-----------------|---------------|-----------------------------------|
| `/design mgc`   | MGC           | skills/design/resources/design.mgc.md      |
| `/design timesync` | TimeSync   | skills/design/resources/design.timesync.md |

---

## Adding a New Project

1. Create a new file: `skills/design/resources/design.<projectname>.md`
2. Fill in the five sections: Color Tokens, Typography, Spacing, PrimeNG Guidelines, Grid/Layout
3. Add the project to the trigger map in `skills/design/SKILL.md`
4. Done — the `/design <projectname>` command works immediately

---

## Installation in VS Code

### Option A — Install from local folder
Run from Command Palette:
```
Chat: Install Plugin From Source
```
Enter the local path to this folder (e.g. `C:/dev/plugins/office-design-plugin`).

### Option B — Install from Git (after pushing to remote)
Run from Command Palette:
```
Chat: Install Plugin From Source
```
Enter your Git repository URL.

---

## Folder Structure

```
office-design-plugin/
├── plugin.json                          # Plugin manifest
├── README.md
└── skills/
    └── design/
        ├── SKILL.md                     # Skill instructions for the agent
        └── resources/
            ├── design.mgc.md            # MGC design tokens
            └── design.timesync.md       # TimeSync design tokens
```

---

## Enabling the Plugin Feature in VS Code

Agent plugins are currently in preview. Enable with:

```json
// settings.json
"chat.plugins.enabled": true
```
