# 🔒 Points sur la sécurité de l'application 📑

## 📑 1. Sécurisation des données

### a. Utilisation de l'ODM Mongoose

L'utilisation des <b>l'ODM (Object Document Mapping) comme `Mongoose`</b> est un excellent choix pour éviter les injections de requêtes car il génère des requêtes MongoDB préparées (ou paramétrées) automatiquement.

- ODM est un programme informatique qui se place entre un back-end et une base de données non relationnelle.
- Il gère les relations entre les données, assure la validation des schémas et permet la traduction entre les objets du code et leur représentation dans la base de données.
- Un schéma `Mongoose` définit la structure du document, les valeurs par défaut, les validateurs, etc., tandis qu'un modèle `Mongoose` fournit une interface avec la base de données pour la création, l'interrogation, la mise à jour et la suppression d'enregistrements, etc..

### b. Zod

- <b>Zod</b> est une bibliothèque de validation de données pour TypeScript. Elle permet de définir des schémas de validation pour vos données et de les valider. Zod est conçu pour être simple à utiliser et à comprendre, tout en étant puissant et flexible.<br />
 
- <b>Typescript</b> ne peut pas garantir que les données reçues respectent les types définis. En validant les données, <b>Zod</b> permet de s'assurer que les données reçues sont correctes, de faire un typage fort, de réduire les erreurs dans l'application et augmenter la sécurité en évitant de traiter des données incorrectes.<br />
  
- Schéma pour contrôler un numéro de téléphone français ou internationnal :<br />
``` 
// Regex téléphone
const phoneRegex = () =>
  z.string()
    .transform((val) => {
      const trimmed = val.trim();
      return trimmed === "" ? undefined : trimmed;
    })
    .optional()
    .refine((val) => {
      if (!val) return true;

      // Supprimer espaces, parenthèses, points, tirets
      const normalized = val.replace(/[\s().-]/g, "");

      // Vérifier que c'est uniquement + et chiffres
      if (!/^\+?\d+$/.test(normalized)) {
        return false;
      }

      // Vérifier la longueur 
      return normalized.length >= 6 && normalized.length <= 20;
    }, {
      message: "Numéro de téléphone invalide",
    });
``` 

### c. Hachage Bcrypt

<b>Bcrypt</b> est une technique de hachage utilisée pour protéger les mots de passe contre les attaques des hackers en stockant les mots de passe sous un format haché.<br />
- Il transforme le mot de passe d'un utilisateur en une chaîne de caractères de longueur fixe au sein d'une fonction de <b>hachage unidirectionnelle</b>, ce qui garantit qu'il ne peut pas être inversé pour retrouver le mot de passe d'origine.
- Lorsque l'utilisateur se connecte, bcrypt ré-hache le mot de passe et compare cette nouvelle valeur à celle stockée dans la base de données pour vérifier leur correspondance.<br />

### d. Cryptage des données sensibles

- utilisation de la librairie <b>crypto-js</b>.
- J'ai crypté l'access_token avant de l'enregistrer dans le cookie et le refresh_token avant de l'enregistrer dans la base de données.

## 👥 2. Sécurisation des sessions

### a. JWS token 

Les <b>JWS token</b> permettent une protection des connexions. <br />
- Ils sont constitués de 3 parties : l'entête, le payload et la signature. <br />
- Le payload contient les informations à transmettre comme l'id du user ou la date d'expiration.
- Le refresh_token, stocké dans la table user, permet aux utilisateurs de générer un nouvel access_token sans devoir se reconnecter à chaque expiration de l'access_token tant que le refresh_token est valide.
- Utilisation de la librairie <b>jsonwebtoken</b>.
- Les tokens ont une durée différente suivant son type et la version de l'application utilisée (web ou mobile) et limitée dans le temps avec un équilibre entre l'expérience utilisateur et la sécurité.

### b. Cookie

- L'utilisation des cookies permettera le bon fonctionnement de l'application.
- Les données du cookie ont une durée limité dans le temps avec un équilibre entre l'expérience utilisateur et la sécurité.
- Les cookies sont protégés avec les paramètres "httpOnly: true" et "secure: true".

### c. Middleware

- J'ai créé un <b>middleware de limitation de débit d'API</b> en limitant le nombre de requêtes par fenêtre de temps.
- J'ai aussi créé un <b>middleware pour contrôler les routes</b> de mon application. Il y a deux catégories de routes :
  - Publique
  - User et Admin
  - Admin
- Le <b>middleware</b> me permet de gérer les <b>tokens</b>. Contrôle de l'existance et de la validité du token access.
<br><br>

## 🌍 3. Sécurisation de l'application avec le https

Une fois que l'application sera finie et opérationnelle, le déploiement se fera sur un serveur debian avec l'utilisation d'un <b>certificat de sécurité TLS</b> pour avoir un accès de l'application en https.<br>
J'ai activé <b>HTTPS</b> sur mon hébergeur AWS, mon application web est bien configuré pour utiliser HTTPS de manière optimale. AWS fournit une interface simple pour activer un <b>certificat SSL/TLS</b>. <br>
J'ai activé la redirection de tout le trafic HTTP vers HTTPS.
- Cela garanti que les données échangées seront chiffrées, ce qui protège contre les interceptions ou attaques potentielles.<br>
- Ce qui permet de chiffrer les requêtes http `POST` notamment.
<br><br>

## 🎯 4. Conclusion


