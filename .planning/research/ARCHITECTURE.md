# Architecture Patterns: Technical Training Presentation

**Domain:** Educational presentation (DevOps introduction, 1h30, M1 MIAGE)
**Researched:** 2026-02-02
**Confidence:** MEDIUM (based on established pedagogical principles and instructional design patterns)

## Recommended Architecture

The presentation should follow a **Progressive Complexity Arc** with strategic engagement points.

### Structural Overview

```
[HOOK] → [FOUNDATION] → [CORE CONCEPTS] → [MODERN PRACTICES] → [INTEGRATION] → [CLOSURE]
  ↓          ↓               ↓                    ↓                  ↓           ↓
 5min      10min          35min                35min              10min       5min
```

### Time Allocation Breakdown (Total: 90 minutes)

| Section | Time | Purpose | Quiz Placement |
|---------|------|---------|----------------|
| 1. Hook & Introduction | 5 min | Capture attention, establish relevance | No |
| 2. Foundation (History + Why DevOps) | 10 min | Context setting, problem definition | No |
| 3. Core Concepts (CALMS + Feedback Loop) | 35 min | Theoretical foundation | **Quiz 1** (5 min, after CALMS) |
| 4. Modern Practices (Docker, IaC, DORA, SRE) | 35 min | Contemporary application | **Quiz 2** (5 min, after Docker+IaC)<br>**Quiz 3** (5 min, after DORA+SRE) |
| 5. Tools & Best Practices | 10 min | Practical orientation | No |
| 6. Closure (Tech Watch + Demo + End) | 10 min | Call to action, resources | Optional feedback quiz |

**Net content time:** 80 minutes + 15 minutes for 3 quizzes = 95 minutes (5 min buffer for questions/transitions)

### Component Boundaries

| Component | Responsibility | Connects To |
|-----------|---------------|-------------|
| Hook | Establish rapport, relevance ("Qui je suis", "C'est quoi DevOps?") | Foundation |
| Foundation | Historical context, problem statement (Dev vs Ops conflict) | Core Concepts |
| Core Concepts | CALMS principles, feedback loop, DoD | Modern Practices |
| Modern Practices | Docker, IaC, DORA metrics, SRE/Observability | Tools & Best Practices |
| Tools & Best Practices | Concrete tools, security, maintainability | Closure |
| Closure | Tech watch resources, live demo, next steps | End |

### Narrative Flow

**Problem → Philosophy → Principles → Modern Implementation → Tooling → Action**

1. **Problem** (Foundation): Dev vs Ops conflict, velocity vs stability
2. **Philosophy** (Core): DevOps as culture (CALMS), not just tooling
3. **Principles** (Core): How CALMS manifests (automation, measurement, collaboration)
4. **Modern Implementation** (Modern Practices): How principles are realized today (containers, IaC, metrics, observability)
5. **Tooling** (Tools): Concrete ecosystem (Jenkins, GitLab, CNCF landscape)
6. **Action** (Closure): How to continue learning (veille techno), seeing it in action (demo)

## Patterns to Follow

### Pattern 1: Attention Wave Management
**What:** Structure content to match natural attention fluctuations in a 90-minute session.

**Why:** Adult attention spans follow predictable curves. Peak attention is at the start (first 15 min), drops significantly after 20-30 min, and can be recovered with strategic breaks or interactive elements.

**Implementation:**
- **0-15 min** (High attention): Hook + Foundation. Establish context quickly.
- **15-50 min** (Declining attention): Core Concepts. Use visual CALMS diagram, breaks between principles. **Insert Quiz 1** at ~40 min mark to re-engage.
- **50-85 min** (Recovered attention via novelty): Modern Practices. New topics (Docker, IaC, DORA, SRE) provide natural novelty. **Insert Quiz 2** and **Quiz 3** to maintain engagement.
- **85-90 min** (Final push): Tools + Closure. Shift to practical, forward-looking content.

**Research basis:** Educational psychology - primacy/recency effect, attention fatigue patterns.

### Pattern 2: Chunking with Signposting
**What:** Group related concepts into clear chunks with explicit transitions.

**Why:** Cognitive Load Theory indicates working memory can handle 3-7 chunks simultaneously. Explicit signposting reduces cognitive overhead.

**Implementation:**
- Use section slides (`layout: section`) as visual breaks between major chunks
- Each major section should have:
  - **Entry signpost**: "We just covered X. Now we'll explore Y."
  - **Internal structure**: 2-4 related concepts
  - **Exit signpost**: "Recap: we learned A, B, C. This sets us up for D."

