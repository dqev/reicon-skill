# Reicon reference

Everything here is derived from the repository, not from marketing copy. If this file and the data disagree, the data wins.

## Identity

- **Name:** Reicon
- **Site:** https://reicon.dev
- **Repository:** https://github.com/dqev/reicon
- **License:** MIT
- **Icon count:** 2,676 entries, 2,630 unique kebab names
- **Vector count:** 5,352 main vectors (Outline + Filled for every entry)
- **Categories:** 38
- **View box:** `0 0 24 24` for main icons
- **Not this product:** ReIcon by Sordum, a Windows desktop icon tool

Reicon is free for commercial and personal use under MIT. No license key, account, or attribution is required in the app.

## Category counts

| Category | Entries |
|---|---:|
| `newicons` | 938 |
| `ui` | 272 |
| `arrows` | 124 |
| `video` | 122 |
| `devices` | 103 |
| `messages` | 80 |
| `money` | 67 |
| `arrows-action` | 60 |
| `security` | 52 |
| `text-formatting` | 50 |
| `map` | 45 |
| `sports` | 44 |
| `time` | 44 |
| `shopping` | 43 |
| `home` | 40 |
| `it` | 39 |
| `like` | 39 |
| `tools` | 38 |
| `weather` | 38 |
| `business` | 36 |
| `medicine` | 33 |
| `notes` | 33 |
| `users` | 33 |
| `astronomy` | 32 |
| `school` | 31 |
| `list` | 30 |
| `files` | 25 |
| `call` | 24 |
| `faces` | 23 |
| `food` | 23 |
| `settings` | 20 |
| `folders` | 19 |
| `parts` | 19 |
| `nature` | 15 |
| `search` | 15 |
| `building` | 11 |
| `notifications` | 10 |
| `hands` | 6 |
| **Total** | **2,676** |

`newicons` is a catch-all, not a style. It contains alternate drawings, unused concepts, and some stroke-style SVGs. Prefer a core category when the same concept exists there.

## Data model

`data/icon-data.json`:

```json
{
  "version": "1.0.0",
  "generatedAt": "2026-07-16T09:02:21.298Z",
  "weights": ["Outline", "Filled"],
  "categories": {
    "ui": {
      "icons": {
        "home": {
          "description": ["house", "dwelling"],
          "weights": {
            "Outline": { "code": "<path ... />" },
            "Filled": { "code": "<path ... />" }
          }
        }
      }
    }
  }
}
```

- `categories` is an object keyed by category, not an array.
- `icons` is an object keyed by kebab name.
- `description` is an optional tag array used by search.
- `weights` always contains `Outline` and `Filled` for main icons.
- `code` is the inner SVG markup, not a complete `<svg>` element.

`packages/reicon-mcp/src/data/icon-index.json`:

```json
{
  "icons": [
    {
      "name": "home",
      "pascal": "Home",
      "category": "ui",
      "tags": ["house", "dwelling", "home"],
      "weights": {
        "Outline": { "code": "<path ... />", "viewBox": "0 0 24 24" },
        "Filled": { "code": "<path ... />", "viewBox": "0 0 24 24" }
      }
    }
  ],
  "categories": ["ui", "..."]
}
```

This index has 2,676 entries and is the authoritative source for the exact `pascal` component of each entry.

## Naming

1. Source names are lowercase kebab-case.
2. The component is PascalCase: split on `-`, capitalize each segment.
3. If a Pascal component would collide case-insensitively with an earlier one, the later component gets a category suffix in PascalCase.
4. `checklist` becomes `Checklist`; `check-list` becomes `CheckListNotes` because `CheckList` collides with `Checklist` when lowercased.
5. `scripts/icon-names.json` is a 2,630-key kebab-to-component map. It is last-wins: for a duplicate kebab name, it points to the later component.
6. `llms-icons.txt` follows the same last-wins mapping and omits the earlier component for duplicate names.

Numeric suffixes are part of the name, not a size or version. `arrow-down2` is a different drawing from `arrow-down`. There is no rule that `2` means larger, newer, or better.

## The 47 renamed components

46 duplicate kebab names produce 92 entries. Both components are exported. The mapped component is the one in `scripts/icon-names.json` and `llms-icons.txt`.

