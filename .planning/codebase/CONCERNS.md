# Codebase Concerns

**Analysis Date:** 2026-02-02

## Tech Debt

**Beta Framework Dependency:**
- Issue: Using Slidev beta version (^0.50.0-beta.7) in production
- Files: `/home/romain/workplace/perso/devops-introduction/package.json`
- Impact: Beta software may contain unstable features, breaking changes, or unexpected behavior. Impacts both development and production builds.
- Fix approach: Upgrade to latest stable Slidev release when available, or pin to specific beta version and establish update schedule

**Floating Theme Dependencies:**
- Issue: `@slidev/theme-default` and `@slidev/theme-seriph` pinned to "latest" instead of semantic versioning
- Files: `/home/romain/workplace/perso/devops-introduction/package.json`
- Impact: Unpredictable builds - different environments may pull different theme versions causing visual inconsistencies or breaking changes
- Fix approach: Replace "latest" with specific semantic versions (e.g., "0.25.0"), lock in pnpm-lock.yaml, and update manually during maintenance windows

**Large Monolithic Slides File:**
- Issue: All presentation content in single 1267-line `slides.md` file
- Files: `/home/romain/workplace/perso/devops-introduction/slides.md`
- Impact: File size makes navigation and editing difficult; any syntax error affects entire presentation
- Fix approach: Split into multiple files by section/topic using Slidev's slide splitting or modularize content structure

**Unused/Debug Components:**
- Issue: `console.log()` in production code with ESLint disable comment
- Files: `/home/romain/workplace/perso/devops-introduction/snippets/external.ts` (line 11: `console.log('Hello from snippets/external.ts')`)
- Impact: Debug code remains in codebase; masking actual issues and adding noise to logs
- Fix approach: Remove debug logging or use proper logging framework with environment-based levels

## Deployment & CI/CD Issues

**Hard-coded Asset Copy Step:**
- Issue: Build pipeline manually copies assets directory: `cp -r assets dist`
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml` (line 38)
- Impact: If assets structure changes or new asset types added, manual step must be updated; risk of missing assets in deployment
- Fix approach: Configure Slidev to include assets in build automatically, or document required step in build configuration

**Generic Node.js LTS Version:**
- Issue: `.nvmrc` specifies `lts/jod` which is a mutable reference
- Files: `/home/romain/workplace/perso/devops-introduction/.nvmrc`
- Impact: Different developers/CI runs may use different Node versions causing environment-dependent bugs
- Fix approach: Pin to specific LTS version (e.g., `20.10.0`) for reproducible builds

**Tool Dependency Chain:**
- Issue: Build pipeline depends on external tool `@antfu/ni` being globally installed
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml` (lines 28-32)
- Impact: If tool is removed from npm registry or maintainer discontinues it, CI pipeline breaks; not self-contained
- Fix approach: Switch to direct `npm install` / `npm ci` commands or vendor the tool locally

**Concurrency Setting - No Progress Cancellation:**
- Issue: `cancel-in-progress: false` means simultaneous deployments don't cancel previous builds
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml` (line 15)
- Impact: Multiple pushes trigger multiple concurrent deployments; if slow build finishes last, it overwrites faster newer version
- Fix approach: Change to `cancel-in-progress: true` to ensure only latest push is deployed

## Security Considerations

**Dependency Type Definition Stub:**
- Issue: @types/dompurify is deprecated stub - dompurify provides its own types
- Files: Reported in pnpm-lock.yaml during analysis
- Impact: Outdated type definitions may mask security issues in dompurify usage; consuming stale security patches
- Fix approach: Remove @types/dompurify from dependencies and verify dompurify types are available

**Public GitHub Pages Deployment:**
- Issue: Educational content deployed to public GitHub Pages with no access controls
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml`
- Impact: No control over who views content; if sensitive information added, it becomes publicly discoverable
- Fix approach: Acceptable for educational material; document that Pages is public in README

**Missing Security Headers:**
- Issue: No security headers configured in deployment (CSP, X-Frame-Options, etc.)
- Files: Not in codebase - would be in deployment configuration
- Impact: Presentation could be framed or attacked by injected scripts if served without headers
- Fix approach: Add GitHub Pages security configuration or serve through secure reverse proxy

## Performance Bottlenecks