**Example for Modern Practices section:**
```
[Section slide: "Modern DevOps Practices"]
→ "Now that we understand CALMS, let's see how these principles manifest in 2026"
→ Docker (2 slides) + IaC (2 slides)
→ Quiz 2 (check understanding)
→ "We've seen how automation works in practice. Now let's talk about measurement."
→ DORA (2 slides) + SRE (2 slides)
→ Quiz 3 (check understanding)
```

### Pattern 3: Concept Scaffolding
**What:** New topics build explicitly on previously established concepts.

**Why:** Ausubel's Subsumption Theory - new knowledge is anchored to existing mental structures.

**Implementation:**

| New Topic | Scaffolds On | Explicit Connection |
|-----------|--------------|---------------------|
| Docker | Automation (CALMS) | "Remember automation? Docker automates environment consistency." |
| IaC | Automation + Lean (CALMS) | "IaC applies automation to infrastructure, eliminating manual waste." |
| DORA | Measurement (CALMS) | "DORA metrics operationalize the Measurement principle - here's how." |
| SRE | Measurement + Share (CALMS) | "SRE formalizes reliability measurement and shared responsibility." |

**Slide placement:** Each new topic slide starts with a callback: "Rappel: [CALMS principle]. Maintenant: [new topic]."

### Pattern 4: Interactive Checkpoints (Quizzes)
**What:** Strategic quiz placement to assess understanding and re-engage attention.

**Why:** Testing Effect (retrieval practice strengthens memory), metacognitive benefits (learners assess their own understanding).

**Quiz Design:**

**Quiz 1: After CALMS (40 min mark)**
- **Purpose:** Verify understanding of core principles before moving to applications
- **Format:** 3-4 MCQ questions
- **Sample questions:**
  - "Quel principe CALMS est la fondation de tous les autres?"
  - "L'automatisation consiste à... (a) éliminer les Ops (b) libérer du temps pour des tâches à valeur ajoutée (c) remplacer les tests manuels"
  - "Vrai/Faux: Le Lean encourage l'ajout de nombreux outils pour couvrir tous les besoins."

**Quiz 2: After Docker + IaC (60 min mark)**
- **Purpose:** Check practical understanding of automation concepts
- **Format:** 2-3 MCQ questions
- **Sample questions:**
  - "Docker résout principalement quel problème? (a) différences entre env dev/prod (b) sécurité (c) monitoring"
  - "Infrastructure as Code permet de... (a) écrire du code plus vite (b) versionner l'infrastructure (c) réduire les coûts cloud"

**Quiz 3: After DORA + SRE (75 min mark)**
- **Purpose:** Verify understanding of measurement and reliability
- **Format:** 2-3 MCQ questions
- **Sample questions:**
  - "Quelle métrique DORA mesure la stabilité? (a) deployment frequency (b) change failure rate (c) lead time"
  - "Un SLO définit... (a) le niveau de service attendu (b) le salaire d'un ops (c) un type de log"

**Implementation notes:**
- Use Slidev's `v-click` or interactive quiz component if available
- Allow 5 minutes per quiz (presentation + discussion of correct answers)
- Show correct answers immediately - this is formative, not evaluative

### Pattern 5: Theory-Practice Oscillation
**What:** Alternate between conceptual explanation and concrete examples.

**Why:** Concrete examples make abstract concepts memorable. Oscillation prevents "concept fatigue."

**Implementation:**

| Slide Type | Ratio | Example |
|------------|-------|---------|
| Concept | 40% | "Le Lean élimine le gaspillage" |
| Example/Visual | 40% | CALMS visual diagram, feedback loop diagram |
| Bridge/Connection | 20% | "Comment cela se traduit-il dans vos projets?" |

**Applied to new sections:**
- **Docker section:** Concept slide ("Qu'est-ce qu'un conteneur?") → Visual slide (image vs container diagram) → Example ("Comment Docker élimine 'ça marche sur ma machine'")
- **IaC section:** Concept slide ("Infrastructure déclarative") → Example (snippet Terraform - visual only, no syntax details) → Connection ("Pourquoi Git devient la source de vérité")
- **DORA section:** Concept slide ("4 métriques clés") → Visual (table of 4 metrics with definitions) → Connection ("Lien avec Measurement de CALMS")
- **SRE section:** Concept slide ("SRE = Dev mindset for Ops") → Visual (SLI/SLO/SLA pyramid) → Example ("Error budget concept")

