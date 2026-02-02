# Domain Pitfalls

**Domain:** DevOps Educational Presentation & Slidev Technical Implementation
**Researched:** 2026-02-02
**Confidence:** MEDIUM (based on training knowledge + project inspection; external sources unavailable)

---

## Critical Pitfalls

Mistakes that cause major pedagogical failures or require complete rewrites.

### Pitfall 1: Tool-First Instead of Principle-First Teaching
**What goes wrong:** Teaching Docker, Kubernetes, Terraform as isolated tools before explaining WHY they exist. Students memorize commands but don't understand the problems these tools solve.

**Why it happens:** DevOps has flashy tools that are easy to demo. It's tempting to show "docker run" commands to look practical. Instructors coming from ops background often jump to tooling.

**Consequences:**
- Students can't choose the right tool for a problem
- They conflate "DevOps" with "using Jenkins"
- When tools change (which they do), their knowledge becomes obsolete
- They miss the cultural transformation aspect entirely

**Prevention:**
- ALWAYS introduce the problem first: "Teams were deploying inconsistently across environments. What if we could..."
- Connect every tool to a CALMS principle (e.g., Docker → Automation, Terraform → Lean via immutable infrastructure)
- Spend 60% of time on principles, 40% on tool examples
- Use tools as illustrations, not the lesson itself

**Detection:**
- If slide titles are tool names ("Docker", "Kubernetes") instead of concepts ("Consistent Environments", "Orchestrating at Scale")
- If you're showing syntax/commands in an intro course
- If students ask "which tool should I learn?" instead of "how do I solve X?"

**Phase impact:** This affects content creation for new sections (Docker, IaC, SRE). Need to restructure around problems, not tools.

---

### Pitfall 2: Oversimplifying DORA Metrics into a Competition
**What goes wrong:** Presenting DORA metrics (deployment frequency, lead time, MTTR, change failure rate) as a scorecard to "win at DevOps" or compare teams. Students think DevOps success = highest numbers.

**Why it happens:** Metrics are concrete and measurable. It's easier to say "deploy 10x per day = good" than to explain context-dependent optimization. The "elite performer" categorization in DORA reports encourages ranking.

**Consequences:**
- Teams optimize for metrics instead of business value (vanity metrics)
- Gaming the system (split one change into 10 tiny deployments)
- Ignoring context (startup vs regulated industry have different constraints)
- Missing the "Measurement" principle: metrics inform improvement, they don't define success

**Prevention:**
- Introduce DORA metrics as diagnostic tools: "These help you see where your bottlenecks are"
- Emphasize context: "Frequent deploys matter for SaaS, less so for medical devices"
- Link to CALMS Measurement: metrics enable learning loops, not competition
- Show trade-offs: faster deploys might mean higher change failure rate during transition
- Mention that DORA elite performers excel in ALL FOUR metrics, not just speed

**Detection:**
- If your slide says "Aim for X deploys per day"
- If you don't mention contexts where different metrics matter
- If metrics feel disconnected from culture/collaboration aspects

**Phase impact:** Critical for the DORA metrics section (1-2 slides). Must frame correctly from the start.

---

### Pitfall 3: CSS Duplication Causing Maintenance Nightmare in Slidev
**What goes wrong:** Copying `<style>` blocks across multiple slides in Slidev. With 5 copies of the CALMS CSS (~60 lines each = 300 lines duplication), any visual change requires updating 5 places. Errors accumulate, styles diverge, presentation becomes unmaintainable.

**Why it happens:**
- Slidev allows inline `<style>` blocks per slide, which feels convenient initially
- Quick prototyping leads to copy-paste
- Documentation doesn't strongly warn against this pattern
- No linter catches CSS duplication in markdown

**Consequences:**
- Technical debt explodes when adding 15-20 new slides
- Inconsistent styling (one CALMS block updated, others forgotten)
- Build performance degrades (Vue recompiles duplicated styles)
- Refactoring becomes risky (which copy is correct?)
- New interactive components (quizz) will face the same duplication trap

