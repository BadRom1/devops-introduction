---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/images/devops-titre.jpg
# some information about your slides (markdown enabled)
title: Introduction au DevOps
info: |
  Cours d'introduction au DevOps pour les étudiants de M1 MIAGE de Grenoble.

  Réalisé par Romain BADINO

  https://badroro.github.io/devops-introduction
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# take snapshot for each slide in the overview
overviewSnapshots: true
addons:
    - slidev-addon-qrcode

layout: cover
---

# Introduction au DevOps

---
transition: fade-out
---

# Qui je suis ?

<br>
<br><br>
<br>
<v-click>

-  Développeur FullStack à la SNCF
</v-click>
<br>
<v-click>


-  Reconversion professionnelle au sein de la SNCF

</v-click>
<br>
<v-click>

-  Ancien étudiant de la MIAGE de Grenoble
</v-click>

<br>
<br><br>
<br>

<v-click>
<span>Et vous qu'est ce que vous voulez faire après votre master ?</span>
</v-click>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

span {align-self: end;}

</style>

<!--
[click:4] Dev, Ops, BI, Data, PO ou Chef de projet, autres ?
-->

---
layout: statement
transition: fade-out
---

# C'est quoi le DevOps ?

<style>
h1 {
  color: #2B90B6;
}
</style>

<!--
Pour vous
Quand on parle d'un ingénieur DevOps, vous pensez à quoi ? 
On va voir si vous avez raison ou pas
-->

---
layout: section
transition: slide-up
---

# Histoire du DevOps

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: default
transition: slide-up
---

# Origine du DevOps

<br>
<br>

Le mouvement DevOps est issu d'une succession de conférences, dont les DevOpsDays, qui se sont déroulées à partir de 2008.

Contrairement à ITIL ou Agile, le DevOps n’a ni norme ni manifeste, mais repose sur une philosophie de collaboration.

Remettons tout de suite les choses en place !

<span v-mark="{at: 1, color: 'red', type: 'circle', padding: 25}">Devops n'est pas une méthode, c'est un mouvement, une culture.</span>

<style>
h1 {
  color: #2B90B6;
}
</style>

<!--
Fun fact : Andrew Shafer organisateur de la première conférence “Agile Infrastructure.” en aout 2008 à Toronto. Il n'y eut qu'une seule personne présente Patrick Debois qui est à l'origine du mot DevOps en créant les DevOpsDays.
-->

---
layout: default
transition: slide-up
---

# Origine du DevOps

Lors de ces conférences, le constat qu'ils tiraient est que le cloisonnement des équipes de développement (Dev) et des opérations (Ops) était contre-productif car leurs méthodes de travail s'opposaient.

<br>
<br>

- Cloisonnement entre équipes Dev (rapides, axées sur les fonctionnalités) et Ops (stabilité, méthodes traditionnelles).

<br>

- Mises en production complexes et fréquents incidents dus à des incompréhensions.

<br>

- Faible vélocité à cause d’une communication limitée (via tickets et demandes de services).

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: default
transition: fade-out
---

# Origine du DevOps

le DevOps tire ses racines des différentes méthodes d'organisation du travail, et des méthodes de gestion de projets Agile.

- Héritage industriel :

  - Taylorisme : Organisation stricte et répétitive, mais limitant l’innovation.
  - Toyotisme (Lean) : Optimisation continue, réduction des gaspillages, et amélioration collaborative (Kaizen).

<br>

- Influences Agile :

  - Flexibilité, itérations courtes, et collaboration étroite avec les parties prenantes.
  - Priorité aux interactions, logiciels opérationnels, et adaptation au changement.

<style>
h1 {
  color: #2B90B6;
}
</style>

<!-- Lean => Supprimé le gaspillage, Amélioration continue, PDCA (roue de Deming) 
Agilité =>- manifeste Agile ? 2001
 -->

---
layout: section
transition: slide-up
---

# Pourquoi la démarche DevOps est-elle apparue ?

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: default
transition: slide-up
---

# Opposition Dev vs Ops

Comme on a vu brièvement, les équipes Dev et Ops ont des objectifs différents.

<br>

- Les développeurs : en charge d'écrire du code, d'apporter de <span v-mark="{at: 1, color: '#60a5fa', type: 'underline', padding: 0}">nouvelles fonctionnalités</span> et de corriger des bugs. Leurs préoccupations : apporter <span v-mark="{at: 1, color: '#60a5fa', type: 'underline', padding: 0}">le plus rapidement</span> des <span v-mark="{at: 1, color: '#60a5fa', type: 'underline', padding: 0}">changements</span> pour répondre aux besoins du client.


