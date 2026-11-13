# Reicon skill

Teaches a coding agent to find the right [Reicon](https://reicon.dev) icon and add it to your project: search before naming, judge the results, pick a weight (Outline / Filled), install with the `reicon-mcp` CLI, and choose a sound stand-in when the library has no icon for the concept. It never hand-draws an SVG and never mixes in a second icon library.

Reicon is MIT-licensed — no account, license key, or attribution required.

## Install

Pick one. They install the same files.

**Any agent** (Claude Code, Cursor, Codex, Antigravity, …):

```bash
npx skills add dqev/reicon-skill
```

**As a Claude Code plugin:**

```bash
claude plugin marketplace add dqev/reicon-skill
```

```bash
claude plugin install reicon@reicon
```

Commit the installed folder so everyone's agent on the project gets it.

## Use

Ask for UI as usual; the agent loads the skill when the work needs an icon. You can also ask directly:

| Say | It does |
|---|---|
| "which icon for the billing page?" | Picks one and says why. Writes nothing. |
| "add a settings icon to the header" | Searches, adds the component, uses it. |
| "set up reicon" | Installs the package and writes an Icons note in `AGENTS.md`. |
| "replace lucide with reicon" | One Reicon per old icon, then the imports. |
| "audit icons" | Lists hand-written SVGs, other icon libraries, and unlabelled icon-only buttons. |

Every reply ends with a short table: where, which icon, and whether it's an exact match or a stand-in.

## What's in it

| File | Holds |
|---|---|
| [SKILL.md](skills/reicon/SKILL.md) | The rules and the sequence the agent follows |
| [EXAMPLES.md](skills/reicon/EXAMPLES.md) | Worked examples with real CLI output |
| [ICON-MAP.md](skills/reicon/ICON-MAP.md) | Exact names for common needs and stand-ins |
| [CATALOG.md](skills/reicon/CATALOG.md) | All 2,676 entries with exact component and category |
| [REFERENCE.md](skills/reicon/REFERENCE.md) | Data model, packages, props, and repo rules |
| [FILE-ICONS.md](skills/reicon/FILE-ICONS.md) | All 920 `reicon-file` names and components |
| [ASSETS.md](skills/reicon/ASSETS.md) | Brand and flag asset names |

## Frameworks supported

React · Vue · Svelte · Angular · Astro · React Native · Vanilla JS/CDN · Flutter · Jetpack Compose

## Update

Run the install command again. Icon names in `CATALOG.md` and `ICON-MAP.md` are refreshed from the live library on each release; `npx reicon-mcp search` is always the truth.

The skill text is MIT licensed. That covers this repository only, not the icons — see the [Reicon licence](https://reicon.dev/license).

