### **Introduction aux Exceptions, `throw` et `try-catch` en Java**

---

#### **Qu'est-ce qu'une exception ?**

Une exception est une situation inhabituelle ou une erreur qui se produit pendant l'exécution d'un programme. Par exemple :
- Un utilisateur entre une donnée invalide.
- Une division par zéro est tentée.
- Un fichier requis est introuvable.

En Java, lorsqu'une exception survient, elle interrompt le flux normal du programme. Pour éviter que le programme ne s'arrête brutalement, Java propose un mécanisme robuste pour **détecter**, **gérer** et **résoudre** ces situations.

---

#### **Types d'exceptions**

1. **Checked Exceptions** :  
   Ces exceptions sont vérifiées au moment de la compilation. Le programmeur doit les gérer explicitement à l'aide d'un bloc `try-catch` ou en les déclarant avec `throws`.  
   Exemples : `IOException`, `SQLException`.

2. **Unchecked Exceptions** :  
   Ces exceptions ne sont pas vérifiées au moment de la compilation. Elles surviennent généralement en raison d'erreurs de logique ou de programmation.  
   Exemples : `NullPointerException`, `ArithmeticException`.

3. **Errors** :  
   Ce sont des problèmes graves liés à l'environnement d'exécution (comme le manque de mémoire). Les erreurs ne doivent pas être gérées via des blocs `try-catch`.  
   Exemple : `OutOfMemoryError`.

---

#### **Le mot-clé `throw`**

Le mot-clé `throw` est utilisé pour **lancer une exception** dans un programme. Lorsque vous utilisez `throw`, vous signalez que quelque chose d'anormal s'est produit et que cette situation doit être gérée.

**Exemple :**
```java
public void checkAge(int age) {
    if (age < 18) {
        throw new IllegalArgumentException("Âge insuffisant pour s'inscrire.");
    }
}
```

Dans cet exemple, si l'âge est inférieur à 18, une exception `IllegalArgumentException` est levée.

---

#### **Le mot-clé `throws`**

Le mot-clé `throws` est utilisé dans la signature d'une méthode pour indiquer que cette méthode pourrait lever une ou plusieurs exceptions. Cela oblige le code qui appelle cette méthode à gérer ces exceptions.

**Exemple :**
```java
public void readFile(String filePath) throws IOException {
    // Code pour lire un fichier
}
```

---

#### **Le bloc `try-catch`**

Le bloc `try-catch` est utilisé pour capturer et gérer les exceptions. Le code qui pourrait générer une exception est placé dans le bloc `try`, tandis que le code pour gérer l'exception est placé dans le bloc `catch`.

**Structure de base :**
```java
try {
    // Code qui peut lever une exception
} catch (ExceptionType e) {
    // Code pour gérer l'exception
}
```

**Exemple :**
```java
try {
    int result = 10 / 0; // Génère une ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Erreur : Division par zéro !");
}
```

---

#### **Bloc `finally`**

Le bloc `finally` est optionnel et est utilisé pour exécuter du code, qu'une exception soit levée ou non. Il est souvent utilisé pour nettoyer des ressources comme fermer un fichier ou une connexion.

**Exemple :**
```java
try {
    int result = 10 / 2;
    System.out.println("Résultat : " + result);
} catch (ArithmeticException e) {
    System.out.println("Erreur : Division par zéro !");
} finally {
    System.out.println("Bloc finally exécuté.");
}
```

---

#### **Résumé du mécanisme des exceptions**

1. **Lancer une exception :** Utilisez `throw` pour signaler une erreur.
2. **Propager une exception :** Utilisez `throws` dans une méthode pour indiquer qu'elle peut lever une exception.
3. **Gérer une exception :** Utilisez `try-catch` pour capturer et gérer les exceptions levées.

---

#### **Avantages du mécanisme des exceptions**

- **Lisibilité :** Les exceptions permettent de séparer le code principal de la gestion des erreurs.
- **Robustesse :** Le programme peut continuer à fonctionner même si une exception survient.
- **Réutilisation :** Les exceptions personnalisées permettent une gestion plus précise et réutilisable des erreurs.

