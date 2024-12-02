## 1-arrayList

Une **ArrayList** en Java est une structure de données basée sur un tableau dynamique qui permet de stocker des éléments (objets) de manière flexible, sans avoir besoin de spécifier sa taille initiale.
---
Voici un exemple complet avec **toutes les principales méthodes de l'`ArrayList`** en Java, utilisé dans un contexte pratique.
Exemple-01
### Code complet
```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        // Création d'une ArrayList de type String
        ArrayList<String> items = new ArrayList<>();

        // 1. Ajout d'éléments avec add()
        items.add("Épée");
        items.add("Bouclier");
        items.add("Potion");
        items.add("Arc");
        System.out.println("Liste initiale : " + items);

        // 2. Insertion à un index spécifique avec add(index, element)
        items.add(2, "Flèche");
        System.out.println("Après insertion à l'index 2 : " + items);

        // 3. Récupération d'un élément avec get()
        System.out.println("Élément à l'index 1 : " + items.get(1));

        // 4. Modification d'un élément avec set()
        items.set(0, "Épée magique");
        System.out.println("Après modification de l'élément à l'index 0 : " + items);

        // 5. Suppression d'un élément par index avec remove(index)
        items.remove(3);
        System.out.println("Après suppression de l'élément à l'index 3 : " + items);

        // 6. Suppression d'un élément par valeur avec remove(object)
        items.remove("Flèche");
        System.out.println("Après suppression de l'élément 'Flèche' : " + items);

        // 7. Vérification de la présence d'un élément avec contains()
        System.out.println("Contient 'Potion' ? " + items.contains("Potion"));

        // 8. Taille de la liste avec size()
        System.out.println("Taille de la liste : " + items.size());

        // 9. Vérification si la liste est vide avec isEmpty()
        System.out.println("La liste est-elle vide ? " + items.isEmpty());

        // 10. Parcours avec une boucle for-each
        System.out.println("Parcours avec une boucle for-each :");
        for (String item : items) {
            System.out.println("- " + item);
        }

        // 11. Conversion en tableau avec toArray()
        Object[] itemsArray = items.toArray();
        System.out.print("Liste convertie en tableau : ");
        for (Object obj : itemsArray) {
            System.out.print(obj + " ");
        }
        System.out.println();

        // 12. Suppression de tous les éléments avec clear()
        items.clear();
        System.out.println("Après avoir vidé la liste avec clear() : " + items);
    }
}
```

---

### Explications des méthodes principales utilisées :

1. **`add(element)`**  
   Ajoute un élément à la fin de la liste.

2. **`add(index, element)`**  
   Insère un élément à un index spécifique.

3. **`get(index)`**  
   Récupère l'élément à un index donné.

4. **`set(index, element)`**  
   Remplace l'élément à un index donné par un autre élément.

5. **`remove(index)`**  
   Supprime l'élément à l'index donné.

6. **`remove(object)`**  
   Supprime le premier élément égal à la valeur donnée.

7. **`contains(object)`**  
   Vérifie si un élément est présent dans la liste.

8. **`size()`**  
   Renvoie le nombre d'éléments dans la liste.

9. **`isEmpty()`**  
   Vérifie si la liste est vide.

10. **`toArray()`**  
    Convertit l'`ArrayList` en tableau.

11. **`clear()`**  
    Supprime tous les éléments de la liste.

---

### Résultat attendu :
```plaintext
Liste initiale : [Épée, Bouclier, Potion, Arc]
Après insertion à l'index 2 : [Épée, Bouclier, Flèche, Potion, Arc]
Élément à l'index 1 : Bouclier
Après modification de l'élément à l'index 0 : [Épée magique, Bouclier, Flèche, Potion, Arc]
Après suppression de l'élément à l'index 3 : [Épée magique, Bouclier, Flèche, Arc]
Après suppression de l'élément 'Flèche' : [Épée magique, Bouclier, Arc]
Contient 'Potion' ? false
Taille de la liste : 3
La liste est-elle vide ? false
Parcours avec une boucle for-each :
- Épée magique
- Bouclier
- Arc
Liste convertie en tableau : Épée magique Bouclier Arc 
Après avoir vidé la liste avec clear() : []
```
---

### **Caractéristiques principales d'une ArrayList**

1. **Taille dynamique** :
   - Une ArrayList ajuste automatiquement sa taille pour s'adapter aux ajouts ou suppressions d'éléments.

2. **Accès rapide par index** :
   - L'accès à un élément via son index est direct et très rapide (\(O(1)\)).

3. **Permet les doublons** :
   - Une ArrayList peut contenir plusieurs fois la même valeur.

4. **Ordre des éléments** :
   - L'ordre d'insertion des éléments est conservé.

