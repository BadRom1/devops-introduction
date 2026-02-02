# Roadmap: Amelioration Presentation DevOps

## Overview

La presentation "Introduction au DevOps" pour les M1 MIAGE de Grenoble doit passer de ~50 minutes a ~1h30. Le travail se decompose en quatre phases : d'abord nettoyer la dette technique pour partir sur une base saine, puis ajouter les quatre nouvelles sections de contenu moderne (Docker, IaC, DORA, SRE) et etoffer la section Outils, ensuite creer les quizz interactifs qui s'appuient sur ce contenu, et enfin polir la structure narrative pour que l'ensemble forme un cours coherent et engageant.

## Phases

**Numerotation des phases :**
- Phases entieres (1, 2, 3, 4) : Travail planifie
- Phases decimales (2.1, 2.2) : Insertions urgentes (marquees INSERTED)

Les phases decimales s'executent entre les phases entieres dans l'ordre numerique.

- [ ] **Phase 1: Nettoyage technique** - Corriger la dette technique avant d'ajouter du contenu
- [ ] **Phase 2: Contenu moderne** - Ajouter les quatre nouvelles sections et etoffer les outils
- [ ] **Phase 3: Quizz interactifs** - Ajouter les checkpoints de comprehension entre les sections
- [ ] **Phase 4: Structure narrative et finitions** - Lier le tout avec des transitions et un recapitulatif

## Phase Details

### Phase 1: Nettoyage technique
**Goal**: La presentation existante est propre, sans erreurs, et le CSS est maintenable pour accueillir du nouveau contenu
**Depends on**: Nothing (first phase)
**Requirements**: DEBT-01, DEBT-02, DEBT-03, DEBT-04
**Success Criteria** (what must be TRUE):
  1. Le texte des slides ne contient plus de fautes d'orthographe (apportes, vide, conference, resume, pose corriges)
  2. Le style CSS CALMS est defini une seule fois dans un fichier global ou un composant, et les 5 slides CALMS l'utilisent sans duplication
  3. Les QR codes de la slide finale pointent vers des URLs valides et coherentes (meme identifiant partout)
  4. Aucune balise HTML mal formee n'apparait dans slides.md (pas de </img> orphelines)
  5. La presentation se build et s'affiche correctement apres les modifications (`pnpm run build` sans erreur)
**Plans**: 2 plans

Plans:
- [ ] 01-01-PLAN.md -- Corrections texte, HTML mal forme et QR codes
- [ ] 01-02-PLAN.md -- Refactoring CSS CALMS en composant Vue CalmsBlock

### Phase 2: Contenu moderne
**Goal**: La presentation couvre les pratiques DevOps modernes essentielles (conteneurs, IaC, DORA, SRE) et la section Outils est etoffee, ajoutant ~30-35 minutes de contenu
**Depends on**: Phase 1 (CSS propre, base saine)
**Requirements**: CONT-01, CONT-02, CONT-03, CONT-04, CONT-05
**Success Criteria** (what must be TRUE):
  1. Une section Docker/Conteneurs de 2-3 slides existe apres la boucle CI/CD, expliquant le probleme ("ca marche sur ma machine"), la solution (conteneurs), et l'impact DevOps -- sans syntaxe ni commandes
  2. Une section IaC & GitOps de 2-3 slides suit Docker, couvrant l'approche declarative, le versioning d'infrastructure, et l'evolution vers GitOps
  3. Une section Metriques DORA de 1-2 slides presente les 4 metriques cles et fait le lien avec le principe Measurement de CALMS
  4. Une section SRE & Observabilite de 2-3 slides couvre les principes SRE (SLI/SLO/SLA) et les trois piliers de l'observabilite (metriques, logs, traces)
  5. La section Outils mentionne des categories au-dela de l'orchestration de pipeline (registries, IaC, observabilite) avec des exemples concrets
**Plans**: TBD

Plans:
- [ ] 02-01: Section Docker & Conteneurs
- [ ] 02-02: Section IaC & GitOps
- [ ] 02-03: Section Metriques DORA
- [ ] 02-04: Section SRE & Observabilite
- [ ] 02-05: Enrichissement section Outils

### Phase 3: Quizz interactifs
**Goal**: Les etudiants sont engages activement via des quizz qui verifient la comprehension a des points strategiques de la presentation
**Depends on**: Phase 2 (le contenu doit exister pour ecrire les questions)
**Requirements**: QUIZ-01
**Success Criteria** (what must be TRUE):
  1. Un quizz de 3-4 questions MCQ est place apres la section CALMS/boucle CI/CD, testant la comprehension des principes fondamentaux
  2. Un quizz de 2-3 questions MCQ est place apres Docker et IaC, testant la comprehension des pratiques d'automatisation
  3. Un quizz de 2-3 questions MCQ est place apres DORA et SRE, testant la comprehension de la mesure et de la fiabilite
  4. Les questions testent la comprehension conceptuelle (scenarios, "pourquoi"), pas la memorisation (definitions, noms d'outils)
  5. Les quizz utilisent v-click pour reveler les reponses progressivement et fonctionnent en mode presentation Slidev
**Plans**: TBD

Plans:
- [ ] 03-01: Quizz 1 (principes CALMS et CI/CD)
- [ ] 03-02: Quizz 2 (Docker et IaC)
- [ ] 03-03: Quizz 3 (DORA et SRE)

### Phase 4: Structure narrative et finitions
**Goal**: La presentation forme un tout coherent avec des transitions fluides entre sections et un fil rouge CALMS visible du debut a la fin
**Depends on**: Phase 3 (tout le contenu et les quizz doivent etre en place)
**Requirements**: NARR-01
**Success Criteria** (what must be TRUE):
  1. Chaque nouvelle section commence par un rappel explicite du principe CALMS qu'elle illustre (ex: "Rappel: Automation -- voyons comment Docker concretise ce principe")
  2. Des slides de transition existent entre les sections majeures, signalant ce qui vient d'etre couvert et ce qui suit
  3. Un slide recapitulatif avant la conclusion montre comment tous les sujets s'articulent autour de CALMS (schema ou liste)
  4. La presentation complete tient dans ~90 minutes (validation par relecture du nombre de slides et estimation du temps)
**Plans**: TBD

Plans:
- [ ] 04-01: Transitions et rappels CALMS
- [ ] 04-02: Recapitulatif global et validation timing

## Progress

**Ordre d'execution :**
Les phases s'executent dans l'ordre numerique : 1 -> 2 -> 3 -> 4

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Nettoyage technique | 0/2 | Not started | - |
| 2. Contenu moderne | 0/5 | Not started | - |
| 3. Quizz interactifs | 0/3 | Not started | - |
| 4. Structure narrative et finitions | 0/2 | Not started | - |