---

#### **Exemple pratique : Gestion des âges**

Voici un exemple complet qui utilise les concepts de `throw`, `throws` et `try-catch` :

```java
public class AgeValidator {
    // Méthode pour vérifier l'âge
    public void checkAge(int age) throws IllegalArgumentException {
        if (age < 18) {
            throw new IllegalArgumentException("Âge insuffisant pour s'inscrire.");
        }
    }

    public static void main(String[] args) {
        AgeValidator validator = new AgeValidator();

        try {
            validator.checkAge(15); // Génère une exception
        } catch (IllegalArgumentException e) {
            System.out.println("Erreur capturée : " + e.getMessage());
        } finally {
            System.out.println("Validation terminée.");
        }
    }
}
```

**Résultat attendu :**
```
Erreur capturée : Âge insuffisant pour s'inscrire.
Validation terminée.
```

---

#### **Conclusion**

Le mécanisme des exceptions en Java est un outil puissant pour gérer les erreurs de manière propre et organisée. En combinant `throw`, `throws`, et `try-catch`, vous pouvez rendre vos applications plus robustes et fiables, tout en améliorant l'expérience utilisateur face aux erreurs.

### **Architecture des Dossiers**
```
src/
│
├── controllers/
│   ├── IUserController.java
│   └── UserController.java
│
├── exceptions/
│   ├── InvalidInputException.java
│   └── UserNotFoundException.java
│
├── models/
│   └── UserModel.java
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

---

### **Code Complété**

#### **1. Classe `UserModel` (Modèle)**
```java
package models;

public class UserModel {
    private String id;
    private String name;
    private String email;

