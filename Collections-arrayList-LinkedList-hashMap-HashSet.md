## 1-LinkedList
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
└── Main.java
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

### Explication du Design
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
