# Film Website - Vue.js Horizontal Scroll

A stunning film website built with Vue.js featuring horizontal scroll-driven sections, inspired by modern cinematic web design.

## Features

- **Horizontal Scroll Navigation**: Vertical scroll translates to horizontal section movement
- **Fixed Navigation Bar**: Stays visible while scrolling with active section highlighting
- **Smooth Transitions**: Elegant animations and transitions between sections
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **5 Unique Sections**:
  - **Intro**: Landing page with call-to-action
  - **Story**: Narrative section with text and imagery
  - **Heroes**: Grid of hero character cards
  - **Villains**: Grid of villain character cards
  - **Photos**: Gallery section with hover effects

## Tech Stack

- **Vue 3** - Composition API with `<script setup>`
- **Tailwind CSS v4** - Modern CSS-first utility framework
- **Vite** - Fast build tool and dev server
- **Google Fonts** - Cinzel and Raleway fonts

## Project Structure

```
raghad/
├── src/
│   ├── components/
│   │   ├── Navbar.vue           # Fixed navigation component
│   │   ├── IntroSection.vue     # Landing section
│   │   ├── StorySection.vue     # Story narrative section
│   │   ├── HeroesSection.vue    # Heroes grid section
│   │   ├── VillainsSection.vue  # Villains grid section
│   │   └── PhotosSection.vue    # Photo gallery section
│   ├── App.vue                   # Main app with scroll logic
│   ├── main.js                   # App initialization
│   └── style.css                 # Tailwind v4 CSS-first configuration
├── index.html
├── package.json
└── vite.config.js
```

> **Note**: Tailwind CSS v4 uses a new CSS-first configuration approach. All customization is done directly in `style.css` using `@theme` directive - no JavaScript config file needed!

## Installation

1. Install dependencies:
```bash
npm install
```

2. Run development server:
```bash
npm run dev
```

3. Build for production:
```bash
npm run build
```

4. Preview production build:
```bash
npm run preview
```

## How It Works

### Horizontal Scrolling
The website uses a custom scroll handler that translates vertical scroll events into horizontal translations. Each section spans the full viewport width, and scrolling moves between sections smoothly.

### Navigation
- Click any navigation item to jump to that section
- The active section is highlighted in the navbar
- Smooth transitions ensure a polished user experience

### Responsive Design
- Desktop: Full-width sections with multi-column grids
- Tablet: Adjusted layouts with 2-column grids
- Mobile: Single-column layouts with optimized spacing

## Customization

### Colors
Edit the `@theme` directive in [src/style.css](src/style.css):
```css
@theme {
  --color-gold: #d4af37;  /* Change the gold accent color */
  --color-custom: #your-color-here;  /* Add new colors */
}
```

Then use in your components: `text-gold`, `bg-gold`, etc.

### Fonts
Update font families in the `@theme` directive in [src/style.css](src/style.css):
```css
@theme {
  --font-family-cinzel: 'Cinzel', serif;
  --font-family-raleway: 'Raleway', sans-serif;
  --font-family-custom: 'YourFont', sans-serif;
}
```

Then use: `font-cinzel`, `font-raleway`, etc.

### Content
- Edit hero/villain data arrays in component `<script setup>` sections
- Modify section titles and descriptions in component templates
- Replace placeholder images by adding `background-image` to image containers using Tailwind's arbitrary values: `bg-[url('/path/to/image.jpg')]`

### Sections
To add a new section:
1. Create a new component in `src/components/` using Tailwind classes
2. Import it in [App.vue](src/App.vue)
3. Add it to the sections array and navigation items in Navbar

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

This project is open source and available for personal and commercial use.
