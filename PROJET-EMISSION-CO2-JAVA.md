**Projet** : Application de Suivi de l'Empreinte Carbone via API  
**Contexte global** :  
Dans ce projet, vous allez développer une application Java qui interagit avec l'API publique **ImpactCO2** pour récupérer et afficher des informations sur les émissions de CO2 générées par différentes activités (transports, consommation énergétique, etc.). Le projet sera divisé en trois itérations avec des fonctionnalités et des améliorations croissantes à chaque étape. Vous appliquerez les concepts de programmation orientée objet (POO), les principes SOLID, et les bonnes pratiques de Clean Code.

L'application interrogera l'API gratuite ImpactCO2 pour obtenir des données sur les émissions de carbone en fonction des activités et affichera les résultats de manière claire et informative.

### Itération 01 : Calcul et Affichage des Émissions de CO2 pour une Activité (sur 12 points)
- **Mission** : Développez une application Java en ligne de commande qui se connecte à l'API ImpactCO2 pour récupérer les émissions de CO2 d'une activité spécifique (par exemple, un trajet en voiture) et les afficher.
  
- **Objectifs** :  
  - **Connexion à l'API** :
    - Utilisez l'API ImpactCO2 pour obtenir les données d'émissions d'une activité donnée.
    - Effectuez des requêtes HTTP GET pour récupérer les données au format JSON.
  - **Affichage des données** :
    - Parsez la réponse JSON pour extraire et afficher les émissions de CO2 calculées pour l'activité.
    - Présentez ces informations de manière lisible dans la console.
  - **Respect des principes POO, SOLID et Clean Code** :
    - **Interfaces** : Séparez la logique d’interrogation de l’API de la présentation des données.
    - **SOLID** : Assurez une séparation claire des responsabilités.
    - **Clean Code** : Codez de manière propre et lisible, en respectant les bonnes pratiques de Java.
  - **Gestion des exceptions** :
    - Gérez les erreurs potentielles liées à la connexion réseau et au parsing JSON avec des blocs try-catch.

- **Spécifications techniques** :
  - **API REST** : Utilisez l'API ImpactCO2 pour récupérer les données d'émissions.
  - **POO** : Appliquez les concepts d'interfaces, polymorphisme et classes abstraites pour structurer l'application.
  - **Gestion des exceptions** : Gérez les erreurs liées aux connexions réseau et à la récupération des données.

- **Notation (sur 12 points)** :
  - Connexion à l'API et récupération des données : 3 points
  - Affichage correct des émissions de CO2 : 3 points
  - Diargamme de classe correcte : 2 points
  - Respect des principes SOLID et Clean Code : 3 points
  - Gestion des exceptions : 1 point

---

### Itération 02 : Consultation des Émissions de CO2 pour Plusieurs Activités (sur 16 points)
- **Mission** : Étendez l’application pour afficher les émissions de CO2 générées par plusieurs types d’activités, avec la possibilité pour l'utilisateur de choisir parmi une liste d'activités.

- **Objectifs supplémentaires** :  
  - **Consultation de plusieurs activités** :
    - Permettez à l'utilisateur de sélectionner une activité parmi une liste (par exemple, transport, alimentation, énergie) pour obtenir l'empreinte carbone associée.
  - **Affichage des émissions pour chaque activité** :
    - Récupérez et affichez les émissions de CO2 pour chaque activité sélectionnée.
  - **Amélioration de l'architecture** :
    - Refactorisez le code pour mieux structurer la logique d’interrogation de l’API, le traitement des données, et l'affichage, en appliquant les principes SOLID.
  - **Gestion des exceptions avancée** :
    - Ajoutez des blocs try-catch plus robustes pour gérer des erreurs spécifiques comme la non-disponibilité de l’API ou une activité non trouvée.

- **Spécifications supplémentaires** :
  - **API** : Interrogez l'API pour obtenir les émissions de plusieurs activités.
  - **Sélection dynamique** : Permettez à l’utilisateur de choisir parmi plusieurs activités.
  - **Refactorisation** : Améliorez la séparation des responsabilités pour une meilleure organisation du code.
  - **Gestion des exceptions** : Ajoutez des blocs d'exceptions pour gérer des erreurs spécifiques.

- **Notation (sur 16 points)** :
  - Récupération et affichage des émissions pour plusieurs activités : 3 points
  - Diargamme de classe correcte : 2 points
  - Ajout de la sélection d'activités : 3 points
  - Respect des principes SOLID et refactorisation : 5 points
  - Gestion des exceptions avancée : 3 points

---

### Itération 03 : Suivi et Historique des Émissions de CO2 avec Base de Données NoSQL (sur 20 points)
- **Mission** : Ajoutez une fonctionnalité de suivi des émissions de CO2 pour chaque activité et enregistrez les données dans une base de données NoSQL, permettant une consultation de l'historique.

- **Objectifs supplémentaires** :
  - **Suivi continu** :
    - Ajoutez une fonctionnalité pour surveiller les émissions de CO2 sur une période définie (par exemple, une mise à jour toutes les heures pour certaines activités).
    - Affichez les tendances des émissions sur plusieurs jours.
  - **Stockage dans une base NoSQL** :
    - Stockez les émissions de CO2 pour chaque activité dans une base NoSQL comme MongoDB ou Redis.
    - Historisez les données pour une consultation ultérieure et affichez les tendances des émissions sur une période (par exemple, l'évolution des émissions mensuelles).
  - **Amélioration continue de l'architecture** :
    - Refactorisez l'architecture pour intégrer les nouvelles fonctionnalités de stockage et de suivi tout en respectant les principes SOLID.

- **Spécifications supplémentaires** :
  - **Suivi continu** : Implémentez une fonctionnalité de mise à jour automatique avec historique.
  - **Base de données NoSQL** : Utilisez MongoDB ou Redis pour stocker les données de manière historisée.
  - **Architecture SOLID** : Continuez à appliquer les principes SOLID en structurant les différentes couches de votre application (API, base de données, suivi).

- **Notation (sur 20 points)** :
  - Mise en place du suivi continu et des tendances : 4 points
  - Diargamme de classe correcte : 2 points
  - Stockage dans une base de données NoSQL : 5 points
  - Respect des principes SOLID et architecture propre : 4 points
  - Gestion des exceptions liées à la base de données : 2 points

---

**Livrables** :
- Code source pour les trois itérations (séparément).
- Documentation des fonctionnalités et de l’architecture.
- Preuve de stockage des données pour l’itération 3.
