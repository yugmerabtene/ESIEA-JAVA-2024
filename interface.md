### Structure des Fichiers
```
src/
│
├── Main.java
├── interfaces/
│   ├── Voler.java
│   ├── Nager.java
│   ├── Marcher.java
│   └── Grimper.java
│
├── classes/
    ├── Oiseau.java
    ├── Poisson.java
    └── Chat.java
```

### Code de chaque fichier

**1. Fichier `src/interfaces/Voler.java`**
```java
package interfaces;

public interface Voler {
    void voler();
}
```

**2. Fichier `src/interfaces/Nager.java`**
```java
package interfaces;

public interface Nager {
    void nager();
}
```

**3. Fichier `src/interfaces/Marcher.java`**
```java
package interfaces;

public interface Marcher {
    void marcher();
}
```

**4. Fichier `src/interfaces/Grimper.java`**
```java
package interfaces;

public interface Grimper {
    void grimper();
}
```

**5. Fichier `src/classes/Oiseau.java`**
```java
package classes;

import interfaces.Voler;
import interfaces.Marcher;

public class Oiseau implements Voler, Marcher {
    private String nom;

    public Oiseau(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    @Override
    public void voler() {
        System.out.println(nom + " vole dans le ciel.");
    }

    @Override
    public void marcher() {
        System.out.println(nom + " marche sur ses pattes.");
    }
}
```

**6. Fichier `src/classes/Poisson.java`**
```java
package classes;

import interfaces.Nager;

public class Poisson implements Nager {
    private String nom;

    public Poisson(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    @Override
    public void nager() {
        System.out.println(nom + " nage dans l'eau.");
    }
}
```

**7. Fichier `src/classes/Chat.java`**
```java
package classes;

import interfaces.Marcher;
import interfaces.Grimper;

public class Chat implements Marcher, Grimper {
    private String nom;

    public Chat(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    @Override
    public void marcher() {
        System.out.println(nom + " marche silencieusement.");
    }

    @Override
    public void grimper() {
        System.out.println(nom + " grimpe aux arbres.");
    }
}
```

**8. Fichier `src/Main.java`**
```java
import classes.Oiseau;
import classes.Poisson;
import classes.Chat;

public class Main {
    public static void main(String[] args) {
        // Instanciation des objets
        Oiseau oiseau = new Oiseau("Moineau");
        Poisson poisson = new Poisson("Nemo");
        Chat chat = new Chat("Miaou");

        // Utilisation des méthodes
        oiseau.voler();
        oiseau.marcher();

        poisson.nager();

        chat.marcher();
        chat.grimper();

        // Affichage des noms avec les getters
        System.out.println("L'oiseau est : " + oiseau.getNom());
        System.out.println("Le poisson est : " + poisson.getNom());
        System.out.println("Le chat est : " + chat.getNom());

        // Modification des noms avec les setters
        oiseau.setNom("Aigle");
        poisson.setNom("Poisson Rouge");
        chat.setNom("Félix");

        // Affichage des nouveaux noms
        System.out.println("Le nouvel oiseau est : " + oiseau.getNom());
        System.out.println("Le nouveau poisson est : " + poisson.getNom());
        System.out.println("Le nouveau chat est : " + chat.getNom());
    }
}
```

### Instructions pour la Compilation
1. Créez les répertoires `src/interfaces` et `src/classes` dans votre projet.
2. Placez chaque fichier de code dans son répertoire correspondant.
3. Compilez et exécutez `Main.java` pour tester le fonctionnement complet.
4. On peux aussi créer un constructeur vide dans les classes et éviter de définir les attributs lors de l'intanciation de l'objet pour les set avec les setters et afficher les attributs avec les getters.  
----


##2eme partie 


### **Cours sur Java : Interfaces et Héritage avec un Exemple de Comptes d'Utilisateurs et Abonnements**

---

### **1. Contexte : Gestion de Comptes et Abonnements**

Dans un système de gestion d'abonnements, un utilisateur peut avoir différents types d'abonnements (par exemple : `Basic`, `Premium`, ou `Enterprise`). Chaque abonnement donne accès à des fonctionnalités spécifiques :
- Les utilisateurs `Basic` peuvent accéder à du contenu gratuit.
- Les utilisateurs `Premium` peuvent accéder au contenu premium.
- Les utilisateurs `Enterprise` peuvent accéder à des outils avancés.

