### Projet : Mod Minecraft de Synchronisation Météo via API

#### Contexte global :
Dans ce projet, vous allez développer un **mod Minecraft** en Java qui utilise une **API publique de météo** pour récupérer les conditions météorologiques en temps réel en fonction de la localisation du joueur et synchroniser la météo du jeu en conséquence. Le projet est structuré en trois itérations, avec des fonctionnalités croissantes à chaque étape. Ce projet met en pratique les concepts de **programmation orientée objet (POO)**, les **principes SOLID**, et les bonnes pratiques de **Clean Code**.

L’application interrogera l’API gratuite [Weatherstack](https://weatherstack.com/) pour obtenir des données en temps réel sur les conditions météorologiques (température, pluie, neige, etc.) et les appliquer à l’environnement de jeu Minecraft.

---

### **Itération 01 : Récupération et Affichage de la Météo en Temps Réel (sur 12 points)**

#### Mission :
Dans cette première étape, vous allez concevoir un mod Minecraft en Java qui interagit avec l’API Weatherstack pour récupérer les **conditions météorologiques en temps réel** en fonction d’une localisation prédéfinie (exemple : Paris) et les afficher dans le jeu. Cette itération vous aidera à vous familiariser avec l’interaction entre un mod Minecraft et une API REST.

#### Objectifs :
1. **Connexion à l'API** :
   - Utilisez l’API Weatherstack pour obtenir les conditions météorologiques actuelles pour une localisation spécifique.
   - Effectuez des requêtes HTTP GET pour recevoir des données au format JSON.

2. **Affichage des données** :
   - Parsez la réponse JSON pour extraire les informations principales sur la météo (température, conditions, pluie).
   - Affichez ces informations dans le chat ou l’interface du jeu Minecraft pour informer le joueur.

3. **Respect des principes POO, SOLID et Clean Code** :
   - **Interfaces** : Séparez la logique d’interrogation de l’API et l’affichage des données dans le jeu avec des interfaces.
   - **SOLID** : Appliquez des séparations de responsabilités pour une meilleure maintenabilité.
   - **Clean Code** : Assurez une structure de code propre et lisible selon les conventions Java.

4. **Gestion des exceptions** :
   - Gérez les erreurs potentielles liées à la connexion réseau et au parsing JSON via des blocs `try-catch`.

#### Spécifications techniques :
- **API REST** : Utilisez Weatherstack pour obtenir les données météorologiques.
- **POO** : Appliquez les concepts d'**interfaces**, **polymorphisme**, **classes abstraites** pour structurer l’application.
- **Gestion des exceptions** : Gérez les erreurs liées aux connexions et aux données manquantes.

#### Notation (sur 12 points) :
- Connexion API et récupération des données : 4 points
- Affichage des informations météo dans le jeu : 2 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et **Clean Code** : 3 points
- Gestion des **exceptions** : 1 point

---

### **Itération 02 : Synchronisation Dynamique de la Météo dans Minecraft (sur 16 points)**

#### Mission :
Dans cette deuxième étape, vous allez **étendre le mod** pour appliquer automatiquement les **conditions météorologiques réelles** (température, pluie, neige, etc.) dans Minecraft, synchronisant ainsi l’environnement du jeu avec la météo réelle.

#### Objectifs supplémentaires :
1. **Synchronisation de la météo** :
   - Transformez les informations récupérées de l’API en effets visuels dans Minecraft (exemple : pluie, neige, ensoleillement).
   - Synchronisez les effets de météo dans le jeu avec les conditions réelles mises à jour périodiquement.

2. **Contrôle des conditions météorologiques** :
   - Permettez à l’utilisateur de configurer la localisation à suivre ou d’utiliser l’emplacement GPS local si possible.
   - Ajoutez une interface utilisateur dans le jeu pour activer/désactiver la synchronisation météo.

3. **Amélioration de l’architecture** :
   - Refactorisez le code pour structurer la logique d’interrogation de l’API, le traitement des données et la synchronisation dans le jeu en appliquant les principes SOLID.

4. **Gestion des exceptions avancée** :
   - Ajoutez des blocs `try-catch` robustes pour gérer les erreurs d’accès à l’API ou de paramètres invalides.

#### Spécifications supplémentaires :
- **API** : Récupérez les données de manière périodique pour synchroniser la météo en temps réel.
- **Configuration** : Donnez la possibilité de définir ou changer la localisation.
- **Refactorisation** : Pour une meilleure organisation du code.
- **Gestion des exceptions** : Gérer des erreurs spécifiques liées à l’API.

#### Notation (sur 16 points) :
- Synchronisation des conditions météorologiques : 5 points
- Contrôle de la localisation et configuration utilisateur : 3 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et **refactorisation** : 5 points
- Gestion des **exceptions avancées** : 1 point

---

### **Itération 03 : Historisation et Gestion des Données Météo avec Base de Données NoSQL (sur 20 points)**

#### Mission :
Pour cette dernière étape, vous allez ajouter une fonctionnalité de **stockage des données météo** dans une base de données NoSQL, permettant ainsi de **garder un historique des conditions météorologiques** et d'appliquer des changements en fonction des tendances (exemple : tempête prolongée dans le jeu si la pluie dure plusieurs jours).

#### Objectifs supplémentaires :
1. **Historisation de la météo** :
   - Enregistrez les conditions météorologiques au fil du temps dans une base de données NoSQL (ex. : MongoDB, Redis) pour garder un historique et influencer les conditions météorologiques du jeu.

2. **Analyse des tendances** :
   - Utilisez l’historique pour déterminer les conditions à venir dans le jeu (par exemple, tempête après plusieurs jours de pluie dans la réalité).
   - Affichez dans le jeu des tendances météorologiques, comme un bulletin météo.

3. **Amélioration continue de l'architecture** :
   - Refactorisez l’architecture du mod pour intégrer les nouvelles fonctionnalités de stockage et d’analyse des tendances, tout en maintenant le respect des principes SOLID.

#### Spécifications supplémentaires :
- **Historisation de la météo** : Enregistrez et consultez les données dans une base NoSQL.
- **Prédictions et tendances** : Ajoutez des fonctionnalités d’analyse de tendances météorologiques.
- **Architecture SOLID** : Continuez à structurer les différentes couches du mod de manière modulaire.

#### Notation (sur 20 points) :
- Historisation des données météo : 5 points
- Analyse des tendances météorologiques : 4 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et architecture modulaire : 5 points
- Gestion des **exceptions** liées à la base de données : 2 points

---

### Livrables :
- **Code source** pour les trois itérations.
- **Documentation** des fonctionnalités et de l’architecture.
- **Preuve de stockage des données** et des tendances pour l’itération 3.

---

**Bonne chance pour ce projet de mod Minecraft !**
