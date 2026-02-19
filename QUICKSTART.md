# Quick Start Guide

## Run the Development Server

```bash
npm run dev
```

Then open your browser to the URL shown (typically `http://localhost:5173`)

## Key Features to Test

### 1. Horizontal Scrolling
- Use your mouse wheel to scroll vertically
- Watch the sections move horizontally
- Each scroll moves you to the next section

### 2. Navigation
- Click on navigation items: HOME, THE STORY, HEROES, VILLAINS, PHOTOS
- Notice the active section is highlighted with gold color
- Smooth transitions between sections

### 3. Interactive Elements
- Hover over buttons to see animations
- Hover over character cards (Heroes/Villains) to see effects
- Hover over photo items to reveal titles and categories

### 4. Responsive Design
- Resize your browser window to see responsive layouts
- Try mobile view (< 768px) for single-column layouts
- Try tablet view (768-1024px) for adjusted grids

## Sections Overview

1. **Intro Section** - Landing page with "Watch Trailer" button
2. **Story Section** - Narrative text with image placeholder
3. **Heroes Section** - 3 hero cards in a grid
4. **Villains Section** - 3 villain cards with dark theme
5. **Photos Section** - Gallery grid with various sized items

## Customization Tips

### Change Colors
Edit [src/style.css](src/style.css) CSS variables:
- `--gold-accent`: Main accent color
- `--text-light`: Primary text color
- `--text-muted`: Secondary text color

### Add Real Images
Replace placeholder backgrounds in component styles with:
```css
background-image: url('/path/to/your/image.jpg');
background-size: cover;
background-position: center;
```

### Modify Content
- Edit hero/villain data in component `data()` sections
- Change section titles in component templates
- Adjust descriptions and text content

## Troubleshooting

**Sections not scrolling?**
- Ensure you're scrolling vertically (mouse wheel)
- Try clicking navigation items instead

**Layout broken?**
- Clear browser cache
- Restart dev server with `npm run dev`

**Slow performance?**
- Reduce animation complexity
- Optimize images if using real photos
- Check browser console for errors

## Production Build

```bash
npm run build
```

Outputs to `dist/` folder, ready for deployment.

Enjoy building your film website!
