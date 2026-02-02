# Phase 1: Nettoyage technique - Research

**Researched:** 2026-02-02
**Domain:** Slidev presentation maintenance - CSS refactoring, content correction, HTML validation
**Confidence:** HIGH

## Summary

Phase 1 involves technical cleanup of an existing Slidev presentation written in French. The work falls into four categories: text corrections (typos), CSS refactoring (duplicated CALMS styles across 6 slides), URL consistency (QR codes), and HTML validation (malformed tags). This is straightforward maintenance work with no architectural changes.

Slidev is a Vue 3-based presentation framework that uses Markdown for content. It supports scoped styles (per-slide `<style>` blocks), global styles (via `styles/` directory), and Vue components (in `components/` directory). The project already has a `components/` directory with one Vue component, making it the ideal location for a reusable CALMS component.

The standard approach for refactoring duplicated CSS in Slidev is to extract it into either global styles (`styles/index.css`) for simple styling, or into a Vue component when the CSS is coupled with HTML structure. Since the CALMS visualization includes both HTML structure (divs with classes) and CSS styling duplicated 6 times, a Vue component is the superior solution.

**Primary recommendation:** Extract duplicated CALMS HTML+CSS into a Vue component in `components/CalmsBlock.vue`, accepting an opacity prop to handle the highlight variations. Fix text/URL/HTML issues via direct edits to `slides.md`.

## Standard Stack

This phase uses the existing project stack with no additional dependencies.

### Core
| Library | Version | Purpose | Why Standard |
|---------|---------|---------|--------------|
| Slidev | 0.50.0-beta.7 | Presentation framework | Already in use, markdown-based slides |
| Vue | 3.5.13 | Component framework | Powers Slidev's component system |
| pnpm | Latest | Package manager | Already configured in project |

### Supporting
| Library | Version | Purpose | When to Use |
|---------|---------|---------|-------------|
| slidev-addon-qrcode | 1.0.2 | QR code generation | Already in use for final slide |
| UnoCSS | Built-in | Utility-first CSS | Available but not needed for this phase |

### Alternatives Considered
| Instead of | Could Use | Tradeoff |
|------------|-----------|----------|
| Vue component | Global CSS in `styles/index.css` | Global CSS simpler but doesn't deduplicate HTML structure |
| Vue component | Scoped CSS with repeated HTML | No change, leaves duplication in place |
| Manual editing | Script-based find/replace | Error-prone for French text, manual verification needed anyway |

**Installation:**
No new packages required.

## Architecture Patterns

### Recommended Project Structure
```
devops-introduction/
├── slides.md              # Main presentation content (edit directly)
├── components/            # Vue components
│   ├── Counter.vue        # Existing example component
│   └── CalmsBlock.vue     # NEW: CALMS visualization component
└── styles/                # NOT NEEDED for this phase
    └── index.css          # Alternative: global styles (simpler but less reusable)
```

### Pattern 1: Vue Component for Reusable Slide Elements
**What:** Extract duplicated HTML+CSS into a Vue component that accepts props for variations
**When to use:** When the same visual element appears multiple times with minor variations (like highlighting different blocks)
**Example:**
```vue
<!-- components/CalmsBlock.vue -->
<script setup lang="ts">
defineProps({
  highlight: {
    type: String,
    default: 'none', // 'culture', 'automation', 'lean', 'measurement', 'share', 'none'
  },
})
</script>

<template>
  <div class="calms-container">
    <div class="ligne1">
      <div class="block automation" :class="{ dimmed: highlight !== 'automation' && highlight !== 'none' }">
        AUTOMATION
      </div>
      <div class="block lean" :class="{ dimmed: highlight !== 'lean' && highlight !== 'none' }">
        LEAN
      </div>
      <div class="block measurement" :class="{ dimmed: highlight !== 'measurement' && highlight !== 'none' }">
        MEASUREMENT
      </div>
      <div class="block share" :class="{ dimmed: highlight !== 'share' && highlight !== 'none' }">
        SHARE
      </div>
    </div>
    <div class="block culture ligne2" :class="{ dimmed: highlight !== 'culture' && highlight !== 'none' }">
      CULTURE
    </div>
  </div>
</template>

<style scoped>
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
/* ... rest of CSS ... */
.dimmed {
  opacity: 0.5;
}
</style>
```

**Usage in slides.md:**
```markdown
::right::

<CalmsBlock highlight="culture" />
```

