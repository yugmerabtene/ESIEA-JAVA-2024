### HASHMAP

### **1. Différence entre `HashMap` et `ArrayList`**

| **Caractéristique**     | **HashMap**                                           | **ArrayList**                                        |
|--------------------------|------------------------------------------------------|-----------------------------------------------------|
| **Structure des données** | Basée sur des paires clé-valeur (`key-value`).        | Basée sur une liste ordonnée d'éléments (index).    |
| **Accès aux éléments**    | Accès via une clé unique.                            | Accès via un index numérique.                      |
| **Unicité**              | Les clés sont uniques, mais les valeurs peuvent se répéter. | Les éléments peuvent être dupliqués.               |
| **Performance d'accès**   | Accès rapide grâce au hachage, O(1) en moyenne.      | Accès rapide par index, O(1).                      |
| **Utilisation typique**   | Lorsque vous avez besoin d'associer une clé à une valeur (exemple : dictionnaire, annuaire). | Lorsque vous avez une liste ordonnée d'éléments (exemple : liste de noms). |
| **Ordre des éléments**    | Pas garanti (non ordonné).                           | L'ordre d'insertion est maintenu.                  |

---

### **2. Introduction à HashMap**
- Une `HashMap` est utilisée pour stocker des paires clé-valeur.
- Elle est efficace pour rechercher, insérer ou supprimer des éléments rapidement.
- Les clés doivent être uniques et non nulles, mais les valeurs peuvent être nulles ou dupliquées.

---

### **3. Exemple pratique avec gestion des exceptions**

Nous allons créer un système de gestion des utilisateurs où :
1. Une `HashMap` est utilisée pour stocker des utilisateurs.
2. Des exceptions personnalisées sont levées pour signaler les erreurs.
3. Le programme principal attrape ces exceptions dans des blocs `try-catch`.
---
Principales méthodes disponibles dans la classe **`HashMap`** de Java :

### **Méthodes de base :**

1. **`put(K key, V value)`**  
   Ajoute une paire clé-valeur à la map. Si la clé existe déjà, la valeur associée est remplacée.

2. **`get(Object key)`**  
   Retourne la valeur associée à une clé donnée, ou `null` si la clé n'est pas présente.

3. **`remove(Object key)`**  
   Supprime la clé (et la valeur associée) de la map.

4. **`containsKey(Object key)`**  
   Vérifie si une clé donnée est présente dans la map.

5. **`containsValue(Object value)`**  
   Vérifie si une valeur donnée est présente dans la map.

6. **`size()`**  
   Retourne le nombre de paires clé-valeur dans la map.

7. **`isEmpty()`**  
   Vérifie si la map est vide (retourne `true` si elle ne contient aucune entrée).

8. **`clear()`**  
   Supprime toutes les paires clé-valeur de la map.

---

### **Méthodes avancées :**

9. **`putIfAbsent(K key, V value)`**  
   Ajoute une paire clé-valeur seulement si la clé n'est pas déjà présente.

10. **`replace(K key, V value)`**  
    Remplace la valeur associée à une clé donnée, uniquement si elle existe.

11. **`replace(K key, V oldValue, V newValue)`**  
    Remplace la valeur d'une clé seulement si la valeur actuelle correspond à `oldValue`.

12. **`getOrDefault(Object key, V defaultValue)`**  
    Retourne la valeur associée à une clé, ou une valeur par défaut si la clé n'existe pas.

13. **`merge(K key, V value, BiFunction<? super V, ? super V, ? extends V> remappingFunction)`**  
    Combine une nouvelle valeur avec une ancienne valeur associée à une clé à l’aide de la fonction donnée.

14. **`compute(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction)`**  
    Calcule une nouvelle valeur pour une clé donnée, avec ou sans sa valeur existante.

15. **`computeIfAbsent(K key, Function<? super K, ? extends V> mappingFunction)`**  
    Calcule une valeur et l’ajoute à la map si la clé n’a pas de valeur associée.

16. **`computeIfPresent(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction)`**  
    Modifie la valeur d'une clé seulement si elle existe déjà dans la map.

---

### **Itération et manipulation des clés/valeurs :**

17. **`keySet()`**  
    Retourne une vue de l'ensemble des clés (type `Set<K>`).

18. **`values()`**  
    Retourne une vue de toutes les valeurs (type `Collection<V>`).

19. **`entrySet()`**  
    Retourne une vue des paires clé-valeur sous forme d'un ensemble (`Set<Map.Entry<K, V>>`).

20. **`forEach(BiConsumer<? super K, ? super V> action)`**  
    Exécute une action pour chaque paire clé-valeur.

---

### **Comparaison et clonage :**

21. **`equals(Object o)`**  
    Compare cette map avec un autre objet pour vérifier leur égalité.

22. **`hashCode()`**  
    Retourne le code de hachage pour cette map.

23. **`clone()`**  
    Crée une copie superficielle de la map.


---

#### **1. Classe `User`**

