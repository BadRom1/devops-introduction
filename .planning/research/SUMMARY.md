# Research Summary: DevOps Introduction Course Content

**Domain:** Educational presentation - DevOps fundamentals for M1 MIAGE students
**Researched:** 2026-02-02
**Overall confidence:** MEDIUM

## Executive Summary

Research focused on identifying what topics a modern DevOps introduction course must cover in 2026, with specific attention to four missing topics: Docker/containers, Infrastructure as Code (IaC), DORA metrics, and SRE/Observability.

**Current state:** The existing presentation (~50 min) provides excellent coverage of DevOps history, culture (CALMS principles), CI/CD concepts, and best practices. This foundation is strong and should be preserved.

**Gap analysis:** Four critical "table stakes" topics are missing that would be expected in any 2026 DevOps introduction:
1. **Docker & Containers** - Now industry standard, essential for understanding modern deployment
2. **Infrastructure as Code** - Fundamental automation practice, natural CI/CD extension
3. **DORA Metrics** - Industry-standard performance measurement framework
4. **SRE & Observability** - Modern approach to operations and system reliability

**Pedagogical approach:** All new content must remain at conceptual "survol" level - no syntax, no detailed commands. Each topic covered in 2-3 slides maximum with visual diagrams. Focus on "why" and "what" rather than "how to implement."

**Time allocation:** Adding these four topics (2-3 slides each, ~8 min per topic) plus brief career paths overview would add approximately 32-40 minutes, bringing the presentation from ~50 minutes to the target ~90 minutes.

## Key Findings

**Table Stakes for 2026:**
- Containers/Docker are non-negotiable - industry moved here
- IaC has become standard practice (no longer "advanced")
- DORA metrics are professional standard for DevOps measurement
- Basic observability concepts are expected foundation
- Security (DevSecOps) should be emphasized more strongly

**Differentiators:**
- GitOps as modern deployment pattern (natural IaC extension)
- SRE principles provide complementary industry perspective
- Real-world SNCF examples leverage instructor's credibility
- Career paths clarity helps student decision-making
- French community resources provide local value

**Critical Anti-Features:**
- Detailed tool syntax/commands (not conceptual, outdated quickly)
- Kubernetes deep dive (too complex without container foundation)
- Tool comparison debates (creates confusion)
- Legacy practice coverage (focus on 2026 reality)

## Implications for Content Development

### Recommended Content Structure

**Preserve existing strong content:**
- History & Culture (CALMS) - Well explained
- Dev vs Ops conflict - Good context
- CI/CD feedback loop - Core concept
- Best practices - Important reminders

**Add missing table stakes (priority order):**

1. **After CI/CD section, add Docker/Containers (3 slides)**
   - Problem: "Works on my machine"
   - Solution: Containers package app + dependencies
   - Impact: Consistent environments, enables cloud-native

2. **After Docker, add IaC & GitOps (3 slides)**
   - Problem: Manual infrastructure setup
   - Solution: Infrastructure as declarative code
   - Evolution: GitOps as deployment methodology

3. **Within Measurement section, add DORA Metrics (2 slides)**
   - Why measure: Objective performance tracking
   - Four metrics: Deployment Frequency, Lead Time, Failure Rate, Recovery Time
   - Fits naturally with existing "Mesure" principle

4. **After Best Practices, add SRE & Observability (3 slides)**
   - SRE: Engineering approach to operations
   - Error budgets balance speed/stability
   - Observability: Metrics, Logs, Traces

**Optional enhancement:**
5. **Career Paths (1 slide)** - Dev, Ops, SRE, Platform Engineer, DevSecOps distinctions

### Content Dependencies Flow

```
1. Culture & History (existing - strong)
   ↓
2. CALMS Principles (existing - strong)
   ↓
3. CI/CD Feedback Loop (existing - strong)
   ↓
4. [NEW] Docker & Containers (enables automation)
   ↓
5. [NEW] IaC & GitOps (infrastructure automation)
   ↓
6. Tools Overview (existing - good)
   ↓
7. [NEW] DORA Metrics (measurement framework)
   ↓
8. Best Practices (existing - important)
   ↓
9. [NEW] SRE & Observability (modern operations)
   ↓
10. [OPTIONAL] Career Paths & Resources
```

This structure maintains logical progression:
- Why DevOps exists → How DevOps works → What enables it → How to measure it → How to sustain it

