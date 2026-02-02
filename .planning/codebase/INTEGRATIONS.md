# External Integrations

**Analysis Date:** 2026-02-02

## APIs & External Services

**Image Assets:**
- Unsplash - Collection 94734566 used for random background images
  - Integration: URL-based, no SDK required
  - Usage: Hero image for presentation title slide via `background: /assets/images/devops-titre.jpg`

## Data Storage

**Databases:**
- Not applicable - Static presentation project

**File Storage:**
- Local filesystem only
  - Assets stored in `assets/images/` directory
  - Static files copied to `dist/` during build process

**Caching:**
- Not explicitly configured
- Browser caching handled by GitHub Pages defaults

## Authentication & Identity

**Auth Provider:**
- Not applicable - Public static presentation

## Monitoring & Observability

**Error Tracking:**
- Not configured - Static presentation

**Logs:**
- Not configured - Static presentation

## CI/CD & Deployment

**Hosting:**
- GitHub Pages - Configured as deployment target
- Repository: `https://github.com/badroro/devops-introduction`
- Base path: `/{repository-name}/` dynamically set during build

**CI Pipeline:**
- GitHub Actions - Configured in `.github/workflows/deploy.yml`
- Trigger events:
  - `push` to `main` branch
  - Manual workflow dispatch
- Build environment: `ubuntu-latest`
- Deployment requires: `pages:write`, `contents:read`, `id-token:write` permissions

**Build Steps:**
1. Checkout code (`actions/checkout@v4`)
2. Setup Node.js LTS (`actions/setup-node@v4`)
3. Install @antfu/ni globally for universal package management
4. Install dependencies via `nci`
5. Build with base path: `nr build --base /${{github.event.repository.name}}/`
6. Copy assets to dist: `cp -r assets dist`
7. Configure GitHub Pages (`actions/configure-pages@v4`)
8. Upload artifacts (`actions/upload-pages-artifact@v3`)
9. Deploy to GitHub Pages (`actions/deploy-pages@v4`)

## Environment Configuration

**Required env vars:**
- No environment variables required for runtime

**Secrets location:**
- No secrets configured - Project is public

**Build Configuration:**
- `GITHUB_PAGES_URL` - Inferred from GitHub environment
- Base path dynamically generated from repository name

## Webhooks & Callbacks

**Incoming:**
- GitHub push webhook triggers CI/CD pipeline

**Outgoing:**
- GitHub Pages deployment webhook (handled by GitHub Actions)

## Content Sources

**Presentation Content:**
- Markdown source: `slides.md` (24625 bytes)
- Slide configuration: YAML frontmatter in `slides.md`
- Theme: `default` (configurable)
- Title: "Introduction au DevOps"
- Metadata: Educational course for M1 MIAGE students, Grenoble

**Components:**
- `components/Counter.vue` - Interactive Vue 3 component with TypeScript
  - Uses Slidev's atomic styling (Unocss)
  - Self-contained state management with `ref`

---

*Integration audit: 2026-02-02*