- Les opérations : en charge de créer et de <span v-mark="{at: 2, color: '#49dd80', type: 'underline', padding: 0}">maintenir</span> les infrastructures hébergeant ces applications. Leurs préoccupations : <span v-mark="{at: 2, color: '#49dd80', type: 'underline', padding: 0}">stabiliser et garantir la disponibilité</span> de celle-ci pour répondre aux exigences du client. Dans les opérationnelles, on trouve les personnes en charge d'administrer, de sécuriser et de connecter les équipements.


<style>
h1 {
  color: #2B90B6;
}
</style>


---
layout: default
transition: fade-out
---

# Un conflit de méthodologies

À cette époque, le décalage entre les méthodes des développeurs (Dev) et des équipes d’opérations (Ops) est de plus en plus présent.  

<br>

- Les **Dev**, de plus en plus tournés vers l’Agile, cherchaient à livrer rapidement des mises à jour et de nouvelles fonctionnalités. Cette approche itérative augmentait la fréquence des mises en production.  

<br>
<br>

- De leur côté, les **Ops** restaient attachées à des méthodes en cascade. Monter et maintenir des infrastructures à cette époque était complexe, chronophage, et nécessitait des ressources importantes.

<style>
h1 {
  color: #2B90B6;
}
</style>


---
layout: section
transition: slide-up
---

# Les principes du DevOps

<style>
h1 {
  color: #2B90B6;
}
</style>

<!-- Toutes ces divergences, entre dev et ops, ont entrainées de nombre discussion lors des différentes conférences sur le sujet. Dans vos entreprises, comment ça se passe ? -->

---
layout: two-cols
transition: slide-up
---

# Apparition des principes

C'est en 2010 que les principes fondateurs du DevOps ont été posés.

Ils sont résumés par l'acronyme **CAMS**, qui signifie :
- **Culture**,
- **Automation**,
- **Measures**
- and **Share**.
  
 <br>

En 2016, cet acronyme évolue avec l’ajout du **Lean**, pour former l'acronyme **CALMS**.

::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
</style>

<!-- Attention quand je dis posé, je ne parle pas de norme ou de méthode, mais de principes qui ont été énoncés et ont commencé à faire consensus. 
-->

---
layout: two-cols
transition: slide-up
---

# Culture

Il s'agit du principe sur lequel tout repose.

Sans cette Culture, toutes les tentatives de l'adopter seront vaines.

Sans appui des dirigeants tout projet est voué à l'échec.

Le DevOps appelle à un renforcement de la collaboration entre deux équipes, que sont les Dev et les Ops.

Cela ne peut se faire sans cet appui.


::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
  opacity: 0.5;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
</style>

---
layout: two-cols
transition: slide-up
---

# Automatisation

C'est souvent le 1er principe qui vient à l'esprit quand on parle de DevOps.

<br>

L'automatisation consiste à libérer les équipes des tâches répétitives et sans véritables valeurs ajoutées.

<br>

Il s’agit aussi de donner aux gens les moyens de faire se concentrer sur celles qui ont réellement de la valeur.

::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
  opacity: 0.5;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
</style>

---
layout: two-cols
transition: slide-up
---

# Lean

Ce principe tire ses origines des méthodes de production de Toyota.

<br>

Le lean signifie "sans gras", c’est une méthode de gestion de la production qui se concentre sur la "chasse aux gaspillages".

<br>

Ce principe de rationalisation cherche à réduire des excès, en limitant au minimum le nombre et la durée des réunions, la taille des équipes et le nombre d'outils susceptibles de fournir les résultats attendus.

::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
  opacity: 0.5;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
</style>

---
layout: two-cols
transition: slide-up
---

# Mesure

Si vous ne pouvez pas mesurer, vous ne pouvez pas vous améliorer.

<br>

On ne se limite pas à mesurer le temps d’un déploiement logiciel.

<br>

Il faut mettre en place d'autres indicateurs pour que le processus puisse être amélioré continuellement.

::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
  opacity: 0.5;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
</style>

