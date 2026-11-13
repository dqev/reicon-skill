# Reicon examples

These are real searches and real CLI output from this repository. Trimmed only where noted.

## 1. React delete button

**Request:** "Add a delete button to each row."

**Wrong move:** search `delete`, take the top result `profile-delete`.

```json
{
  "results": [
    { "name": "profile-delete", "weight": "Outline", "category": "newicons", "score": 5246 },
    { "name": "profile-delete", "weight": "Filled", "category": "newicons", "score": 5246 },
    { "name": "trash", "weight": "Outline", "category": "ui", "score": 2955 },
    { "name": "trash", "weight": "Filled", "category": "ui", "score": 2955 },
    { "name": "backspace", "weight": "Outline", "category": "text-formatting", "score": 2651 }
  ]
}
```

**Right move:** search `trash` with `weight: "Outline"`.

```json
{
  "results": [
    {
      "name": "trash",
      "weight": "Outline",
      "category": "ui",
      "tags": ["trash can", "wastepaper basket", "trash"],
      "score": 23655
    },
    { "name": "trash9", "weight": "Outline", "category": "newicons", "score": 5654 },
    { "name": "trash2", "weight": "Outline", "category": "ui", "score": 3354 },
    { "name": "trash3", "weight": "Outline", "category": "ui", "score": 3354 },
    { "name": "trash4", "weight": "Outline", "category": "ui", "score": 3354 }
  ]
}
```

`trash4` is tagged `pot` and `cooking-pot`. The first result is the correct UI trash can.

```tsx
import { Trash } from 'reicon-react';

<button type="button" aria-label="Delete item" onClick={onDelete}>
  <Trash size={18} aria-hidden="true" />
</button>
```

`Icon: trash -> Trash (ui, Outline)`.

## 2. Navigation with an active state

**Request:** "Make the active tab filled."

```tsx
import { Home, Search, User } from 'reicon-react';

const items = [
  { key: 'home', label: 'Home', Icon: Home },
  { key: 'search', label: 'Search', Icon: Search },
  { key: 'profile', label: 'Profile', Icon: User },
];

<nav>
  {items.map(({ key, label, Icon }) => (
    <a key={key} href={`/${key}`} aria-current={active === key ? 'page' : undefined}>
      <Icon size={20} weight={active === key ? 'Filled' : 'Outline'} aria-hidden="true" />
      {label}
    </a>
  ))}
</nav>
```

One icon per destination. Filled marks the active tab. Do not swap `Home` for `House` when active.

## 3. Empty state

**Request:** "Add an empty state for the inbox."

```tsx
import { Inbox } from 'reicon-react';

<div role="status">
  <Inbox size={48} aria-hidden="true" />
  <h2>No messages yet</h2>
  <p>New messages will appear here.</p>
</div>
```

`Icon: inbox -> Inbox (messages, Outline)`.

If the empty state is a generic table with no rows, `box` or `search` can fit better. State the choice in one line.

## 4. HTML and CDN

**Request:** "Add a favorite button to a static page."

```html
<script src="https://unpkg.com/reicon/cdn/reicon.js"></script>

<button type="button" aria-label="Add to favorites">
  <re-icon icon="star" size="20" weight="filled"></re-icon>
</button>
```

Real CLI output for this snippet:

```json
{
  "importStatement": "<script src=\"https://unpkg.com/reicon/cdn/reicon.js\"></script>",
  "docsSnippet": "<re-icon icon=\"star\" size=\"20\" weight=\"filled\"></re-icon>",
  "meta": {
    "name": "star",
    "weight": "Filled",
    "framework": "html",
    "size": 20
  }
}
```

CDN weight is lowercase. Package weight is PascalCase.

## 5. Vue action card

**Request:** "Add a settings action to the card."

```vue
<script setup>
import { Settings } from 'reicon-vue';
</script>

<template>
  <button type="button" aria-label="Card settings">
    <Settings :size="18" aria-hidden="true" />
  </button>
</template>
```

Real CLI output:

```json
{
  "importStatement": "import { Settings } from 'reicon-vue';",
  "docsSnippet": "<Settings :size=\"18\" />",
  "meta": { "name": "settings", "weight": "Outline", "framework": "vue", "size": 18 }
}
```

## 6. Replacing Lucide

**Request:** "Replace Lucide with Reicon."

Map by intent, not by Lucide name:

| Lucide | Reicon |
|---|---|
| `Trash2` | `trash` |
| `Search` | `search` |
| `Settings` | `settings` |
| `Bell` | `bell` |
| `User` | `user` |
| `Users` | `users` |
| `Home` | `home` |
| `ChevronDown` | `chevron-down` |
| `ArrowUpRight` | `arrow-up-right` |
| `MoreHorizontal` | `more-h` |
| `CheckCircle2` | `check-circle` |
| `AlertTriangle` | `alert-triangle` |
| `CreditCard` | `credit-card` |
| `ShoppingCart` | `shopping-cart` |
| `FolderOpen` | `folder-open` |
| `FileText` | `file-text` |
| `Loader2` | `loader` |
| `Calendar` | `calendar` |
| `Clock` | `clock` |
| `Eye` | `eye` |
| `EyeOff` | `eye-off` |
| `Lock` | `lock` |
| `ShieldCheck` | `shield-check` |

Do not keep both libraries. Remove the old import and dependency after replacing all usages.

## 7. Missing concept: terminal

**Request:** "Add a terminal icon."

There is no `terminal` in the dataset.

```bash
npx reicon-mcp search terminal --weight Outline
```

Use `browser-terminal` for a developer console or browser terminal, or `terminal-square` for a square glyph.

```tsx
import { BrowserTerminal } from 'reicon-react';

<BrowserTerminal size={20} aria-hidden="true" />
```