## Anti-Patterns to Avoid

### Anti-Pattern 1: Information Overload
**What:** Cramming too much detail into slides (walls of text, complex diagrams, excessive bullet points).

**Why bad:** Violates Cognitive Load Theory - learners' working memory saturates, comprehension drops.

**Detection:** More than 5 bullet points per slide, paragraphs of text, multi-layered diagrams.

**Instead:**
- **One concept per slide** - if a slide needs extensive explanation, split it
- **Visual over text** - use diagrams, icons, color coding (already done well with CALMS visual)
- **Progressive disclosure** - use `v-click` to reveal points sequentially (already used in existing slides)

### Anti-Pattern 2: Quiz as Punishment
**What:** Quizzes feel like "testing" rather than learning checkpoints.

**Why bad:** Creates anxiety, reduces engagement, defeats formative assessment purpose.

**Detection:** Quizzes at end of session only, no discussion of answers, punitive language ("Avez-vous bien suivi?").

**Instead:**
- Frame as "checkpoint" or "récapitulatif interactif"
- Discuss answers collaboratively - "Qui a choisi A? B? Pourquoi?"
- Position as helping learners self-assess - "Êtes-vous prêts pour la suite?"

### Anti-Pattern 3: Topic Silos
**What:** New topics presented in isolation without connecting to core principles.

**Why bad:** Students miss the coherence - Docker, IaC, DORA, SRE feel like random add-ons rather than manifestations of DevOps philosophy.

**Detection:** Section transitions lack callbacks to CALMS, students ask "why are we talking about this?"

**Instead:**
- **Explicit scaffolding** (Pattern 3 above)
- **Recurring visual motif** - show CALMS diagram again when introducing Docker, highlight "Automation" pillar
- **Verbal bridges** - "Souvenez-vous: CALMS dit qu'il faut mesurer. DORA nous dit quoi mesurer."

### Anti-Pattern 4: Front-Loading Complexity
**What:** Starting with difficult concepts before establishing foundation.

**Why bad:** Learners without schema to anchor new knowledge experience cognitive overload.

**Detection:** Docker introduced before CALMS, technical details before big picture.

**Instead:**
- **Current structure is correct**: History → Why → Principles → Applications
- **Keep it**: Don't reorder to put "cool stuff" (Docker) upfront
- **Maintain arc**: Simple → Complex, Abstract → Concrete, Problem → Solution

### Anti-Pattern 5: Passive Final Act
**What:** Ending with administrative details, dry recap, or trailing off.

**Why bad:** Recency effect means last 5-10 minutes are highly memorable - wasting it on weak content undermines entire session.

**Detection:** Last slides are just "questions?", "merci", or list of links.

**Instead:**
- **Current plan is good**: Demo → QR codes with feedback
- **Strengthen it**:
  - Demo should show real pipeline in action (existing: GitLab pipeline demo)
  - Final slide should have clear call-to-action: "Continuez votre apprentissage" with QR to resources
  - Consider ending with provocative question: "Votre entreprise de stage/alternance fait-elle vraiment du DevOps, ou juste des outils DevOps?"

## Section-by-Section Architecture

### Section 1: Hook & Introduction (5 min, slides 1-3)

**Goal:** Establish credibility and relevance.

**Current structure:** ✓ Working well
- Slide 1: Title
- Slide 2: "Qui je suis?" (background, SNCF, MIAGE alumnus)
- Slide 3: "C'est quoi le DevOps?" (engage audience with question)

**Recommendation:** Keep as-is. Opens with personal connection, then poses the driving question.

**Timing:** 5 min total (1 min title, 2 min bio, 2 min question/discussion)

---

### Section 2: Foundation (10 min, slides 4-9)

**Goal:** Establish historical context and core problem statement.

**Current structure:** ✓ Working well
- Section slide: "Histoire du DevOps"
- Origin slides: DevOpsDays, culture not method, cloisonnement Dev/Ops
- Section slide: "Pourquoi la démarche DevOps?"
- Opposition Dev vs Ops, conflict of methodologies

**Recommendation:** Keep as-is. Provides essential grounding.

**Timing:** 10 min total (2 min per slide pair, allows for brief discussion)

---

### Section 3: Core Concepts (35 min, slides 10-25)

**Goal:** Teach CALMS principles and feedback loop.

