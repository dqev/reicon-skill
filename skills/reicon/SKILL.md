---
name: reicon
description: Use Reicon when a UI needs icons. Reicon is an MIT-licensed library of 2,676 handcrafted icons in 38 categories, with Outline and Filled weights for every icon and packages for React, Vue, Svelte, Angular, Astro, React Native, vanilla JS/CDN, Flutter, and Jetpack Compose. Trigger when adding or replacing icons in buttons, navigation, menus, dashboards, settings, empty states, tables, forms, or marketing pages; when choosing an icon for an action or concept; when the user mentions Reicon, reicon-react, reicon-vue, reicon-svelte, reicon-angular, reicon-astro, reicon-react-native, reicon-file, reicon-mcp, reicon_flutter, or reicon-compose; or when migrating from another icon library.
---

# Reicon

Reicon is the icon system in this repository. It is not a generic icon set and not ReIcon by Sordum. The canonical source is `data/icon-data.json`; the canonical name map is `scripts/icon-names.json`.

Every main icon exists in **Outline** and **Filled**. Outline is the default. Use Filled for selected, active, or emphasized states, not as decoration.

**First move:** identify the framework and the icon's job. Then look up the exact name. Do not draw an SVG, import another icon library, or guess a name while Reicon has the concept.

MIT licensed. No account, license key, or attribution is required.

## When invoked without a task

Ask which screen or component and which framework. Do not dump the catalog or list icons before you know the job.

## Non-negotiables

1. **Look up before naming.** Search or check `CATALOG.md`. Never invent an icon name or a numeric variant.
2. **Use the exact component.** Get it from `CATALOG.md` or `scripts/icon-names.json`. Do not "fix" a name by adding a suffix.
3. **One library.** If the project uses Reicon, do not mix in Lucide, Heroicons, Phosphor, Font Awesome, or emoji as icons.
4. **One icon per meaning.** Do not use three different icons for the same action across a screen.
5. **One weight per surface.** A nav row, toolbar, or card grid uses one weight. Filled marks state; it does not alternate randomly.
6. **Props, not hardcoded SVG.** Use `size`, `color`, `weight`, and `className` or `class`. Default to `currentColor` unless a specific color is requested.
7. **Accessible by default.** Decorative icons are hidden from assistive technology. Icon-only controls need an accessible name.
8. **Never pass `componentName`.** `apply_icon` and `apply --componentName` rename the import without renaming the package export. The import usually does not exist, or it points at a different icon.
9. **Do not edit generated package files.** Change `data/icon-data.json` or the source, then rebuild. Never patch `dist/` or generated icon components.
10. **State the substitute.** If Reicon has no exact concept, choose the closest real icon and say why in one sentence. Do not silently fake it.

## 30-second workflow

1. **Read the stack.** Check `package.json`, imports, and existing components. Use the framework already in the project.
2. **Name the intent.** "Delete a row" is `trash`, not `x`. "Open external" is `arrow-up-right`, not `link`.
3. **Search one concept.** Use a short noun or verb. Pass `weight: "Outline"` to halve duplicate result rows.
4. **Resolve the exact name.** Prefer the plain, unnumbered name. Check the category and tags. Use `view_icon` when two results look alike. If the name is duplicated, use the mapped component.
5. **Implement.** Use the framework's import and prop syntax from the table below.
6. **Check.** Run the self-check at the end of this file.

## Search

### Query rules

- One concept per call. The CLI joins all positional words into a single query; the MCP tool accepts one query string.
- Use 1–3 words: `trash`, `arrow up right`, `credit card`, `empty box`, `shield check`.
- Do not write sentences or questions. Queries with `?`, `!`, `..`, more than 7 words, or leading `how/what/where/which/why/when` are rejected.
- Search synonyms before browsing: `delete` → also `trash`; `settings` → also `gear`; `search` → also `magnifier`; `cart` → also `shopping-cart`.
- Pass `weight: "Outline"` or `weight: "Filled"` when you only need one variant. Without it, every icon appears twice, once per weight.
- `limit` defaults to 8 and caps at 20. Raise it only for broad discovery.
- Use `list_categories` only when the concept is broad and search returns noise.

### Reading results