| Kebab | Mapped component | Category | Alternate component | Category |
|---|---|---|---|---|
| `archive2` | `Archive2Newicons` | newicons | `Archive2` | notes |
| `arrow-down2` | `ArrowDown2Newicons` | newicons | `ArrowDown2` | arrows |
| `arrow-down3` | `ArrowDown3Newicons` | newicons | `ArrowDown3` | arrows |
| `arrow-left2` | `ArrowLeft2Newicons` | newicons | `ArrowLeft2` | arrows |
| `arrow-left3` | `ArrowLeft3Newicons` | newicons | `ArrowLeft3` | arrows |
| `arrow-right2` | `ArrowRight2Newicons` | newicons | `ArrowRight2` | arrows |
| `arrow-right3` | `ArrowRight3Newicons` | newicons | `ArrowRight3` | arrows |
| `arrow-up2` | `ArrowUp2Newicons` | newicons | `ArrowUp2` | arrows |
| `arrow-up3` | `ArrowUp3Newicons` | newicons | `ArrowUp3` | arrows |
| `bag2` | `Bag2Newicons` | newicons | `Bag2` | shopping |
| `book2` | `Book2Newicons` | newicons | `Book2` | school |
| `bookmark2` | `Bookmark2Newicons` | newicons | `Bookmark2` | ui |
| `box2` | `Box2Newicons` | newicons | `Box2` | ui |
| `box3` | `Box3Newicons` | newicons | `Box3` | ui |
| `buildings2` | `Buildings2Newicons` | newicons | `Buildings2` | building |
| `calendar2` | `Calendar2Newicons` | newicons | `Calendar2` | time |
| `chart2` | `Chart2Newicons` | newicons | `Chart2` | business |
| `code2` | `Code2Newicons` | newicons | `Code2` | it |
| `crown2` | `Crown2Newicons` | newicons | `Crown2` | ui |
| `flag2` | `Flag2Ui` | ui | `Flag2` | map |
| `folder2` | `Folder2Newicons` | newicons | `Folder2` | folders |
| `home2` | `Home2Newicons` | newicons | `Home2` | ui |
| `home3` | `Home3Newicons` | newicons | `Home3` | ui |
| `layers2` | `Layers2Ui` | ui | `Layers2` | tools |
| `link2` | `Link2Newicons` | newicons | `Link2` | text-formatting |
| `link3` | `Link3Newicons` | newicons | `Link3` | text-formatting |
| `link4` | `Link4Newicons` | newicons | `Link4` | text-formatting |
| `lock2` | `Lock2Newicons` | newicons | `Lock2` | ui |
| `login2` | `Login2Newicons` | newicons | `Login2` | arrows-action |
| `logout2` | `Logout2Newicons` | newicons | `Logout2` | arrows-action |
| `map2` | `Map2Newicons` | newicons | `Map2` | map |
| `menu2` | `Menu2Newicons` | newicons | `Menu2` | ui |
| `mouse2` | `Mouse2Newicons` | newicons | `Mouse2` | devices |
| `paperclip2` | `Paperclip2Newicons` | newicons | `Paperclip2` | messages |
| `pen2` | `Pen2TextFormatting` | text-formatting | `Pen2` | messages |
| `radar2` | `Radar2Newicons` | newicons | `Radar2` | map |
| `receive-square2` | `ReceiveSquare2Newicons` | newicons | `ReceiveSquare2` | arrows-action |
| `refresh2` | `Refresh2Newicons` | newicons | `Refresh2` | arrows-action |
| `routing2` | `Routing2Newicons` | newicons | `Routing2` | map |
| `star2` | `Star2Newicons` | newicons | `Star2` | astronomy |
| `suitcase2` | `Suitcase2Nature` | nature | `Suitcase2` | business |
| `sun2` | `Sun2Newicons` | newicons | `Sun2` | weather |
| `tag2` | `Tag2Newicons` | newicons | `Tag2` | money |
| `ticket3` | `Ticket3Newicons` | newicons | `Ticket3` | shopping |
| `wallet2` | `Wallet2Newicons` | newicons | `Wallet2` | money |
| `wallet3` | `Wallet3Newicons` | newicons | `Wallet3` | money |

