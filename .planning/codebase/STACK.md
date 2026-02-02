# Technology Stack

**Analysis Date:** 2026-02-02

## Languages

**Primary:**
- TypeScript - Used in Vue components, slide configuration, and project setup

**Secondary:**
- Markdown - Slide content defined in `slides.md`
- HTML/CSS - Rendered through Vue templates and Slidev themes

## Runtime

**Environment:**
- Node.js (LTS) - Specified in `.nvmrc` as `lts/jod`
- Browser - Client-side presentation runtime

**Package Manager:**
- pnpm - Lockfile: `pnpm-lock.yaml` present
- Configuration: `.npmrc` with `shamefully-hoist=true` and `auto-install-peers=true`

## Frameworks

**Core:**
- Slidev 0.50.0-beta.7 - Presentation framework (`@slidev/cli`)
- Vue.js 3.5.13 - UI component framework

**Themes:**
- @slidev/theme-default (latest) - Default theme option
- @slidev/theme-seriph (latest) - Alternative theme option
- slidev-theme-mint 0.1.0 - Custom theme

**Addons:**
- slidev-addon-qrcode 1.0.2 - QR code generation for slides

## Key Dependencies

**Critical:**
- @slidev/cli 0.50.0-beta.7 - Build, development, and export tooling for presentations
- Vue 3.5.13 - Core component framework for interactive elements
- slidev-addon-qrcode 1.0.2 - Enables QR code insertion in slides

**Build & Compilation:**
- @babel/core - JavaScript compilation and transformation
- Rollup - Module bundler (included in Slidev)
- Postcss - CSS transformation and processing
- TypeScript 5.6.3 - Type checking and compilation

**Utilities:**
- @antfu/ni 0.23.1 - Universal package manager wrapper for CI/CD
- @nuxt/kit - Kit for Slidev extensions

## Configuration

**Environment:**
- Node.js version management via `.nvmrc`
- pnpm with peer dependency auto-installation enabled
- No `.env` files detected - configuration is build-time only

**Build:**
- No build configuration files (Slidev uses defaults from `@slidev/cli`)
- Build output: `dist/` directory
- Assets copied to `dist/` during build process

## Platform Requirements

**Development:**
- Node.js LTS (Jod, version 22.x or 24.x)
- pnpm package manager
- Git (for version control)

**Production:**
- Static hosting (GitHub Pages configured)
- Build artifacts served as static files
- No server-side runtime required

## Scripts

**Development:**
```bash
npm run dev        # Start development server (http://localhost:3030)
```

**Build:**
```bash
npm run build      # Build slides for static hosting with base path
npm run export     # Export slides (likely to PDF or image formats)
```

---

*Stack analysis: 2026-02-02*