Pour modéliser ce système :
1. Utiliser des **interfaces** pour définir des comportements spécifiques des abonnements.
2. Créer une **classe de base** pour représenter les propriétés communes d’un utilisateur.
3. Implémenter des **classes concrètes** pour chaque type d'abonnement.

---

### **2. Structure des Interfaces et Classes**

#### **Interfaces :**
1. **FreeContentAccess** : pour accéder au contenu gratuit.
2. **PremiumContentAccess** : pour accéder au contenu premium.
3. **AdvancedToolsAccess** : pour accéder aux outils avancés.

#### **Classe de Base :**
- **UserAccount** : contient les informations générales comme le nom, l'email, et le type d'abonnement.

#### **Classes Concrètes :**
- **BasicAccount** : implémente l’accès au contenu gratuit.
- **PremiumAccount** : ajoute l’accès au contenu premium.
- **EnterpriseAccount** : ajoute l’accès aux outils avancés.

---

### **3. Code Exemple**

#### **Définition des Interfaces :**
```java
interface FreeContentAccess {
    void accessFreeContent();
}

interface PremiumContentAccess {
    void accessPremiumContent();
}

interface AdvancedToolsAccess {
    void accessAdvancedTools();
}
```

#### **Classe de Base :**
```java
class UserAccount {
    protected String name;
    protected String email;

    public UserAccount(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Email: " + email);
    }
}
```

#### **Classes Concrètes :**
```java
class BasicAccount extends UserAccount implements FreeContentAccess {
    public BasicAccount(String name, String email) {
        super(name, email);
    }

    @Override
    public void accessFreeContent() {
        System.out.println("Accessing free content...");
    }
}

class PremiumAccount extends UserAccount implements FreeContentAccess, PremiumContentAccess {
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
}

class EnterpriseAccount extends UserAccount implements FreeContentAccess, PremiumContentAccess, AdvancedToolsAccess {
    public EnterpriseAccount(String name, String email) {
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
    public void accessAdvancedTools() {
        System.out.println("Accessing advanced tools...");
    }
}
```

#### **Programme Principal :**
```java
public class SubscriptionManager {
    public static void main(String[] args) {
        // Création des comptes
        BasicAccount basicUser = new BasicAccount("Alice", "alice@example.com");
        PremiumAccount premiumUser = new PremiumAccount("Bob", "bob@example.com");
        EnterpriseAccount enterpriseUser = new EnterpriseAccount("Charlie", "charlie@example.com");

        // Afficher les informations et accéder aux fonctionnalités
        System.out.println("--- Basic Account ---");
        basicUser.displayInfo();
        basicUser.accessFreeContent();

        System.out.println("\n--- Premium Account ---");
        premiumUser.displayInfo();
        premiumUser.accessFreeContent();
        premiumUser.accessPremiumContent();

        System.out.println("\n--- Enterprise Account ---");
        enterpriseUser.displayInfo();
        enterpriseUser.accessFreeContent();
        enterpriseUser.accessPremiumContent();
        enterpriseUser.accessAdvancedTools();
    }
}
```

---

### **4. Analyse du Système**

1. **Modularité** :  
   Les interfaces permettent de définir des comportements spécifiques. Cela rend le système flexible pour ajouter de nouvelles fonctionnalités (ex. : accès VIP).

2. **Réutilisation du Code** :  
   La classe de base `UserAccount` centralise les informations communes à tous les types de comptes (nom, email).

3. **Évolutivité** :  
   Si un nouvel abonnement est ajouté (ex. : `VIPAccount`), il suffit de créer une nouvelle classe qui implémente les interfaces nécessaires.

---

### **5. Extensions Possibles**
- Ajouter un système de facturation via une interface `Billable`.
- Intégrer un niveau de sécurité via une interface `SecureAccess` avec des méthodes comme `authenticate()`.
- Permettre aux administrateurs d'accéder à une interface `AdminToolsAccess`.

---


