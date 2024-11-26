## **Concepts Clés : Classes concrètes, Interfaces, et Classes Abstraites**

### **1. Classes concrètes**
- **Instanciables directement** : Représentent des entités complètes.
- **Contiennent des attributs et des méthodes concrètes**.

#### Exemple :
```java
class UserAccount {
    private String name;
    private String email;

    public UserAccount(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public void displayInfo() {
        System.out.println("Name: " + name + ", Email: " + email);
    }
}
```

---

### **2. Interfaces**
- **Définissent des comportements via des méthodes abstraites.**
- **Multiples implémentations possibles** pour une classe.
- Pas d’attributs d’instance, uniquement des constantes.

#### Exemple :
```java
interface FreeContentAccess {
    void accessFreeContent();
}

interface PremiumContentAccess {
    void accessPremiumContent();
}
```

---

### **3. Classes Abstraites**
- **Non instanciables directement** : Fournissent une base commune.
- Contiennent des **méthodes concrètes et abstraites**.
- Utilisées pour partager des comportements communs.

#### Exemple :
```java
abstract class AbstractUserAccount {
    protected String name;
    protected String email;

    public AbstractUserAccount(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public void displayInfo() {
        System.out.println("Name: " + name + ", Email: " + email);
    }

    public abstract void accountType();
}
```

---

### **4. Classes Concrètes Spécialisées**
- **Héritent de classes abstraites** et **implémentent des interfaces**.

#### Exemple :
```java
class BasicAccount extends AbstractUserAccount implements FreeContentAccess {
    public BasicAccount(String name, String email) {
        super(name, email);
    }

    @Override
    public void accessFreeContent() {
        System.out.println("Accessing free content...");
    }

    @Override
    public void accountType() {
        System.out.println("Basic Account");
    }
}

class PremiumAccount extends AbstractUserAccount implements FreeContentAccess, PremiumContentAccess {
    public PremiumAccount(String name, String email) {
        super(name, email);
    }

    @Override
    public void accessFreeContent() {
        System.out.println("Accessing free content...");
    }

    @Override
    public void accessPremiumContent() {
        System.out.println("Accessing premium content...");
    }

    @Override
    public void accountType() {
        System.out.println("Premium Account");
    }
}
```

---

### **5. Programme Principal**
- Gère différents types de comptes à l’aide du polymorphisme.

#### Exemple :
```java
public class SubscriptionManager {
    public static void main(String[] args) {
        AbstractUserAccount basicUser = new BasicAccount("Alice", "alice@example.com");
        AbstractUserAccount premiumUser = new PremiumAccount("Bob", "bob@example.com");

        basicUser.displayInfo();
        basicUser.accountType();
        ((FreeContentAccess) basicUser).accessFreeContent();

        premiumUser.displayInfo();
        premiumUser.accountType();
        ((FreeContentAccess) premiumUser).accessFreeContent();
        ((PremiumContentAccess) premiumUser).accessPremiumContent();
    }
}
```

---

### **6. Tableau Comparatif**

| **Aspect**       | **Classe concrètes**        | **Interface**                       | **Classe Abstraite**                |
|-------------------|---------------------------|-------------------------------------|--------------------------------------|
| **Instanciable**  | Oui                       | Non                                 | Non                                  |
| **Héritage**      | Une seule classe parente  | Multiples implémentations possibles | Une seule classe parente            |
| **Méthodes**      | Concrètes                 | Abstraites ou par défaut            | Concrètes et abstraites             |
| **Attributs**     | Variables d’instance      | Constantes (`static final`)         | Variables d’instance et constantes  |

---

### **Résumé**
- **Classes concrètes** : Pour des entités instanciables directement.
- **Interfaces** : Pour définir des comportements spécifiques et garantir la modularité.
- **Classes abstraites** : Pour structurer un système avec des fonctionnalités partagées et flexibles.

Avec ce modèle, le code devient **extensible**, **organisé**, et **orienté vers la réutilisabilité**.

## exemple UML : 
Est défini avec {classe abstraite}

![image](https://github.com/user-attachments/assets/e90a947b-10ec-4f90-ae63-625b367a8583)