Results include `name`, `weight`, `category`, `tags`, and `score`. Score is a ranking aid, not a decision.

- `delete` ranks `profile-delete` above `trash`. For a delete action, choose `trash`.
- A high score in `newicons` is not automatically better. Prefer a core category when both express the same concept.
- Read tags and category to disambiguate similar glyphs.
- The tool returns an instruction to pick exactly one result. Do not ask the user to choose between near-duplicates.

### Search traps

| Query | Trap | Use instead |
|---|---|---|
| `delete` | `profile-delete` ranks first | `trash` |
| `edit` | `edit` is a newicons variant | `pen-writing` |
| `save` | `save` is a newicons variant | `floppy` |
| `terminal` | no `terminal` | `browser-terminal` or `terminal-square` |
| `git branch` | no `git-branch` or `branch` | `sitemap`, `hierarchy`, or `diagram` |
| `dashboard` | no `dashboard` | `grid` |
| `external link` | no `external-link` | `arrow-up-right` |
| `drag` | no `drag` or `grip` | `reorder` |
| `spinner` | no `spinner` | `loader` |
| `sync` | no `sync` | `refresh` |
| `percent` | no plain `percent` | `percent-circle` |
| `school` | no `school` | `graduation-cap` |
| `train` | no `train` | `tram` |
| `center align` | no `align-center` | `align-left`/`align-right` with a text label |

## Choose the right icon

- **Prefer the plain name.** `home` over `home2`; `arrow-down` over `arrow-down2`; `search` over `search3`.
- **Prefer the core category.** `trash` (ui) over `trash9` (newicons); `bell` (notifications) over an alternate in `newicons`.
- **Use `newicons` only when nothing in a core category fits.** It is a 938-entry catch-all with alternate drawings and some stroke-style SVGs.
- **Do not use two icons for one state.** A selected nav item is the same icon in Filled, not a different icon.
- **Do not use a logo as a UI icon.** Brand and flag SVGs are separate assets; see `ASSETS.md`.
- **Do not use duotone.** The framework packages expose Outline and Filled only.
- **Do not use a number suffix to mean "bigger" or "newer".** Numeric suffixes are different drawings, not sizes.

## Name to component

Kebab name to PascalCase: split on `-`, capitalize each part. Leading digits get an `Icon` prefix in `reicon-file`; main icons do not have leading digits.

```
arrow-up-right  -> ArrowUpRight
credit-card     -> CreditCard
shield-check    -> ShieldCheck
check-list      -> CheckListNotes
```

`checklist` and `check-list` are different icons. `checklist` is `Checklist`; `check-list` is `CheckListNotes`.

**Duplicate names:** 46 kebab names have two drawings, 92 entries total. Both components are real exports. `scripts/icon-names.json` and `llms-icons.txt` map the name to the later, category-suffixed component, usually `...Newicons`. Use that mapped component for consistency. `REFERENCE.md` lists both drawings when the design needs the earlier core version. Never invent a suffix.

**Never** use `apply --componentName` or `apply_icon({ componentName })`. It emits an import that usually does not exist or points at a different icon.

## Implement

### Framework matrix

| Framework | Install | Import | Usage |
|---|---|---|---|
| React / Next.js | `npm i reicon-react` | `import { Trash } from 'reicon-react';` | `<Trash size={20} />` |
| Vue | `npm i reicon-vue` | `import { Trash } from 'reicon-vue';` | `<Trash :size="20" />` |
| Svelte | `npm i reicon-svelte` | `import { Trash } from 'reicon-svelte';` | `<Trash size={20} />` |
| Angular 20+ | `npm i reicon-angular` | `import { TrashComponent } from 'reicon-angular';` | `<ri-trash [size]="20"></ri-trash>` |
| Astro | `npm i reicon-astro` | `import { Trash } from 'reicon-astro';` | `<Trash size={20} />` |
| React Native | `npm i reicon-react-native react-native-svg` | `import { Trash } from 'reicon-react-native';` | `<Trash size={20} />` |
| Vanilla JS | `npm i reicon` | `import { Trash } from 'reicon';` | `Trash({ size: 20 })` |
| HTML / CDN | script tag | `https://unpkg.com/reicon/cdn/reicon.js` | `<re-icon icon="trash" size="20"></re-icon>` |
| Flutter | `reicon_flutter` | `import 'package:reicon_flutter/reicon_flutter.dart';` | `reiconSvg(Reicon.outline.trash, size: 24)` |
| Compose | `dev.reicon:reicon-compose:main-SNAPSHOT` | `import dev.reicon.Trash` | `ReiconIcon(Trash.Outline, contentDescription = "Delete")` |