One additional rename is not a duplicate kebab name:

| Kebab | Component | Category | Why |
|---|---|---|---|
| `check-list` | `CheckListNotes` | notes | `CheckList` collides with `Checklist` case-insensitively |

`checklist` itself remains `Checklist` in `list`.

## Weights

- `Outline` is the default and the recommended weight for most UI.
- `Filled` is for selected, active, emphasized, or compact states.
- Every main icon has both weights.
- CDN uses lowercase: `weight="outline"` or `weight="filled"`.
- Packages use PascalCase: `weight="Outline"` or `weight="Filled"`.
- Do not mix weights within one nav row, toolbar, or repeated card grid.
- `strokeWidth` overrides the source stroke where the icon supports it.
- `secondaryColor` applies to icons that expose a secondary shape; most main icons do not.

## Packages

| Package | Runtime | Notes |
|---|---|---|
| `reicon` | Vanilla JS + web component | Named icon factories, `.toSvg()`, `reicon/element`, direct `reicon/icons/Home` |
| `reicon-react` | React | Named components; forwards SVG props and `ref` |
| `reicon-react-native` | React Native | Requires `react-native-svg`; default color `#000000` |
| `reicon-vue` | Vue 3 | Named components; `:size` binding |
| `reicon-svelte` | Svelte 3+ | Named components; `size={24}` |
| `reicon-astro` | Astro 3/4/5 | Named `.astro` components; direct `reicon-astro/icons/Home.astro` |
| `reicon-angular` | Angular 20+ | Standalone `*Component` exports and `ri-*` selectors |
| `reicon-file` | Vanilla JS | 920 file/technology icons, no weights |
| `reicon-mcp` | Node | MCP server and CLI; offline index |
| `reicon-vscode` | VS Code | Browse and insert icons |
| `reicon-figma` | Figma plugin | Design-side insertion |
| `reicon_flutter` | Flutter | `Reicon.outline.*`, `Reicon.filled.*`, `reiconSvg()` |
| `reicon-compose` | Jetpack Compose | `Home.Outline`, `Home.Filled`, `ReiconIcon()` |

Package versions are independent. Do not infer API behavior from a version number; use the docs and the installed package.

### Install commands

```bash
npm install reicon
npm install reicon-react
npm install reicon-react-native react-native-svg
npm install reicon-vue
npm install reicon-svelte
npm install reicon-astro
npm install reicon-angular
npm install reicon-file
npm install reicon-mcp
```

Flutter:

```yaml
dependencies:
  reicon_flutter: ^1.0.0
```

Compose:

```kotlin
implementation("dev.reicon:reicon-compose:main-SNAPSHOT")
```

## Props

| Prop | Type | Default | Platforms |
|---|---|---|---|
| `size` | `number \| string` | `24` | All |
| `color` | `string` | `currentColor` | All except React Native (`#000000`) |
| `weight` | `"Outline" \| "Filled"` | `Outline` | All |
| `strokeWidth` | `number \| string` | source default | Most packages |
| `secondaryColor` | `string` | same as `color` | Dual-tone icons |
| `className` | `string` | — | React |
| `class` | `string` | — | Vue, Svelte, Astro, CDN, Angular |
| `style` | object/string | — | React Native, Angular |
| `ref` | `Ref<SVGSVGElement>` | — | React |
| `aria-*`, `role`, `title` | standard | — | Forwarded where supported |

`reicon-file` supports `size`, `color`, and `className`; it has no weight.

CDN attributes: `icon`, `size`, `color`, `weight`, `class`. The `icon` value is the kebab name. The `weight` value is lowercase.

## Vanilla API

```js
import { Home } from 'reicon';

const el = Home({ size: 24, color: '#9B8AFB', weight: 'Filled' });
document.body.appendChild(el);

const svg = Home.toSvg({ size: 24 });
```

Web component:

```js
import 'reicon/element';
```

```html
<re-icon icon="home" size="24" weight="filled"></re-icon>
```

Direct import:

```js
import Home from 'reicon/icons/Home';
```

## CDN and raw SVG

