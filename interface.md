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

