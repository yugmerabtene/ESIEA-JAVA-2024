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
