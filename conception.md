# 📑 Conception 📑

<br />
La création de cette application web me permet de concevoir un outil numérique pratique pour répertorier, organiser et consulter les candidatures. L'objectif est de créer une interface simple et intuitive, accessible à tous.<br /> 
Voici une présentation générale pour la conception d'une telle application : <br /><br />

---

## 1. 🚀 Objectifs de l'application

###    • Facilité d'utilisation : 
Permettre aux utilisateurs suivre efficacement ces candidatures.
###    • Suivre efficacement ces candidatures : 
Offres, plateformes, retours, correspondances entre les stacks/compétences, alerte relance, contacts, coordonnées des entreprises.
###    • Accessibilité : 
Permettre un accès facile sur différents appareils (ordinateurs, tablettes, smartphones) via un navigateur web.
<br /><br />

---

## 2. 💡 Fonctionnalités principales

###    • Création de fiches de candidatures : Les utilisateurs peuvent ajouter une candidature avec les détails suivants :

        ◦  poste
        ◦  entreprise
        ◦  depot  
        ◦  etat: "en cours" | "close" | "recruté(e)";
        ◦  date
        ◦  type de Contrat
        ◦  temps Travail
        ◦  conditions du Contrat 
        ◦  jours de Télétravail
        ◦  lieu de Travail
        ◦  temps de Trajet
        ◦  stacks ou compétences
        ◦  texte d'intérêt
        ◦  lettre de motivation courte
        ◦  blocNote
        ◦  contacts du l'entreprise
        ◦  différents documents : "Offre", "CV", "LM", "Retour", "Contact", "Rendezvous", "Action", "Suite"

###    • Création de fiches de entreprise : Les utilisateurs peuvent ajouter une entreprise avec les détails suivants :

        ◦ nom
        ◦ secteur
        ◦ type de Société
        ◦ adresse
        ◦ cp
        ◦ ville
        ◦ téléphone
        ◦ mobile
        ◦ email
        ◦ linkedIn
        ◦ site Web
        ◦ service

###    • Création de fiches de contact entreprise : Les utilisateurs peuvent ajouter un contact avec les détails suivants :

        ◦ Nom
        ◦ Prénom
        ◦ email du contact
        ◦ téléphone du contact
        ◦ mobile du contact
        ◦ le lien linkedIn
        ◦ service
        ◦ entreprise

###    • Recherche et filtrage : 
Implémenter une fonctionnalité de recherche avancée permettant aux utilisateurs de trouver facilement une candidature en fonction de critères (poste, entreprise), une entreprise ( nom, type de sociéte, secteur, ville), contact (nom, entreprise, service).
###    • Interface conviviale : 
Une interface simple avec un tableau de bord clair pour gérer les candidatures et les informations associées. Cela inclut des boutons clairs pour ajouter, modifier ou supprimer des fiches, ainsi qu'une vue en liste.
###    • Gestion des utilisateurs : 
Les utilisateurs peuvent créer des comptes pour enregistrer et synchroniser leurs candidatures en ligne. 
###    • Sauvegarde et exportation : 
Les utilisateurs peuvent exporter leur fiche ou tableaux de suivi sous forme de fichier PDF ou CSV pour le conserver en local ou le partager facilement.
<br /><br />

---

## 3. 🛠️ Technologies utilisées

###    • Frontend (interface utilisateur) : 
Utilisation de technologies modernes telles que HTML5, `TypeScript` avec les bibliothèques comme `React`, `Taiwind CSS`, `Material Taiwind`  pour construire une interface dynamique et interactive.
Utilisation de la librairie `react-big-calendar` pour le calendrier et `chart.js` pour les graphiques du Dashboard.
###    • Backend (gestion des données) : 
Un serveur basé sur `Node.js` avec `Express.Js`, et l'ODM (Object Document Mapping) `Mongoose` pour gérer les requêtes les données des candidatures, les comptes utilisateurs, etc...
###    • Base de données : 
Une base de données NoSQL `MongoDB`, pour stocker les informations relatives aux candidatures et aux utilisateurs.<br />
`MongoDB` est une base de données de documents NoSQL sans schéma. Cela signifie que l'on peut y stocker des documents JSON, dont la structure peut varier, car elle n'est pas imposée comme dans les bases de données SQL. C'est l'un des avantages de NoSQL : il accélère le développement des applications et simplifie les déploiements
###    • Hébergement et déploiement : 
Utilisation du service `AWS` pour l'hébergement de l'application, offrant ainsi une solution scalable et accessible à tous.
<br /><br />

