# @cocm/theme

Shared design tokens for COCM apps — currently `cocm-internal` and `bookstore`.
Single source of truth for colors, fonts, shadows, radii, page background,
and the aurora background utility. Edit here, both apps update on next build.

## Contents

- `tailwind.preset.cjs` — Tailwind preset: `cocm.*` color tokens, `font-serif`/
  `font-sans`, `shadow-card`/`shadow-card-hover`/`shadow-panel`/`shadow-red-glow`,
  `rounded-card`/`rounded-panel`.
- `theme.css` — global CSS: `body` background, `.brand-wash-bg` aurora utility,
  `::selection`, custom scrollbar, `.card-hover`.

## Usage

`package.json`:

```json
"@cocm/theme": "github:Oasis-Coders/cocm-theme#main"
```

`tailwind.config.ts`:

```ts
const themePreset = require('@cocm/theme/tailwind.preset.cjs');
const config: Config = {
  presets: [themePreset],
  content: ['./app/**/*.{ts,tsx}', './components/**/*.{ts,tsx}', './lib/**/*.{ts,tsx}'],
  plugins: [],
};
```

`app/globals.css` (after the font `@import`, before `@tailwind`):

```css
@import '@cocm/theme/theme.css';
```

Then delete the app's local copies of the tokens / `.brand-wash-bg` /
scrollbar / `.card-hover` so there is exactly one definition.
