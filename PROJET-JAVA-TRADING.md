### Projet : Application de Trading en Temps Réel via une API Financière

#### Contexte global :
Ce projet consiste à développer une application Java qui se connecte à une **API publique de trading** pour récupérer et afficher des informations financières en temps réel sur divers actifs (actions, devises, cryptomonnaies, etc.). Le projet sera découpé en trois itérations avec une complexité croissante, couvrant des fonctionnalités supplémentaires à chaque étape. Vous devrez appliquer les principes de **programmation orientée objet (POO)**, **SOLID**, ainsi que les bonnes pratiques de **Clean Code**.

L'application utilisera une API financière gratuite (exemple : [Alpha Vantage](https://www.alphavantage.co/documentation/)) pour obtenir des données sur les prix en temps réel, les variations de marché, et des indicateurs financiers.

---

### **Itération 01 : Récupération et Affichage du Prix d'un Actif Financier (sur 12 points)**

#### Mission :
Votre première tâche est de concevoir une **application Java en ligne de commande** capable de se connecter à une API financière pour obtenir et afficher le **prix actuel** d’un actif particulier (exemple : une action ou une cryptomonnaie). Cette étape vous aidera à maîtriser l’interaction entre une application Java et une API REST.

#### Objectifs :
1. **Connexion à l'API** :
   - Utilisez une API publique comme Alpha Vantage pour récupérer le prix d'un actif.
   - Effectuez des requêtes HTTP GET pour recevoir des données en JSON.

2. **Affichage des données** :
   - Parsez le JSON pour extraire et afficher le **prix** de l’actif choisi dans une devise (ex. USD ou EUR).
   - Présentez ces informations de manière claire dans la console.

3. **Respect des principes POO, SOLID et Clean Code** :
   - **Interfaces** : Séparez la logique de récupération de l’API et la présentation des données via des interfaces.
   - **SOLID** : Appliquez une séparation des responsabilités pour un code maintenable et évolutif.
   - **Clean Code** : Code lisible et bien structuré respectant les conventions de Java.

4. **Gestion des exceptions** :
   - Gérez les erreurs potentielles liées au réseau et au parsing JSON via `try-catch`.

#### Spécifications techniques :
- **API REST** : Utilisez Alpha Vantage ou une autre API publique.
- **POO** : Concepts d'**interfaces**, **polymorphisme**, **classes abstraites** pour structurer l'application.
- **Gestion des exceptions** : Prévoir les erreurs liées aux connexions et récupération de données.

#### Notation (sur 12 points) :
- Connexion API et récupération de données : 4 points
- Affichage du **prix de l’actif** : 2 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** et **Clean Code** : 3 points
- Gestion des **exceptions** : 1 point

---

### **Itération 02 : Affichage des Variations et Consultation de Plusieurs Actifs (sur 16 points)**

#### Mission :
Dans cette itération, étendez l’application pour qu’elle affiche non seulement le prix, mais aussi les **variations** des prix (hausse/baisse) sur une période définie, et permettez à l'utilisateur de consulter différents actifs financiers.

#### Objectifs supplémentaires :
1. **Consultation de plusieurs actifs financiers** :
   - Permettre à l'utilisateur de sélectionner un actif (action, devise, crypto) pour consulter ses variations et son prix actuel.

2. **Affichage des variations** :
   - Affichez les **variations en pourcentage** sur une journée ou une semaine.

3. **Amélioration de l'architecture** :
   - Refactorisez pour organiser les fonctionnalités en respectant les principes SOLID.

4. **Gestion des exceptions avancée** :
   - Ajouter des blocs `try-catch` plus spécifiques pour traiter des erreurs comme l'indisponibilité de l'API ou la non-existence d'un actif.

#### Spécifications supplémentaires :
- **API** : Récupérez les prix, variations.
- **Sélection dynamique** : Permettez à l’utilisateur de choisir parmi plusieurs actifs.
- **Refactorisation** : Pour une meilleure organisation.
- **Gestion des exceptions** : Gérer des erreurs spécifiques.

#### Notation (sur 16 points) :
- Récupération et affichage des **variations** : 4 points
- Consultation de différents actifs : 3 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** : 5 points
- Gestion des **exceptions avancées** : 2 points

---

### **Itération 03 : Suivi en Temps Réel et Historisation dans une Base de Données (sur 20 points)**

#### Mission :
Pour cette dernière itération, ajoutez une fonctionnalité de **suivi continu** et **historisez** les prix dans une base de données NoSQL (MongoDB, Redis) pour permettre une consultation historique.

#### Objectifs supplémentaires :
1. **Suivi en temps réel** :
   - L'application mettra à jour automatiquement les prix à intervalle régulier et affichera les **tendances**.

2. **Stockage dans une base NoSQL** :
   - Stockez prix et variations pour consultation historique (ex : évolution sur 7 jours).

3. **Amélioration continue de l'architecture** :
   - Refactorisez pour intégrer les nouvelles fonctionnalités en respectant SOLID.

#### Spécifications supplémentaires :
- **Suivi continu** : Implémentez une mise à jour automatique.
- **Base NoSQL** : Utilisez MongoDB ou Redis.
- **Architecture SOLID** : Structurer les différentes couches.

#### Notation (sur 20 points) :
- Mise en place du **suivi en temps réel** : 5 points
- Historisation dans une base NoSQL : 5 points
- Diagramme de classe : 2 points
- Respect des principes **SOLID** : 4 points
- Gestion des **exceptions liées à la base de données** : 2 points

---

### Livrables :
- **Code source** pour les trois itérations.
- **Documentation** des fonctionnalités et architecture.
- **Preuve de stockage historique** pour l’itération 3.

---

**Bonne chance pour ce projet de trading !**