**Beta Framework Overhead:**
- Issue: Slidev beta version may have performance issues not optimized in stable release
- Files: `/home/romain/workplace/perso/devops-introduction/package.json` (`@slidev/cli`)
- Impact: Slow development mode (`npm run dev`) and build times; affects productivity
- Fix approach: Profile build times once on stable version; compare against beta

**Large Lockfile:**
- Issue: pnpm-lock.yaml is 221KB - significantly larger than needed for simple presentation project
- Files: `/home/romain/workplace/perso/devops-introduction/pnpm-lock.yaml`
- Impact: Slow git operations; increased repository clone/checkout time
- Fix approach: Audit dependencies for unused packages; consider lightweight alternative if only presenting slides

## Fragile Areas

**Counter Component - No Input Validation:**
- Issue: Counter accepts any numeric value from props with no constraints
- Files: `/home/romain/workplace/perso/devops-introduction/components/Counter.vue` (lines 4-8)
- Impact: Negative counter values possible; no max/min bounds; could produce confusing UI
- Fix approach: Add prop validation with `validator` function and type hints, establish bounds

**Build Process Sequence Fragility:**
- Issue: Asset copy happens after build - if build changes output structure, assets may end up in wrong location
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml` (lines 34-38)
- Impact: Timing-dependent; if Slidev changes build output directory structure, deployment silently fails to copy assets
- Fix approach: Make asset inclusion part of build configuration; add verification step to confirm assets in dist/

**Hardcoded Repository Name:**
- Issue: GitHub Actions build uses `${{github.event.repository.name}}` for base path
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml` (line 35)
- Impact: Works for current repo name but if repository renamed, build path becomes wrong
- Fix approach: Document this dependency; consider making base path configurable or validate in pre-build

## Missing Critical Features

**No Build Verification:**
- Issue: CI pipeline has no validation that build succeeded (no test, no artifact verification)
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml`
- Impact: Invalid builds could be deployed without detection; no safety net
- Fix approach: Add smoke test step checking dist/ contains expected files

**No Environment-Specific Configuration:**
- Issue: No dev vs. production build distinction; same build serves all environments
- Files: All build configuration in single workflow
- Impact: Cannot safely add analytics, logging, or API calls specific to production
- Fix approach: Add environment variable configuration and conditional build steps

**No Documentation of Build Process:**
- Issue: Build steps in YAML not documented; reasons for each step unclear
- Files: `/home/romain/workplace/perso/devops-introduction/.github/workflows/deploy.yml`
- Impact: Future maintainers cannot modify pipeline safely; unclear why `@antfu/ni` is needed
- Fix approach: Add inline comments explaining each step; document in README

## Known Issues

**Image Management Complexity:**
- Issue: Commit history shows multiple image-related fixes (commits "dce85ab", "9ee3cb0")
- Files: `/home/romain/workplace/perso/devops-introduction/assets/images/`
- Impact: Image display has been fragile; likely browser/rendering path issues
- Workaround: Check recent commit messages before modifying image references
- Fix approach: Document image requirements and paths in README; standardize image format handling

## Test Coverage Gaps

**No Automated Tests:**
- Issue: No test files found in codebase; no test framework configured
- Files: No `*.test.ts`, `*.spec.ts`, or test configuration files
- Impact: Counter component behavior unpredictable; no regression detection; build process untested
- Priority: **Medium** - for production presentation platform
- Recommendation: Add Jest/Vitest with tests for Counter component logic and build script validation

**No Build Output Validation:**
- Issue: No verification that generated HTML/JS is valid and deployable
- Files: No post-build validation step in workflow
- Impact: Broken presentations can be deployed; no warning until viewer discovers issue
- Priority: **High** - prevents production incidents
- Recommendation: Add HTML validation and asset presence checks post-build

## Dependency Risks

**Slidev Theme Version Drift:**
- Risk: Themes pinned to "latest" can diverge from CLI version compatibility
- Impact: CLI and theme versions may become incompatible; presentation fails to render
- Migration plan: Pin both to same release version; establish coordinated update schedule

**Minor Addon Risk:**
- Risk: `slidev-addon-qrcode@1.0.2` is small/niche package; may not be actively maintained
- Impact: If maintainer abandons, security patches not available; integration breaks with future Slidev updates
- Mitigation: Check GitHub for activity; monitor release dates; consider forking if unmaintained

---

*Concerns audit: 2026-02-02*