5. **Pas thread-safe** :
   - L'utilisation dans des environnements multi-threads nécessite une synchronisation explicite.

---

### **Fonctionnement des opérations dans une ArrayList**

#### 1. **Ajout d'un élément**
- Les éléments sont ajoutés à la fin par défaut.
- Si la capacité actuelle est insuffisante, l'ArrayList crée un tableau plus grand et copie les anciens éléments.

**Complexité** :
- \(O(1)\) pour un ajout simple.
- \(O(n)\) si un redimensionnement est nécessaire.

#### 2. **Accès à un élément**
- L'accès à un élément se fait directement via son index.

**Complexité** : \(O(1)\).

#### 3. **Suppression d'un élément**
- Après suppression, les éléments suivants sont déplacés pour combler l'espace.

**Complexité** : \(O(n)\).

#### 4. **Recherche d'un élément**
- La recherche d'un élément nécessite un parcours de la liste.

**Complexité** : \(O(n)\).

---

### **Exemple-02 avec ArrayList**

#### Création et manipulation
```java
import java.util.ArrayList;

public class Example {
    public static void main(String[] args) {
        // Création d'une ArrayList
        ArrayList<String> list = new ArrayList<>();

        // Ajout d'éléments
        list.add("Alice");
        list.add("Bob");
        list.add("Charlie");

        // Affichage des éléments
        System.out.println("Liste : " + list);

        // Accès à des éléments
        System.out.println("Premier élément : " + list.get(0));
        System.out.println("Deuxième élément : " + list.get(1));

        // Suppression d'un élément
        list.remove(1); // Supprime l'élément à l'index 1 (Bob)
        System.out.println("Liste après suppression : " + list);

        // Recherche d'un élément
        boolean containsAlice = list.contains("Alice");
        System.out.println("Contient 'Alice' ? " + containsAlice);

        // Taille de la liste
        System.out.println("Taille de la liste : " + list.size());
    }
}
```

---

### **Quand utiliser une ArrayList ?**

1. **Accès rapide par index** :
   - Idéal si vous accédez souvent aux éléments par leur position.

2. **Ajout principalement à la fin** :
   - Les ajouts en fin de liste sont rapides et efficaces.

3. **Peu de suppressions ou réarrangements** :
   - Une ArrayList est plus efficace lorsque les suppressions ou réarrangements d'éléments sont rares.

---




### EXO-01  
### Structure des Fichiers
```
src/
│
├── controllers/
│   ├── UserController.java
│   └── IUserController.java
│
├── models/
│   └── User.java
│
├── views/
│   └── UserView.java
│
├── services/
│   ├── UserService.java
│   └── IUserService.java
│
└── app
    └──Main.java
```

### Code de chaque fichier

**1. Fichier `src/models/User.java`**
```java
package models;

public class User {
    private String id;
    private String name;
    private String email;

    public User(String id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    // Getters et setters
    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

**2. Fichier `src/services/IUserService.java`**
```java
package services;

import models.User;
import java.util.List;

public interface IUserService {
    void addUser(User user);
    User getUserById(String id);
    List<User> getAllUsers();
}
```

**3. Fichier `src/services/UserService.java`**
```java
package services;

import models.User;
import java.util.ArrayList;
import java.util.List;

public class UserService implements IUserService {
    private List<User> users = new ArrayList<>(); // Utilisation d'ArrayList pour stocker les utilisateurs

    @Override
    public void addUser(User user) {
        users.add(user);
        System.out.println("Utilisateur ajouté : " + user.getName());
    }

    @Override
    public User getUserById(String id) {
        for (User user : users) {
            if (user.getId().equals(id)) {
                return user;
            }
        }
        return null;
    }

    @Override
    public List<User> getAllUsers() {
        return users;
    }
}
```

**Explication des `ArrayList`** :
- Une `ArrayList` est une collection dynamique qui peut contenir des objets. Contrairement à un tableau statique, elle peut changer de taille automatiquement lorsqu'on y ajoute ou retire des éléments.
- Les méthodes courantes incluent `add()` pour ajouter des éléments, `get()` pour accéder à un élément à un index spécifique, et `size()` pour obtenir la taille de la liste.

**4. Fichier `src/views/UserView.java`**
```java
package views;

import models.User;
import java.util.List;

public class UserView {
    public void displayUser(User user) {
        if (user != null) {
            System.out.println("Détails de l'utilisateur :");
            System.out.println("ID : " + user.getId());
            System.out.println("Nom : " + user.getName());
            System.out.println("Email : " + user.getEmail());
        } else {
            System.out.println("Utilisateur non trouvé.");
        }
    }