<!-- 
Tout d’abord le délai de changement, donc le temps entre le commit du code et la mise en production
La fréquence de déploiement, donc à quel intervalle le code est déployé en production
Le temps de récupération, c'est-à-dire le temps nécessaire pour restaurer le service après un incident
Le taux d’échec des changements ou le pourcentage des changements qui diminue le service ou requièrent une intervention -->

---
layout: two-cols
transition: slide-up
---

# Partage

L'objectif est de créer une contribution partagée.

<br>

Les gens sont prêts à travailler ensemble si leurs pensées et leurs opinions sont entendues.
Ils partagent donc leurs idées, leurs analyses, leurs données et leurs résultats.

<br>

Le partage exprime la nécessité d'une communication permanente entre les équipes chargées des développements et celles chargées de l'exploitation.

::right::

<div class="calms-container">
  <div class="ligne1">
    <div class="block automation">
      AUTOMATION
    </div>
    <div class="block lean">
      LEAN
    </div>
    <div class="block measurement">
      MEASUREMENT
    </div>
    <div class="block share">
      SHARE
    </div>
  </div>
  <div class="block culture ligne2">
    CULTURE
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.calms-container {
  display: flex;
  gap: 20px;
  flex-direction: column;
 
  align-items: center;
  justify-content: center;
}
.ligne1 {
  display: flex;
  gap: 20px;
  width: 80%;
  height: 300px;
}
.ligne2 {
  width: 80%;
  height: 80px;
}
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  flex-grow: 1;
}
.culture {
  background-color: green;
  opacity: 0.5;
}
.automation {
  background-color: #FFB612;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.lean {
  background-color: #A1006B;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.measurement {
  background-color: #00A1DE;
  writing-mode: vertical-rl;
  rotate: 180deg;
  opacity: 0.5;
}
.share {
  background-color: red;
  writing-mode: vertical-rl;
  rotate: 180deg;
}
</style>


---
layout: default
transition: fade-out
---

# Les Principes Agiles

Tous les principes Agiles sont également à respecter dans le DevOps puisqu’il s’en inspire.

<br>

Attention toutefois sous couvert de la simplicité, certains y justifient le moyen de ne pas respecter les bonnes pratiques de sécurité, de maintenabilité et de disponibilité.

<br>

Ne tombez pas dans ce piège !

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: section
transition: slide-up
---

# La boucle de rétroaction

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: image
image: /assets/images/devops-boucle.webp
backgroundSize:  70%
transition: slide-up
---

# La boucle de rétroaction

<style>
h1 {
  color: #2B90B6;
}
</style>

<!-- 
Partie Dev en agilité classique avec un backlog, la planification du sprint et sa réalisation
Partie CI : avec le build, les tests (unitaires, des intégrations, end to end …) et enfin la création de l’artefact
Partie CD (déploiement) dans les environnements de test, d’intégration pour tester et enfin livrer sur les env de prod
 -->

---
layout: default
transition: fade-out
---

# Definition of Done

C'est la liste de critères à vérifier, afin de déterminer si les tickets sont vraiment terminés. 

<br>

Cela peut comporter :

- Un rapport de test réalisé avec succès

<br>

- Un taux de couverture de code respectant les objectifs fixés

<br>

- Un rapport de succès à l'analyse des vulnérabilités des artefacts et des dépendances

<br>

- Une documentation conforme

<br>

- …
 
<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: section
transition: slide-up
---

# Les outils


<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: iframe
url: https://landscape.cncf.io/
transition: slide-up
---

<!-- une carte qui tente de catégoriser la plupart des projets de technologie native du cloud -->

---
layout: default
transition: slide-up
---

# Les outils d'orchestration de pipeline

<div class="container">
 <img src="/assets/images/Jenkins_logo.svg.png" />
 <img src="/assets/images/gitlab-ci-cd-logo.png" />
 <img src="/assets/images/GitHub_Invertocat_Logo.svg.png" />
</div>


<style>
h1 {
  color: #2B90B6;
}
.container {
  display: flex;
  gap: 20px;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
  width: 100%;
  margin-top: 80px;
}
img {
  width: 200px;
}
</style>

---
layout: default
transition: fade-out
---

# Les autres outils

Comme on l'a vu, il existe de nombreux outils utilisés dans le DevOps.

<br>

- Du stockage des artefacts que ce soit des images de conteneurs, des packages applicatifs, des libraires, ...,
- Des tests automatisés,
- Du provisionnement de ressources,
- De gestion de configuration,
- De gestion de la sécurité dont celle de la supply chain,
- De secret management,
- De monitoring,
- De gestion des logs,
- ...

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: section
transition: slide-up
---


