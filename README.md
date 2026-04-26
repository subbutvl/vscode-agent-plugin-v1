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

### Internal Projects

| Command            | Project   | File                                        |
|--------------------|-----------|---------------------------------------------|
| `/design mgc`      | MGC       | skills/design/resources/mgc.design.md       |
| `/design timesync` | TimeSync  | skills/design/resources/timesync.design.md  |

### Brand Reference Library

Use `/design <brand>` with any of the following brands. Files follow the pattern `skills/design/resources/<brand>_design.md`.

airbnb · airtable · apple · binance · bmw · bugatti · cal · claude · clay · clickhouse · cohere · coinbase · composio · cursor · elevenlabs · expo · ferrari · figma · framer · hashicorp · ibm · intercom · kraken · lamborghini · linear.app · lovable · mastercard · minimax · mintlify · miro · mistral.ai · mongodb · notion · nvidia · ollama · opencode.ai · pinterest · platstation · posthog · raycast · renault · replicate · resend · revolut · runwayml · sanity · sentry · shopify · spacex · spotify · starbucks · stripe · supabase · superhuman · tesla · theverge · together.ai · uber · vercel · vodafone · voltagent · warp · webflow · wired · wise · x.ai · zapier

---

## Adding a New Project

1. Create a new file using the appropriate naming pattern:
   - Internal project: `skills/design/resources/<projectname>.design.md`
   - Brand reference: `skills/design/resources/<projectname>_design.md`
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
├── README.md
└── skills/
    └── design/
        ├── SKILL.md                     # Skill instructions for the agent
        └── resources/
            ├── mgc.design.md            # MGC design tokens
            ├── timesync.design.md       # TimeSync design tokens
            └── <brand>_design.md        # Brand reference tokens (airbnb, stripe, etc.)
```

---

## Enabling the Plugin Feature in VS Code

Agent plugins are currently in preview. Enable with:

```json
// settings.json
"chat.plugins.enabled": true
```
