# 🧠 Retour d’expérience et choix techniques 🧠


## ⚙️ 1. Stack utilisée

* Frontend : React v19
* Backend : Express
* Base de données : MongoDB avec Mongoose

### 🗄️ a. Base de données : MongoDB + Mongoose

* Grande **flexibilité du schéma**
* Possibilité d’utiliser une **même collection pour plusieurs types de documents**
* Ajout de nouveaux champs **sans migration complexe**

Ce choix m’a permis d'ajouter rapidement de nouveaux types de documents au fur et à mesure du développement.

### 🛠️ b. Back-end : Express

* Nécessite de **construire toute l’architecture manuellement**
* Peu de conventions → risque de manque d’homogénéité
* Moins adapté à mesure que le projet grandit

Une architecture plus cadrée faciliterait la création du projet et la maintenance.

### ⚛️ c. Front-end : React v19

* Certaines **incompatibilités avec des librairies React v18**
* Nécessité d’adapter certaines dépendances
* Nécessité d’adapter certains composants material-tailwind


## 🔄 3. Comparaison avec ma stack habituelle

Dans ce projet, j’ai volontairement utilisé une stack différente de celle que j’utilise habituellement afin d’explorer d’autres approches.

### 🧰 a. Stack du projet

* React v19
* Express
* MongoDB + Mongoose

### 🧰 b. Stack que j’utilise habituellement

* React
* NestJS
* MySQL
* Prisma

### ⚖️ c. Différences observées

#### 🗄️ i. Base de données

**MongoDB**

* Très flexible
* Évolution rapide du schéma
* Utilisation d'une seule collection de documents pour plusieurs types de données (candidature, entretien, relance, etc.) grâce au polymorphisme documentaire.
* Ajout de nouveaux champs sans migration : l'évolution du modèle de données est immédiate.
* Idéal pour les phases d'exploration où le schéma évolue fréquemment.

**Mongoose ODM**
* Définition de schémas avec validation intégrée malgré la nature sans-schéma de MongoDB.
* Middleware Mongoose (pre/post hooks) pratiques pour l'horodatage et l'audit.
* La gestion des types hétérogènes dans une même collection nécessite une discipline de documentation.

**MySQL**

* Schéma structuré et strict
* Meilleure gestion des relations
* Schéma strict avec contraintes d'intégrité référentielle natives.
* Toute évolution du modèle de données nécessite une migration explicite.* 
* Plus sécurisé sur la cohérence des données
* Moins adapté si les types de données varient selon les candidatures ou évoluent souvent.

**Prisma ORM**

* DX (Developer Experience) excellente : typage TypeScript généré automatiquement depuis le schéma.
* Migrations versionnées et traçables.
* ORM moderne qui remplace avantageusement Sequelize ou TypeORM dans l'écosystème Node.js.
* Moins de flexibilité pour les structures documentaires polymorphes.

👉 MongoDB est le choix le plus adapté pour des données à structure variable,<br>
👉 MySQL + Prisma serait préférable si le schéma se stabilise et que l'intégrité relationnelle devient critique.

#### 🛠️ ii. Backend

**Express**

* Léger et rapide à mettre en place
* Liberté totale d’organisation
* L'architecture doit être définie et construite manuellement : routing, middlewares, séparation des responsabilités.
* Absence de structure imposée : chaque développeur peut organiser le projet différemment, rendant la maintenance complexe.
* La gestion de l'injection de dépendances, des modules ou des guards est entièrement à la charge du développeur.

**NestJS**

* Architecture modulaire : chaque fonctionnalité est encapsulée dans un module (candidature, utilisateur, etc.).
* Code plus structuré et homogène
* Séparation claire des responsabilités entre controllers, services et providers
* Injection de dépendances native, facilitant les tests unitaires. 
* Guards, interceptors et pipes intégrés pour la validation, l'authentification et la gestion des erreurs.
* Meilleure maintenabilité sur le long terme

👉 Express offre de la liberté,<br>
👉 NestJS apporte un cadre solide.


#### ⚙️ iii. Expérience globale

| Critère         | Stack du projet | Stack habituelle |
| --------------- | --------------- | ---------------- |
| Flexibilité     | ⭐⭐⭐⭐⭐           | ⭐⭐               |
| Structure       | ⭐⭐              | ⭐⭐⭐⭐⭐            |
| Rapidité de dev | ⭐⭐⭐           | ⭐⭐⭐⭐              |
| Maintenabilité  | ⭐⭐              | ⭐⭐⭐⭐⭐            |

---

## 🧾 4. Ce que j’en retiens

* Cette stack m’a permis de **développer rapidement** et d’expérimenter
* J’ai pu identifier les **limites d’une architecture non structurée**
* Cela confirme l’intérêt d’une stack plus cadrée pour des projets complexes

Cette expérience m’a surtout permis de **comparer concrètement deux approches** et de mieux comprendre leurs cas d’usage.
