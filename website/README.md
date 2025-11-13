# Human Agency Protocol Website

The official website for humanagencyprotocol.org

## Project Structure

```
website/
├── src/
│   ├── content/
│   │   └── docs/          # Markdown content from ../content/0.1/
│   ├── layouts/
│   │   ├── BaseLayout.astro
│   │   └── ContentLayout.astro
│   ├── pages/
│   │   ├── index.astro    # Homepage
│   │   ├── protocol.astro
│   │   ├── service.astro
│   │   ├── governance.astro
│   │   └── about.astro
│   └── styles/
│       └── global.css
└── public/
```

## Commands

All commands are run from the root of the website directory:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |

## Content Management

The website uses content from `../content/0.1/` as the source of truth. To update content:

1. Edit the markdown files in `../content/0.1/`
2. Copy updated files to `src/content/docs/`
3. Rebuild the site

## Deployment

The site is configured for deployment to GitHub Pages at humanagencyprotocol.org

GitHub Actions workflow in `.github/workflows/deploy.yml` will automatically deploy on push to main branch.

## Design System

- **Colors**: Near-monochrome with accent color `#6366f1`
- **Typography**: System fonts, responsive scaling
- **Layout**: 1200px max-width, generous spacing
- **Principles**: Simplicity, accessibility, performance

## License

MIT
