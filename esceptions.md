### **Cours sur les Exceptions et le Bloc `try-catch` en Java**

---

### **Contexte**


---

### **1. Exemple : Gestion d'Utilisateurs avec une Liste**

Dans ce programme :
1. Chaque utilisateur est représenté par un objet `User`.
2. Les exceptions personnalisées sont levées lorsqu’une action échoue (par exemple, utilisateur non trouvé ou données invalides).
3. Les exceptions remontent jusqu’à la **classe principale**, où elles sont gérées avec un bloc `try-catch`.

---

### **2. Implémentation**

#### **Étape 1 : Définir la Classe Utilisateur**
```java
class User {
    private String name;
    private String email;

    public User(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }
}
```

---

#### **Étape 2 : Créer les Exceptions Personnalisées**
```java
class UserNotFoundException extends Exception {
    public UserNotFoundException(String message) {
        super(message);
    }
}

class InvalidDataException extends Exception {
    public InvalidDataException(String message) {
        super(message);
    }
}
```

---

#### **Étape 3 : Définir l’Interface du Service Utilisateur**
```java
interface UserService {
    void addUser(String name, String email) throws InvalidDataException;
    String getUserEmail(String name) throws UserNotFoundException;
}
```

---

#### **Étape 4 : Implémenter la Classe de Service**
```java
import java.util.ArrayList;
import java.util.List;

class UserServiceImpl implements UserService {
    private List<User> users = new ArrayList<>();

    @Override
    public void addUser(String name, String email) throws InvalidDataException {
        // Validation des données
        if (name == null || name.isEmpty()) {
            throw new InvalidDataException("Name cannot be empty.");
        }
        if (email == null || !email.contains("@")) {
            throw new InvalidDataException("Invalid email format.");
        }

        // Ajout de l'utilisateur à la liste
        users.add(new User(name, email));
        System.out.println("User added: " + name);
    }

    @Override
    public String getUserEmail(String name) throws UserNotFoundException {
        // Recherche de l'utilisateur dans la liste
        for (User user : users) {
            if (user.getName().equalsIgnoreCase(name)) {
                return user.getEmail();
            }
        }

        // Si aucun utilisateur correspondant n'est trouvé
        throw new UserNotFoundException("User not found: " + name);
    }
}
```

---

#### **Étape 5 : Gérer les Exceptions dans la Classe Principale**
```java
public class UserManagementApp {
    public static void main(String[] args) {
        UserService userService = new UserServiceImpl();

        try {
            // Ajouter un utilisateur valide
            userService.addUser("Alice", "alice@example.com");

            // Ajouter un utilisateur avec un email invalide
            userService.addUser("Bob", "invalid-email");

        } catch (InvalidDataException e) {
            System.err.println("Error adding user: " + e.getMessage());
        }

        try {
            // Récupérer l'email d'un utilisateur existant
            System.out.println("Alice's Email: " + userService.getUserEmail("Alice"));

            // Récupérer un utilisateur inexistant
            System.out.println("Charlie's Email: " + userService.getUserEmail("Charlie"));

        } catch (UserNotFoundException e) {
            System.err.println("Error retrieving user: " + e.getMessage());
        }
    }
}
```

---

### **3. Explication du Programme**

1. **Classe `User` :**  
   Représente les informations d’un utilisateur avec ses attributs `name` et `email`.

2. **Exceptions Personnalisées :**  
   - `UserNotFoundException` : levée si un utilisateur n’est pas trouvé.  
   - `InvalidDataException` : levée si les données fournies (nom ou email) sont invalides.

3. **Classe `UserServiceImpl` :**  
   Implémente les méthodes pour ajouter un utilisateur ou récupérer son email. La liste `users` stocke les objets utilisateur.

4. **Classe Principale :**  
   Utilise un **bloc `try-catch`** pour gérer les exceptions remontées par le service.

---

### **4. Résultat Attendu**

#### Cas Valide
```
User added: Alice
Alice's Email: alice@example.com
```

#### Cas Invalide
```
Error adding user: Invalid email format.
Error retrieving user: User not found: Charlie
```

---

### **5. Extensions Possibles**
1. Ajouter une méthode pour supprimer un utilisateur (`deleteUser`) et lever une exception si l'utilisateur n'existe pas.
2. Permettre la mise à jour des informations utilisateur avec validation.
3. Inclure une gestion plus sophistiquée des erreurs avec des journaux (ex. : via `Logger`).

---
