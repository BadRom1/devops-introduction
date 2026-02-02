# Requirements: Amelioration Presentation DevOps

**Defined:** 2026-02-02
**Core Value:** Les etudiants repartent avec une vision claire et complete du DevOps : culture, principes, pratiques modernes et outils.

## v1 Requirements

Requirements pour la version amelioree de la presentation. Chaque requirement correspond a une phase du roadmap.

### Dette technique (DEBT)

- [x] **DEBT-01**: Corriger les coquilles dans le texte (apportes->apporter, vide, conference->conferences, resume->resumes, pose->poses)
- [x] **DEBT-02**: Factoriser le CSS CALMS duplique 5 fois (~60 lignes chaque) en un seul bloc global (style.css ou composant Vue)
- [x] **DEBT-03**: Corriger l'URL incoherente dans les QR codes (badrom1 vs badroro)
- [x] **DEBT-04**: Corriger les balises HTML mal formees (</img> inutiles)

### Contenu moderne (CONT)

- [ ] **CONT-01**: Ajouter une section Conteneurs & Docker (2-3 slides, survol conceptuel : pourquoi les conteneurs, images, registries, orchestration en un mot)
- [ ] **CONT-02**: Ajouter une section IaC & GitOps (2-3 slides, survol : Infrastructure as Code, approche declarative, GitOps)
- [ ] **CONT-03**: Ajouter une section Metriques DORA (1-2 slides : les 4 metriques cles, lien avec le principe Measurement de CALMS)
- [ ] **CONT-04**: Ajouter une section SRE & Observabilite (2-3 slides, survol : SRE, SLI/SLO/SLA, monitoring/logs/traces)
- [ ] **CONT-05**: Etoffer la section Outils existante (au-dela des 3 logos, mentionner les categories : registries, IaC, observabilite)

### Interactivite (QUIZ)

- [ ] **QUIZ-01**: Ajouter des quizz entre les sections principales (questions a choix multiples pour verifier la comprehension, 3 quizz places strategiquement)

### Structure narrative (NARR)

- [ ] **NARR-01**: Ameliorer la structure narrative (transitions entre sections, recapitulatif avant la fin, fil rouge CALMS tout au long)

## v2 Requirements

Differes pour une version future. Non inclus dans le roadmap actuel.

### Ameliorations optionnelles

- **OPT-01**: Ajouter un slide parcours de carriere DevOps (Dev, Ops, SRE, Platform Engineer, DevSecOps)
- **OPT-02**: Ajouter des exemples SNCF concrets si partageables
- **OPT-03**: Ajouter des ressources communaute DevOps Grenoble
- **OPT-04**: Creer un composant Vue Quiz.vue interactif (au lieu de v-click simple)
- **OPT-05**: Mettre a jour vers une version stable de Slidev (hors beta)

## Out of Scope

| Feature | Raison |
|---------|--------|
| Syntaxe detaillee / commandes (Dockerfile, terraform plan) | Cours d'introduction, pas un TP |
| Exercices pratiques / hands-on | Pas le format du cours magistral |
| Refonte du theme Slidev | Le theme actuel est fonctionnel |
| Decoupage en plusieurs seances | Le cours reste sur 1h30 |
| Etudes de cas detaillees | Pas le temps dans le format |
| Deep dive Kubernetes | Trop complexe sans fondation conteneurs |
| Comparaisons d'outils detaillees | Cree de la confusion, se perime vite |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| DEBT-01 | Phase 1 | Complete |
| DEBT-02 | Phase 1 | Complete |
| DEBT-03 | Phase 1 | Complete |
| DEBT-04 | Phase 1 | Complete |
| CONT-01 | Phase 2 | Pending |
| CONT-02 | Phase 2 | Pending |
| CONT-03 | Phase 2 | Pending |
| CONT-04 | Phase 2 | Pending |
| CONT-05 | Phase 2 | Pending |
| QUIZ-01 | Phase 3 | Pending |
| NARR-01 | Phase 4 | Pending |

**Coverage:**
- v1 requirements: 11 total
- Mapped to phases: 11
- Unmapped: 0

---
*Requirements defined: 2026-02-02*
*Last updated: 2026-02-02 after roadmap creation*
