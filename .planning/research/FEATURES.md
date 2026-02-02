# Feature Landscape: DevOps Introduction Course

**Domain:** Educational presentation - DevOps fundamentals for M1 MIAGE students
**Researched:** 2026-02-02
**Confidence:** MEDIUM (based on training knowledge, web sources unavailable)

## Table Stakes

Topics that MUST be covered in a modern DevOps introduction in 2026. Missing any of these would make the course feel incomplete or outdated.

| Feature | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| DevOps History & Culture (CALMS) | Foundational understanding of "why" DevOps exists | Low | Already covered well in existing slides |
| CI/CD Pipeline Concepts | Core automation pattern, universal expectation | Medium | Already covered, could expand with modern practices |
| Docker & Containers Basics | Industry standard, essential for modern development | Medium | **MISSING** - Critical gap for 2026 |
| Infrastructure as Code (IaC) Concepts | Treating infrastructure like code is now standard practice | Medium | **MISSING** - Table stakes in 2026 |
| Version Control (Git) Integration | Foundation of DevOps automation | Low | Implied in current content, could be explicit |
| Cloud-Native Concepts | Most organizations run on cloud infrastructure | Medium | Partially covered via tools, needs dedicated section |
| DORA Metrics Overview | Industry-standard performance measurement | Low | **MISSING** - Professional standard for measurement |
| Basic Observability Concepts | Monitoring, logging, alerting fundamentals | Medium | Tool mentions exist, conceptual coverage needed |
| Security in DevOps (DevSecOps) | Security cannot be afterthought anymore | Medium | Brief mention exists, could strengthen |
| Collaboration & Communication | Core cultural aspect of DevOps | Low | Well covered in CALMS principles |

## Differentiators

Topics that would make this course stand out and provide exceptional value to students. Not expected, but highly valuable.

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| GitOps Concepts | Modern deployment pattern gaining rapid adoption | Medium | Natural extension of IaC + Git |
| SRE Principles | Google's approach to reliability, complements DevOps | Medium | Adds industry perspective beyond pure DevOps |
| Platform Engineering Introduction | Emerging discipline (2023-2026), future career path | Medium | Shows where industry is heading |
| FinOps Awareness | Cost optimization in cloud, increasingly important | Low | Brief mention would differentiate |
| Chaos Engineering Concepts | Proactive resilience testing, cutting edge | High | Too complex for intro, but cool to mention |
| Real-world Case Studies | SNCF or French company examples | Low | Instructor's strength - use personal experience |
| Career Paths in DevOps Ecosystem | Dev, Ops, SRE, Platform Engineer, DevSecOps distinctions | Low | Helps students understand options |
| French DevOps Community Resources | Local meetups, conferences, communities | Low | Practical value for students in Grenoble region |

## Anti-Features

Topics to explicitly NOT include or de-emphasize at introductory level. Common mistakes in DevOps education.

| Anti-Feature | Why Avoid | What to Do Instead |
|--------------|-----------|-------------------|
| Detailed tool syntax/commands | Overwhelming, tools change rapidly, not conceptual | Show concepts with visual diagrams, mention tools by name only |
| Deep Kubernetes dive | Too complex for intro, assumes container knowledge | Brief mention as orchestration evolution, focus on "why orchestrate" |
| Detailed pipeline YAML | Implementation detail, distracts from concepts | Show pipeline stages visually, explain flow not syntax |
| Tool comparisons/debates | Creates confusion, becomes outdated quickly | Focus on categories (CI/CD, IaC, monitoring) not specific tools |
| Production incident war stories | Can be scary/discouraging for beginners | Keep examples positive or neutral, focus on learning |
| Microservices architecture deep dive | Architectural pattern beyond DevOps scope | Mention as deployment pattern, don't explain implementation |
| Detailed security scanning tools | Too specialized for intro course | Explain DevSecOps concept, mention scanning exists |
| Performance optimization details | Advanced topic requiring deep expertise | Cover "why measure" (DORA) not "how to optimize" |
| Legacy/deprecated practices | Confuses history with current practice | Focus on 2026 reality, brief history context only |
| Tool installation tutorials | Not conceptual, time-consuming, environment-dependent | Provide links for self-study, don't spend class time |

## Feature Dependencies

```
DevOps Culture (CALMS)
  ├─> Automation Principles
  │     ├─> CI/CD Pipeline Concepts
  │     ├─> Infrastructure as Code
  │     └─> GitOps (advanced)
  │
  ├─> Measurement Principles
  │     ├─> DORA Metrics
  │     └─> Observability Concepts
  │           └─> SRE Principles (complements)
  │
  └─> Containerization (enables automation)
        ├─> Docker Concepts
        └─> Cloud-Native Patterns

Logical flow for presentation:
1. Culture & History (why DevOps exists)
2. CI/CD Loop (the core workflow)
3. Containers (how modern apps are packaged)
4. IaC (how infrastructure is automated)
5. Measurement (DORA metrics for success)
6. Observability & SRE (how to maintain reliability)
7. Best Practices & Career Paths
```