**Current structure:** Mostly good, needs quiz addition
- Section slide: "Les principes du DevOps"
- CALMS introduction slide
- 5 slides on CALMS (Culture, Automation, Lean, Measurement, Share)
- Agile principles slide
- Section slide: "La boucle de rétroaction"
- Feedback loop diagram
- Definition of Done

**Recommendation:**
1. **Keep existing CALMS slides** - visual is excellent, explanations clear
2. **After DoD slide, INSERT QUIZ 1** (5 min)
   - Slide title: "Récapitulatif interactif 1: Les principes"
   - 4 MCQ questions testing CALMS understanding
   - Format: Question → Click to reveal answer → Brief discussion
3. **Timing:**
   - CALMS section slides: 20 min (intro + 5 principles + Agile note)
   - Feedback loop: 5 min
   - DoD: 5 min
   - **Quiz 1: 5 min**
   - **Total: 35 min**

**Quiz 1 Questions (suggested):**

```markdown
## Quiz 1: Les Principes DevOps

**Q1:** Quel est le principe fondamental sans lequel les autres échouent?
- A) Automation
- B) Culture ✓
- C) Measurement
- D) Share

**Q2:** L'automatisation vise principalement à...
- A) Remplacer les équipes Ops
- B) Éliminer tous les tests manuels
- C) Libérer du temps pour des tâches à valeur ajoutée ✓
- D) Accélérer le code

**Q3:** Le Lean consiste à...
- A) Réduire les effectifs
- B) Chasser les gaspillages et excès ✓
- C) Adopter tous les outils disponibles
- D) Faire des réunions quotidiennes

**Q4:** Vrai ou Faux: La "Definition of Done" peut inclure des critères de couverture de code et de sécurité.
- A) Vrai ✓
- B) Faux
```

---

### Section 4: Modern Practices (35 min, slides 26-43)

**Goal:** Show how CALMS principles manifest in contemporary DevOps practices.

**Current structure:** MISSING - this is the expansion area

**Recommended structure:**

#### 4.1: Docker & Containers (10 min, 3 slides)

**Slide 26:** Section slide "Pratiques DevOps Modernes"
- Transition: "Nous avons vu les principes CALMS. Voyons maintenant comment ils se traduisent dans les pratiques actuelles."
- Time: 1 min

**Slide 27:** Docker - Concept
- Title: "Conteneurs & Docker"
- Content:
  - "Rappel: Automation (CALMS) élimine les tâches répétitives"
  - "Problème: 'Ça marche sur ma machine' - environnements divergent"
  - "Solution: Conteneurs encapsulent app + dépendances"
  - Visual: Simple diagram showing app + dependencies in container
- Speaker notes: Mention that containers aren't new (2000s), Docker democratized them (2013+)
- Time: 4 min

**Slide 28:** Docker - Images, Registries, Orchestration
- Title: "Écosystème Docker"
- Content:
  - **Images**: Templates immuables (like a recipe)
  - **Registries**: Docker Hub, GitHub Container Registry (like a cookbook library)
  - **Orchestration**: Kubernetes, Docker Swarm (managing containers at scale)
  - Visual: Simple flow diagram: Dockerfile → Image → Registry → Container → Orchestrator
- Speaker notes: Don't dive into Dockerfile syntax - this is conceptual
- Time: 5 min

#### 4.2: Infrastructure as Code (IaC) (10 min, 3 slides)

**Slide 29:** IaC - Concept
- Title: "Infrastructure as Code (IaC)"
- Content:
  - "Rappel: Automation + Lean (CALMS)"
  - "Avant: Infrastructure provisionnée manuellement (clics, commandes, tickets)"
  - "Après: Infrastructure décrite dans du code (versionnée, testable, reproductible)"
  - "Approche déclarative: 'Je veux 3 serveurs avec ces specs' (pas 'Clique ici, tape ceci')"
- Visual: Side-by-side comparison - manual process (messy flowchart) vs IaC (clean Git repo)
- Time: 4 min

**Slide 30:** IaC - Tools & GitOps
- Title: "Outils IaC & GitOps"
- Content:
  - **Terraform**: Multi-cloud, large écosystème
  - **Ansible**: Configuration management
  - **CloudFormation / ARM**: Cloud-specific
  - **GitOps**: Git = source de vérité pour l'infrastructure
- Visual: Logos of Terraform, Ansible + simple GitOps flow (Git push → CI/CD → Infrastructure change)
- Speaker notes: GitOps extends IaC - desired state in Git, automated reconciliation
- Time: 5 min

