# 📑 Page Liste : Recherche, Tri et Pagination 📑

Une interface de gestion de listes permettant d’explorer, filtrer et analyser efficacement des données volumineuses via une navigation fluide, des filtres dynamiques et une gestion optimisée côté serveur.

---

## 🎯 1. Objectifs

* Proposer une **interface ergonomique et performante** pour la consultation de données.
* Permettre une **navigation fluide même avec de grands volumes**.
* Offrir des outils avancés de :

  * Recherche
  * Tri
  * Filtrage (dont temporel)
* Mettre en place une **séparation claire des responsabilités front/back**.
* Illustrer mes compétences en **optimisation des performances et UX data-driven**.

---

## 🛠️ 2. Stack technique

### a. Frontend

* **React** avec gestion avancée des hooks :

  * `useEffect` → récupération des données
  * `useMemo` → optimisation du rendu
* Gestion des états :

  * Pagination
  * Filtres
  * Tri
* Stockage temporaire :

  * `sessionStorage` pour persistance des filtres (dates)

---

### b. Backend

* **API REST avec MongoDB (aggregation pipeline)** :

  * `$match` → filtrage
  * `$lookup` → jointure entreprise
  * `$unwind` → normalisation
  * `$sort` → tri dynamique
  * `$facet` → pagination + total

---

### c. Données

* Structuration paginée :

  * `registrations`
  * `candidatures`

* Métadonnées :

  * `total`
  * `pages`
  * `limit`
  * `page`

---

## 📊 3. Fonctionnalités principales

### Pagination serveur

* Chargement des données **page par page**
* Réduction du volume côté client
* Synchronisation avec :

  * nombre d’éléments par page
  * navigation utilisateur

👉 Côté front :

```ts
useEffect(() => {
  setCurrentPage(1);
}, [searchRegistration, searchEntreprise, itemsPerPage, filterInterim, filterEntreprise, sortField, sortDirection]);
```

---

### Recherche multicritère

* Recherche côté serveur pour :

  * Nom
  * Entreprise
* Utilisation de **regex MongoDB** pour flexibilité

👉 Backend :

```ts
matchFilters.nom = { $regex: req.query.searchRegistration, $options: 'i' };
```

---

### Tri dynamique

* Tri personnalisable :

  * Nom
  * Date d'inscription
  * Mise à jour

* Mapping sécurisé des champs :

```ts
const SORT_FIELD_MAP = {
  nom: "nom",
  dateRegistration: "dateRegistration",
  updateCV: "updateCV",
};
```

* Gestion de la casse avec collation MongoDB :

```ts
.collation({ locale: 'fr', strength: 2 })
```

---

### Filtrage avancé

* Filtres combinables :

  * Intérim
  * Présence entreprise
  * Statut (candidatures)
* Filtrage après jointure (`$lookup`)

---

### Filtrage par date (UX avancée)

* Sélection d’une période :

  * Date de début
  * Date de fin
* Persistance utilisateur :

```ts
sessionStorage.setItem(STORAGE_KEY_DEBUT, v);
```

* Chargement conditionnel :

```ts
(filterDateDebut || filterDateFin)
  ? getCandidaturesFiltered(...)
  : getCandidature();
```

---

### Chargement optimisé (multi-sources)

* Utilisation de `Promise.all` :

```ts
const [candidaturesData, entreprisesData, contactsData, profileViewsData] = await Promise.all([...]);
```

👉 Permet :

* parallélisation
* réduction du temps de chargement

---

## 🧩 4. Architecture de récupération des données

### Frontend

* Déclenchement automatique via dépendances :

```ts
useEffect(() => {
  fetchRegistration();
}, [currentPage, itemsPerPage, ...]);
```

---

### Backend

Pipeline structuré :

```ts
[
  { $match },
  { $lookup },
  { $unwind },
  { $match (optionnel) },
  { $sort },
  { $facet }
]
```

👉 Permet :

* filtrage progressif
* pagination optimisée
* réponse unique avec total + données

---

## 🖥️ 5. Organisation de l’interface

* **Zone filtres**

  * Recherche texte
  * Filtres dynamiques
  * Dates

* **Zone résultats**

  * Liste paginée
  * Tri actif

* **Zone navigation**

  * Pagination
  * Nombre d’éléments/page

---

## 🚀 6. Compétences mises en avant

### a. Gestion de données

* Manipulation de volumes importants
* Filtrage et tri côté serveur
* Optimisation des requêtes MongoDB

---

### b. Frontend avancé

* Gestion complexe des états React
* Synchronisation UI / API
* Optimisation des re-renders (`useMemo`)

---

### c. Performance

* Pagination serveur
* Requêtes parallèles (`Promise.all`)
* Réduction du payload

---

### d. Expérience utilisateur

* Navigation fluide
* Filtres persistants
* Recherche rapide et ciblée

---

## 🎯 7. Conclusion

Ce module de **page liste** illustre ma capacité à :

* Concevoir des interfaces orientées **exploration de données**
* Optimiser les performances via une **logique front/back complémentaire**
* Structurer des requêtes complexes avec **MongoDB aggregation**
* Offrir une **expérience utilisateur fluide et personnalisable**

Cette approche est essentielle pour toute application manipulant des **données volumineuses et dynamiques**.

## 🚀 8. Perspectives d’évolution

* Ajout de plus de filtres sauvegardés (localStorage / profil utilisateur).