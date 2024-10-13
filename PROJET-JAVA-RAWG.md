### Projet : Application de Consultation de Jeux Vidéo via API

#### Contexte global :
Dans ce projet, vous allez développer une application Java qui interagit avec une **API publique de jeux vidéo** pour récupérer et afficher des informations détaillées sur différents jeux vidéo en temps réel. Le projet est structuré en trois itérations, chacune ajoutant des fonctionnalités et des améliorations progressives. Vous devrez utiliser les concepts de **programmation orientée objet (POO)**, appliquer les **principes SOLID**, et respecter les bonnes pratiques de **Clean Code**.

L’application interrogera l’API gratuite [RAWG](https://rawg.io/apidocs) pour obtenir des informations telles que les noms de jeux, les genres, les éditeurs, et les avis des utilisateurs.

---

### **Itération 01 : Récupération et Affichage des Détails d’un Jeu (sur 12 points)**

#### Mission :
Votre première tâche est de créer une **application Java en ligne de commande** qui se connecte à l’API RAWG pour récupérer les **détails d’un jeu vidéo spécifique** et les afficher. Cette première itération vise à vous familiariser avec l’intégration d’une API REST dans une application Java.

#### Objectifs :
1. **Connexion à l'API** :
   - Utilisez l’API RAWG pour récupérer les détails d’un jeu spécifique (nom, description, date de sortie, etc.).
   - Effectuez une requête HTTP GET pour obtenir des données au format JSON.

2. **Affichage des données** :
   - Parsez la réponse JSON pour extraire les **informations principales** du jeu (nom, description, genre).
   - Affichez ces informations de manière structurée dans la console.

3. **Respect des principes POO, SOLID et Clean Code** :
   - **Interfaces** : Utilisez des interfaces pour séparer la logique d’interrogation de l’API et l’affichage des données.
   - **SOLID** : Assurez-vous que chaque classe a une responsabilité bien définie pour faciliter la maintenance.
   - **Clean Code** : Code lisible et bien structuré en respectant les conventions Java.

4. **Gestion des exceptions** :
   - Gérez les erreurs potentielles liées à la connexion réseau et au parsing JSON via des blocs `try-catch`.

#### Spécifications techniques :
- **API REST** : Utilisez l’API RAWG pour obtenir des informations de jeux.
- **POO** : Appliquez les concepts d'**interfaces**, **polymorphisme**, et **classes abstraites** pour structurer l’application.
- **Gestion des exceptions** : Gérez les erreurs liées aux connexions réseau et à la récupération de données.

#### Notation (sur 12 points) :
- Connexion API et récupération des données : 4 points
- Affichage correct des informations du jeu : 2 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et **Clean Code** : 3 points
- Gestion des **exceptions** : 1 point

---

### **Itération 02 : Consultation et Affichage de Jeux par Catégorie et Classement (sur 16 points)**

#### Mission :
Dans cette deuxième itération, vous allez **étendre l’application** pour permettre à l’utilisateur de rechercher des jeux vidéo par **catégorie (genre, plateforme)** et de récupérer les **classements** des jeux les plus populaires ou les mieux notés dans chaque catégorie.

#### Objectifs supplémentaires :
1. **Consultation de plusieurs jeux vidéo** :
   - Permettez à l’utilisateur de choisir un genre ou une plateforme spécifique (ex. : RPG, action, PS5) pour afficher une liste de jeux correspondants.

2. **Affichage des classements** :
   - Affichez les jeux selon leur popularité ou note moyenne, en fonction de la catégorie choisie.

3. **Amélioration de l’architecture** :
   - Refactorisez le code pour structurer la logique de requête API, le traitement des données et l’affichage en appliquant les principes SOLID.

4. **Gestion des exceptions avancée** :
   - Ajoutez des blocs `try-catch` plus robustes pour gérer des erreurs spécifiques, telles que la **non-disponibilité de l’API** ou des **catégories non trouvées**.

#### Spécifications supplémentaires :
- **API** : Récupérez les listes de jeux par genre, plateforme, ou autre critère.
- **Sélection dynamique** : Permettez à l’utilisateur de choisir parmi différentes catégories.
- **Refactorisation** : Améliorez la séparation des responsabilités.
- **Gestion des exceptions** : Prévoyez des erreurs spécifiques pour une meilleure robustesse.

#### Notation (sur 16 points) :
- Récupération et affichage des **classements** : 4 points
- Consultation par genre ou plateforme : 3 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et **refactorisation** : 5 points
- Gestion des **exceptions avancées** : 2 points

---

### **Itération 03 : Historique et Suivi des Jeux Préférés avec Base de Données NoSQL (sur 20 points)**

#### Mission :
Pour cette troisième itération, vous ajouterez une fonctionnalité permettant de **suivre les jeux préférés** de l’utilisateur et d’enregistrer ces informations dans une base de données NoSQL telle que **MongoDB** ou **Redis**. Les données seront historisées pour pouvoir consulter une **liste des jeux favoris** au fil du temps.

#### Objectifs supplémentaires :
1. **Suivi des jeux préférés** :
   - Permettez à l’utilisateur de sélectionner des jeux qu’il souhaite suivre et stockez ces jeux dans une liste de favoris.

2. **Stockage dans une base NoSQL** :
   - Enregistrez les informations de jeux favoris et les détails associés (note, popularité) dans une base NoSQL comme MongoDB ou Redis.

3. **Amélioration continue de l’architecture** :
   - Refactorisez l’architecture du projet pour intégrer proprement les fonctionnalités de stockage et de suivi, tout en respectant les principes SOLID.

#### Spécifications supplémentaires :
- **Suivi des favoris** : Implémentez une fonctionnalité pour sauvegarder les jeux préférés.
- **Base de données NoSQL** : Utilisez MongoDB ou Redis pour stocker et historiser les favoris.
- **Architecture Applicative** : Structurez les différentes couches de votre application selon une architecture coherente ( MVC multicouche ou micro service, etc...).

#### Notation (sur 20 points) :
- Mise en place du **suivi des jeux préférés** : 4 points
- Stockage des favoris dans une base NoSQL : 5 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et architecture modulaire : 5 points
- Gestion des **exceptions** liées à la base de données : 2 points

---

### Livrables :
- **Code source** pour les trois itérations.
- **Documentation** des fonctionnalités et de l’architecture.
- **Preuve de stockage des favoris** pour l’itération 3.

---

**Bonne chance**