**Slide 31:** Quiz 2 - Docker & IaC
- Title: "Récapitulatif interactif 2: Conteneurs & IaC"
- **Q1:** Docker résout principalement quel problème?
  - A) Différences entre environnements dev/prod ✓
  - B) Sécurité des applications
  - C) Monitoring en temps réel
- **Q2:** Infrastructure as Code permet de...
  - A) Écrire du code applicatif plus rapidement
  - B) Versionner et reproduire l'infrastructure ✓
  - C) Réduire automatiquement les coûts cloud
- **Q3:** GitOps signifie...
  - A) Utiliser Git pour le code seulement
  - B) Git comme source de vérité pour l'infrastructure ✓
  - C) Déployer uniquement via GitHub Actions
- Time: 5 min

#### 4.3: DORA Metrics (8 min, 2 slides)

**Slide 32:** DORA - Introduction
- Title: "Métriques DORA"
- Content:
  - "Rappel: Measurement (CALMS) - mesurer pour s'améliorer"
  - "Problème: Quoi mesurer?"
  - "DORA (DevOps Research and Assessment): 4 métriques clés identifiées par recherche empirique"
  - "Corrélation entre ces métriques et performance organisationnelle"
- Time: 3 min

**Slide 33:** DORA - Les 4 Métriques
- Title: "Les 4 Métriques DORA"
- Visual: Table with 4 metrics

| Métrique | Définition | Que mesure-t-elle? |
|----------|------------|-------------------|
| **Deployment Frequency** | Fréquence de déploiement en prod | Vélocité (delivery speed) |
| **Lead Time for Changes** | Temps entre commit et déploiement | Vélocité (delivery speed) |
| **Change Failure Rate** | % de déploiements causant incident | Stabilité (quality) |
| **Time to Restore Service** | Temps pour restaurer après incident | Stabilité (recovery) |

- Content:
  - "Équipes performantes: déploiements multiples/jour, lead time < 1h, CFR < 15%, MTTR < 1h"
  - "Lien direct avec CALMS Measurement"
- Time: 5 min

#### 4.4: SRE & Observability (12 min, 3 slides)

**Slide 34:** SRE - Concept
- Title: "Site Reliability Engineering (SRE)"
- Content:
  - "Rappel: Measurement + Share (CALMS)"
  - "SRE = Appliquer un mindset Dev aux tâches Ops"
  - "Née chez Google (livre 'Site Reliability Engineering', 2016)"
  - "Principes: Automatiser les tâches opérationnelles, mesurer la fiabilité, partager la responsabilité"
  - "SRE et DevOps sont complémentaires (SRE = implémentation de DevOps axée fiabilité)"
- Time: 4 min

**Slide 35:** SRE - SLI/SLO/SLA
- Title: "SLI, SLO, SLA"
- Visual: Pyramid diagram (SLI at base → SLO middle → SLA top)

```
        SLA (Service Level Agreement)
          Contrat avec client externe
               ↑ basé sur ↑
        SLO (Service Level Objective)
          Objectif interne de fiabilité
               ↑ basé sur ↑
        SLI (Service Level Indicator)
          Métrique mesurable (ex: latence, dispo)
```

- Content:
  - **SLI**: "Qu'est-ce qu'on mesure?" (ex: 99.9% de disponibilité, latence p95 < 200ms)
  - **SLO**: "Quel objectif?" (ex: 99.95% dispo mensuelle)
  - **SLA**: "Qu'arrive-t-il si on rate?" (pénalités contractuelles)
  - **Error budget**: Marge entre 100% et SLO (si SLO = 99.9%, budget = 0.1% downtime)
- Time: 5 min

**Slide 36:** Observability
- Title: "Observabilité"
- Content:
  - "Monitoring classique: 'Le service est-il up?'"
  - "Observabilité: 'Pourquoi le service est lent pour ce cas edge?'"
  - "3 piliers de l'observabilité:"
    - **Logs**: Événements discrets (errors, warnings, info)
    - **Metrics**: Valeurs numériques dans le temps (CPU, latency, request rate)
    - **Traces**: Parcours d'une requête à travers services distribués
  - "Outils: Prometheus (metrics), ELK/Loki (logs), Jaeger/Tempo (traces)"
- Visual: Diagram showing 3 pillars feeding into observability platform
- Time: 3 min

**Slide 37:** Quiz 3 - DORA & SRE
- Title: "Récapitulatif interactif 3: Métriques & Fiabilité"
- **Q1:** Quelle métrique DORA mesure la stabilité?
  - A) Deployment Frequency
  - B) Lead Time for Changes
  - C) Change Failure Rate ✓
  - D) Time to Restore Service ✓ (accept both C and D)
