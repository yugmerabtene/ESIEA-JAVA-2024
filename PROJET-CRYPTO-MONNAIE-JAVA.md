### Projet : Application de Consultation de Cryptomonnaies via API

#### Contexte global :
Dans ce projet, vous allez développer une application Java qui interagit avec une **API publique de cryptomonnaies** pour récupérer et afficher des informations en temps réel sur différentes devises. Le projet sera découpé en trois itérations, avec des fonctionnalités et des améliorations croissantes à chaque étape. Vous devrez utiliser les concepts de **programmation orientée objet (POO)**, les **principes SOLID**, et respecter les bonnes pratiques de **Clean Code**.

L’application interrogera une API gratuite (exemple : [CoinGecko](https://www.coingecko.com/fr/api)) pour obtenir des informations telles que les prix actuels des cryptomonnaies, leur variation et leur classement.

---

### **Itération 01 : Récupération et Affichage du Prix des Cryptomonnaies (sur 12 points)**

#### Mission :
Votre première mission est de développer une **application Java en ligne de commande** qui se connecte à une API publique pour récupérer le **prix actuel** d'une cryptomonnaie spécifique (par exemple, le Bitcoin) et l'afficher en temps réel. Cette étape vous permettra de vous familiariser avec l'interaction entre une application Java et une API REST.

#### Objectifs :
1. **Connexion à l'API** :
   - Utilisez une API de cryptomonnaies (comme CoinGecko) pour récupérer le prix d'une cryptomonnaie.
   - Effectuez des requêtes HTTP GET pour obtenir les données au format JSON.
   
2. **Affichage des données** :
   - Parsez la réponse JSON pour extraire et afficher le **prix** de la cryptomonnaie dans une devise donnée (par exemple, USD ou EUR).
   - Affichez ces informations de manière claire dans la console.

3. **Respect des principes POO, SOLID et Clean Code** :
   - **Interfaces** : Utilisez des interfaces pour séparer la logique d’interrogation de l’API de la présentation des données.
   - **SOLID** : Assurez une séparation claire des responsabilités pour faciliter la maintenance et l'évolution du code.
   - **Clean Code** : Codez de manière propre et lisible, en respectant les bonnes pratiques de Java.

4. **Gestion des exceptions** :
   - Gérez les erreurs potentielles liées à la connexion réseau et au parsing JSON avec des blocs `try-catch`.

#### Spécifications techniques :
- **API REST** : Utilisez l'API CoinGecko ou une autre API publique pour récupérer le prix des cryptomonnaies.
- **POO** : Appliquez les concepts d'**interfaces**, **polymorphisme**, et **classes abstraites** pour structurer l'application.
- **Gestion des exceptions** : Gérez les erreurs liées aux connexions réseau et à la récupération des données.

#### Notation (sur 12 points) :
- Connexion à l’API et récupération des données : 4 points
- Affichage correct du **prix des cryptomonnaies** : 4 points
- Respect des principes **SOLID** et **Clean Code** : 3 points
- Gestion des **exceptions** : 1 point

---

### **Itération 02 : Consultation des Variations et Classements (sur 16 points)**

#### Mission :
Dans cette deuxième itération, vous allez **étendre l’application** pour qu’elle affiche non seulement le prix, mais également les **variations** des prix (hausse/baisse) sur 24 heures et le **classement** de la cryptomonnaie dans le marché global. L'utilisateur doit pouvoir choisir une cryptomonnaie parmi plusieurs pour récupérer ces informations.

#### Objectifs supplémentaires :
1. **Consultation de plusieurs cryptomonnaies** :
   - Permettez à l'utilisateur de sélectionner une cryptomonnaie parmi une liste (par exemple, Bitcoin, Ethereum, etc.) pour en afficher le prix, la variation sur 24h et le classement global.

2. **Affichage des variations et du classement** :
   - Récupérez et affichez la **variation en pourcentage** du prix de la cryptomonnaie sur 24h.
   - Récupérez et affichez le **classement global** de la cryptomonnaie par capitalisation de marché.

3. **Amélioration de l'architecture** :
   - Refactorisez votre code pour mieux structurer la logique d’interrogation de l’API, le traitement des données, et l'affichage en appliquant les principes SOLID.

4. **Gestion des exceptions avancée** :
   - Ajoutez des blocs `try-catch` plus robustes pour gérer des erreurs spécifiques comme la **non-disponibilité de l’API** ou des **cryptomonnaies non trouvées**.

#### Spécifications supplémentaires :
- **API** : Interrogez l'API pour récupérer non seulement les prix, mais aussi la variation et le classement.
- **Sélection dynamique** : Permettez à l’utilisateur de choisir parmi plusieurs cryptomonnaies.
- **Refactorisation** : Améliorez la séparation des responsabilités pour une meilleure organisation du code.
- **Gestion des exceptions** : Ajoutez des blocs d'exceptions plus précis pour gérer des erreurs spécifiques.

#### Notation (sur 16 points) :
- Récupération et affichage des **variations** et du **classement** : 5 points
- Ajout de la sélection de cryptomonnaies : 3 points
- Respect des principes **SOLID** et **refactorisation** : 5 points
- Gestion des **exceptions avancées** : 3 points

---

### **Itération 03 : Suivi et Historique des Cryptomonnaies avec Base de Données NoSQL (sur 20 points)**

#### Mission :
Pour cette troisième itération, vous allez ajouter une fonctionnalité de **suivi continu** des prix des cryptomonnaies, ainsi qu’un **stockage des données** dans une base de données NoSQL de type **MongoDB** ou **Redis**. Les données stockées devront être historisées afin de permettre une **consultation des tendances** sur une période donnée.

#### Objectifs supplémentaires :
1. **Suivi continu** :
   - Ajoutez une fonctionnalité pour que l'application puisse surveiller automatiquement les **prix** des cryptomonnaies sur une période définie (par exemple, mise à jour toutes les heures).
   - Affichez les **tendances** des prix sur plusieurs jours ou heures.
   
2. **Stockage dans une base NoSQL** :
   - Stockez les informations sur les prix, les variations et le classement des cryptomonnaies dans une base NoSQL comme MongoDB ou Redis.
   - Les données doivent être historisées pour permettre une consultation ultérieure (par exemple, afficher l’évolution des prix sur 7 jours).

3. **Amélioration continue de l'architecture** :
   - Refactorisez l’architecture du projet pour intégrer proprement les nouvelles fonctionnalités de stockage et de suivi, tout en maintenant une application modulaire et respectueuse des principes SOLID.

#### Spécifications supplémentaires :
- **Suivi continu** : Implémentez une fonctionnalité de mise à jour automatique des prix avec historique.
- **Base de données NoSQL** : Utilisez MongoDB ou Redis pour stocker les données de manière historisée.
- **Architecture SOLID** : Continuez à appliquer les principes SOLID en structurant les différentes couches de votre application (API, base de données, suivi).

#### Notation (sur 20 points) :
- Mise en place du **suivi continu** et des tendances : 6 points
- Stockage dans une **base de données NoSQL** : 5 points
- Respect des principes **SOLID** et architecture propre : 4 points
- Gestion des **exceptions** liées à la base de données : 2 points

---

### Livrables :
- **Code source** pour les trois itérations (séparément).
- **Documentation** des fonctionnalités et de l’architecture.
- **Preuve de stockage des données** pour l’itération 3.

---

**Bonne chance pour ce projet !**