# Les bonnes pratiques

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: default
transition: slide-up
---

# Rappel

Faites attention à ce que vous trouvez sur internet.

<br>

Tout ce qui est disponible sur internet (et avec les IA) l'est à des fins de démonstrations, voir de formation.

<br>

Il est vidé, pour en faciliter la compréhension, de toute notion de fiabilité, de maintenabilité, d'exploitabilité et de sécurité.

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: image-right
image: /assets/images/cooper-howard-fallout.gif
backgroundSize:  70%
transition: fade-out
---

# Les bonnes pratiques

Gardez toujours en tête les points suivants, dans la partie dev comme dans la partie ops.

- La sécurité
- La fiabilité 
- L’exploitabilité
- La maintenabilité
- l’industrialisation

<style>
h1 {
  color: #2B90B6;
}
</style>

<!-- La sécurité, c'est l'affaire de tous pas d'un seul d'un spécialiste ! Alors, replaçons la sécurité comme une fondation de toute construction.
indicateurs, haute disponibilité, auto-remédiation…,

NoOps => Génial si tout automatique! mais en pratique si y’a un gros problème on fait comment ?

Sauvegarder, documenter et tester pour pouvoir remettre en service en cas de problème

Industrialiser veut dire sérialiser. Cela veut dire construit de manière cohérente. -->

---
layout: section
transition: slide-up
---

# La veille technologique

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: default
transition: fade-out
---

# Les sites de veille

Il existe de nombreux sites de veille technologique. En voici quelques uns que j'utilise régulièrement :

- [Developpez.com](https://www.developpez.com/)
- [Le journal du hacker](https://www.journalduhacker.net/)
- [RudeOps](https://rudeops.com/) (mailling liste hebdo)
- [Human coders](https://news.humancoders.com/)
- [Quoi de neuf les devs](https://happytodev.substack.com/)
- …

Pour se former sur les DevOps : [Le blog de Stéphane Robert](https://blog.stephane-robert.info/)

<style>
h1 {
  color: #2B90B6;
}
</style>

---
layout: section
transition: slide-up
---

# Démonstration d'un pipeline de CI/CD

<style>
h1 {
  color: #2B90B6;
}
</style>

<!-- 
https://gitlab.com/gitlab-org/gitlab/-/pipelines/

https://gitlab.com/gitlab-org/gitlab/-/pipelines/1559732529 
-->

---
layout: center
---
<div class="flex flex-col items-center">
<h1>Merci de votre attention</h1>

Retrouvez les diapositives à l'adresse suivante : [https://badroro.github.io/devops-introduction](https://badroro.github.io/devops-introduction)

<div class="flex flex-row items-center container">
  <LightOrDark>
    <template #dark>
      <div class="flex flex-col items-center">
      <QRCode
          :width="200"
          :height="200"
          type="svg"
          data="https://badroro.github.io/devops-introduction"
          :margin="10"
          :dotsOptions="{ type: 'square', color: 'white' }"
      />
      <span>Lien vers les slides</span>
      </div>
      <div class="flex flex-col items-center">
      <QRCode
          :width="200"
          :height="200"
          type="svg"
          data="https://openfeedback.io/o4cKuvoeESCMKha2QIHs/2024-12-02/FRUMzon5XrlhBdhJBpk3"
          :margin="10"
          :dotsOptions="{ type: 'square', color: 'white' }"
      />
      <span>Me laisser un feedback</span>
      </div>
    </template>
    <template #light>
      <QRCode
          :width="200"
          :height="200"
          type="svg"
          data="https://badroro.github.io/devops-introduction"
          :margin="10"
          :dotsOptions="{ type: 'square', color: 'black' }"
      />
    </template>
    <span>Lien vers les slides</span>
     <QRCode
          :width="200"
          :height="200"
          type="svg"
          data="https://openfeedback.io/o4cKuvoeESCMKha2QIHs/2024-12-02/FRUMzon5XrlhBdhJBpk3"
          :margin="10"
          :dotsOptions="{ type: 'square', color: 'black' }"
      />
      <span>Me laisser un feedback</span>
  </LightOrDark>
  </div>
</div>

<style>
h1 {
  color: #2B90B6;
}
.container {
  display: flex;
  justify-content: space-around;
}
</style>