- **Q2:** Un SLO définit...
  - A) Le niveau de service attendu en interne ✓
  - B) Le salaire d'un ingénieur Ops
  - C) Un type de fichier de logs
- **Q3:** Les 3 piliers de l'observabilité sont...
  - A) Logs, Metrics, Traces ✓
  - B) CPU, RAM, Disque
  - C) Dev, Ops, QA
- Time: 5 min

**Total Section 4 time:** 3 slides intro + 10 min Docker + 10 min IaC + 5 min Quiz 2 + 8 min DORA + 12 min SRE + 5 min Quiz 3 = **53 min**

**ADJUSTMENT NEEDED:** This is too long (53 min vs 35 min target). Need to compress.

**Revised timing:**
- Docker: 8 min (2 slides instead of 3 - merge ecosystem into concept slide)
- IaC: 8 min (2 slides instead of 3 - merge tools into concept slide)
- Quiz 2: 4 min
- DORA: 6 min (2 slides)
- SRE: 8 min (2 slides - merge SLI/SLO/SLA into SRE concept, brief observability mention)
- Quiz 3: 4 min
- **Total: 38 min** (close to 35 min target, 3 min buffer acceptable)

**Revised Section 4 structure:**

**Slides 26-27:** Docker (8 min, 2 slides)
- Slide 26: Section intro "Pratiques DevOps Modernes" (1 min)
- Slide 27: Docker concept + ecosystem combined (7 min)
  - Top half: What problem does it solve? (consistency)
  - Bottom half: Images, registries, orchestration overview

**Slides 28-29:** IaC (8 min, 2 slides)
- Slide 28: IaC concept (4 min) - declarative infrastructure
- Slide 29: IaC tools + GitOps (4 min) - Terraform, Ansible, GitOps flow

**Slide 30:** Quiz 2 (4 min)

**Slides 31-32:** DORA (6 min, 2 slides)
- Slide 31: DORA introduction (2 min) - why metrics matter
- Slide 32: 4 metrics table (4 min)

**Slides 33-34:** SRE & Observability (8 min, 2 slides)
- Slide 33: SRE concept + SLI/SLO/SLA (5 min)
- Slide 34: Observability 3 pillars (3 min)

**Slide 35:** Quiz 3 (4 min)

**Total Modern Practices:** 1 + 7 + 4 + 4 + 4 + 2 + 4 + 5 + 3 + 4 = **38 min**

---

### Section 5: Tools & Best Practices (10 min, slides 36-39)

**Goal:** Ground conceptual knowledge in concrete ecosystem.

**Current structure:**
- Section slide: "Les outils"
- CNCF landscape iframe
- Pipeline orchestration tools (Jenkins, GitLab, GitHub)
- Other tools (brief list)
- Section slide: "Les bonnes pratiques"
- Reminder about internet examples
- Best practices list (security, reliability, exploitability, maintainability, industrialization)

**Recommendation:** Slight reorganization to improve flow after Modern Practices

**Slide 36:** Section slide "Outils & Bonnes Pratiques" (1 min)

**Slide 37:** CNCF Landscape (2 min)
- Keep iframe - visual impact, shows ecosystem breadth

**Slide 38:** Pipeline Orchestration + Expanded Tooling (4 min)
- Keep Jenkins/GitLab/GitHub logos
- Add brief mentions tying back to Modern Practices:
  - "Registries: Docker Hub, GitHub Container Registry"
  - "IaC: Terraform, Ansible"
  - "Observability: Prometheus, Grafana, ELK"
- Don't expand too much - just contextualizing the ecosystem

**Slide 39:** Best Practices (3 min)
- Keep existing slide with security, reliability, exploitability, maintainability
- Add one bullet: "Mesurer avec DORA metrics" (callback to Modern Practices)

**Total Section 5:** 10 min

---

### Section 6: Closure (10 min, slides 40-43)

**Goal:** Provide resources for continued learning and demonstrate DevOps in action.

**Current structure:**
- Section slide: "La veille technologique"
- Sites de veille (various French tech news sources)
- Section slide: "Démonstration d'un pipeline de CI/CD"
- Final slide: "Merci" with QR codes

**Recommendation:** Keep structure, strengthen transitions

**Slide 40:** Section slide "Veille Technologique" (1 min)

