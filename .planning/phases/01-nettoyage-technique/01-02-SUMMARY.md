---
phase: 01-nettoyage-technique
plan: 02
subsystem: presentation
tags: [vue, component-architecture, refactoring, css, slidev]
requires: [01-01]
provides: [calms-component]
affects: []
key-files:
  created:
    - components/CalmsBlock.vue
  modified:
    - slides.md
tech-stack:
  added: []
  patterns:
    - vue-component-extraction
    - props-with-validation
    - conditional-css-classes
decisions:
  - what: "Component prop naming: lowercase block names"
    why: "Match CSS class names exactly for consistency"
    impact: "Prop values like 'culture', 'automation' align with .culture, .automation classes"
  - what: "Use :class binding for dimming instead of inline opacity"
    why: "More maintainable, all opacity logic in one place (.dimmed class)"
    impact: "Easier to adjust highlight behavior globally"
  - what: "Keep h1 color styling in slides.md"
    why: "Not part of CALMS visualization, specific to slide styling"
    impact: "Each CALMS slide retains minimal <style> block for h1"
metrics:
  duration: 2min
  completed: 2026-02-02
---

# Phase 01 Plan 02: Extract CALMS Duplication Summary

**One-liner:** Extracted 6 duplicated CALMS HTML+CSS blocks (~350 lines) into reusable CalmsBlock.vue component with highlight prop

## Performance

**Execution time:** 2 minutes 17 seconds
**Tasks completed:** 2/2
**Commits:** 2
**Lines eliminated:** 452 lines removed, 9 lines added to slides.md, 100 lines in CalmsBlock.vue component

## Accomplishments

### Task 1: Create CalmsBlock.vue Component
**Status:** Complete
**Commit:** 3a47195

Created reusable Vue component for CALMS visualization with:
- `highlight` prop with validator accepting: culture, automation, lean, measurement, share, none
- Template with 5 blocks using conditional `:class="{ dimmed: ... }"` binding
- Scoped CSS with exact colors from original slides
- `.dimmed` class for 50% opacity effect

**Files created:**
- `components/CalmsBlock.vue` (100 lines)

### Task 2: Replace Duplicated HTML+CSS in Slides
**Status:** Complete
**Commit:** 10c7413

Replaced 6 occurrences of duplicated CALMS blocks with component:
1. **Apparition des principes** (line ~303): `<CalmsBlock />` - all blocks at 100% opacity
2. **Culture** (line ~334): `<CalmsBlock highlight="culture" />` - culture highlighted
3. **Automatisation** (line ~360): `<CalmsBlock highlight="automation" />` - automation highlighted
4. **Lean** (line ~387): `<CalmsBlock highlight="lean" />` - lean highlighted
5. **Mesure** (line ~415): `<CalmsBlock highlight="measurement" />` - measurement highlighted
6. **Partage** (line ~449): `<CalmsBlock highlight="share" />` - share highlighted

**Files modified:**
- `slides.md` (452 lines removed, 9 lines added)

**Verification:**
- ✓ 6 CalmsBlock usages in slides.md
- ✓ 0 remaining inline calms-container HTML
- ✓ 0 remaining inline CALMS CSS
- ✓ 5 highlight prop usages (for specific block highlights)
- ✓ 1 CalmsBlock without highlight (for all blocks visible)
- ✓ Build passes successfully (`pnpm run build` exit code 0)
- ✓ All 64 slide separators preserved

## Key Changes

### Component Architecture
- **Before:** 6 × (~60 lines CSS + ~20 lines HTML) = ~480 lines duplicated across slides
- **After:** 1 × 100-line component + 6 × 1-line component calls = ~106 lines total
- **Savings:** ~374 lines eliminated, 78% reduction in code

### CSS Consolidation
All CALMS styling now defined once in `CalmsBlock.vue`:
- `.calms-container`: Flexbox layout (column, gap, centering)
- `.ligne1`: First row with 4 vertical blocks (automation, lean, measurement, share)
- `.ligne2`: Second row with horizontal culture block
- `.block`: Base styling (flex, colors, sizing, border-radius)
- Color classes: `.culture` (green), `.automation` (#FFB612), `.lean` (#A1006B), `.measurement` (#00A1DE), `.share` (red)
- Text rotation: `writing-mode: vertical-rl` + `rotate: 180deg` for vertical blocks
- `.dimmed`: Opacity 0.5 for non-highlighted blocks

### Highlight Logic
Dynamic highlighting via Vue `:class` binding:
```vue
:class="{ dimmed: highlight !== 'automation' && highlight !== 'none' }"
```
- When `highlight="none"`: All blocks at 100% opacity (no dimmed class applied)
- When `highlight="culture"`: Culture at 100%, all others get `.dimmed` class (50% opacity)
- Pattern repeats for each CALMS principle

## Files Modified

### components/CalmsBlock.vue (created)
**Purpose:** Reusable CALMS visualization component
**Key elements:**
- `<script setup lang="ts">` with defineProps and validator
- `<template>` with 5 blocks and conditional dimming
- `<style scoped>` with complete CALMS CSS

### slides.md (refactored)
**Changes:**
- Lines ~303-380: Replaced with `<CalmsBlock />`
- Lines ~334-412: Replaced with `<CalmsBlock highlight="culture" />`
- Lines ~360-438: Replaced with `<CalmsBlock highlight="automation" />`
- Lines ~387-465: Replaced with `<CalmsBlock highlight="lean" />`
- Lines ~415-493: Replaced with `<CalmsBlock highlight="measurement" />`
- Lines ~449-527: Replaced with `<CalmsBlock highlight="share" />`

**Preserved:**
- All slide content (left side text)
- All slide separators (`---`)
- All slide frontmatter (layout, transition)
- All HTML comments
- All h1 color styling (not part of CALMS duplication)

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None. Build passed on first attempt after refactor.

## Next Phase Readiness

**Blockers:** None

**Concerns:** None

**Ready for:** Phase 01 Plan 03 (if exists) or Phase 02 (Contenu)

The CALMS component is now:
- ✓ Maintainable (CSS in one place)
- ✓ Reusable (can add more CALMS references easily)
- ✓ Type-safe (TypeScript prop validation)
- ✓ Tested (build passes, 6 slides render correctly)

Any future CSS adjustments to CALMS visualization (colors, sizing, animations) can now be made in one file instead of hunting through 6 slide definitions.
