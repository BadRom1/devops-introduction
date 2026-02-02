# Amélioration Présentation DevOps

## What This Is

Amélioration d'une présentation Slidev existante intitulée "Introduction au DevOps", destinée aux étudiants de M1 MIAGE de Grenoble. Le cours doit passer de ~50 minutes à ~1h30 en enrichissant le contenu, corrigeant la dette technique, et ajoutant de l'interactivité via des quizz.

## Core Value

Les étudiants doivent repartir avec une vision claire et complète de ce qu'est le DevOps : sa culture, ses principes, ses pratiques modernes et ses outils -- le tout en restant accessible et engageant.

## Requirements

### Validated

- ✓ Histoire et origines du DevOps (conférences, DevOpsDays, Patrick Debois) — existing
- ✓ Opposition Dev vs Ops et conflit de méthodologies — existing
- ✓ Principes CALMS (Culture, Automation, Lean, Measurement, Share) avec visuel interactif — existing
- ✓ Boucle de rétroaction CI/CD avec schéma — existing
- ✓ Definition of Done — existing
- ✓ Présentation des outils d'orchestration de pipeline (Jenkins, GitLab CI, GitHub Actions) — existing
- ✓ Bonnes pratiques (sécurité, fiabilité, exploitabilité, maintenabilité) — existing
- ✓ Veille technologique avec ressources — existing
- ✓ Slide de fin avec QR codes (slides + feedback) — existing
- ✓ Déploiement GitHub Pages avec CI/CD — existing

### Active

- [ ] Corriger les coquilles dans le texte (apportés→apporter, vidé, conférence→conférences, résumé→résumés, posé→posés)
- [ ] Factoriser le CSS CALMS dupliqué 5 fois (~60 lignes chaque) en un seul bloc global
- [ ] Corriger l'URL incohérente dans les QR codes (badrom1 vs badroro)
- [ ] Corriger les balises HTML mal formées (</img> inutiles)
- [ ] Ajouter une section Conteneurs & Docker (2-3 slides, survol conceptuel : pourquoi les conteneurs, images, registries, orchestration en un mot)
- [ ] Ajouter une section IaC & GitOps (2-3 slides, survol : Infrastructure as Code, approche déclarative, GitOps)
- [ ] Ajouter une section Métriques DORA (1-2 slides : les 4 métriques clés, lien avec le principe Measurement de CALMS)
- [ ] Ajouter une section SRE & Observabilité (2-3 slides, survol : SRE, SLI/SLO/SLA, monitoring/logs/traces)
- [ ] Ajouter des quizz entre les sections principales (questions à choix multiples pour vérifier la compréhension)
- [ ] Améliorer la structure narrative (transitions entre sections, récapitulatif avant la fin)
- [ ] Étoffer la section Outils existante (au-delà des 3 logos)

### Out of Scope

- Syntaxe détaillée ou commandes (Dockerfile, terraform plan, etc.) — c'est un cours d'introduction, pas un TP
- Exercices pratiques / hands-on — pas le format du cours
- Refonte du thème Slidev — le thème actuel est fonctionnel
- Découpage en plusieurs séances — le cours reste sur 1h30
- Études de cas détaillées — pas le temps dans le format

## Context

- **Audience :** Étudiants M1 MIAGE, Grenoble. Niveau technique varié, certains se destinent au dev, d'autres à la gestion de projet.
- **Format :** Cours magistral de 1h30, présenté en live avec Slidev.
- **Stack existante :** Slidev 0.50.0-beta.7, Vue 3, déployé sur GitHub Pages.
- **Contenu existant :** ~40 slides couvrant histoire, principes CALMS, boucle CI/CD, outils, bonnes pratiques, veille techno. Bonne base mais manque de profondeur sur les pratiques modernes.
- **Problème principal :** Le cours actuel fait ~50 min et ne couvre pas les sujets devenus incontournables (conteneurs, IaC, DORA, observabilité). Il faut combler les 40 min restantes avec du contenu pertinent et engageant.
- **Dette technique :** CSS dupliqué massivement, QR code cassé, coquilles dans le texte.

## Constraints

- **Durée** : 1h30 total, actuellement ~50 min — il faut ajouter ~40 min de contenu
- **Niveau** : Introduction / survol conceptuel — pas de syntaxe ni de commandes détaillées
- **Stack** : Slidev existant, ne pas changer de framework
- **Langue** : Tout le contenu est en français

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Survol conceptuel pour tous les nouveaux sujets | Cours d'introduction pour M1, pas un cours spécialisé | — Pending |
| Quizz comme seule forme d'interactivité | Format cours magistral, pas de TP, 1h30 seulement | — Pending |
| 2-3 slides max par nouveau sujet | Contrainte de 40 min à ajouter, 4 sujets + quizz | — Pending |

---
*Last updated: 2026-02-02 after initialization*