**Slide 41:** Sites de veille (3 min)
- Keep current list
- Add framing: "Le DevOps évolue rapidement. Voici comment rester à jour."

**Slide 42:** Demo intro (1 min)
- Section slide: "Démonstration: Voir un pipeline en action"

**Slide 43:** Live demo (4 min)
- Navigate to GitLab pipeline (current plan: gitlab.com/gitlab-org/gitlab/-/pipelines/)
- Show pipeline stages, logs, artifacts
- Tie back: "Vous voyez ici: automatisation (CI/CD), mesure (pipeline metrics), partage (pipeline visible à tous)"

**Slide 44:** Merci + QR codes (1 min)
- Keep current slide
- Add verbal CTA: "Continuez à apprendre, expérimentez dans vos projets, et n'oubliez pas: DevOps est une culture, pas un titre de poste."

**Total Section 6:** 10 min

---

## Final Time Budget Validation

| Section | Slides | Time |
|---------|--------|------|
| 1. Hook & Intro | 1-3 | 5 min |
| 2. Foundation | 4-9 | 10 min |
| 3. Core Concepts + Quiz 1 | 10-25 | 35 min |
| 4. Modern Practices + Quiz 2 + Quiz 3 | 26-35 | 38 min |
| 5. Tools & Best Practices | 36-39 | 10 min |
| 6. Closure | 40-44 | 10 min |
| **Total** | **~44 slides** | **108 min** |

**Problem:** This exceeds 90 min by 18 min.

**Adjustment needed:** Trim 18 minutes across sections.

**Revised allocation:**

| Section | Adjusted Time | Cut From |
|---------|---------------|----------|
| 1. Hook & Intro | 4 min (-1) | Brief bio, less Q&A |
| 2. Foundation | 8 min (-2) | Tighten history slides |
| 3. Core Concepts + Quiz 1 | 30 min (-5) | 15 min CALMS (not 20), 4 min Quiz 1, 4 min feedback loop, 4 min DoD, 3 min Agile note |
| 4. Modern Practices + Quizzes | 33 min (-5) | Docker 7 min, IaC 7 min, Quiz 2: 3 min, DORA 5 min, SRE 7 min, Quiz 3: 4 min |
| 5. Tools & Best Practices | 8 min (-2) | 1 min CNCF, 3 min tools, 2 min best practices |
| 6. Closure | 9 min (-1) | 2 min veille, 5 min demo, 1 min merci |
| **Total** | **92 min** | Within 90 min + 2 min buffer |

**Final validated timing:**

```
[4 min] Hook
[8 min] Foundation
[30 min] Core Concepts (incl 4 min Quiz 1)
[33 min] Modern Practices (incl 3+4 min Quizzes 2&3)
[8 min] Tools & Best Practices
[9 min] Closure
────────
92 min total (within 90 min target with 2 min flex for transitions)
```

## Integration Strategy: Where to Insert New Content

### Current slides.md structure analysis:

Based on the existing slides.md, the current structure has:
- Slides 1-3: Intro (title, bio, "C'est quoi DevOps")
- Slides 4-9: History and Why DevOps (6 slides)
- Slides 10-25: CALMS principles (section + 5 principles + Agile note = 8 slides), Feedback loop (section + diagram + DoD = 3 slides)
- Slides 26-30: Tools (section + CNCF iframe + orchestration + other tools = 4 slides)
- Slides 31-35: Best practices (section + reminder + practices + veille section + sites = 5 slides)
- Slides 36-37: Demo (section + demo instructions = 2 slides)
- Slide 38: Merci

**Total existing:** ~38 slides

### Insertion points:

**After slide 25 (DoD), BEFORE slide 26 (Tools section):**

**INSERT:**
- **Quiz 1** (1 slide) - Tests CALMS understanding
- **Modern Practices section slide** (1 slide)
- **Docker** (2 slides: concept+ecosystem)
- **IaC** (2 slides: concept, tools+GitOps)
- **Quiz 2** (1 slide) - Tests Docker+IaC understanding
- **DORA** (2 slides: intro, 4 metrics)
- **SRE & Observability** (2 slides: SRE+SLI/SLO/SLA, Observability)
- **Quiz 3** (1 slide) - Tests DORA+SRE understanding

**Total insertions:** 12 slides

**New total slide count:** ~50 slides (38 existing + 12 new)