    public void displayAllUsers(List<User> users) {
        System.out.println("Liste des utilisateurs :");
        for (User user : users) {
            System.out.println("ID : " + user.getId() + ", Nom : " + user.getName() + ", Email : " + user.getEmail());
        }
    }
}
```

**5. Fichier `src/controllers/IUserController.java`**
```java
package controllers;

public interface IUserController {
    void addUser(String id, String name, String email);
    void showUser(String id);
    void showAllUsers();
}
```

**6. Fichier `src/controllers/UserController.java`**
```java
package controllers;

import models.User;
import services.IUserService;
import views.UserView;

public class UserController implements IUserController {
    private IUserService userService;
    private UserView userView;

    public UserController(IUserService userService, UserView userView) {
        this.userService = userService;
        this.userView = userView;
    }

    @Override
    public void addUser(String id, String name, String email) {
        User user = new User(id, name, email);
        userService.addUser(user);
    }

    @Override
    public void showUser(String id) {
        User user = userService.getUserById(id);
        userView.displayUser(user);
    }

    @Override
    public void showAllUsers() {
        userView.displayAllUsers(userService.getAllUsers());
    }
}
```

**7. Fichier `src/Main.java`**
```java
import controllers.UserController;
import services.UserService;
import views.UserView;

public class Main {
    public static void main(String[] args) {
        // Initialisation des services et des vues
        UserService userService = new UserService();
        UserView userView = new UserView();
        UserController userController = new UserController(userService, userView);

        // Ajout de quelques utilisateurs
        userController.addUser("1", "Alice", "alice@example.com");
        userController.addUser("2", "Bob", "bob@example.com");
        userController.addUser("3", "Charlie", "charlie@example.com");

        // Affichage des détails d'un utilisateur
        userController.showUser("2");

        // Affichage de tous les utilisateurs
        userController.showAllUsers();
    }
}
```

### Explication de l'architecture MVC
- **Interfaces (`IUserService`, `IUserController`)** : Fournissent un contrat que les classes `UserService` et `UserController` implémentent, permettant de respecter les principes SOLID (interface segregation).
- **`ArrayList`** : Utilisée dans la classe `UserService` pour gérer dynamiquement la liste des utilisateurs, ajoutant et accédant facilement aux données.
- **Couche de service** : Contient la logique métier liée à la gestion des utilisateurs.
- **Couche de contrôleur** : Gère l'interaction entre la vue et la couche de service.
- **Vue** : Responsable de l'affichage des informations à l'utilisateur.

Cette structure modulaire rend le code plus facile à maintenir et à étendre.  

### Exo-02        

### Énoncé du TP : Système de Gestion d'Utilisateurs avec Menu Interactif

#### Description Technique
Ce TP consiste à développer un programme Java pour gérer un système d'utilisateurs avec une architecture en couches (Modèle-Vue-Contrôleur - MVC). L'application permettra à un administrateur d'effectuer les opérations suivantes :
- Ajouter un utilisateur
- Supprimer un utilisateur par ID
- Rechercher un utilisateur par ID ou par nom
- Afficher tous les utilisateurs
- Quitter le programme

L'architecture du programme utilise des `ArrayList` pour stocker dynamiquement les utilisateurs et suit un modèle MVC structuré en dossiers.

### Architecture des Dossiers
```
src/
│
├── controllers/
│   ├── IUserController.java
│   └── UserController.java
│
├── models/
│   └── User.java
│
├── services/
│   ├── IUserService.java
│   └── UserService.java
│
├── views/
│   └── UserView.java
│
└── Main.java
```

### Code Complet

**1. Fichier `src/models/User.java`**
```java
package models;

public class User {
    private String id;
    private String name;
    private String email;

