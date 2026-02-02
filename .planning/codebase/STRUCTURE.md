# Codebase Structure

**Analysis Date:** 2026-02-02

## Directory Layout

```
devops-introduction/
├── .github/              # GitHub-specific configurations
│   └── workflows/        # CI/CD pipeline definitions
├── .slidev/              # Slidev framework internal data
│   └── snapshots/        # Generated slide snapshots
├── .planning/            # GSD planning documentation (not source code)
├── .claude/              # Claude-specific hooks and configuration
├── assets/               # Static assets for presentation
│   └── images/           # Image files used in slides
├── components/           # Vue 3 reusable components
├── snippets/             # TypeScript utility code and examples
├── slides.md             # Main presentation content (Markdown)
├── package.json          # Project dependencies and scripts
├── pnpm-lock.yaml        # Locked dependency versions
├── README.md             # Project documentation
├── LICENSE               # License file
├── .gitignore            # Git ignore rules
├── .npmrc                # npm configuration
└── .nvmrc                # Node.js version specification
```

## Directory Purposes

**`.github/`:**
- Purpose: GitHub-specific automation and CI/CD configuration
- Contains: GitHub Actions workflow definitions
- Key files: `.github/workflows/deploy.yml`

**`.slidev/`:**
- Purpose: Slidev framework runtime data (generated and cached)
- Contains: Slide snapshots, framework cache
- Generated: Yes
- Committed: Typically not (should be in .gitignore)

**`.planning/`:**
- Purpose: GSD (Getting Stuff Done) planning documentation for codebase analysis
- Contains: Codebase mapping documents (ARCHITECTURE.md, STRUCTURE.md, etc.)
- Generated: Yes (by GSD mappers)
- Committed: Yes

**`.claude/`:**
- Purpose: Claude-specific hooks and configuration
- Contains: JavaScript hooks for GSD integration (`gsd-statusline.js`, `gsd-check-update.js`)
- Committed: Yes

**`assets/`:**
- Purpose: Store static media files used in presentation
- Contains: Images, animations (JPG, PNG, GIF, WebP)
- Key files: `assets/images/` subdirectory with presentation images

**`components/`:**
- Purpose: Vue 3 single-file components for interactive slide elements
- Contains: .vue files with script, template, style sections
- Key files: `components/Counter.vue` - example interactive counter component
- Auto-discovered: Yes (Slidev auto-discovers components in this directory)

**`snippets/`:**
- Purpose: Reusable TypeScript utility code and code examples
- Contains: .ts files with utility functions for use in slides or as code examples
- Key files: `snippets/external.ts` - utility functions like `emptyArray()`, `sayHello()`

## Key File Locations

**Entry Points:**
- `slides.md`: Primary presentation content file; main entry point for slide development
- `package.json`: Project manifest and dependency declaration

**Configuration:**
- `.github/workflows/deploy.yml`: CI/CD pipeline configuration for GitHub Pages deployment
- `.nvmrc`: Specifies Node.js version requirement (file content indicates LTS version)
- `.npmrc`: npm registry and behavior configuration
- `pnpm-lock.yaml`: Lockfile for reproducible dependency installation

**Core Logic:**
- `components/Counter.vue`: Interactive Vue component with state management via `ref()`
- `snippets/external.ts`: Utility functions with TypeScript generics

**Testing:**
- Not present - presentation codebase does not include unit tests

## Naming Conventions

**Files:**
- Markdown files: `slides.md` (singular, lowercase, descriptive)
- Vue components: PascalCase (e.g., `Counter.vue`)
- TypeScript/JavaScript files: camelCase (e.g., `external.ts`)
- Configuration files: Dot-prefixed (e.g., `.npmrc`, `.nvmrc`) or extension-based (e.g., `package.json`)

**Directories:**
- Lowercase (e.g., `assets`, `components`, `snippets`, `.github`)
- Descriptive, plural when containing multiple items (e.g., `components`, `assets/images`)
- Dot-prefixed for internal/hidden directories (e.g., `.github`, `.slidev`, `.claude`)

**Component Properties:**
- Props and state: camelCase (e.g., `count` prop in Counter)
- CSS classes: Unocss utility syntax (e.g., `flex="~" w="min"`)
- Event handlers: camelCase with @ prefix in templates (e.g., `@click`)

## Where to Add New Code

**New Slide Content:**
- Primary file: `slides.md`
- Add Markdown sections with `---` separators for new slides
- Reference components by name: `<Counter :count="5" />`
- Use Slidev layout directives in YAML frontmatter: `layout: cover`

**New Interactive Component:**
- Implementation: Create `components/YourComponent.vue`
- Pattern: Use `<script setup lang="ts">` with Vue 3 composition API
- Styling: Use Unocss utility classes (not scoped CSS)
- State: Use `ref()` for reactive data, `props` for configuration
- Auto-discovered: Component automatically available in `slides.md`

**New Utility Functions:**
- Shared helpers: `snippets/[name].ts`
- Pattern: Export functions as `export function name() {}`
- Use TypeScript for type safety

**New Assets:**
- Images: Place in `assets/images/`
- Reference in slides: Use relative path `/assets/images/filename.ext`
- Ensure assets copied in build: `.github/workflows/deploy.yml` handles this via `cp -r assets dist`

**New Dependencies:**
- Add to `package.json` or use `pnpm add package-name`
- Lock versions with `pnpm-lock.yaml`
- Slidev addons: Add to `slidev.addons` array in `package.json`

## Special Directories

**`assets/images/`:**
- Purpose: Contains all image assets referenced in presentation
- Generated: No (manually created and committed)
- Committed: Yes (part of source)
- Build behavior: Copied to `dist/assets/` during build

**`.slidev/snapshots/`:**
- Purpose: Generated slide preview images
- Generated: Yes (by Slidev during build)
- Committed: No (should be in .gitignore)

**`dist/`:**
- Purpose: Build output directory (generated during build)
- Generated: Yes (by Slidev build command)
- Committed: No (not present in repo)
- Created during: `npm run build`

---

*Structure analysis: 2026-02-02*
