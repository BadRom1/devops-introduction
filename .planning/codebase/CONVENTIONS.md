# Coding Conventions

**Analysis Date:** 2026-02-02

## Project Type

This is a Slidev presentation codebase with minimal custom TypeScript code. Most code is presentation content in Markdown with light interactive Vue components.

## Naming Patterns

**Files:**
- Vue components: PascalCase (e.g., `Counter.vue`)
- TypeScript modules: camelCase (e.g., `external.ts`)
- Markdown slides: lowercase (e.g., `slides.md`)

**Functions:**
- Exported functions use camelCase (e.g., `emptyArray`, `sayHello` in `snippets/external.ts`)
- Generic type parameters use PascalCase (e.g., `<T>`)

**Variables:**
- Local variables use camelCase (e.g., `counter`, `length`)
- Component refs use camelCase (e.g., `const counter = ref(props.count)`)

**Types:**
- TypeScript types not explicitly defined in this minimal codebase; Vue components use implicit typing with `lang="ts"`

## Code Style

**Formatting:**
- No Prettier config found; project relies on default formatting
- Vue templates use shorthand directives (e.g., `@click`, `v-click`)
- Attributes use kebab-case in templates (e.g., `hover:bg`, `border`)
- Vue class bindings use Tailwind-like utility syntax

**Linting:**
- No ESLint config found
- One lint disable comment used: `/* eslint-disable no-console */` in `snippets/external.ts`
- This suggests console usage for demo code is intentional

**Indentation:**
- 2 spaces (inferred from `.editorconfig` defaults and Vue template formatting)

## Import Organization

**Patterns:**
- Vue imports come first: `import { ref } from 'vue'`
- Then named imports from project modules
- Type imports not used in current codebase

**Example** (from `Counter.vue`):
```typescript
import { ref } from 'vue'
```

**Path Aliases:**
- No path aliases configured in this project; relative paths would need to be added if expanding

## Error Handling

**Patterns:**
- No explicit error handling code present in the minimal codebase
- Console logging used for non-critical output (see `snippets/external.ts`)
- Demo/snippet code, not production-grade error handling expected

## Logging

**Framework:** Native `console` object

**Patterns:**
- `console.log()` used in snippet demos
- Isolated to non-critical code with explicit `eslint-disable` comment
- Not used in component code

**Example** (from `snippets/external.ts`):
```typescript
console.log('Hello from snippets/external.ts')
```

## Comments

**When to Comment:**
- Region markers used for code snippets: `// #region snippet` and `// #endregion snippet`
- These mark code sections for extraction into slides

**JSDoc/TSDoc:**
- Not currently used in codebase; minimal code volume doesn't require it
- Would add if code library grows

**Example** (from `snippets/external.ts`):
```typescript
// #region snippet
// Inside ./snippets/external.ts
export function emptyArray<T>(length: number) {
  return Array.from<T>({ length })
}
// #endregion snippet
```

## Vue Component Design

**Structure:**
- Use `<script setup lang="ts">` for modern Vue 3 composition
- Props defined with `defineProps()` with type inference
- Template uses utility classes (Tailwind-like shorthand)

**Example** (from `components/Counter.vue`):
```vue
<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0,
  },
})

const counter = ref(props.count)
</script>

<template>
  <div flex="~" w="min" border="~ main rounded-md">
    <button @click="counter -= 1">-</button>
    <span m="auto" p="2">{{ counter }}</span>
    <button @click="counter += 1">+</button>
  </div>
</template>
```

**Patterns:**
- Props typed implicitly through runtime definition
- Reactive state via `ref()`
- Shorthand event binding: `@click`
- Inline styles for theme overrides

## Module Design

**Exports:**
- Named exports preferred (e.g., `export function emptyArray()`)
- Single module exports full functionality, no barrel files used

**Example** (from `snippets/external.ts`):
```typescript
export function emptyArray<T>(length: number) {
  return Array.from<T>({ length })
}

export function sayHello() {
  console.log('Hello from snippets/external.ts')
}
```

---

*Convention analysis: 2026-02-02*