```java
public class User {
    private String name;
    private String email;

    // Constructeur
    public User(String name, String email) {
        this.name = name;
        this.email = email;
    }

    // Accesseurs
    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }

    // Redéfinition de toString() pour afficher les détails
    @Override
    public String toString() {
        return "Name: " + name + ", Email: " + email;
    }
}
```

---

#### **2. Exceptions personnalisées**

```java
// Exception pour un utilisateur déjà existant
class UserAlreadyExistsException extends Exception {
    public UserAlreadyExistsException(String message) {
        super(message);
    }
}

// Exception pour un utilisateur non trouvé
class UserNotFoundException extends Exception {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```

---

#### **3. Gestion des utilisateurs avec `HashMap`**

```java
import java.util.HashMap;

public class UserManager {
    private HashMap<Integer, User> users;

    public UserManager() {
        users = new HashMap<>();
    }

    // Ajouter un utilisateur
    public void addUser(int id, User user) throws UserAlreadyExistsException {
        if (users.containsKey(id)) {
            throw new UserAlreadyExistsException("L'utilisateur avec l'ID " + id + " existe déjà.");
        }
        users.put(id, user);
    }

    // Supprimer un utilisateur
    public void removeUser(int id) throws UserNotFoundException {
        if (!users.containsKey(id)) {
            throw new UserNotFoundException("Aucun utilisateur trouvé avec l'ID " + id);
        }
        users.remove(id);
    }

    // Obtenir un utilisateur
    public User getUser(int id) throws UserNotFoundException {
        if (!users.containsKey(id)) {
            throw new UserNotFoundException("Aucun utilisateur trouvé avec l'ID " + id);
        }
        return users.get(id);
    }

    // Lister tous les utilisateurs
    public void listUsers() {
        if (users.isEmpty()) {
            System.out.println("Aucun utilisateur enregistré.");
        } else {
            for (Integer id : users.keySet()) {
                System.out.println("ID: " + id + ", " + users.get(id));
            }
        }
    }
}
```

---

#### **4. Programme principal avec gestion des exceptions**

```java
public class Main {
    public static void main(String[] args) {
        UserManager userManager = new UserManager();

        try {
            // Création d'utilisateurs
            User user1 = new User("Alice", "alice@example.com");
            User user2 = new User("Bob", "bob@example.com");
            User user3 = new User("Charlie", "charlie@example.com");

            // Ajout d'utilisateurs
            System.out.println("Ajout des utilisateurs...");
            userManager.addUser(1, user1);
            userManager.addUser(2, user2);
            userManager.addUser(3, user3);

            // Liste des utilisateurs
            System.out.println("\nListe des utilisateurs :");
            userManager.listUsers();

            // Obtenir un utilisateur par ID
            System.out.println("\nObtenir l'utilisateur avec ID 2 :");
            System.out.println(userManager.getUser(2));

            // Tentative d'ajout d'un utilisateur avec un ID existant
            System.out.println("\nTentative d'ajout d'un utilisateur avec un ID déjà existant :");
            userManager.addUser(2, new User("Duplicate", "duplicate@example.com"));

        } catch (UserAlreadyExistsException e) {
            System.err.println("Erreur : " + e.getMessage());
        } catch (UserNotFoundException e) {
            System.err.println("Erreur : " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Une erreur inattendue est survenue : " + e.getMessage());
        }

        try {
            // Supprimer un utilisateur
            System.out.println("\nSuppression de l'utilisateur avec ID 2 :");
            userManager.removeUser(2);

            // Liste des utilisateurs après suppression
            System.out.println("\nListe des utilisateurs après suppression :");
            userManager.listUsers();

            // Tentative de suppression d'un utilisateur non existant
            System.out.println("\nTentative de suppression d'un utilisateur inexistant :");
            userManager.removeUser(4);

        } catch (UserNotFoundException e) {
            System.err.println("Erreur : " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Une erreur inattendue est survenue : " + e.getMessage());
        }
    }
}
```

---

#### **5. Résultat attendu**

**Ajout d'utilisateurs :**
```
Ajout des utilisateurs...
Ajout réussi.
Ajout réussi.
Ajout réussi.
```

**Liste des utilisateurs :**
```
Liste des utilisateurs :
ID: 1, Name: Alice, Email: alice@example.com
ID: 2, Name: Bob, Email: bob@example.com
ID: 3, Name: Charlie, Email: charlie@example.com
```

**Erreur d'ajout d'un ID existant :**
```
Erreur : L'utilisateur avec l'ID 2 existe déjà.
```

**Suppression et tentative de suppression d'un utilisateur inexistant :**
```
Suppression de l'utilisateur avec ID 2 :
Suppression réussie.

Liste des utilisateurs après suppression :
ID: 1, Name: Alice, Email: alice@example.com
ID: 3, Name: Charlie, Email: charlie@example.com

Erreur : Aucun utilisateur trouvé avec l'ID 4
```