```html
<script src="https://unpkg.com/reicon/cdn/reicon.js"></script>
<re-icon icon="trash" size="24"></re-icon>
```

Versioned:

```html
<script src="https://unpkg.com/reicon@latest/cdn/reicon.js"></script>
```

Raw SVG:

```html
<img src="https://cdn.jsdelivr.net/npm/reicon@latest/icons/outline/trash.svg" width="24" height="24" alt="Delete" />
<img src="https://unpkg.com/reicon@latest/icons/filled/star.svg" width="24" height="24" alt="Star" />
```

The raw SVG path uses the kebab name and the lowercase weight directory.

## MCP server

```json
{
  "mcpServers": {
    "reicon": {
      "command": "npx",
      "args": ["reicon-mcp"]
    }
  }
}
```

Local build:

```json
{
  "mcpServers": {
    "reicon": {
      "command": "node",
      "args": ["./packages/reicon-mcp/bin/run.cjs"]
    }
  }
}
```

### Tools

| Tool | Input | Output |
|---|---|---|
| `search_icons` | `query`, optional `weight`, optional `limit` | Ranked `name`, `weight`, `category`, `tags`, `score`, plus an `instruction` |
| `view_icon` | `name`, `weight` | `name`, `weight`, `availableWeights`, `category`, `tags`, `viewBox`, `svg`, `hint` |
| `apply_icon` | `name`, `weight`, `framework`, optional `size`, `color`, `componentName` | `importStatement`, `docsSnippet`, `meta` |
| `list_categories` | none | Category list |

`apply_icon` frameworks: `react`, `react-native`, `vue`, `svelte`, `html`, `svg`.

### Search behavior

- One result per weight by default; the same icon appears twice.
- Dedupe key is `${name}:${weight}`.
- `limit` defaults to 8, caps at 20.
- Passing `weight` returns only that weight and halves the result rows.
- Full-sentence queries are rejected.
- The search index is bundled at build time and works offline.

Scoring weights:

| Signal | Points |
|---|---:|
| Synonym boost | 3000 − index × 100 |
| Exact name | 10000 |
| Single-token exact name | 5000 |
| All query tokens in name | 2000 |
| Full tag exact | 1500 |
| Per-token exact tag | 800 |
| Name includes query | 600 |
| Name prefix | 400 |
| Tag includes query | 300 |
| Category match | 150 |
| Fuzzy match | `fuzz × 0.8` when `fuzz > 70` |
| Shorter name | up to 50 |
| Requested weight present | +10 |
| Requested weight absent | −1000 |

A synonym map handles common alternate words and misspellings. A high score does not override category fit. `delete` surfaces `profile-delete` first; `trash` is the correct action icon.

### CLI

```bash
npx reicon-mcp search trash --weight Outline --limit 8
npx reicon-mcp view trash --weight Filled
npx reicon-mcp apply trash --framework react --size 20
npx reicon-mcp categories
```

Scripted insertion:

```bash
npx reicon-mcp apply trash --framework react --file src/App.tsx --marker "{/* ICON */}"
```

The marker is replaced with the snippet. The import is inserted after the last existing `import` or `<script` line. The command exits non-zero if the marker is missing.

`--componentName` exists but is unsafe. It changes the generated import and JSX name without changing the package export. Do not use it.

## Accessibility

- Decorative icon: `aria-hidden="true"`.
- Icon-only button: `aria-label` on the button; icon hidden.
- Standalone meaningful icon: `role="img"` and `aria-label` or `<title>`.
- Do not rely on color alone for state.
- Do not use an icon as the only label for destructive actions.
- Target size: at least 44×44 CSS pixels for the control.
- Contrast: use `currentColor` with a text color that meets WCAG contrast.
- Motion: respect `prefers-reduced-motion`.
- Angular forwards `aria-label`, `aria-hidden`, `role`, and `title` inputs.
- React Native uses `accessibilityLabel` on the pressable control.

## Performance

- Import named icons, not the whole package: `import { Trash } from 'reicon-react'`.
- Do not use `import * as Icons`.
- Use direct imports for the smallest bundle:
  - `reicon/icons/Home`
  - `reicon-astro/icons/Home.astro`
