### Projet : Application de Consultation des Prix de Jeux Vidéo via l’API Steam

#### Contexte global :
Dans ce projet, vous allez développer une **application Java** qui interagit avec l’**API Steam** pour récupérer et afficher les prix de jeux vidéo en temps réel, ainsi que d'autres informations pertinentes. Le projet sera découpé en trois itérations avec des fonctionnalités croissantes, respectant les principes de **programmation orientée objet (POO)**, **SOLID**, et **Clean Code**.

L'application utilisera l'**API Steam** (ou une API tierce comme [Steam Store API](https://store.steampowered.com/api)) pour obtenir des informations sur les prix des jeux, leurs détails, et d'autres fonctionnalités comme le classement des jeux par popularité.

---

### **Itération 01 : Récupération et Affichage des Prix de Jeux Steam (sur 12 points)**

#### Mission :
Votre première mission est de développer une **application Java en ligne de commande** qui se connecte à l'API Steam pour récupérer le **prix d'un jeu vidéo** spécifique et l'afficher en temps réel. Vous utiliserez les concepts de POO pour structurer votre code et respecterez les principes SOLID et Clean Code.

#### Objectifs :
1. **Connexion à l'API Steam** :
   - Utilisez l’API Steam ou une API tierce pour récupérer les prix des jeux vidéo.
   - Effectuez des requêtes HTTP GET pour obtenir les données sous format JSON.

2. **Affichage des informations** :
   - Parsez la réponse JSON pour extraire et afficher le **prix** du jeu dans une devise choisie (par exemple, EUR ou USD).
   - Affichez également des informations supplémentaires comme le **titre** du jeu et les **réductions** éventuelles.

3. **Respect des principes POO, SOLID et Clean Code** :
   - Utilisez des **interfaces** pour séparer la logique d’interrogation de l’API et l’affichage des données.
   - Appliquez les principes **SOLID** pour assurer une architecture flexible et maintenable.
   - Assurez-vous que le code est lisible et respectueux des standards **Clean Code**.

4. **Gestion des exceptions** :
   - Gérez les erreurs potentielles liées à la connexion réseau, à l'API et au parsing JSON à l’aide de blocs `try-catch`.

#### Spécifications techniques :
- **API REST** : Utilisez l'API Steam pour récupérer les prix des jeux vidéo.
- **POO** : Appliquez les concepts d'**interfaces**, **polymorphisme**, et **classes abstraites**.
- **Gestion des exceptions** : Traitez les erreurs liées aux connexions réseau et à la récupération des données.

#### Notation (sur 12 points) :
- Connexion à l’API et récupération des données : 3 points
- Diargamme de classe correcte : 2 points
- Affichage correct du **prix des jeux** : 3 points
- Respect des principes **SOLID** et **Clean Code** : 3 points
- Gestion des **exceptions** : 1 point

---

### **Itération 02 : Recherche de Jeux et Affichage des Détails (sur 16 points)**

#### Mission :
Dans cette deuxième itération, vous allez **améliorer l'application** en permettant à l'utilisateur de **rechercher des jeux** par titre et d'afficher plus d’informations détaillées sur le jeu, comme la description, la catégorie et les évaluations des utilisateurs. 

#### Objectifs supplémentaires :
1. **Recherche de jeux par titre** :
   - Permettez à l'utilisateur de rechercher un jeu vidéo en tapant son titre. Récupérez les résultats correspondants à la recherche via l'API Steam.
   - Affichez une liste de jeux correspondants avec leurs prix.

2. **Affichage des détails du jeu** :
   - Pour chaque jeu trouvé, récupérez et affichez des détails supplémentaires, comme :
     - **Description** du jeu
     - **Catégories** et **tags**
     - **Évaluations** des utilisateurs (positives, négatives, etc.)
   
3. **Amélioration de l'architecture** :
   - Refactorisez votre code pour une meilleure séparation des responsabilités : création de nouvelles classes pour gérer les jeux, les résultats de recherche et les détails.
   - Appliquez les principes **SOLID** pour organiser correctement les classes et les méthodes.

4. **Gestion avancée des exceptions** :
   - Gérer les erreurs spécifiques comme les jeux non trouvés ou les interruptions de service de l’API.

#### Spécifications supplémentaires :
- **API** : Utilisez les fonctionnalités de recherche de jeux de l'API Steam.
- **Recherche dynamique** : Permettez à l’utilisateur de rechercher un jeu par son titre et de consulter les informations détaillées.
- **Refactorisation** : Améliorez la structure du code pour mieux séparer les responsabilités.
- **Gestion des exceptions** : Ajoutez des blocs `try-catch` plus précis pour gérer des erreurs spécifiques.

#### Notation (sur 16 points) :
- Recherche de **jeux par titre** : 3 points
- Diargamme de classe correcte : 2 points
- Affichage des **détails des jeux** : 4 points
- Respect des principes **SOLID** et refactorisation : 5 points
- Gestion des **exceptions avancées** : 2 points

---

### **Itération 03 : Classement et Suivi des Jeux Populaires avec Base de Données NoSQL (sur 20 points)**

#### Mission :
Pour cette troisième itération, vous allez ajouter une fonctionnalité de **classement des jeux les plus populaires** sur Steam et de **suivi** de certains jeux par l'utilisateur, en stockant ces informations dans une base de données NoSQL telle que MongoDB ou Redis.

#### Objectifs supplémentaires :
1. **Classement des jeux populaires** :
   - Ajoutez une fonctionnalité pour afficher les **jeux les plus populaires** sur Steam, en fonction des évaluations ou des ventes, récupérées via l’API.
   - Affichez une liste des jeux classés par popularité.

2. **Suivi des jeux** :
   - Permettez à l’utilisateur de **suivre** certains jeux pour voir leur évolution de prix ou de popularité au fil du temps.
   - Stockez ces jeux suivis dans une base NoSQL et récupérez les informations historiques à chaque nouvelle connexion.

3. **Stockage dans une base NoSQL** :
   - Utilisez MongoDB ou Redis pour stocker les jeux suivis et leur évolution.
   - Les données doivent inclure l'évolution des prix et des évaluations sur plusieurs jours.

4. **Amélioration continue de l'architecture** :
   - Refactorisez l’architecture du projet pour intégrer les nouvelles fonctionnalités de classement, de suivi et de stockage, tout en appliquant les principes SOLID.

#### Spécifications supplémentaires :
- **Classement des jeux populaires** : Implémentez la fonctionnalité d'affichage des jeux les plus populaires sur Steam.
- **Suivi des jeux** : Implémentez le suivi et l'historique des jeux suivis par l'utilisateur.
- **Base de données NoSQL** : Utilisez MongoDB ou Redis pour stocker les informations suivies.
- **Architecture SOLID** : Continuez à appliquer les principes SOLID en structurant les différentes couches de votre application.

#### Notation (sur 20 points) :
- Mise en place du **classement des jeux populaires** : 4 points
- Diargamme de classe correcte : 2 points
- Suivi des **jeux et historique des prix/évaluations** : 5 points
- Stockage dans une **base de données NoSQL** : 5 points
- Respect des principes **SOLID** et architecture propre : 3 points
- Gestion des **exceptions** liées à la base de données : 1 point

---

### Livrables :
- **Code source** pour les trois itérations (séparément).
- **Documentation** des fonctionnalités et de l’architecture.
- **Preuve de stockage des données** pour l’itération 3.

---

**Bonne chance pour ce projet !**