    public User(String id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    // Getters et setters
    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

**2. Fichier `src/services/IUserService.java`**
```java
package services;

import models.User;
import java.util.List;

public interface IUserService {
    void addUser(User user);
    void removeUserById(String id);
    User getUserById(String id);
    User getUserByName(String name);
    List<User> getAllUsers();
}
```

**3. Fichier `src/services/UserService.java`**
```java
package services;

import models.User;
import java.util.ArrayList;
import java.util.List;

public class UserService implements IUserService {
    private List<User> users = new ArrayList<>();

    @Override
    public void addUser(User user) {
        users.add(user);
        System.out.println("Utilisateur ajouté : " + user.getName());
    }

    @Override
    public void removeUserById(String id) {
        users.removeIf(user -> user.getId().equals(id));
        System.out.println("Utilisateur avec l'ID " + id + " supprimé.");
    }

    @Override
    public User getUserById(String id) {
        for (User user : users) {
            if (user.getId().equals(id)) {
                return user;
            }
        }
        return null;
    }

    @Override
    public User getUserByName(String name) {
        for (User user : users) {
            if (user.getName().equalsIgnoreCase(name)) {
                return user;
            }
        }
        return null;
    }

    @Override
    public List<User> getAllUsers() {
        return users;
    }
}
```

**4. Fichier `src/views/UserView.java`**
```java
package views;

import models.User;
import java.util.List;

public class UserView {
    public void displayUser(User user) {
        if (user != null) {
            System.out.println("Détails de l'utilisateur :");
            System.out.println("ID : " + user.getId());
            System.out.println("Nom : " + user.getName());
            System.out.println("Email : " + user.getEmail());
        } else {
            System.out.println("Utilisateur non trouvé.");
        }
    }

    public void displayAllUsers(List<User> users) {
        System.out.println("Liste des utilisateurs :");
        for (User user : users) {
            System.out.println("ID : " + user.getId() + ", Nom : " + user.getName() + ", Email : " + user.getEmail());
        }
    }

    public void displayMessage(String message) {
        System.out.println(message);
    }
}
```

**5. Fichier `src/controllers/IUserController.java`**
```java
package controllers;

public interface IUserController {
    void addUser(String id, String name, String email);
    void removeUser(String id);
    void searchUserById(String id);
    void searchUserByName(String name);
    void showAllUsers();
}
```

**6. Fichier `src/controllers/UserController.java`**
```java
package controllers;

import models.User;
import services.IUserService;
import views.UserView;

public class UserController implements IUserController {
    private IUserService userService;
    private UserView userView;

    public UserController(IUserService userService, UserView userView) {
        this.userService = userService;
        this.userView = userView;
    }

    @Override
    public void addUser(String id, String name, String email) {
        User user = new User(id, name, email);
        userService.addUser(user);
    }

    @Override
    public void removeUser(String id) {
        userService.removeUserById(id);
        userView.displayMessage("Utilisateur supprimé avec l'ID : " + id);
    }

    @Override
    public void searchUserById(String id) {
        User user = userService.getUserById(id);
        userView.displayUser(user);
    }

    @Override
    public void searchUserByName(String name) {
        User user = userService.getUserByName(name);
        userView.displayUser(user);
    }

    @Override
    public void showAllUsers() {
        userView.displayAllUsers(userService.getAllUsers());
    }
}
```

**7. Fichier `src/Main.java`**
```java
import controllers.UserController;
import services.UserService;
import views.UserView;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        UserService userService = new UserService();
        UserView userView = new UserView();
        UserController userController = new UserController(userService, userView);

        Scanner scanner = new Scanner(System.in);
        boolean running = true;

        while (running) {
            System.out.println("\nMenu:");
            System.out.println("1. Ajouter un utilisateur");
            System.out.println("2. Supprimer un utilisateur par ID");
            System.out.println("3. Rechercher un utilisateur par ID");
            System.out.println("4. Rechercher un utilisateur par nom");
            System.out.println("5. Afficher tous les utilisateurs");
            System.out.println("6. Quitter");
            System.out.print("Choisissez une option : ");

            int choix = scanner.nextInt();
            scanner.nextLine(); // Consomme la nouvelle ligne

            switch (choix) {
                case 1:
                    System.out.print("Entrez l'ID : ");
                    String id = scanner.nextLine();
                    System.out.print("Entrez le nom : ");
                    String name = scanner.nextLine();
                    System.out.print("Entrez l'email : ");
                    String email = scanner.nextLine();
                    userController.addUser(id, name, email);
                    break;
                case 2:
                    System.out.print("Entrez l'ID de l'utilisateur à supprimer : ");
                    String idToRemove = scanner.nextLine();
                    userController.removeUser(idToRemove);
                    break;
                case 3:
                    System.out.print("Entrez l'ID de l'utilisateur à rechercher : ");
                    String idToSearch = scanner.nextLine();
                    userController.searchUserById(idToSearch);
                    break;
                case 4:
                    System.out.print("Entrez le nom de l'utilisateur à rechercher : ");
                    String nameToSearch = scanner.nextLine();
                    userController.searchUserByName(nameToSearch);
                    break;
                case 5:
                    userController.showAllUsers();
                    break;
                case 6:
                    running = false;
                    System.out.println("Programme terminé.");
                    break;
                default:
                    System.out.println("Option invalide. Veuillez réessayer.");
                    break;
            }
        }
        scanner.close();
    }
}
```

### Instructions pour le TP
1. **Organisation des fichiers** : Placez chaque fichier Java dans les dossiers spécifiés.
2. **Compilation et exécution** : Compilez et exécutez `Main.java` pour lancer l'application.
3. **Utilisation** : Utilisez le menu interactif pour tester les fonctionnalités du programme.