`Icon: browser-terminal -> BrowserTerminal (it, Outline)`. No exact `terminal` icon exists.

## 8. Duplicate name: archive

**Request:** "Use the archive icon."

```bash
npx reicon-mcp search archive --weight Outline --limit 5
```

`archive` is unique, but `archive2` is one of the 46 duplicate names. The mapped component is `Archive2Newicons`; the alternate is `Archive2` in `notes`.

```tsx
import { Archive2Newicons } from 'reicon-react';

<Archive2Newicons size={20} aria-hidden="true" />
```

Both exports exist. Use the mapped component unless the design specifically needs the earlier `Archive2` drawing. Never write `Archive2Something` by hand.

## 9. Icon-only accessibility

**Request:** "Add a close button to the modal."

```tsx
import { X } from 'reicon-react';

<button type="button" aria-label="Close dialog" onClick={onClose}>
  <X size={20} aria-hidden="true" />
</button>
```

The button gets the name. The icon is hidden. Do not put `aria-label` on the SVG and leave the button unnamed.

## 10. Brand logo

**Request:** "Add the GitHub logo."

The framework packages do not export brand logos. `reicon-file` is a vanilla factory/CDN package, not a React component package. Use it directly, or use the web component:

```js
import { Github } from 'reicon-file';

document.body.appendChild(Github({ size: 24, color: 'currentColor' }));
```

```html
<script src="https://unpkg.com/reicon-file/cdn/reicon-file.js"></script>
<re-file icon="github" size="24"></re-file>
```

For an official brand logo with brand color, use the asset from `data/brands.json` or the official brand kit. Do not import `Github` from `reicon-react`.

## 11. MCP transcript

```text
search_icons({ "query": "credit card", "weight": "Outline", "limit": 5 })
```

```json
{
  "results": [
    { "name": "credit-card", "weight": "Outline", "category": "money", "score": 18849 },
    { "name": "card", "weight": "Outline", "category": "money", "score": 6756 },
    { "name": "credit-card-off", "weight": "Outline", "category": "money", "score": 5845 },
    { "name": "card-receive", "weight": "Outline", "category": "money", "score": 3948 },
    { "name": "subtitles", "weight": "Outline", "category": "ui", "score": 2951 }
  ]
}
```

`subtitles` is noise: it is tagged `chip card` and `payment method`. The first result is the card icon.

```text
apply_icon({
  "name": "credit-card",
  "weight": "Outline",
  "framework": "react",
  "size": 20
})
```

```json
{
  "importStatement": "import { CreditCard } from 'reicon-react';",
  "docsSnippet": "<CreditCard size={20} />",
  "meta": { "name": "credit-card", "weight": "Outline", "framework": "react", "size": 20 }
}
```

## 12. Sentence rejection

This fails:

```bash
npx reicon-mcp search "what icon should I use for delete"
```

```json
{
  "error": "Query looks like a full sentence. Use concise keywords instead, such as \"cart\", \"user\", or \"settings\"."
}
```

Search `delete` or `trash`, not the question.

## 13. Unsafe component override

Do not do this:

```bash
npx reicon-mcp apply heart --framework react --componentName BellIcon
```

It returns:

```json
{
  "importStatement": "import { BellIcon } from 'reicon-react';",
  "docsSnippet": "<BellIcon size={24} />",
  "meta": { "name": "heart", "weight": "Outline", "framework": "react", "size": 24 }
}
```

`BellIcon` is not exported by `reicon-react`. The override changed the import name without changing the package.

## 14. View before applying

```bash
npx reicon-mcp view heart --weight Filled
```

```json
{
  "name": "heart",
  "weight": "Filled",
  "availableWeights": ["Outline", "Filled"],
  "category": "like",
  "tags": ["love", "affection", "heart"],
  "viewBox": "0 0 24 24",
  "svg": "<svg xmlns=\"http://www.w3.org/2000/svg\" viewBox=\"0 0 24 24\" fill=\"none\"><path d=\"...\" fill=\"currentColor\"/></svg>",
  "hint": "Call apply_icon with this name and weight to generate framework-specific code."
}
```

The `svg` path is trimmed here; the tool returns the full path. Use `view` when the name is ambiguous or the visual must be confirmed. Do not paste the SVG into app code when a component import exists.

## 15. Angular standalone component

```ts
import { Component } from '@angular/core';
import { BellComponent } from 'reicon-angular';

@Component({
  selector: 'app-notifications',
  standalone: true,
  imports: [BellComponent],
  template: `
    <button type="button" aria-label="Notifications">
      <ri-bell [size]="20" aria-hidden="true"></ri-bell>
    </button>
  `,
})
export class NotificationsComponent {}
```

Angular exports are `*Component` and selectors are `ri-*`.

## 16. Astro card

```astro
---
import { ShieldCheck } from 'reicon-astro';
---

<div class="card">
  <ShieldCheck size={20} aria-hidden="true" />
  <span>Verified</span>
</div>
```

For the smallest bundle:

```astro
---
import ShieldCheck from 'reicon-astro/icons/ShieldCheck.astro';
---
```

## 17. What not to do

```tsx
// Wrong: guessed name
import { Delete } from 'reicon-react';

// Wrong: renamed export
import { BellIcon } from 'reicon-react';

// Wrong: mixed library
import { Trash2 } from 'lucide-react';

// Wrong: hand-drawn replacement for an existing icon
<svg viewBox="0 0 24 24"><path d="..." /></svg>

// Wrong: two weights in one nav row
<Home weight="Filled" />
<Search />
<User weight="Filled" />

// Wrong: icon as the only label on a destructive control
<button onClick={deleteAccount}><Trash /></button>
```

Use the exact export, one library, one weight per surface, and a label on the control.