**Prevention:**
- Use Slidev's `./style.css` or `./styles/` directory for global styles
- For component-specific styles, create Vue components in `./components/` with scoped styles
- Extract `.calms-container`, `.block`, and all CALMS-related classes to global stylesheet
- Establish CSS architecture before adding new content: global → layout → component → utility
- Use CSS custom properties (variables) for theme colors

**Detection:**
- Grep for repeated `<style>` blocks: `grep -c '<style>' slides.md`
- If modifying a visual element requires editing multiple slides
- If adding new slides makes you copy-paste CSS

**Phase impact:** MUST fix in Phase 1 (CSS refactoring) before adding new content. Otherwise new quizz components will inherit the duplication pattern.

**Slidev-specific fix:**
```css
/* In ./style.css or ./styles/main.css */
.calms-container { /* extracted global styles */ }
.block { /* ... */ }
.culture { /* ... */ }
/* etc */
```
Then slides just use `<div class="calms-container">` without inline styles.

---

### Pitfall 4: Confusing Containers with Virtual Machines
**What goes wrong:** When teaching Docker to beginners, using imprecise language like "containers are lightweight VMs" or failing to explain the shared kernel architecture. Students build a mental model of containers as mini-VMs, leading to incorrect assumptions about isolation, security, and resource usage.

**Why it happens:**
- VMs are a familiar concept, containers are new
- "Isolated environments" applies to both, making the analogy tempting
- The differences (shared kernel, process isolation vs hardware virtualization) require deeper technical knowledge
- Trying to simplify too much

**Consequences:**
- Students expect VM-level isolation and are surprised by container security considerations
- They don't understand why containers start in milliseconds vs minutes for VMs
- Confusion about when to use VMs vs containers vs bare metal
- Misunderstanding resource limits and namespace isolation

**Prevention:**
- Use the analogy but immediately state the difference: "Like VMs, containers isolate applications. UNLIKE VMs, containers share the host OS kernel."
- Show a diagram: VM stack (Hardware → Hypervisor → Guest OS → App) vs Container stack (Hardware → Host OS → Container Runtime → App)
- Emphasize the trade-off: faster startup and lighter resource usage, but shared kernel means less isolation than VMs
- For M1 MIAGE intro level: keep it conceptual, focus on the USE CASE (consistent environments) not the internals

**Detection:**
- If your slides say "containers are lightweight VMs" without qualification
- If you don't have a visual comparing VM and container architecture
- If students leave thinking containers = VMs

**Phase impact:** Critical for Docker/Containers section (2-3 slides). The architecture diagram is essential.

---

## Moderate Pitfalls

Mistakes that cause confusion or technical debt but are recoverable.

### Pitfall 5: Treating IaC as "Just Scripts"
**What goes wrong:** Presenting Infrastructure as Code as glorified bash scripts for provisioning. Missing the declarative nature, idempotency, and state management that distinguish IaC tools (Terraform, Pulumi) from imperative scripting.

**Why it happens:** For beginners, writing a script to launch servers feels like IaC. The abstraction leap to declarative desired state is non-obvious. Demos often show simple examples that look script-like.

**Consequences:**
- Students conflate IaC with automation scripts
- They don't understand why Terraform tracks state or why you can't just "run the script again"
- Missing the GitOps connection (declarative config in Git = source of truth)
- Confusion when real IaC projects don't behave like scripts

**Prevention:**
- Introduce declarative vs imperative clearly: "Script says HOW (step by step). IaC says WHAT (desired end state)."
- Example: Script = "create server, install nginx, configure firewall" / IaC = "I want a server with nginx and this firewall, figure out how to get there"
- Mention idempotency: running IaC twice = same result, running script twice = potential errors
- Connect to CALMS Lean: IaC enables treating infrastructure as cattle, not pets