---

## 4. 🧩 Maquettes de l'application

L'interface doit être claire, simple et agréable à utiliser. Voici les éléments clés de la maquette :
###    • Page d'accueil : 
Présentation générale de l'application et bouton de connexion/inscription.
###    • Page dashboard : 
Affichage des 10 dernières candidatures, des rendez-vous, actions à effectuer, des statisques et graphiques du suivi.
###    • Page profil : 
Permet de modifier les informations du profil ou le supprimer.
###    • Page de liste des candidature : 
Affichage la liste des candidatures en cours par défaut.
Possibilité de recherche, export excel.
###    • Page de fiche candidature : 
Affichage le détail complet de la candidature.
Possibilité de l'exporter en pdf.
###    • Page de création/mise à jour d'une candidature : 
Affichage le formulaire de création ou de mise à jour de la candidature.
###    • Page de calendrier : 
Affichage le détail des évènements liès aux candidatures.
###    • Page de liste des entreprises : 
Affichage la liste des entreprises.
Possibilité de recherche, export excel.
###    • Page de fiche entreprise: 
Affichage le détail complet de l'entreprise.
Possibilité de l'exporter en pdf.
###    • Page de création/mise à jour d'une entreprise : 
Affichage le formulaire de création ou de mise à jour de l'entreprise.
###    • Page de liste des contacts : 
Affichage la liste des contacts.
Possibilité de recherche, export excel.
###    • Page de fiche contact : 
Affichage le détail complet du contact.
Possibilité de l'exporter en pdf.
###    • Page de création/mise à jour d'un contact : 
Affichage le formulaire de création ou de mise à jour du contact.
###    • Page de liste des modèles de candidature : 
Affichage le poste, les fichiers de CV ou LM téléchargeables, un texte d'intérêt et un texte court de motivation.
Possibilité de recherche par poste.
###    • Page de création/mise à jour d'un contact : 
Affichage le formulaire de création ou de mise à jour d'un modèle.
<br /><br />

---

## 5. 📝 Étapes de développement

###    • Phase 1 : Planification : 
Définir précisément les fonctionnalités nécessaires et les exigences techniques. Concevoir les maquettes de l'interface.
###    • Phase 2 : Développement Frontend : 
Créer l'interface utilisateur (UI) avec un design simple et responsive.
###    • Phase 3 : Développement Backend : 
Créer la logique serveur pour gérer les utilisateurs, les candidatures, les entreprises, les contacts et la base de données.
###    • Phase 4 : Test : 
Tester l'application sur différents appareils et navigateurs pour s'assurer de son bon fonctionnement.
###    • Phase 5 : Lancement et maintenance : 
Déployer l'application et effectuer des mises à jour régulières en fonction des retours des utilisateurs.
<br /><br />

---

## 6. 🎯 Conclusion

- La conception de cette application marque une étape importante dans la mise en place d’un outil moderne, ergonomique et accessible pour le suivi des candidatures. Grâce à son interface intuitive, ses fonctionnalités de gestion complètes et ses possibilités de recherche et d’exportation, elle répond aux besoins essentiels des utilisateurs souhaitant organiser efficacement leurs démarches de recherche d'emploi.

- L’utilisation de technologies fiables et performantes telles que React, Node.js et MongoDB, couplées à un hébergement évolutif sur AWS, garantit non seulement la robustesse de la solution mais aussi sa capacité à évoluer selon les futurs besoins.

- En définitive, ce projet pose des bases solides pour offrir une expérience fluide et productive, et pourra être enrichi au fil du temps par de nouvelles fonctionnalités afin de s’adapter encore davantage aux attentes des utilisateurs.