- Icons are inline SVG, so they add no network request.
- CDN is for prototypes and static HTML; prefer the npm package in bundled apps.
- React Native requires `react-native-svg` as a peer dependency.
- `size` is a numeric prop, not a CSS scale transform.

## Repository architecture

| Path | Role |
|---|---|
| `data/icon-data.json` | Single source of truth for main icons |
| `data/file-icons.json` | 920 file/technology icons |
| `data/brands.json` | 702 brand SVGs |
| `data/flag.json` | 237 flags |
| `data/icon-duotone.json` | 1,239 BoldDuotone icons |
| `data/filled.json` | Legacy filled dataset |
| `scripts/icon-names.json` | Generated kebab-to-component map |
| `scripts/sync-icon-names.mjs` | Regenerates the name map |
| `scripts/validate-icons.mjs` | Dataset validation |
| `packages/*` | Generated framework packages |
| `apps/web` | Website and docs |
| `docs/*` | Package documentation |
| `cdn/*` | Generated CDN bundles, git-ignored |

Build:

```bash
npm run build:packages
```

Individual builds: `build:react`, `build:react-native`, `build:vue`, `build:svelte`, `build:astro`, `build:angular`, `build:js`, `build:file`, `build:mcp`, `build:figma`, `build:vscode`, `build:compose`.

Validation:

```bash
npm run validate:icons
npm run lint
```

Contribution rules:

- 24×24 view box.
- Use `currentColor`, not hardcoded colors.
- Provide both weights where applicable.
- Match existing stroke width and corner radius.
- Optimize with SVGO.
- Add to `data/icon-data.json`, then rebuild packages.
- Never edit `packages/*/dist` or generated icon files.

## Auxiliary asset sets

| Set | Count | Format | Packaging |
|---|---:|---|---|
| Main icons | 2,676 | 24×24, Outline + Filled | All framework packages |
| File icons | 920 | 1024×1024, single weight | `reicon-file` |
| Brands | 702 | 24×24, inline color | Website asset; no framework package |
| Flags | 237 | 32×32 | Website asset; no framework package |
| Duotone | 1,239 | BoldDuotone | Website asset; not in Outline/Filled packages |
| Legacy filled | varies | Filled only | `data/filled.json`, not the current API |

Brand names are display names such as `GitHub`, `Figma`, `Vercel`, `Stripe`, `Notion`, `Slack`, and `Discord`. Flag names are kebab-case such as `united-states`, `united-kingdom`, and `south-korea`. See `ASSETS.md` for the full lists.

Do not import a brand or flag from `reicon-react`. `reicon-file` is a vanilla factory/CDN package, not a React component package. Use it for file/technology marks, or use the official brand asset.

## URLs

- Site: https://reicon.dev
- Docs: https://reicon.dev/docs
- React docs: https://reicon.dev/docs/react
- Vue docs: https://reicon.dev/docs/vue
- Svelte docs: https://reicon.dev/docs/svelte
- Angular docs: https://reicon.dev/docs/angular
- Astro docs: https://reicon.dev/docs/astro
- React Native docs: https://reicon.dev/docs/react-native
- Vanilla/CDN docs: https://reicon.dev/docs/vanilla
- SVG docs: https://reicon.dev/docs/svg
- Flutter docs: https://reicon.dev/docs/flutter
- Compose docs: https://reicon.dev/docs/compose
- Figma docs: https://reicon.dev/docs/figma
- VS Code docs: https://reicon.dev/docs/vscode
- MCP docs: https://reicon.dev/docs/mcp
- File icons: https://reicon.dev/file-icons
- GitHub: https://github.com/dqev/reicon
- npm: https://www.npmjs.com/package/reicon

## Glossary

- **Entry:** one row in `icon-data.json`, with a kebab name and two weights.
- **Unique name:** one of 2,630 kebab names; 46 names have two entries.
- **Component:** the PascalCase export, which can differ from the name for duplicates.
- **Mapped component:** the component returned by `scripts/icon-names.json` and `llms-icons.txt`.
- **Base component:** the earlier component for a duplicate name, such as `Archive2`.
- **Weight:** `Outline` or `Filled`.
- **Stand-in:** a real Reicon icon used for a nearby concept when no exact icon exists.