**Detection:**
- If your IaC slides focus on syntax instead of declarative philosophy
- If you don't explain state management or idempotency
- If students think "Terraform is like ansible"

**Phase impact:** Moderate priority for IaC & GitOps section (2-3 slides). Needs conceptual clarity, not depth.

---

### Pitfall 6: SLI/SLO/SLA Jargon Overload
**What goes wrong:** Introducing SRE concepts with a wall of acronyms (SLI, SLO, SLA, MTBF, MTTR, error budget) without grounding them in a narrative. Students memorize definitions but can't apply them.

**Why it happens:** SRE terminology is dense and interlocking. Explaining one term requires using others. Easy to info-dump.

**Consequences:**
- Students tune out during jargon-heavy slides
- They can't distinguish SLI (measurement) from SLO (target) from SLA (contract)
- Missing the point: SRE uses these to balance velocity and reliability
- Feels disconnected from DevOps principles

**Prevention:**
- Tell a story: "Your API is down. How do you measure reliability? That's an SLI. What's acceptable? That's an SLO. What did you promise customers? That's an SLA."
- Use a concrete example: API response time SLI, 99% requests < 200ms SLO, 99.9% uptime SLA
- Introduce only what's needed for intro level: SLI/SLO/SLA, skip MTBF/error budgets/toil
- Connect to CALMS Measurement: SLIs are the metrics, SLOs are the learning loops

**Detection:**
- If your slide is a table of definitions
- If you introduce more than 5 acronyms in the SRE section
- If you don't provide a concrete example

**Phase impact:** Important for SRE & Observability section (2-3 slides). Needs narrative structure, not definition list.

---

### Pitfall 7: Quiz Questions that Test Memorization, Not Understanding
**What goes wrong:** Writing multiple-choice quizzes that ask "What does CALMS stand for?" or "Which tool is used for containers?". Students can pass by memorizing slides without understanding concepts.

**Why it happens:** Memorization questions are easy to write. Conceptual questions require more thought and nuance. Fear that deeper questions are "too hard" for intro level.

**Consequences:**
- Quizzes don't reveal misunderstandings
- Students feel they understand but can't apply knowledge
- Missed opportunity to reinforce problem-solving over tool naming
- Boring for students who already got the concepts

**Prevention:**
- Write scenario-based questions: "Your team deploys manually once a month. Which CALMS principle would most improve this?" (Answer: Automation)
- Use "which is NOT true" questions to catch misconceptions
- Include questions about trade-offs: "Why might a team choose longer release cycles?" (regulated industry, complexity, etc.)
- Test principles, not tool names: "What problem do containers solve?" not "What is Docker?"

**Detection:**
- If answers are facts from slides (definitions, tool names)
- If questions can be answered without understanding WHY
- If you're tempted to write "All of the above" questions

**Phase impact:** Critical for quiz design phase. Bad quiz questions waste the interactive opportunity.

---

### Pitfall 8: Slidev Build Performance Degradation with 60+ Slides
**What goes wrong:** Slidev build times increase, dev server becomes sluggish, hot reload slows down. With the current ~40 slides at 1267 lines + adding 15-20 slides, the presentation will hit 70-80 slides and ~2000+ lines. Vite/Vue build may struggle.

**Why it happens:**
- Slidev uses Vite which rebuilds on changes
- Each slide is a Vue component
- CSS duplication (300 lines of repeated styles) increases bundle size
- Large images or custom components add to parse time
- Beta version (0.50.0-beta.7) may have unoptimized build paths

**Consequences:**
- Slow dev experience makes iteration painful
- Build times for GitHub Pages deployment increase
- Hot reload lag frustrates content creation
- Risk of hitting memory limits in CI/CD