## New Topics: Key Concepts to Cover (2-3 slides each)

### Docker & Containers (2-3 slides)

**Slide 1: Le problème des dépendances**
- "Ça marche sur ma machine" problem
- Application dependencies: OS, libraries, runtime
- Traditional deployment challenges: environment drift

**Slide 2: La solution des conteneurs**
- Container = Application + All Dependencies packaged together
- Isolation without full VM overhead
- Docker as industry standard tool
- Visual: VM vs Container diagram

**Slide 3: Impact sur le DevOps**
- Consistent environments: dev → test → prod
- Faster deployments, easier rollbacks
- Foundation for cloud-native architecture
- Enables microservices pattern

**Key Concepts:**
1. Application isolation and portability
2. Image vs Container distinction (blueprint vs running instance)
3. Lightweight compared to VMs
4. Industry standard format (OCI)
5. Enables consistent environments across lifecycle

### Infrastructure as Code (IaC) (2-3 slides)

**Slide 1: Infrastructure traditionnelle**
- Manual server setup via UI/command line
- Configuration drift over time
- "Pets vs Cattle" analogy
- Difficult to reproduce, document, version

**Slide 2: IaC - Infrastructure en tant que code**
- Infrastructure defined in text files (code)
- Version controlled like application code
- Automated provisioning and configuration
- Examples: Terraform, Ansible, CloudFormation

**Slide 3: GitOps - L'évolution de l'IaC**
- Git as single source of truth
- Declarative infrastructure: describe desired state
- Automated reconciliation (system matches git)
- Pull-based deployments
- Natural evolution: Git → CI/CD → Infrastructure

**Key Concepts:**
1. Infrastructure as declarative code (not scripts)
2. Version control for infrastructure
3. Reproducibility and disaster recovery
4. Immutable infrastructure pattern
5. GitOps as deployment methodology

### DORA Metrics (2 slides)

**Slide 1: Mesurer la performance DevOps**
- Need for objective performance measurement
- DORA = DevOps Research and Assessment
- Industry standard since 2018, backed by research
- Four key metrics framework

**Slide 2: Les 4 métriques DORA**
1. **Deployment Frequency** - How often deploy to production
   - Elite: Multiple times per day
2. **Lead Time for Changes** - Commit to production time
   - Elite: Less than one hour
3. **Change Failure Rate** - % deployments causing incidents
   - Elite: 0-15%
4. **Time to Restore Service** - Recovery time from incidents
   - Elite: Less than one hour

**Visual:** Performance levels: Elite / High / Medium / Low performers

**Key Concepts:**
1. Four metrics measure velocity AND stability
2. Used to benchmark DevOps maturity
3. Based on years of industry research
4. Links DevOps practices to business outcomes
5. Guides improvement priorities

### SRE & Observability (2-3 slides)

**Slide 1: L'évolution des Ops**
- Traditional Ops: Reactive, "keep lights on"
- SRE = Site Reliability Engineering (Google approach)
- Apply software engineering to operations
- Reliability as product feature

**Slide 2: Principes clés du SRE**
- **Error Budgets**: Balance innovation vs stability
  - 99.9% uptime = 0.1% "allowed" errors
  - Budget spent = slow down features, improve reliability
- **Toil Reduction**: Automate repetitive manual work
- **Blameless Postmortems**: Learn from incidents
- Complements DevOps culture

**Slide 3: Observabilité (Observability)**
- Beyond simple monitoring
- **Three pillars:**
  1. **Metrics**: Numbers over time (CPU, latency)
  2. **Logs**: Event records (what happened)
  3. **Traces**: Request flow through system
- Ask new questions without predefined dashboards
- Essential for distributed systems

**Key Concepts:**
1. SRE as operations engineering discipline
2. Error budgets balance speed and stability
3. Toil reduction through automation
4. Three pillars of observability
5. Proactive vs reactive operations

## Content Expansion Recommendations

### Current Presentation (~50 min) → Target (~90 min)

**Already Strong (Keep as-is):**
- History & Culture sections
- CALMS principles explanation
- Dev vs Ops conflict context
- Tools landscape overview
- Best practices section

**Expand These Sections:**
1. **Measurement section** (currently brief)
   - Add DORA metrics (2 slides) - ~5 min
   - Links to existing "Mesure" principle

2. **After CI/CD Loop section**
   - Add Docker/Containers (3 slides) - ~8 min
   - Add IaC & GitOps (3 slides) - ~8 min
   - Natural progression in automation journey

