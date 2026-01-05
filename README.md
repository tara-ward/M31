# M31 Website

A beautiful Vue 3 application with animated snowflakes, a winter-night gradient background, and an interactive slide carousel.

## Setup

1. Install dependencies:
```bash
npm install
```

2. Run the development server:
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

## Features

- Vue 3 with Composition API
- Vue Router for navigation
- Animated snowflake background using layered PNGs
- Winter-night gradient background
- Interactive slide carousel with touch support
- Navigation bar with 8 pages
- Modern build setup with Vite
- SCSS support for styling

## Pages

1. **Home** - Features the animated slide carousel
2. **About** - About page
3. **Projects** - Projects showcase
4. **News & Events** - Latest news and events
5. **Contact** - Contact information
6. **Social Media** - Social media links
7. **Portfolio** - Portfolio showcase
8. **CV** - Curriculum vitae

## Project Structure

```
├── index.html              # Main HTML file
├── package.json            # Dependencies and scripts
├── vite.config.js          # Vite configuration
├── src/
│   ├── main.js            # Vue app entry point
│   ├── App.vue            # Main Vue component
│   ├── style.css          # Global styles with snow animation
│   ├── router/
│   │   └── index.js       # Vue Router configuration
│   ├── components/
│   │   ├── NavigationBar.vue    # Navigation bar component
│   │   └── SlideCarousel.vue    # Slide carousel component
│   ├── views/             # Page components
│   │   ├── Home.vue
│   │   ├── About.vue
│   │   ├── Projects.vue
│   │   ├── NewsEvents.vue
│   │   ├── Contact.vue
│   │   ├── SocialMedia.vue
│   │   ├── Portfolio.vue
│   │   └── CV.vue
│   └── styles/
│       └── slide-carousel.scss  # Slide carousel styles
└── README.md              # This file
```

