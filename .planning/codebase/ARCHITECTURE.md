# Architecture

**Analysis Date:** 2026-02-02

## Pattern Overview

**Overall:** Slidev Presentation Framework - Markdown-driven slide presentation system with Vue 3 components

**Key Characteristics:**
- Markdown-driven presentation content (`slides.md` as single source of truth)
- Vue 3 reactive components for interactive elements
- Static site generation output (built to `dist/`)
- Minimal application state - primarily content-driven presentation logic
- GitHub Pages deployment architecture

## Layers

**Content Layer:**
- Purpose: Define presentation structure, slides, and narrative flow
- Location: `slides.md`
- Contains: Markdown with YAML frontmatter, Slidev-specific syntax (layout, transitions, v-click directives)
- Depends on: Slidev theme framework
- Used by: Slidev build system and browser renderer

**Component Layer:**
- Purpose: Provide interactive Vue 3 components for slide content
- Location: `components/`
- Contains: Vue single-file components (.vue files) with TypeScript support
- Depends on: Vue 3, CSS utilities (Tailwind-like Unocss patterns)
- Used by: Slide content via component references in `slides.md`

**Asset Layer:**
- Purpose: Store static media resources (images, animations)
- Location: `assets/images/`
- Contains: JPG, PNG, GIF, WebP images used in slide presentations
- Depends on: Build system for copying to output
- Used by: Slide content via image references

**Snippet/Utility Layer:**
- Purpose: Provide helper code and reusable logic for slides
- Location: `snippets/`
- Contains: TypeScript utility functions used in code examples or slide logic
- Depends on: Vue 3 ecosystem
- Used by: Slide content, component examples

**Build/Configuration Layer:**
- Purpose: Configure Slidev framework and build pipeline
- Location: Root level configuration (implicitly handled by Slidev), CI/CD pipeline
- Contains: package.json scripts, GitHub Actions workflows
- Depends on: Slidev CLI, Node.js, pnpm
- Used by: Development and deployment processes

## Data Flow

**Development Flow:**

1. Developer edits `slides.md` with Slidev syntax and Vue components
2. Slidev dev server parses Markdown and renders slides in browser
3. Components in `components/` are automatically discovered and can be used in `slides.md`
4. Vue 3 reactivity handles interactive elements (e.g., Counter component state)
5. Assets are served from `assets/` directory

**Build & Deploy Flow:**

1. GitHub Actions workflow triggered on push to main branch
2. Dependencies installed via pnpm
3. Slidev build command generates static SPA in `dist/` directory
4. Assets copied from `assets/` to `dist/assets/`
5. Build artifact uploaded to GitHub Pages
6. Static site deployed to GitHub Pages (https://badroro.github.io/devops-introduction/)

**State Management:**
- Minimal component-level state (e.g., Counter component uses Vue `ref()`)
- No global state management needed
- Presentation flow controlled by Slidev framework (slides.md defines order and transitions)
- No backend state or API calls

## Key Abstractions

**Slide Layout System:**
- Purpose: Define visual structure and behavior of individual slides
- Examples: `cover` layout (title slide), `statement` layout (emphasis slide), default layout
- Pattern: YAML frontmatter directives in `slides.md` control layout per slide

**Vue Components:**
- Purpose: Encapsulate interactive or reusable presentation elements
- Examples: `Counter.vue` - interactive counter component with increment/decrement buttons
- Pattern: Single-file components with `<script setup>` syntax, Unocss utility classes for styling

**Slidev Addons:**
- Purpose: Extend Slidev framework with additional features
- Examples: `slidev-addon-qrcode` for QR code generation, themes (mint, seriph, default)
- Pattern: Plugins registered in `package.json` slidev.addons array

**Markdown Extension Syntax:**
- Purpose: Add presentation-specific markup beyond standard Markdown
- Pattern: Slidev-specific directives like `<v-click>` for animations, `---` for slide breaks

## Entry Points

**Development Entry Point:**
- Location: `slides.md`
- Triggers: `npm run dev` command
- Responsibilities: Single Markdown file containing all slide content, controls presentation structure and narrative

**Build Entry Point:**
- Location: `package.json` build script
- Triggers: `npm run build` command
- Responsibilities: Invokes Slidev build system to compile `slides.md` and components into static HTML/JS

**Deployment Entry Point:**
- Location: `.github/workflows/deploy.yml`
- Triggers: Push to main branch or manual workflow_dispatch
- Responsibilities: Install dependencies, build presentation, copy assets, deploy to GitHub Pages

**Component Discovery Entry Point:**
- Location: `components/` directory
- Triggers: Slidev auto-discovery during build/dev
- Responsibilities: Register Vue components globally for use in `slides.md`

## Error Handling

**Strategy:** Minimal error handling needed due to presentation-only nature; build-time validation

**Patterns:**
- Markdown parse errors caught by Slidev build system
- Component undefined errors caught during Slidev component resolution
- Build failures halt GitHub Actions workflow (no partial deployments)

## Cross-Cutting Concerns

**Styling:** Unocss atomic CSS utility classes (observed in Counter.vue: `flex="~" w="min" border="~ main rounded-md"`)

**Theming:** Slidev theme system provides CSS variables and base styles; themes configured in slides.md frontmatter

**Responsive Design:** Slidev handles responsive slide layouts; components should use flexible CSS utilities

**Code Highlighting:** Slidev framework provides syntax highlighting for code blocks in Markdown

---

*Architecture analysis: 2026-02-02*
