# Tailwind CSS v4 - CSS-First Configuration

This project uses **Tailwind CSS v4**, which introduces a revolutionary **CSS-first configuration approach**.

## What's New in v4?

### ✨ No JavaScript Config File
- ❌ No more `tailwind.config.js` or `tailwind.config.ts`
- ✅ All configuration done in CSS using `@theme` directive
- 🚀 Faster builds and simpler setup

### 📝 CSS-First Configuration

All customization is done directly in your CSS file:

```css
@import "tailwindcss";

@theme {
  /* Custom Colors */
  --color-gold: #d4af37;
  --color-brand: #ff6b6b;

  /* Custom Fonts */
  --font-family-cinzel: 'Cinzel', serif;
  --font-family-raleway: 'Raleway', sans-serif;

  /* Custom Spacing (optional) */
  --spacing-huge: 128px;

  /* Custom Breakpoints (optional) */
  --breakpoint-tablet: 800px;
}
```

## How It Works

### 1. Import Tailwind
```css
@import "tailwindcss";
```

This single import replaces the old three directives:
```css
/* Old v3 way ❌ */
@tailwind base;
@tailwind components;
@tailwind utilities;

/* New v4 way ✅ */
@import "tailwindcss";
```

### 2. Define Theme Variables
```css
@theme {
  --color-primary: #3b82f6;
  --font-family-display: 'Inter', sans-serif;
}
```

### 3. Use in Components
```html
<h1 class="text-primary font-display">Hello World</h1>
```

## Custom Values in This Project

### Colors
```css
--color-gold: #d4af37;
```
Usage: `text-gold`, `bg-gold`, `border-gold`, etc.

### Fonts
```css
--font-family-cinzel: 'Cinzel', serif;
--font-family-raleway: 'Raleway', sans-serif;
```
Usage: `font-cinzel`, `font-raleway`

### Breakpoints
```css
--breakpoint-sm: 640px;
--breakpoint-md: 768px;
--breakpoint-lg: 1024px;
--breakpoint-xl: 1280px;
--breakpoint-2xl: 1536px;
```
Usage: `md:text-xl`, `lg:grid-cols-3`, etc.

## Benefits of v4

### 🚀 Performance
- **Faster builds** - No JavaScript config parsing
- **Smaller bundle** - More efficient tree-shaking
- **Better caching** - CSS-based configuration is easier to cache

### 🎨 Simplicity
- **One file** - Everything in CSS
- **Native CSS** - Uses CSS custom properties
- **Less complexity** - No build configuration needed

### 🔧 Developer Experience
- **Better autocomplete** - CSS variables work better with IDEs
- **Easier debugging** - Inspect theme values in DevTools
- **More flexible** - Can change values at runtime

## Migration from v3

### Before (v3) ❌
```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        gold: '#d4af37',
      },
      fontFamily: {
        cinzel: ['Cinzel', 'serif'],
      },
    },
  },
}
```

### After (v4) ✅
```css
/* style.css */
@import "tailwindcss";

@theme {
  --color-gold: #d4af37;
  --font-family-cinzel: 'Cinzel', serif;
}
```

## Advanced Features

### Runtime Theme Changes
Since themes use CSS custom properties, you can change them at runtime:

```js
// Change gold color dynamically
document.documentElement.style.setProperty('--color-gold', '#FFD700');
```

### Multiple Themes
```css
@theme {
  --color-primary: #3b82f6;
}

@media (prefers-color-scheme: dark) {
  @theme {
    --color-primary: #60a5fa;
  }
}
```

### Container Queries Support
v4 has built-in container query support:

```html
<div class="@container">
  <div class="@lg:grid-cols-2">
    <!-- Responsive to container size, not viewport -->
  </div>
</div>
```

## File Structure

```
src/
└── style.css       # All Tailwind configuration here
    ├── @import "tailwindcss"
    ├── @theme { ... }
    └── @layer base { ... }
```

## Resources

- [Tailwind CSS v4 Documentation](https://tailwindcss.com/docs)
- [v4 Migration Guide](https://tailwindcss.com/docs/upgrade-guide)
- [CSS Theme Configuration](https://tailwindcss.com/docs/theme)

## Summary

Tailwind v4's CSS-first approach makes configuration:
- ✅ Simpler (no config file)
- ✅ Faster (better performance)
- ✅ More flexible (runtime changes)
- ✅ More maintainable (everything in CSS)

This is the future of Tailwind CSS! 🎉