    public UserModel(String id, String name, String email) {
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

---

#### **2. Exceptions Personnalisées**
##### **Exception : `UserNotFoundException`**
```java
package exceptions;

public class UserNotFoundException extends Exception {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```

##### **Exception : `InvalidInputException`**
```java
package exceptions;

public class InvalidInputException extends Exception {
    public InvalidInputException(String message) {
        super(message);
    }
}
```

---

#### **3. Interface et Classe de Service**
##### **Interface : `IUserService`**
```java
package services;

import models.UserModel;
import exceptions.UserNotFoundException;

import java.util.List;

public interface IUserService {
    void addUser(UserModel user) throws IllegalArgumentException;
    void removeUserById(String id) throws UserNotFoundException;
    UserModel getUserById(String id) throws UserNotFoundException;
    UserModel getUserByName(String name) throws UserNotFoundException;
    List<UserModel> getAllUsers();
}
```

##### **Classe : `UserService`**
```java
package services;

import models.UserModel;
import exceptions.UserNotFoundException;

import java.util.ArrayList;
import java.util.List;

public class UserService implements IUserService {
    private List<UserModel> users = new ArrayList<>();

    @Override
    public void addUser(UserModel user) throws IllegalArgumentException {
        if (user.getId().isEmpty() || user.getName().isEmpty() || user.getEmail().isEmpty()) {
            throw new IllegalArgumentException("Les champs ID, nom et email sont obligatoires.");
        }
        users.add(user);
        System.out.println("Utilisateur ajouté : " + user.getName());
    }

    @Override
    public void removeUserById(String id) throws UserNotFoundException {
        boolean found = false;
        for (UserModel user : users) {
            if (user.getId().equals(id)) {
                users.remove(user);
                found = true;
                System.out.println("Utilisateur avec l'ID " + id + " supprimé.");
                break;
            }
        }
        if (!found) {
            throw new UserNotFoundException("Utilisateur avec l'ID " + id + " introuvable.");
        }
    }

    @Override
    public UserModel getUserById(String id) throws UserNotFoundException {
        for (UserModel user : users) {
            if (user.getId().equals(id)) {
                return user;
            }
        }
        throw new UserNotFoundException("Utilisateur avec l'ID " + id + " introuvable.");
    }

    @Override
    public UserModel getUserByName(String name) throws UserNotFoundException {
        for (UserModel user : users) {
            if (user.getName().equalsIgnoreCase(name)) {
                return user;
            }
        }
        throw new UserNotFoundException("Utilisateur avec le nom " + name + " introuvable.");
    }

    @Override
    public List<UserModel> getAllUsers() {
        return users;
    }
}
```

---

#### **4. Contrôleur**
##### **Interface : `IUserController`**
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

##### **Classe : `UserController`**
```java
package controllers;

import models.UserModel;
import services.IUserService;
import views.UserView;
import exceptions.UserNotFoundException;

public class UserController implements IUserController {
    private IUserService userService;
    private UserView userView;

    public UserController(IUserService userService, UserView userView) {
        this.userService = userService;
        this.userView = userView;
    }

    @Override
    public void addUser(String id, String name, String email) {
        try {
            UserModel user = new UserModel(id, name, email);
            userService.addUser(user);
        } catch (IllegalArgumentException e) {
            userView.displayMessage("Erreur : " + e.getMessage());
        }
    }

    @Override
    public void removeUser(String id) {
        try {
            userService.removeUserById(id);
        } catch (UserNotFoundException e) {
            userView.displayMessage("Erreur : " + e.getMessage());
        }
    }

    @Override
    public void searchUserById(String id) {
        try {
            UserModel user = userService.getUserById(id);
            userView.displayUser(user);
        } catch (UserNotFoundException e) {
            userView.displayMessage("Erreur : " + e.getMessage());
        }
    }

    @Override
    public void searchUserByName(String name) {
        try {
            UserModel user = userService.getUserByName(name);
            userView.displayUser(user);
        } catch (UserNotFoundException e) {
            userView.displayMessage("Erreur : " + e.getMessage());
        }
    }

    @Override
    public void showAllUsers() {
        userView.displayAllUsers(userService.getAllUsers());
    }
}
```

---

#### **5. Vue**
```java
package views;

import models.UserModel;

import java.util.List;

public class UserView {
    public void displayUser(UserModel user) {
        if (user != null) {
            System.out.println("Détails de l'utilisateur :");
            System.out.println("ID : " + user.getId());
            System.out.println("Nom : " + user.getName());
            System.out.println("Email : " + user.getEmail());
        } else {
            System.out.println("Utilisateur non trouvé.");
        }
    }

    public void displayAllUsers(List<UserModel> users) {
        if (users.isEmpty()) {
            System.out.println("Aucun utilisateur enregistré.");
        } else {
            System.out.println("Liste des utilisateurs :");
            for (UserModel user : users) {
                System.out.println("ID : " + user.getId() + ", Nom : " + user.getName() + ", Email : " + user.getEmail());
            }
        }
    }

    public void displayMessage(String message) {
        System.out.println(message);
    }
}
```

---

#### **6. Classe Principale**
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
            scanner.nextLine();

            switch (choix) {
                case 1 -> {
                    System.out.print("Entrez l'ID : ");
                    String id = scanner.nextLine();
                    System.out.print("Entrez le nom : ");
                    String name = scanner.nextLine();
                    System.out.print("Entrez l'email : ");
                    String email = scanner.nextLine();
                    userController.addUser(id, name, email);
                }
                case 2 -> {
                    System.out.print("Entrez l'ID de l'utilisateur à supprimer : ");
                    String id = scanner.nextLine();
                    userController.removeUser(id);
                }
                case 3 -> {
                    System.out.print("Entrez l'ID de l

'utilisateur à rechercher : ");
                    String id = scanner.nextLine();
                    userController.searchUserById(id);
                }
                case 4 -> {
                    System.out.print("Entrez le nom de l'utilisateur à rechercher : ");
                    String name = scanner.nextLine();
                    userController.searchUserByName(name);
                }
                case 5 -> userController.showAllUsers();
                case 6 -> {
                    running = false;
                    System.out.println("Programme terminé.");
                }
                default -> System.out.println("Option invalide. Veuillez réessayer.");
            }
        }
        scanner.close();
    }
}
```

---