3. **After "Best Practices" section**
   - Add SRE & Observability (3 slides) - ~8 min
   - Modern evolution of Ops role

4. **Optional: Career Paths** (1 slide) - ~3 min
   - Dev, Ops, SRE, Platform Engineer, DevSecOps
   - Helps students understand job market

**Total additional content:** ~32 minutes
**With discussion/questions:** ~40 minutes
**New total:** ~90 minutes ✓

## Pedagogical Considerations

### For French M1 MIAGE Students

**Strengths to leverage:**
- Software engineering background (M1 level)
- Some exposure to Agile methodologies
- Grenoble tech ecosystem exposure

**Adjust for:**
- Limited operational experience (most are developers)
- May not have cloud experience yet
- Need concrete career path guidance
- Appreciate structured frameworks (French education style)

### Language Approach
- Technical terms: Use English terms with French explanations
  - "Error budget (budget d'erreur)"
  - "Lead time (délai de livraison)"
- Slides: French text, English technical terms in bold
- Acronyms: Keep as-is (CALMS, DORA, SRE)

### Engagement Strategy
- Use SNCF examples where relevant (instructor credibility)
- Visual diagrams over text (already well done)
- "Et vous?" questions to involve audience
- Avoid overwhelming with tool names (category focus)

## Anti-Patterns to Avoid in Teaching

### 1. The "Tools Focus" Trap
**Problem:** Spending too much time on specific tools
**Instead:** Teach concepts, mention tools as examples
**Example:** "CI/CD orchestration" (concept) with Jenkins/GitLab/GitHub Actions (examples)

### 2. The "Too Much Too Soon" Trap
**Problem:** Covering advanced topics before foundations
**Instead:** Progressive complexity: Culture → Workflow → Tools → Advanced
**Example:** Cover containers before Kubernetes, IaC before GitOps

### 3. The "Perfect World" Trap
**Problem:** Only showing ideal scenarios
**Instead:** Acknowledge real-world challenges briefly
**Example:** "Not all organizations are elite performers - that's okay, it's a journey"

### 4. The "One True Way" Trap
**Problem:** Presenting one approach as only solution
**Instead:** Acknowledge multiple valid approaches
**Example:** "GitOps is one approach to CD, push-based CD also works"

### 5. The "Jargon Overload" Trap
**Problem:** Using too many buzzwords without explanation
**Instead:** Define terms clearly first time, use consistently
**Example:** Define "artifact" before using throughout presentation

## Content Validation Checklist

For each new topic, ensure:
- [ ] Connects to CALMS principles (shows it's part of DevOps philosophy)
- [ ] Explains "why" before "what" (motivation before solution)
- [ ] Uses visual diagrams, not text walls
- [ ] No code/syntax examples (conceptual only)
- [ ] Relevant to 2026 reality (not outdated practices)
- [ ] 2-3 slides maximum per topic
- [ ] Includes real-world context
- [ ] Connects to student career interests

## Sources & Confidence Notes

**HIGH Confidence:**
- CALMS principles (well-established, verified in training data)
- Docker/Container concepts (industry standard, mature)
- CI/CD fundamentals (unchanged core concepts)
- Git workflows (stable, mature)

**MEDIUM Confidence:**
- DORA metrics specifics (from training, but web verification blocked)
- SRE principles (Google's public materials well-known, but details may have evolved)
- GitOps terminology (rapidly evolving 2019-2026, definitions may have shifted)
- Current tool landscape (changes frequently)

**LOW Confidence / Needs Validation:**
- Exact DORA metric thresholds for "Elite" performers (may have been updated 2024-2026)
- Latest Platform Engineering trends (emerging field, definitions still fluid)
- Current French DevOps community resources (local/temporal information)

**Research Limitations:**
- WebSearch and WebFetch tools were unavailable during research
- Based on training knowledge (cutoff: January 2025)
- Could not verify current DORA.dev content
- Could not check latest SRE.google content
- Could not verify current Docker documentation

**Recommendations for Instructor:**
- Verify DORA metric thresholds before presenting (check dora.dev)
- Review Google SRE resources for any 2025-2026 updates
- Validate that Docker conceptual model hasn't changed significantly
- Consider reviewing local Grenoble DevOps community for current resources

## Recommended Resources for Instructor Preparation

**Official Sources (to verify before course):**
- DORA State of DevOps Report (annual, check 2025 edition)
- Google SRE Book (free online, stable content)
- Docker Getting Started (concepts stable, verify terminology)
- CNCF Landscape (for current tool ecosystem)

**French Resources:**
- Stéphane Robert's blog (already referenced in slides)
- French DevOps community meetups/conferences
- Local Grenoble tech community resources

**Academic Context:**
- Consider syllabus learning objectives for M1 MIAGE
- Align with other courses in program
- Consider prerequisite knowledge level
