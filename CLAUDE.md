# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the static website for Zenon Network (zenon.network), a cryptocurrency project. The site is built with vanilla HTML, CSS (Sass), and JavaScript, and is hosted on GitHub Pages.

## Development Commands

Since this is a static site without a build process:
- **Local development**: Use any static file server (e.g., `python -m http.server 8000` or `npx serve`)
- **Sass compilation**: If modifying styles, compile manually: `sass css/styles.sass css/styles.css`
- **Testing**: Open index.html in a browser and verify functionality
- **Deployment**: Push to master branch; GitHub Pages will automatically deploy

## Architecture

### File Structure
- `index.html` - Single page application with all content
- `css/styles.sass` - Main Sass file that imports all partials from `css/parts/`
- `js/main.js` - Custom JavaScript for site functionality
- `img/` - All assets including SVGs, PNGs, and Lottie animations
- `download/` - Downloadable files (whitepaper, etc.)

### Key JavaScript Functionality (js/main.js)
- **API Integration**: 
  - CoinGecko API for live ZNN/QSR prices
  - GitHub API for latest Syrius wallet releases
- **UI Components**:
  - Smooth scroll navigation
  - Modal windows for videos
  - Tab switching for protocol information
  - Platform detection for appropriate download links
  - Countdown timer functionality

### CSS Architecture (css/parts/)
- Modular Sass with components split into:
  - Layout sections (header, hero, features, etc.)
  - Components (buttons, cards, modals, etc.)
  - Utilities (mixins, variables, reset)

### Third-party Dependencies
- jQuery (CDN)
- Flipster.js (local)
- Font Awesome (CDN)
- Lottie Player (CDN)
- PostHog Analytics (CDN)

## Important Implementation Details

1. **Download Links**: The site dynamically fetches the latest Syrius wallet release from GitHub API and updates download links based on the user's platform. See `updateDownloadLinks()` function in main.js.

2. **Price Updates**: Cryptocurrency prices are fetched from CoinGecko API every 30 seconds. Handle API failures gracefully.

3. **Responsive Design**: Site uses CSS Grid and Flexbox with breakpoints defined in Sass variables.

4. **Performance**: Images should be optimized. Consider lazy loading for below-fold content.

5. **Cross-browser**: Test in Chrome, Firefox, Safari, and Edge. Internet Explorer is not supported.