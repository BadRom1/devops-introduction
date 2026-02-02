# Testing Patterns

**Analysis Date:** 2026-02-02

## Test Framework Status

**No Test Framework Detected**

This is a Slidev presentation codebase with no testing infrastructure configured.

- No `jest.config.*`, `vitest.config.*`, or test runner configuration files
- No test dependencies in `package.json`
- No `.test.ts`, `.spec.ts`, or test files anywhere in codebase
- Testing not a requirement for presentation content

## Run Commands

**Testing:**
- Not available
- No test command in `package.json` scripts

**Build/Dev Commands** (presentation-related):
```bash
npm run build              # Build slides to dist/
npm run dev                # Start dev server with --open
npm run export             # Export slides
```

**Test Setup** (if testing were added):
Would recommend:
```bash
npm run test               # Run all tests
npm run test:watch        # Watch mode
npm run test:coverage     # Coverage report
```

## Project Type: Presentation Framework

This codebase uses **Slidev** - a presentation-focused framework where:
- Content is in Markdown (`slides.md`)
- Interactive components are Vue components
- Code snippets are demo/example code, not libraries

Therefore:
- Unit testing not applicable to presentation content
- Component testing would apply only if adding interactive components beyond `Counter.vue`
- Snippet code is educational, not production code

## Minimal Component Code

Only one interactive component exists: `components/Counter.vue`

**Current Code:**
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

This is a simple state management component with no complex logic requiring test coverage.

## Snippet Code

Location: `snippets/external.ts`

**Code:**
```typescript
export function emptyArray<T>(length: number) {
  return Array.from<T>({ length })
}

export function sayHello() {
  console.log('Hello from snippets/external.ts')
}
```

These are demonstration snippets extracted into slides, not production code requiring tests.

## Test Coverage

**Requirements:** Not enforced

**Current Coverage:** 0% (no tests exist)

## Recommendation: When to Add Testing

**Add tests if:**
1. Interactive components grow beyond simple state management
2. Complex business logic added to utilities
3. Snippet code becomes reusable library code
4. Deploy to production with automated validation

**Suggested Framework when needed:**
- **Vitest** - For unit testing Vue components and TypeScript utilities
- **Vue Test Utils** - For component-specific testing
- **Happy-dom** - Lightweight DOM for snapshot tests

## Development Environment

**Node Version:** `lts/jod` (specified in `.nvmrc`)

**Package Manager:** pnpm with shamefully-hoist enabled (see `.npmrc`)

**No Tooling:**
- No linter configured
- No code formatter configured
- No type checker (TypeScript present but not validated in CI)
- No pre-commit hooks

---

*Testing analysis: 2026-02-02*
