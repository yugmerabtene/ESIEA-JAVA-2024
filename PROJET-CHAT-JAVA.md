### Projet : Application de Chat en Console avec Java

#### Contexte global :
Dans ce projet, vous allez développer une **application de chat** multi-utilisateurs en ligne de commande avec Java. Le projet sera divisé en trois itérations, chacune introduisant de nouvelles fonctionnalités et améliorations. Le respect des principes de **programmation orientée objet (POO)**, des **principes SOLID**, ainsi que les notions de **Clean Code** et de **chiffrement** des données seront essentiels à chaque étape.

Votre mission sera de concevoir une application bien structurée, fonctionnelle et testée à chaque itération, tout en vous conformant aux exigences supplémentaires définies pour chaque étape.

---

### **Itération 01 : Application de Chat en Console (sur 12 points)**

#### Mission :
Votre première mission est de concevoir une **application de chat en ligne de commande** où plusieurs utilisateurs peuvent se connecter à un serveur, envoyer des messages, et les recevoir en temps réel. Vous devrez respecter les **principes de la programmation orientée objet (POO)** ainsi que ceux du **SOLID** et du **Clean Code**.

#### Objectifs :
1. **Développement du serveur de chat** :
   - Le serveur doit accepter plusieurs connexions clients et diffuser les messages entre eux.
   - Chaque connexion doit être gérée dans un **thread** distinct pour permettre la communication simultanée.
   
2. **Développement du client de chat** :
   - Les clients doivent pouvoir se connecter au serveur via une adresse IP et un port, envoyer des messages, et recevoir les messages des autres clients en temps réel.

3. **Respect des principes POO, SOLID et Clean Code** :
   - **Interfaces** : Utilisez des interfaces pour définir les comportements communs des entités.
   - **Classes abstraites** : Centralisez les fonctionnalités communes dans des classes abstraites.
   - **Héritage et polymorphisme** : Implémentez ces concepts pour garantir une architecture évolutive.
   - **Enumérations** : Utilisez des énumérations pour les statuts des utilisateurs et les types de messages.
   - **SOLID** : Appliquez les principes SOLID pour assurer une conception flexible, modulaire, et facile à maintenir.
   - **Clean Code** : Respectez les principes de Clean Code en assurant des noms de variables explicites, des méthodes concises et une lisibilité globale du code.

4. **Gestion des exceptions** :
   - Entourez les opérations sensibles (connexion réseau, entrées/sorties) de blocs `try-catch` pour gérer les erreurs.

#### Spécifications techniques :
- **Multithreading** : Utilisez des threads pour gérer les connexions des clients de manière simultanée.
- **POO** : Utilisez des concepts d'**interfaces**, **héritage**, **polymorphisme**, **classes abstraites**, et **énumérations**.
- **SOLID** : Votre application doit respecter les principes **SOLID**.
- **Clean Code** : Le code doit être lisible, modulaire, et bien structuré.
- **Gestion des exceptions** : Traitez correctement les erreurs liées aux connexions réseau et aux entrées/sorties.

#### Notation (sur 12 points) :
- Respect des principes **POO** : 3 points
- Utilisation des **threads** et gestion multi-utilisateurs : 3 points
- Application des principes **SOLID** et **Clean Code** : 4 points
- Gestion correcte des **exceptions** : 2 points

---

### **Itération 02 : Application de Chat avec Chiffrement (sur 16 points)**

#### Mission :
Dans cette deuxième itération, vous allez **ajouter une couche de chiffrement** aux communications entre les clients et le serveur. Les messages doivent être chiffrés avant d’être envoyés et déchiffrés à la réception, en utilisant l'algorithme **AES (Advanced Encryption Standard)** avec une clé symétrique. Vous devrez également tester l'application avec **Wireshark** pour vous assurer que les messages ne sont pas visibles en clair sur le réseau.

#### Objectifs supplémentaires :
1. **Chiffrement des messages** :
   - Utilisez **AES** pour chiffrer les messages avant leur envoi et les déchiffrer à leur réception.
   - Le serveur et les clients doivent partager une clé de chiffrement symétrique.
   
2. **Tests avec Wireshark** :
   - Utilisez **Wireshark** pour capturer les communications réseau et vérifier que les messages ne sont pas visibles en clair.
   - Comparez les résultats avant et après l'ajout du chiffrement.

3. **Gestion des clés** :
   - Vous pouvez utiliser une clé statique ou mettre en place une phase d’**initialisation** pour échanger la clé de manière sécurisée.

4. **Gestion des exceptions liées au chiffrement** :
   - Utilisez des blocs `try-catch` pour gérer les exceptions spécifiques au chiffrement (ex : `InvalidKeyException`, `NoSuchAlgorithmException`).

#### Spécifications supplémentaires :
- **Chiffrement avec AES** : Utilisez une clé AES de **128 bits** avec la bibliothèque Java `javax.crypto`.
- **Wireshark** : Capturer le trafic réseau pour vérifier que les communications sont chiffrées.
- **Gestion des exceptions** : Ajoutez des blocs `try-catch` pour traiter les erreurs de chiffrement.

#### Notation (sur 16 points) :
- Implémentation correcte du **chiffrement** : 5 points
- Tests avec **Wireshark** (avant et après chiffrement) : 4 points
- Gestion des **exceptions liées au chiffrement** : 3 points
- Respect des principes **SOLID** et **Clean Code** (adaptation du code pour le chiffrement) : 4 points

---

### **Itération 03 : Application de Chat avec Base de Données NoSQL Redis (sur 20 points)**

#### Mission :
Pour cette troisième itération, vous allez ajouter une **base de données NoSQL de type Redis** pour stocker les messages échangés dans le chat. Les données stockées dans Redis devront être chiffrées avec une clé symétrique, similaire à celle utilisée pour les communications.

#### Objectifs supplémentaires :
1. **Intégration de Redis** :
   - Utilisez Redis pour stocker les messages échangés entre les utilisateurs.
   - Les messages doivent être **chiffrés avant d’être stockés** dans Redis, et déchiffrés lorsqu'ils sont récupérés.

2. **Chiffrement des données dans Redis** :
   - Utilisez le même algorithme AES pour chiffrer les messages avant de les stocker dans la base de données.
   
3. **Gestion des connexions à Redis** :
   - Gérez correctement la connexion à Redis et assurez-vous que les messages sont bien stockés et récupérés lors des sessions de chat.

4. **Respect des principes SOLID et Clean Code** :
   - Votre code doit être organisé et modulaire, en respectant les principes **SOLID** et **Clean Code**.

#### Spécifications supplémentaires :
- **Redis** : Utilisez Redis pour stocker et récupérer les messages du chat.
- **Chiffrement des données dans Redis** : Les messages doivent être chiffrés avant d’être stockés.
- **Gestion des exceptions** : Gérez les erreurs possibles liées aux connexions Redis et au chiffrement.

#### Notation (sur 20 points) :
- Intégration de **Redis** et stockage chiffré des messages : 6 points
- Implémentation du **chiffrement des données** dans Redis : 5 points
- Gestion correcte des **connexions Redis** : 3 points
- Respect des principes **SOLID** et **Clean Code** : 4 points
- Gestion des **exceptions liées à Redis et au chiffrement** : 2 points

---

### Livrables :
- **Code source** pour les trois itérations (séparément).
- **Documentation** des fonctionnalités et de l’architecture.
- **Résultats des tests Wireshark** pour l'itération 2.
- **Preuve de fonctionnement de Redis** avec capture de données chiffrées pour l'itération 3.

---

**Bonne chance pour vos différentes missions !**
