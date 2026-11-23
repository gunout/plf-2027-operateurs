<div align="center">

# 🇫🇷 PLF 2027 · Opérateurs

**Dashboard open source d'analyse des subventions aux opérateurs de l'État dans le projet de loi de finances 2027.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub last commit](https://img.shields.io/github/last-commit/gunout/plf-2027-operateurs)](https://github.com/gunout/plf-2027-operateurs/commits)
[![GitHub issues](https://img.shields.io/github/issues/gunout/plf-2027-operateurs)](https://github.com/gunout/plf-2027-operateurs/issues)
[![GitHub stars](https://img.shields.io/github/stars/gunout/plf-2027-operateurs?style=social)](https://github.com/gunout/plf-2027-operateurs/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/gunout/plf-2027-operateurs?style=social)](https://github.com/gunout/plf-2027-operateurs/network/members)

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.x-FF6384?logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)
[![API](https://img.shields.io/badge/API-data.economie.gouv.fr-000091)](https://data.economie.gouv.fr)
[![Backend](https://img.shields.io/badge/backend-none-success)](#)
[![Status](https://img.shields.io/badge/status-stable-brightgreen)](#)

[🚀 Démarrage](#-démarrage-rapide) · [✨ Fonctionnalités](#-fonctionnalités) · [📊 Analyses](#-analyses) · [🛠️ Stack](#️-stack-technique) · [📄 Licence](#-licence)

</div>

---

## 📖 À propos

**PLF 2027 · Opérateurs** est un tableau de bord **mono-fichier** qui interroge directement l'[API Explore v2.1](https://data.economie.gouv.fr/api/explore/v2.1) d'`Opendatasoft` et affiche en temps réel les subventions versées par l'État à ses opérateurs, telles que chiffrées dans le **projet de loi de finances 2027**.

Le moniteur compare, opérateur par opérateur, les **subventions pour charges de service public (SCSP)** votées en **LFI 2026** et celles proposées en **PLF 2027**. Il révèle les arbitrages budgétaires du gouvernement : coupes ciblées, fusions d'entités, gel des crédits et pression sur l'emploi.

Aucun backend, aucun build, aucune dépendance npm. Un fichier HTML, un navigateur, et c'est parti.

> Conçu pour les journalistes, chercheurs, élus, syndicalistes et citoyens qui veulent **explorer et comprendre** l'impact du PLF 2027 sur le paysage des opérateurs de l'État.

---

## ✨ Fonctionnalités

- 📊 **10 KPI synthétiques** : nb opérateurs, SCSP PLF vs LFI, évolution, médiane, Gini, poids top 10
- 📈 **6 visualisations interactives** (Chart.js) : distribution, Pareto, top hausses/baisses, nuage log, ministères, missions
- 🧮 **Programmes budgétaires** : top 10 en hausse et top 10 en baisse
- 📋 **Tableau détaillé** : tri par colonne, recherche plein texte, filtres ministère & catégorie
- 🏷️ **Badges colorés** : hausse / baisse / stable / nouveau / supprimé
- 🔍 **Faits saillants** auto-générés à partir des données
- 📥 **Export CSV** (BOM UTF-8, compatible Excel)
- 🎨 **Design inspiré du DSFR** (Système de Design de l'État)
- 📱 **Responsive** : mobile, tablette, desktop
- 🌐 **0 dépendance** à l'exécution (hors CDN Chart.js)
- ⚡ **Pagination automatique** de l'API (100 enregistrements/requête)

---

## 🚀 Démarrage rapide

### Option 1 — Cloner le dépôt

    git clone https://github.com/gunout/plf-2027-operateurs.git
    cd plf-2027-operateurs

### Option 2 — Télécharger directement

    curl -O https://raw.githubusercontent.com/gunout/plf-2027-operateurs/main/index.html

### Ouvrir le dashboard

    # Linux
    xdg-open index.html

    # macOS
    open index.html

    # Windows
    start index.html

Ou simplement **double-cliquer** sur `index.html` dans ton explorateur de fichiers.

> ⚠️ **CORS** : l'API `data.economie.gouv.fr` applique une politique restrictive. Si le chargement échoue en `file://`, utilise un petit serveur HTTP local :
>
>     python3 -m http.server 8000
>     # puis ouvrir http://localhost:8000/index.html

---

## 🧭 Utilisation

| Action | Résultat |
|---|---|
| Ouvrir `index.html` | Charge automatiquement les données depuis l'API |
| **🔍 Recherche** (tableau) | Filtre sur opérateur, ministère, programme, mission |
| **Filtre ministère** | Restreint aux opérateurs d'un ministère |
| **Filtre catégorie** | Hausse / baisse / stable / nouveau / supprimé |
| **Tri colonne** | Cliquer sur n'importe quel en-tête |
| **📥 Export CSV** | Télécharge les données enrichies (17 colonnes) |
| **Scroll** | Navigue dans le tableau (en-têtes figés) |

### Exemples de recherche

    CNRS
    France Travail
    Recherche
    P172

---

## 📊 Analyses

Le dashboard calcule et affiche automatiquement :

### Indicateurs globaux

- **SCSP PLF 2027** vs **SCSP LFI 2026** (en € et en %)
- **Médiane des évolutions** (plus robuste que la moyenne face aux valeurs extrêmes)
- **Indice de Gini** (concentration budgétaire entre opérateurs)
- **Poids du top 10** dans le budget total
- **Ventilation** : hausse / baisse / stable / nouveau / supprimé

### Visualisations

| Graphique | Ce qu'il révèle |
|---|---|
| **Distribution** | Répartition des opérateurs par tranche d'évolution |
| **Pareto** | Concentration du budget (règle des 80/20) |
| **Top 10 hausses / baisses** | Décisions politiques structurantes |
| **Nuage LFI×PLF (log)** | Vue d'ensemble : qui gagne, qui perd |
| **Variation par ministère** | Priorités sectorielles du gouvernement |
| **Programmes impactés** | Dispositifs concrets touchés (P172, P150, P345…) |
| **Répartition missions** | Poids relatif de chaque mission budgétaire |

### Méthodologie

- `delta = PLF − LFI` ; `évolution = delta / LFI × 100` (si LFI > 0, sinon `null`)
- **Catégorisation** :
  - `stable` : LFI = PLF = 0, ou \|évo\| < 0,5 %
  - `nouveau` : LFI = 0, PLF > 0
  - `supprime` : LFI > 0, PLF = 0
  - `hausse` : évo ≥ +0,5 %
  - `baisse` : évo ≤ −0,5 %
- **Gini** : `(2·Σ(i·xᵢ)) / (n·Σxᵢ) − (n+1)/n`

---

## 🛠️ Stack technique

| Composant | Technologie |
|---|---|
| **Frontend** | HTML5 + CSS3 (variables, grid, flexbox) |
| **Logique** | JavaScript vanilla (ES2022) |
| **API** | data.economie.gouv.fr — Explore v2.1 (Opendatasoft) |
| **Graphiques** | Chart.js 4.x (CDN) |
| **Parsing** | JSON natif (`fetch` + `Response.json()`) |
| **Exports** | Blob API native |
| **Zéro build** | Aucun npm, webpack, ou transpileur |

---

## 📁 Structure du projet

    plf-2027-operateurs/
    ├── index.html      ← l'application complète (HTML + CSS + JS)
    ├── README.md       ← ce fichier
    └── LICENSE         ← MIT

---

## 📚 Source des données

Le jeu de données est publié par la **Direction du Budget** sur `data.economie.gouv.fr` :

- **Titre** : *PLF 2027 - PAP Opérateurs - Subventions LFI N-1 et PLF N*
- **Producteur** : Ministère de l'Économie et des Finances
- **Licence** : Licence Ouverte 2.0 (Etalab)
- **API** : `https://data.economie.gouv.fr/api/explore/v2.1/catalog/datasets/plf-2027-pap-operateurs-subventions-lfi-n-1-et-plf-n/records`

### Champs exploités

| Champ technique | Signification |
|---|---|
| `operateur` | Nom de l'opérateur |
| `ministere` | Ministère de rattachement |
| `programme` / `libelle_programme` | Programme budgétaire |
| `mission` | Mission budgétaire |
| `lfi_n_1_ae_scsp_32` / `plf_n_ae_scsp_32` | SCSP (titre 3, chapitre 2) |
| `*_subv_inv_53` | Subventions d'investissement (titre 5) |
| `*_transferts_t6` | Transferts (titre 6) |
| `*_dot_fonds_propre_72` | Dotations aux fonds propres (chapitre 7) |

---

## 🔧 Personnalisation

### Changer la source API

Ouvre `index.html`, cherche la constante `API_BASE` en haut du `<script>` :

    const API_BASE = 'https://data.economie.gouv.fr/api/explore/v2.1/catalog/datasets/.../records';

### Changer la taille de page

    const PAGE_SIZE = 100;  // 100 max côté API

### Ajouter un graphique

Les fonctions de rendu sont isolées : `renderDistribution()`, `renderPareto()`, `renderGainersLosers()`, `renderScatter()`, `renderMinistry()`, `renderPrograms()`, `renderMissions()`. Chacune reçoit le tableau `clean` et instancie son propre `Chart`.

---

## ⚠️ Limites connues

- Les **données sont des chiffres de projet de loi** déposé en octobre 2026 — la navette parlementaire les modifiera.
- Le dashboard ne fait **aucun recoupement** avec d'autres sources (presse, rapports parlementaires).
- Les KPI portent **uniquement sur la SCSP** ; investissements, transferts et dotations figurent dans le tableau et le CSV, mais ne sont pas agrégés.
- **Dépendance réseau** : aucune donnée n'est embarquée, l'API doit être accessible.
- **CORS** : ouverture `file://` possiblement bloquée → utiliser un serveur HTTP local.
- **Opérateurs multi-programmes** : agrégés dans les KPI et graphiques, bruts dans le tableau.
- Le **niveau de solidité** des chiffrages n'est pas exposé dans le CSV source.

---

## 🗺️ Roadmap

- [x] **v1.0** — Dashboard mono-fichier avec 10 KPI et 6 graphiques
- [ ] **v1.1** — Sélecteur multi-millésimes (LFI N-1 vs PLF N)
- [ ] **v1.2** — Comparateur multi-opérateurs (cases à cocher)
- [ ] **v1.3** — Export PNG des graphiques
- [ ] **v1.4** — Filtres mission/programme appliqués aux KPI
- [ ] **v2.0** — Mode sombre (`prefers-color-scheme` + toggle)
- [ ] **v2.1** — Tests unitaires (Gini, médiane, catégorisation)

---

## 🤝 Contribution

Les contributions sont **les bienvenues** !

1. Fork le projet
2. Crée une branche (`git checkout -b feature/ma-fonctionnalite`)
3. Commit tes changements (`git commit -m 'Ajout de ma fonctionnalité'`)
4. Push (`git push origin feature/ma-fonctionnalite`)
5. Ouvre une Pull Request

**Conventions** :

- Commits au format [Conventional Commits](https://www.conventionalcommits.org/fr/) (`feat:`, `fix:`, `docs:`, `refactor:`)
- Pas de dépendance ajoutée sans discussion préalable (projet mono-fichier)
- Toute modification des calculs doit être documentée dans la section Méthodologie

### Signaler un bug

Ouvre une [issue](https://github.com/gunout/plf-2027-operateurs/issues) en précisant :

- Le navigateur et sa version
- Les étapes pour reproduire
- Le comportement attendu vs observé

---

## 📄 Licence

Distribué sous licence **MIT**. Voir `LICENSE` pour plus d'informations.

Les **données** affichées proviennent de [data.economie.gouv.fr](https://data.economie.gouv.fr) et sont publiées par la **Direction du Budget**. Elles sont soumises à la [Licence Ouverte 2.0 (Etalab)](https://www.etalab.gouv.fr/licence-ouverte-open-licence).

> ⚠️ **Avertissement** : ces chiffres sont issus d'un **projet de loi** et ne valent pas budget voté. Ils sont susceptibles d'évoluer au fil des débats parlementaires.

---

## 🙏 Remerciements

- [data.economie.gouv.fr](https://data.economie.gouv.fr) — pour l'API publique
- [Direction du Budget](https://www.budget.gouv.fr) — pour la publication des données
- [Opendatasoft](https://www.opendatasoft.com) — pour la plateforme Explore v2.1
- [Chart.js](https://www.chartjs.org) — pour les graphiques
- [Etalab](https://www.etalab.gouv.fr) — pour l'ouverture des données
- [Shields.io](https://shields.io) — pour les badges

---

<div align="center">

**⭐ Si ce projet t'est utile, mets-lui une étoile ! ⭐**

[Signaler un bug](https://github.com/gunout/plf-2027-operateurs/issues) · [Proposer une fonctionnalité](https://github.com/gunout/plf-2027-operateurs/issues) · [Contribuer](https://github.com/gunout/plf-2027-operateurs/pulls)

Fait avec 🇫🇷 pour les données publiques françaises.

</div>

---

<div align="center">

### 🇫🇷 Gunout · 2026

![Made in France](https://img.shields.io/badge/Made_in-France-002395?style=flat-square&labelColor=FFFFFF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjYwMCIgZmlsbD0iIzAwMjM5NSIvPjxyZWN0IHdpZHRoPSI5MDAiIGhlaWdodD0iNDAwIiB5PSIxMDAiIGZpbGw9IiNmZmYiLz48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjIwMCIgeT0iNDAwIiBmaWxsPSIjZWQyOTM5Ii8+PC9zdmc+)
![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github&logoColor=white)
![Year](https://img.shields.io/badge/2026-ED2939?style=flat-square&labelColor=FFFFFF)

<sub>© 2026 <strong>Gunout</strong> — Tous droits réservés.</sub>

</div>