**Prevention:**
- Fix CSS duplication FIRST (eliminates 300 lines)
- Optimize images: use WebP, compress, ensure assets are properly sized
- Split long slides with complex components into simpler slides
- Use `v-click` sparingly (each click creates Vue reactivity overhead)
- Consider lazy-loading for heavy components
- Monitor build times: `time pnpm run build` to catch regressions
- Upgrade to stable Slidev version if available (beta may have perf issues)

**Detection:**
- `pnpm run dev` takes >10 seconds to start
- Hot reload takes >3 seconds after a change
- Build time for `pnpm run build` exceeds 60 seconds
- Dev server becomes unresponsive during editing

**Phase impact:** Should be monitored throughout. CSS refactoring in Phase 1 helps. If performance degrades during content addition phases, pause and optimize.

---

### Pitfall 9: Forgetting the "Share" in CALMS When Teaching
**What goes wrong:** Focusing presentation content on Culture, Automation, Lean, Measurement, but neglecting the **Share** principle itself in the course design. Ironic: teaching DevOps collaboration without modeling it.

**Why it happens:** Share feels like a "soft" principle compared to Automation (tools!) or Measurement (metrics!). It's easy to mention but hard to embed in a lecture format.

**Consequences:**
- Students don't see how knowledge sharing works in practice
- They miss that DevOps culture includes blameless postmortems, documentation, and cross-team communication
- Course becomes one-way info dump instead of collaborative learning

**Prevention:**
- Use quizzes as a sharing mechanism: pause for discussion, not just right/wrong answers
- Reference real-world knowledge sharing: "DevOpsDays, tech blogs, open-source contributions are how practitioners Share"
- Model transparency: if you don't know something, say so and show how you'd find out
- Include resources slide (already exists) but explain WHY those resources matter (Share principle)
- Mention blameless postmortems explicitly: "Share includes sharing failures to learn collectively"

**Detection:**
- If "Share" gets one bullet point and no follow-up
- If your teaching style is lecture-only without interaction
- If students can't name examples of sharing in DevOps culture

**Phase impact:** Low priority for content changes, but important mindset for course delivery. Can be reinforced in quizzes and narrative transitions.

---

## Minor Pitfalls

Mistakes that cause annoyance but are easily fixable.

### Pitfall 10: Inconsistent Terminology (French vs English)
**What goes wrong:** Mixing French and English terms inconsistently. Using "déploiement" sometimes, "deployment" other times. Using English acronyms (CI/CD, DORA) without explaining them in French context.

**Why it happens:** DevOps terminology is primarily English. French tech education often uses English terms. Trying to translate everything feels awkward ("intégration continue" vs "CI").

**Consequences:**
- Students confused by which terms are standard (need to know English terms for job market)
- Slides feel inconsistent in tone
- International students or francophones may struggle with different terms

**Prevention:**
- Establish a glossary decision: technical terms stay in English (CI/CD, Docker, SRE) with French explanations
- First mention: "CI/CD (Continuous Integration / Continuous Deployment) ou Intégration et Déploiement Continus"
- Subsequent mentions: use acronym
- Slide titles can be French, technical terms in content can be English
- Include a glossary slide if needed

**Detection:**
- Students asking "what's the French word for X?"
- Inconsistent terminology across slides
- Translated terms that sound awkward ("conteneur" vs "container")

**Phase impact:** Low priority. Can be fixed during copy-editing phase. Establish glossary at the start of content addition.

---

### Pitfall 11: QR Code / URL Inconsistencies Breaking Links
**What goes wrong:** QR codes on final slide pointing to wrong URL (badrom1 vs badroro). Students scan, link breaks, they can't access slides or give feedback.

**Why it happens:** Username changed, or multiple accounts, or typo during QR code generation. Easy to forget to regenerate QR code after URL change.