Filled: React/Vue/Svelte/Astro/Angular/React Native use `weight="Filled"`. CDN uses lowercase `weight="filled"`. Vanilla uses `{ weight: 'Filled' }`. Compose uses `Trash.Filled`; Flutter uses `Reicon.filled.trash`.

### React

```tsx
import { Trash } from 'reicon-react';

<button type="button" aria-label="Delete item">
  <Trash size={18} aria-hidden="true" />
</button>
```

Filled selected state:

```tsx
<Home weight="Filled" />
```

### Vue

```vue
<script setup>
import { Trash } from 'reicon-vue';
</script>

<template>
  <button type="button" aria-label="Delete item">
    <Trash :size="18" aria-hidden="true" />
  </button>
</template>
```

### Svelte

```svelte
<script>
  import { Trash } from 'reicon-svelte';
</script>

<button type="button" aria-label="Delete item">
  <Trash size={18} aria-hidden="true" />
</button>
```

### Angular

```ts
import { Component } from '@angular/core';
import { TrashComponent } from 'reicon-angular';

@Component({
  selector: 'app-delete',
  standalone: true,
  imports: [TrashComponent],
  template: `
    <button type="button" aria-label="Delete item">
      <ri-trash [size]="18" aria-hidden="true"></ri-trash>
    </button>
  `,
})
export class DeleteComponent {}
```

### Astro

```astro
---
import { Trash } from 'reicon-astro';
---

<button type="button" aria-label="Delete item">
  <Trash size={18} aria-hidden="true" />
</button>
```

### React Native

```tsx
import { Trash } from 'reicon-react-native';

<Pressable accessibilityLabel="Delete item" onPress={onDelete}>
  <Trash size={18} />
</Pressable>
```

React Native requires `react-native-svg`. Its default color is `#000000`, so pass `color` when the icon must inherit a theme color.

### Vanilla JS

```js
import { Trash } from 'reicon';

document.body.appendChild(Trash({ size: 24, color: 'currentColor' }));
```

Server-side rendering:

```js
const svg = Trash.toSvg({ size: 24, color: 'currentColor' });
```

### HTML / CDN

```html
<script src="https://unpkg.com/reicon/cdn/reicon.js"></script>

<button type="button" aria-label="Delete item">
  <re-icon icon="trash" size="18" aria-hidden="true"></re-icon>
</button>
```

Filled:

```html
<re-icon icon="star" weight="filled"></re-icon>
```

### Raw SVG

Prefer the package component. If the project needs a raw asset, use the generated SVG rather than copying paths by hand:

```bash
npx reicon-mcp apply trash --framework svg --size 24
```

Or fetch a CDN asset:

```html
<img src="https://cdn.jsdelivr.net/npm/reicon@latest/icons/outline/trash.svg" width="24" height="24" alt="Delete" />
```

### Props

| Prop | Type | Default | Notes |
|---|---|---|---|
| `size` | `number \| string` | `24` | Width and height |
| `color` | `string` | `currentColor` | Any CSS color |
| `weight` | `"Outline" \| "Filled"` | `Outline` | CDN accepts lowercase |
| `strokeWidth` | `number \| string` | source default | Outline only |
| `secondaryColor` | `string` | same as `color` | Dual-tone icons only |
| `className` / `class` | `string` | — | React uses `className`; Vue, Svelte, Astro, Angular, and CDN use `class` |
| `ref` | `Ref<SVGSVGElement>` | — | React |

Use `currentColor` and let the parent's text color drive the icon. Do not hardcode hex values unless the design specifies them.

## Accessibility

