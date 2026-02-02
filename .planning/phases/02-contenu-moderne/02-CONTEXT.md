# Phase 2: Contenu moderne - Context

**Gathered:** 2026-02-02
**Status:** Ready for planning

<domain>
## Phase Boundary

Ajouter 4 nouvelles sections de contenu (Docker/Conteneurs, IaC/GitOps, Metriques DORA, SRE/Observabilite) et etoffer la section Outils existante. Ces sections ajoutent ~30-35 minutes de contenu pedagogique a la presentation Slidev destinee a des M1 MIAGE. Le scope est le contenu des slides uniquement -- les quizz et la structure narrative sont des phases separees.

</domain>

<decisions>
## Implementation Decisions

### Niveau de profondeur
- Approche coherente sur les 4 sections : conceptuel + schema (diagramme visuel)
- Pas de syntaxe ni de commandes techniques dans les slides
- Chaque section explique le probleme, la solution, et l'impact DevOps
- Section Outils : une slide par categorie d'outils (pas un tableau dense)

### Style pedagogique
- Ton conversationnel, phrases directes et courtes
- Densite moderee : bullet points avec phrases courtes completes (l'etudiant peut relire et comprendre sans le presentateur)
- Schemas en Mermaid integres dans Slidev (maintenables, pas d'images externes)
- v-click modere : revelation progressive sur les slides conceptuelles, pas sur les schemas ou listes de reference

### Exemples et cas concrets
- Docker : scenario avant/apres generique ("sans conteneurs" vs "avec conteneurs"), universel et pas date
- DORA : scenario narratif -- raconter l'histoire d'une equipe qui ameliore ses metriques, avec consequences concretes avant/apres
- SRE/SLI/SLO/SLA : double approche -- analogie du quotidien pour introduire le concept + exemple tech accessible (service qu'ils connaissent) pour ancrer dans le DevOps
- Outils : mentionner les leaders du marche (Docker Hub, Terraform, Prometheus/Grafana, ArgoCD) -- ce qu'ils verront en entreprise

### Claude's Discretion
- Choix exact des diagrammes Mermaid (type de diagramme, niveau de detail)
- Placement precis des slides dans la presentation (ordre au sein de chaque section)
- Formulation exacte des titres de slides
- Analogie specifique pour SRE (tant qu'elle est du quotidien et accessible)

</decisions>

<specifics>
## Specific Ideas

- Les schemas doivent etre en Mermaid (pas d'images externes) pour rester maintenables dans Slidev
- Le ton doit rester conversationnel comme si on expliquait a un collegue, pas academique
- Pour DORA, l'approche narrative (histoire d'une equipe) est preferee aux tableaux comparatifs de chiffres
- Pour SRE, toujours commencer par l'analogie avant l'exemple technique

</specifics>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 02-contenu-moderne*
*Context gathered: 2026-02-02*