## Confidence Assessment

| Area | Confidence | Notes |
|------|------------|-------|
| Docker/Containers concepts | HIGH | Mature, stable concepts from training |
| IaC fundamentals | HIGH | Well-established practices |
| GitOps concepts | MEDIUM | Definitions evolving 2019-2026, may need verification |
| DORA metrics framework | MEDIUM | Core framework stable, specific thresholds may have updated |
| SRE principles | MEDIUM | Google's public content well-known, details may have evolved |
| Observability pillars | HIGH | Three pillars model is standard |
| Current tool landscape | LOW | Changes rapidly, would benefit from verification |
| French local resources | LOW | Temporal/geographic information, needs local validation |

## Research Limitations & Gaps

**Tool Access Issues:**
- WebSearch was blocked during research session
- WebFetch was blocked during research session
- Could not verify current official documentation (DORA.dev, SRE.google, Docker docs)

**Impact:**
- Research based entirely on training knowledge (cutoff: January 2025)
- Could not verify 2025-2026 updates to frameworks
- Could not check current educational best practices
- Local/temporal information (French DevOps community) not validated

**Mitigation:**
- All findings clearly marked with confidence levels
- Recommendations include verification steps for instructor
- Focused on stable, foundational concepts over trends
- Honest about what couldn't be verified

## Recommended Next Steps

### For Content Development:

1. **Priority 1: Docker/Containers section**
   - 3 slides: Problem → Solution → DevOps Impact
   - Visual: VM vs Container diagram
   - No syntax, pure concepts

2. **Priority 2: IaC & GitOps section**
   - 3 slides: Traditional → IaC → GitOps evolution
   - Visual: Code → Git → Automated deployment
   - Connects to existing CI/CD content

3. **Priority 3: DORA Metrics section**
   - 2 slides: Framework → Four Metrics
   - Visual: Performance tiers (Elite/High/Med/Low)
   - Extends existing "Mesure" principle

4. **Priority 4: SRE & Observability section**
   - 3 slides: SRE → Error Budgets → Observability Pillars
   - Visual: Three pillars diagram
   - Modern evolution of Ops

### Before Presenting:

**Verification tasks:**
- [ ] Check DORA.dev for latest metric thresholds (2025 report)
- [ ] Review Google SRE book for any recent updates
- [ ] Verify Docker conceptual model hasn't changed
- [ ] Research current Grenoble DevOps community resources
- [ ] Confirm M1 MIAGE student prerequisite knowledge

**Optional improvements:**
- [ ] Add brief career paths slide (Dev/Ops/SRE/Platform/DevSecOps)
- [ ] Include recent SNCF DevOps example (if shareable)
- [ ] Add link to local Grenoble DevOps community resources
- [ ] Consider 1-2 min "hands-on" demo (optional, if time permits)

## Open Questions

**For instructor to determine:**
1. Should GitOps be included or is IaC sufficient for intro level?
   - Recommendation: Include it (1 slide) - shows evolution, highly relevant 2026
2. Should Platform Engineering be mentioned?
   - Recommendation: Brief mention in career paths, not dedicated section
3. How technical can container concepts get?
   - Recommendation: Stay conceptual - isolation, portability, consistency
4. Should security (DevSecOps) get dedicated section?
   - Recommendation: Strengthen existing mentions, not separate section (security is woven throughout)

**For validation:**
1. What are the current DORA elite performer thresholds? (check 2025 report)
2. Has observability model evolved beyond three pillars? (check current content)
3. What is current state of GitOps terminology standardization?
4. What local resources exist in Grenoble DevOps community?

## Ready for Content Development

Research provides:
- ✓ Clear categorization: table stakes vs differentiators vs anti-features
- ✓ Specific topics with slide-by-slide breakdown
- ✓ Key concepts to cover (3-5 per topic)
- ✓ Logical content flow and dependencies
- ✓ Pedagogical considerations for M1 MIAGE audience
- ✓ Time allocation to reach 90-minute target
- ✓ Anti-patterns to avoid in teaching
- ✓ Honest confidence levels and verification needs

**Confidence for proceeding:** MEDIUM-HIGH
- Core recommendations are sound and based on stable concepts
- Specific details (metric thresholds, tool names) should be verified before presenting
- Overall structure and approach is appropriate for target audience
- Content expansion aligns with 2026 industry expectations
