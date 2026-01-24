# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Development server (http://localhost:4321)
npm run dev

# Build static site (outputs to dist/)
npm run build

# Preview production build locally
npm run preview
```

## Deployment

Site deploys automatically to GitHub Pages on push to `master` via `.github/workflows/deploy.yml`. The live site is at https://www.gastag.app.

## Architecture

This is an Astro static site with Tailwind CSS for the GasTag marketing website.

### Project Structure

```
src/
├── layouts/Layout.astro    # Base HTML layout with Google Analytics
├── pages/                  # File-based routing (index, app, diy-guide, get-one, privacy)
├── components/             # Reusable UI (Navigation, Footer, Button, FeatureCard, SectionHeading)
├── styles/global.css       # Tailwind imports
└── images/                 # Source images (PSD files, HEIC photos)
public/
└── images/                 # Optimized images served directly (JPG, PNG)
```

### Key Patterns

- **Relative links**: All internal links use `import.meta.env.BASE_URL` prefix (stored in `base` variable) to ensure proper routing
- **Tailwind colors**: Custom theme colors defined in `tailwind.config.mjs` - `primary` (#1a365d), `accent` (#0d9488), `warning` (#d97706)
- **Component props**: Components use TypeScript interfaces for prop types in the frontmatter
- **HTML in content**: Some content arrays use `set:html` directive to render inline HTML (links in descriptions)

### Navigation

Navigation links are defined in `src/components/Navigation.astro`. The mobile menu uses vanilla JS toggle.

### Instructions for Code Modification
When making code changes follow these best practices,
- **Create a feature Branch**: Always create a branch named feature/<name of new feature> or bug/<what we are fixing>
- **Commit often**: Use git history as your memory, commit often with a detailed message
- **Squash Commits**: When done with the branch, confirm first but squash the commits to a single concise message, then merge back to master
- **Never Push**: Never push, always let the owner push to remote. 