**Source:** [Slidev Components Documentation](https://sli.dev/guide/component), [Vue 3 Styling Best Practices](https://dev.to/sucodelarangela/vue3-how-to-style-components-global-scoped-and-modules-4230)

### Pattern 2: Direct Markdown Editing for Content Fixes
**What:** Edit text, URLs, and HTML directly in slides.md
**When to use:** Simple corrections that don't benefit from automation
**Example:**
```markdown
<!-- BEFORE -->
des principes qui ont été posé

<!-- AFTER -->
des principes qui ont été posés
```

**Why:** French grammar corrections require human judgment, automated tools unreliable for context

### Anti-Patterns to Avoid
- **Don't use global CSS for component-specific styles:** Pollutes global scope, harder to maintain
- **Don't leave duplicated code because "it works":** Each duplicate is a maintenance burden (change must be repeated 6 times)
- **Don't use scoped `<style>` blocks for repeated elements:** Slidev scopes styles per-slide, but duplicating 60 lines across 6 slides is unmaintainable
- **Don't use child combinators (`.a > .b`) in scoped styles:** Vue's scoping mechanism breaks these selectors (Slidev limitation)

## Don't Hand-Roll

Problems that look simple but have existing solutions:

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| French spell checking | Manual proofreading only | LTeX or Code Spell Checker (VS Code) | Manual checking misses patterns, extensions catch typos systematically |
| CSS duplication detection | Visual inspection | Grep/search for repeated class names | Systematic search finds all duplicates, visual inspection misses some |
| QR code URL validation | Manual clicking | Simple grep + regex validation | URLs in 3 locations (frontmatter, text, QRCode components), easy to miss inconsistencies |
| Build verification | Trust it works | Run `pnpm run build` | Catches malformed HTML, missing imports, broken Vue components before commit |

**Key insight:** Maintenance tasks benefit from systematic verification. Use existing tools (grep, build command, spell checkers) rather than trusting manual review alone.

## Common Pitfalls

### Pitfall 1: Scoped Styles Don't Deduplicate Across Slides
**What goes wrong:** Developer sees duplicated CSS in 6 slides, adds `<style scoped>` thinking it's "better" than inline styles, but duplication remains
**Why it happens:** Misunderstanding of Slidev's scoping - each slide is a separate scope, so scoped styles still duplicate 6 times
**How to avoid:** Use Vue components for repeated visual elements, or global styles for truly universal styling
**Warning signs:** Seeing the same `<style>` block in multiple slides, even with `scoped` attribute

### Pitfall 2: QR Code Addon Requires `value` Not `data` (or vice versa)
**What goes wrong:** QR codes don't render after changing URLs, or build fails with unknown prop warning
**Why it happens:** Different versions or forks of slidev-addon-qrcode use different prop names
**How to avoid:** Check the actual addon's API - this project uses `data` property (confirmed by grep in slides.md line 1217, 1240)
**Warning signs:** QR code displays in dev but fails in build, or vice versa

### Pitfall 3: French Typos Masked by Technical Terms
**What goes wrong:** Spell checker flags technical terms (DevOps, CI/CD) but misses French grammar errors (posé vs posés, conférence vs conférences)
**Why it happens:** Technical presentations mix English and French, creating noise in spell check results
**How to avoid:** Use LTeX with French grammar checking enabled, not just spell checking. Review grammatically similar words manually.
**Warning signs:** Spell checker shows 50+ warnings, developer ignores them all, misses real errors

### Pitfall 4: Malformed HTML in Markdown Silently Renders Wrong
**What goes wrong:** Invalid tags like `</img>` don't break the build but render incorrectly or create DOM issues
**Why it happens:** Markdown parsers are forgiving, Vue rendering is forgiving, so malformed HTML "works" until it doesn't
**How to avoid:** Run `pnpm run build` to catch issues. Vite build is stricter than dev server. Use HTML validation if available.
**Warning signs:** Slide looks fine in dev but broken after build, or browser console shows DOM warnings

### Pitfall 5: pnpm Hoisting Issues with Slidev Addons
**What goes wrong:** Build fails with "cannot find module" for addons that work in dev
**Why it happens:** Slidev requires `shamefully-hoist=true` in .npmrc for some addons to resolve correctly
**How to avoid:** Project already has this configured (confirmed in .npmrc). If adding new addons, verify they work in both dev and build modes.
**Warning signs:** `pnpm run dev` works, `pnpm run build` fails with module resolution errors

## Code Examples

Verified patterns from official sources and project analysis:

### Extracting Duplicated CSS to Vue Component
```vue
<!-- components/CalmsBlock.vue -->
<script setup lang="ts">
// Source: Vue 3 Composition API + Slidev component conventions
defineProps({
  highlight: {
    type: String,
    default: 'none', // none = all blocks full opacity
    validator: (value: string) =>
      ['culture', 'automation', 'lean', 'measurement', 'share', 'none'].includes(value)
  },
})
</script>

<template>
  <div class="calms-container">
    <div class="ligne1">
      <div class="block automation" :class="{ dimmed: highlight !== 'automation' && highlight !== 'none' }">
        AUTOMATION
      </div>
      <div class="block lean" :class="{ dimmed: highlight !== 'lean' && highlight !== 'none' }">
        LEAN
      </div>
      <div class="block measurement" :class="{ dimmed: highlight !== 'measurement' && highlight !== 'none' }">
        MEASUREMENT
      </div>
      <div class="block share" :class="{ dimmed: highlight !== 'share' && highlight !== 'none' }">
        SHARE
      </div>
    </div>
    <div class="block culture ligne2" :class="{ dimmed: highlight !== 'culture' && highlight !== 'none' }">
      CULTURE
    </div>
  </div>
</template>

<style scoped>
/* Source: Extracted from slides.md lines 327-380 (repeated 6 times) */
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.dimmed {
  opacity: 0.5;
}
</style>
```

**Usage patterns from slides.md:**

```markdown
# Introduction to CALMS (line ~299)
::right::
<CalmsBlock />

---

# Culture (line ~390, currently highlights culture)
::right::
<CalmsBlock highlight="culture" />

---

# Automation (line ~480, currently highlights automation)
::right::
<CalmsBlock highlight="automation" />

---

# Lean (line ~590)
::right::
<CalmsBlock highlight="lean" />

---

# Measurement (line ~695)
::right::
<CalmsBlock highlight="measurement" />

---

# Share (line ~800)
::right::
<CalmsBlock highlight="share" />
```

### Text Corrections (French Grammar)
```markdown
<!-- Source: DEBT-01 requirement and grep findings -->

<!-- Line ~291: résumé → résumés (plural) -->
BEFORE: Ils sont résumé par l'acronyme **CAMS**
AFTER:  Ils sont résumés par l'acronyme **CAMS**

<!-- Other corrections from DEBT-01 -->
- apportes → apporter (infinitive needed)
- vide → [context needed - likely "vides" plural or "vidé" past participle]
- conference → conférences (plural + accent)
- resume → résumé or résumés (depends on context)
- pose → posé, posée, posés, or posées (depends on gender/number)
```

**Note:** Actual corrections require reading context in slides.md. Requirements list these as known issues but don't specify exact locations beyond what grep can find.

### QR Code URL Consistency
```markdown
<!-- Source: DEBT-03 requirement + grep findings lines 1217, 1240 -->

<!-- Current state (INCONSISTENT) -->
Frontmatter line 14: https://BadRom1.github.io/devops-introduction
Text link line 1207: https://BadRom1.github.io/devops-introduction
QRCode line 1217:    https://badrom1.github.io/devops-introduction  ❌ WRONG
QRCode line 1240:    https://badrom1.github.io/devops-introduction  ❌ WRONG

<!-- After fix (CONSISTENT) -->
ALL locations: https://BadRom1.github.io/devops-introduction

<!-- QRCode component usage -->
<QRCode
  :width="300"
  :height="300"
  type="svg"
  data="https://BadRom1.github.io/devops-introduction"
  :margin="1"
  :dotsOptions="{ type: 'extra-rounded', color: 'purple' }"
  :imageOptions="{ hideBackgroundDots: true, imageSize: 0.4, margin: 0 }"
  image="https://avatars.githubusercontent.com/u/7274432?s=200&v=4"
/>
```

**Source:** [slidev-addon-qrcode README](https://github.com/k2tzumi/slidev-addon-qrcode)

### HTML Validation - Removing Malformed Tags
```markdown
<!-- Source: DEBT-04 requirement -->

<!-- BEFORE: Invalid self-closing img with closing tag -->
<img src="/path/to/image.png" /></img>

<!-- AFTER: Valid self-closing img -->
<img src="/path/to/image.png" />

<!-- OR: Valid paired tags (rarely needed in Markdown) -->
<img src="/path/to/image.png">
```

**Note:** DEBT-04 mentions `</img>` orphan tags but grep didn't find these. They may have been removed already, or requirement may be preventative. Verify during execution.

### Build Verification
```bash
# Source: Project scripts in package.json + Slidev best practices
# Always run before committing changes

pnpm run build

# Expected output:
# - No TypeScript errors
# - No module resolution errors
# - No HTML parsing errors
# - Successful static file generation in dist/

# Common error patterns:
# ❌ "Cannot find module 'components/CalmsBlock.vue'" → component not created or wrong path
# ❌ "Unexpected token" → malformed HTML/Vue template
# ❌ "Unknown custom element" → component not auto-imported (check name matches file)
```

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| Scoped styles per slide | Vue components for reusable elements | Vue 3 era (2020+) | Better reusability, type safety, single source of truth |
| Global CSS files | UnoCSS utility classes | Slidev v0.40+ (2023) | Faster styling, smaller bundles, but not needed for this phase |
| Manual QR code generation | slidev-addon-qrcode | Slidev addons ecosystem (2021+) | Live updates, consistent styling, easier maintenance |
| Slidev beta versions | Stable v1.x | Not yet (project on 0.50.0-beta.7) | Beta is stable enough for production use, but v1.0 will bring API stability |

**Deprecated/outdated:**
- Using `<style>` in frontmatter: Slidev removed this feature, use `styles/` directory or scoped styles instead
- `data-` attributes for slide metadata: Use frontmatter `---` blocks instead
- Old QR code addons (pre-1.0): Some use `value` prop, current standard is `data` prop (verify per addon)

**Note:** This project uses Slidev 0.50.0-beta.7 from 2024. As of 2026, this is ~2 years old but still functional. No breaking changes expected for this phase's work.

## Open Questions

Things that couldn't be fully resolved:

1. **Exact locations of all typos from DEBT-01**
   - What we know: Requirements list 5 typo categories (apportes, vide, conference, resume, pose)
   - What's unclear: Grep only found "résumé" (line 291) and "posé" (line 382 in comment). Other typos not found - may be in different forms or already fixed
   - Recommendation: During execution, grep for each variant (conférence/conference, résumé/resume, etc.) and manually review all French text for grammar errors

2. **Whether `</img>` orphan tags still exist**
   - What we know: DEBT-04 says they exist, grep found none
   - What's unclear: Were they already fixed, or are they in a pattern grep didn't match?
   - Recommendation: Search for all `<img` tags and verify proper formatting. If none found, mark DEBT-04 as already resolved.

3. **CalmsBlock component: opacity toggle vs. highlight prop**
   - What we know: Current code uses `opacity: 0.5` on non-highlighted blocks
   - What's unclear: Is the visual intent to dim others (0.5) or highlight one (others at 0.5)? Semantically same but affects prop naming.
   - Recommendation: Use `highlight` prop (positive framing) with `dimmed` class (0.5 opacity) on non-highlighted blocks. Clearer intent.

4. **Global styles vs. component for h1 color**
   - What we know: Each CALMS slide has `h1 { color: #2B90B6; }` in its `<style>` block
   - What's unclear: Is this a CALMS-specific color or a presentation-wide standard?
   - Recommendation: Check other slides. If only CALMS slides use it, include in CalmsBlock. If used elsewhere, consider global style. Not blocking for this phase.

## Sources

### Primary (HIGH confidence)
- [Slidev Directory Structure](https://sli.dev/custom/directory-structure) - Official documentation for project organization
- [Slidev Slide Scope Styles](https://sli.dev/features/slide-scope-style) - Official documentation for scoped vs global styles
- [Slidev Components Guide](https://sli.dev/guide/component) - Official documentation for component usage
- [slidev-addon-qrcode GitHub](https://github.com/k2tzumi/slidev-addon-qrcode) - Official addon repository with API documentation
- Project files analysis (`slides.md`, `package.json`, `components/Counter.vue`) - Direct inspection of current implementation

### Secondary (MEDIUM confidence)
- [Vue 3 Styling Components](https://dev.to/sucodelarangela/vue3-how-to-style-components-global-scoped-and-modules-4230) - Vue best practices verified with official docs
- [Slidev Markdown Validation Issue #1749](https://github.com/slidevjs/slidev/issues/1749) - Community discussion on markdown validation
- [Slidev pnpm Hoisting Issue #1257](https://github.com/slidevjs/slidev/issues/1257) - Known issue with pnpm configuration

### Tertiary (LOW confidence)
- LTeX and Code Spell Checker extensions - Recommended by community but not verified for this specific use case
- CSS refactoring patterns - General Vue best practices, not Slidev-specific

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH - Existing project, no new dependencies, well-documented frameworks
- Architecture: HIGH - Component pattern is standard Vue/Slidev practice, verified in official docs and existing project structure
- Pitfalls: MEDIUM - Based on issue tracker and community reports, but specific manifestations may vary

**Research date:** 2026-02-02
**Valid until:** 2026-03-02 (30 days - Slidev is mature, no rapid changes expected)

**Research notes:**
- No CONTEXT.md found - full research freedom
- Project already has components/ directory with Counter.vue example - confirms component approach is appropriate
- Slidev version is 2 years old (beta) but still functional - no urgent upgrade needed for this phase
- French language adds complexity to spell checking - recommend manual review over pure automation