**Consequences:**
- Embarrassing in front of students
- Students can't access materials after course
- Broken feedback loop (can't collect quiz results or course feedback)

**Prevention:**
- Use URL shortener or custom domain that you control (not tied to GitHub username)
- Test QR codes before presentation: scan them yourself on phone
- Generate QR codes programmatically with slidev-addon-qrcode (already installed) instead of embedding images
- Store the source URL in a variable at top of slides.md, reference it in QR code generation
- Include text fallback URL on slide in case QR code fails

**Detection:**
- QR code scans to 404 or wrong repo
- URL in text doesn't match URL in QR code
- Students reporting broken links

**Phase impact:** Low priority, quick fix in Phase 1 (technical debt cleanup).

---

### Pitfall 12: Overloading Slides with Text Walls
**What goes wrong:** Trying to be comprehensive leads to dense paragraphs on slides. Students can't read, listen, and absorb simultaneously. Slide becomes documentation, not presentation.

**Why it happens:** Fear of leaving things out. Trying to make slides "self-contained" for students who review later. Academic background encourages thoroughness.

**Consequences:**
- Students zone out, read ahead instead of listening
- Presenter reads the slide word-for-word (boring)
- Key messages buried in paragraphs
- Slides don't work as visual aids

**Prevention:**
- Follow the "6x6 rule" guideline: max 6 bullets, max 6 words per bullet (flexible, not strict)
- Use speaker notes for details (Slidev supports presenter mode)
- Visual > Text: diagrams for architecture, icons for concepts, minimal text
- If a slide needs a wall of text, split into multiple slides with progressive disclosure (v-click)
- Use "Here's what you need to know" slide after complex topics: 3 bullet takeaways

**Detection:**
- If you can't present a slide in 60-90 seconds
- If students are reading instead of watching
- If bullets are full sentences instead of phrases

**Phase impact:** Moderate priority. Review during content creation phase. Each new slide (Docker, IaC, DORA, SRE) should be visually simple.

---

### Pitfall 13: Not Testing Interactive Components on Presentation Day Tech
**What goes wrong:** Quizzes or interactive Slidev components work fine on dev machine but fail during presentation (wrong resolution, browser compatibility, mobile display if students follow along).

**Why it happens:** Dev environment != presentation environment. Assumptions about screen size, browser, network. No dry run.

**Consequences:**
- Scrambling to fix tech issues in front of students
- Skipping planned quizzes, losing engagement opportunity
- Looking unprepared

**Prevention:**
- Test on actual presentation hardware (projector resolution, different browser)
- If students follow along on phones/tablets, test responsive design
- Have a backup: print quiz questions as a fallback, or use verbal questions
- Dry run the full presentation at least once
- Check Slidev presenter mode works

**Detection:**
- Haven't tested on presentation environment
- Slidev components untested on target screen resolution
- No fallback plan for tech failures

**Phase impact:** Low priority during development, HIGH priority during final verification phase. Add to checklist.

---

### Pitfall 14: Missing Narrative Connective Tissue Between Sections
**What goes wrong:** Each section (CALMS, CI/CD, Docker, IaC, DORA, SRE) feels like a standalone module. Students don't see how they connect into a coherent DevOps philosophy.

**Why it happens:** Content is added incrementally, each section designed in isolation. Logical flow isn't revisited after all sections are complete.

**Consequences:**
- Students see DevOps as a grab-bag of tools and buzzwords
- They can't explain how CI/CD enables SRE, or how IaC connects to CALMS Automation
- Presentation feels fragmented
- Low retention because concepts don't form a mental model

**Prevention:**
- Add transition slides: "Now that we've covered CALMS principles, let's see how Automation applies to infrastructure..."
- Use recurring visual motifs: highlight which CALMS principle each section addresses
- Include a "How it all fits together" slide before conclusion: diagram showing Culture → Automation (CI/CD, IaC, Containers) → Measurement (DORA, SRE) → Share loop
- Start each new section with "Remember CALMS? This section focuses on [principle]."

**Detection:**
- If you can rearrange sections without breaking the narrative (they should have dependencies)
- If students ask "how does Docker relate to DevOps?" (should be obvious from flow)
- If conclusion slide doesn't reference earlier concepts

**Phase impact:** Important during content addition phase. After adding all new sections, step back and add transitions. Include in final review phase.

---

## Phase-Specific Warnings

| Phase Topic | Likely Pitfall | Mitigation |
|-------------|---------------|------------|
| CSS Refactoring | Breaking existing CALMS visual during extraction | Test visual output after extracting to global CSS. Take screenshot before/after. |
| Docker/Containers | Tool-first teaching (Pitfall 1), VM confusion (Pitfall 4) | Lead with problem ("inconsistent environments"), show VM vs Container diagram, minimal commands. |
| IaC & GitOps | Treating IaC as scripts (Pitfall 5) | Emphasize declarative vs imperative, show idempotency example, connect to CALMS Lean. |
| DORA Metrics | Metrics as competition (Pitfall 2) | Frame as diagnostics, emphasize context, link to CALMS Measurement, show trade-offs. |
| SRE & Observability | Jargon overload (Pitfall 6) | Story-driven (API downtime), limit acronyms (SLI/SLO/SLA only), concrete example. |
| Quiz Design | Memorization questions (Pitfall 7) | Scenario-based questions, test WHY not WHAT, focus on problem-solving. |
| Slidev Scaling | Performance degradation (Pitfall 8) | Monitor build times, fix CSS duplication first, optimize images, test after each content addition. |
| Final Review | Text walls (Pitfall 12), missing transitions (Pitfall 14) | Apply 6x6 guideline, add transition slides, create "how it fits together" diagram. |

---

## Research Confidence & Sources

**Confidence levels by area:**

| Area | Confidence | Rationale |
|------|-----------|-----------|
| DevOps Education Pitfalls (1, 2, 4, 5, 6) | MEDIUM | Based on common patterns in DevOps education from training knowledge. Not verified with 2026 sources (WebSearch unavailable). Principles stable over time. |
| Slidev Technical Pitfalls (3, 8, 13) | MEDIUM | Based on Vite/Vue build patterns, Slidev architecture knowledge from training, and inspection of project's actual CSS duplication. Specific to beta version 0.50.0-beta.7 not verified with current docs. |
| Pedagogical Patterns (7, 9, 12, 14) | HIGH | General teaching principles, not DevOps-specific. Applicable across technical education. |
| Minor Technical Issues (10, 11) | HIGH | Observed directly in PROJECT.md requirements and common presentation issues. |

**Sources:**
- Training knowledge of DevOps education patterns (as of January 2025)
- Direct inspection of `/home/romain/workplace/perso/devops-introduction/slides.md` (CSS duplication confirmed: 6 instances of ~60-line style blocks)
- Project requirements from `.planning/PROJECT.md`
- Slidev architectural patterns from training knowledge

**Verification status:**
- WebSearch: UNAVAILABLE (permission denied)
- WebFetch: UNAVAILABLE (permission denied)
- Context7: Not attempted (Slidev may not be available, focus on general patterns)
- Official Slidev docs: Not accessible for 2026 updates

**What might I have missed:**
- Slidev 0.50.0-beta.7 specific performance issues or best practices (beta version, may have undocumented quirks)
- Recent changes in DevOps education best practices (2025-2026 trends)
- French-specific DevOps teaching resources or terminology conventions
- MIAGE Grenoble specific context (student background, previous courses, expectations)

**Recommendation for roadmap:**
- Treat technical pitfalls (CSS, performance) as HIGH confidence → act on immediately
- Treat pedagogical pitfalls as MEDIUM confidence → use as guidelines, validate with sample slides
- Consider consulting with experienced DevOps educators or MIAGE faculty if pitfalls seem misaligned
- Monitor Slidev build performance as objective validation (build times, dev server responsiveness)

---

**Note for orchestrator:** All pitfalls are domain-specific (not generic advice). Each includes detection signs, prevention strategies, and phase impact. Ready for roadmap creation.