**Slide numbering after insertion:**
- Slides 1-25: Unchanged (Intro → Foundation → CALMS → Feedback loop)
- **Slides 26-37: NEW CONTENT** (Quiz 1 + Modern Practices + 2 more quizzes)
- Slides 38-41: Tools (renumbered from old 26-30)
- Slides 42-46: Best practices (renumbered from old 31-35)
- Slides 47-48: Demo (renumbered from old 36-37)
- Slide 49-50: Merci (renumbered from old 38)

## Quiz Implementation Details

### Quiz Format in Slidev

Since Slidev supports interactive components, quizzes can be implemented as:

**Option A: Simple v-click reveals (lightweight)**
```markdown
---
layout: default
---

# Récapitulatif interactif 1: Les Principes

<v-clicks>

**Q1:** Quel est le principe fondamental sans lequel les autres échouent?

- A) Automation
- B) Culture ✓
- C) Measurement
- D) Share

</v-clicks>

<v-click>

**Réponse:** B - La Culture est la fondation. Sans elle, les autres principes échouent.

</v-click>
```

**Option B: Custom Vue component (if time permits)**
- Create `components/Quiz.vue` with interactive MCQ
- Track answers, reveal correct answer on click
- More polished but requires dev time

**Recommendation:** Use Option A (v-click) for MVP. Simple, works with existing Slidev setup, no additional development needed.

### Quiz Timing Strategy

Each quiz should follow this pattern:
1. **Present question** (30 sec) - read aloud, let students think
2. **Poll audience** (30 sec) - "Qui a choisi A? B? C? D?" (hand raise or verbal)
3. **Reveal answer** (1 min) - click to show correct answer, explain why
4. **Repeat for 3-4 questions** (3-4 min total)

**Total per quiz:** 4-5 minutes including transitions

## Sources

**Pedagogical Principles:**
- **Cognitive Load Theory** (Sweller): Chunking, working memory limits
- **Testing Effect** (Roediger & Karpicke): Retrieval practice strengthens retention
- **Subsumption Theory** (Ausubel): Scaffolding new knowledge on existing schema
- **Primacy/Recency Effect**: Attention patterns in presentations
- **Formative Assessment** (Black & Wiliam): Quizzes as learning tools, not evaluation

**Instructional Design:**
- **90-minute session structure**: Common university lecture format
- **Attention management**: 15-min peak, 20-30 min decline, recovery via interactivity
- **Theory-practice oscillation**: Concrete examples anchor abstract concepts

**DevOps Education:**
- Industry practice: DevOps training typically covers principles → tools → practices
- DORA State of DevOps reports: Metrics research validating measurement approach
- SRE Book (Google): SLI/SLO/SLA framework

**Confidence Level:** MEDIUM
- Pedagogical principles are well-established (HIGH confidence)
- Application to this specific 90-min DevOps course is researcher's synthesis (MEDIUM confidence)
- Timing estimates based on typical presentation pacing (MEDIUM confidence)
- Quiz content not pilot-tested with M1 MIAGE students (LOW confidence, should be validated)

## Notes for Roadmap Creation

**Key recommendations for phase structure:**

1. **Phase 1: Content cleanup** (technical debt)
   - Fix typos, CSS refactoring, URL corrections
   - Low risk, high value - clean foundation

2. **Phase 2: Quiz creation** (3 quizzes)
   - Can be developed independently
   - Test with sample questions before finalizing
   - Consider peer review with another instructor

3. **Phase 3: Modern Practices slides** (12 slides total)
   - Docker → IaC → DORA → SRE (in that order)
   - Each sub-topic scaffolds on CALMS
   - Visual diagrams needed (Docker flow, GitOps, DORA table, SLI/SLO/SLA pyramid, Observability pillars)

4. **Phase 4: Integration & timing**
   - Insert new content after slide 25
   - Renumber existing slides
   - Test full presentation timing (dry run)

5. **Phase 5: Polish**
   - Strengthen transitions between sections
   - Add verbal bridges referencing CALMS in new sections
   - Update demo section if needed

**Dependencies:**
- Quizzes depend on content being finalized (can't write Quiz 2 until Docker/IaC slides exist)
- Integration phase depends on all new slides being created
- Timing validation requires full deck to exist

**Risk areas:**
- **Timing accuracy:** Estimates based on typical pacing, but presenter's style affects actual duration. Recommend dry run.
- **Audience engagement:** M1 students' DevOps knowledge varies. Quizzes may be too easy or too hard. Consider pilot testing questions.
- **Technical depth:** Balance between "introductory" and "useful" is subjective. Some students may want more detail (IaC syntax), others may find DORA metrics too abstract. Stick to conceptual level.