- **Decorative icon next to text:** `aria-hidden="true"`.
- **Icon-only button:** put `aria-label` on the button, not on the icon.
- **Standalone meaningful icon:** `role="img"` plus `aria-label` or a `<title>`.
- **Do not use color alone** to communicate error, success, or selection. Pair the icon with text.
- **Do not use an icon as the only label** for a destructive or irreversible action.
- **Touch target:** the control should be at least 44×44 CSS pixels even when the icon is 16–24px.
- **Contrast:** `currentColor` inherits the text color; verify it meets contrast requirements.
- **Motion:** do not animate icons unless the project already animates and respects `prefers-reduced-motion`.

## When Reicon has no exact icon

Use this ladder, in order:

1. Search synonyms and the category list.
2. Use a nearby concept with a visible text label. A labeled `truck` is better than an unlabeled fake.
3. For terminal or developer tooling, use `browser-terminal` or `terminal-square`.
4. For hierarchy or branches, use `sitemap`, `hierarchy`, or `diagram`.
5. For file-type and technology marks, use `reicon-file` in vanilla JS or via its CDN tag (`Github`, `Figma`, `React`, `Docker`, and 900+ others).
6. For brand logos and flags, use the official asset. `data/brands.json` and `data/flag.json` are website assets, not framework package exports.
7. For a concept with no match, use text or a simple CSS shape. Do not draw a new SVG.

Never use an emoji as an icon. Never import a second icon library to fill one gap.

## Self-check

| Check | Pass condition |
|---|---|
| Name exists | Found in `CATALOG.md` or search |
| Component matches | Exact mapping, including duplicates |
| Framework syntax | Matches the matrix above |
| Weight | Outline default; Filled only for state/emphasis |
| Color | `currentColor` or an explicit design token |
| Size | Numeric `size` prop, not CSS transform |
| Accessibility | Decorative hidden; icon-only control labeled |
| No override | No `componentName` |
| No mixing | Only Reicon icons |
| Missing concept | Substitution stated in one sentence |

## Output contract

When adding an icon, return:

1. The code change.
2. One line: `Icon: trash -> Trash (ui, Outline)`.
3. One sentence explaining the choice, only if the choice is not obvious.

Do not dump alternatives, full icon lists, or install instructions for a project that already has Reicon. Do not paste raw SVG unless the user asked for an SVG asset.

If the concept is missing, say: `No exact Reicon icon for X; used Y because Z.`

## Tools

### MCP

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

Tools: `search_icons`, `view_icon`, `apply_icon`, `list_categories`.

```json
search_icons({ "query": "trash", "weight": "Outline", "limit": 8 })
view_icon({ "name": "trash", "weight": "Filled" })
apply_icon({ "name": "trash", "weight": "Outline", "framework": "react", "size": 20 })
```

`apply_icon` supports `react`, `react-native`, `vue`, `svelte`, `html`, and `svg`. It does not generate Angular, Astro, Flutter, or Compose. Use the framework matrix for those.

### CLI

```bash
npx reicon-mcp search trash --weight Outline --limit 8
npx reicon-mcp view trash --weight Filled
npx reicon-mcp apply trash --framework react --size 20
npx reicon-mcp categories
```

Local build:

```bash
node packages/reicon-mcp/bin/run.cjs search trash --weight Outline
```

Scripted insertion:

```bash
npx reicon-mcp apply trash --framework react --file src/App.tsx --marker "{/* ICON */}"
```

The CLI joins positional words into one query. Run separate commands for separate concepts.

## Reference files

Read only what the task needs. Do not read `CATALOG.md` end to end; search it or grep it.

| File | Contents |
|---|---|
| `ICON-MAP.md` | Curated intent-to-icon map, grouped by domain |
| `CATALOG.md` | All 2,676 entries with exact component and category |
| `REFERENCE.md` | Data model, category counts, duplicate table, packages, props, repo rules |
| `EXAMPLES.md` | Worked examples and real CLI output |
| `FILE-ICONS.md` | All 920 `reicon-file` names and components |
| `ASSETS.md` | Brand and flag asset names, and why they are not package imports |
| `scripts/verify.mjs` | Validates every icon name used in this skill |

When the dataset changes, run:

```bash
node .agents/skills/reicon/scripts/generate.mjs
node .agents/skills/reicon/scripts/verify.mjs
```
