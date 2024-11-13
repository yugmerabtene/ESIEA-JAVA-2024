### Exercice : Interfaces et Implémentation de Classes

#### Interfaces
1. **Interface `Voler`** : Méthode `void voler()`.
2. **Interface `Nager`** : Méthode `void nager()`.
3. **Interface `Marcher`** : Méthode `void marcher()`.
4. **Interface `Grimper`** : Méthode `void grimper()`.

#### Classes qui implémentent ces interfaces
1. **Classe `Oiseau`** : Implémente `Voler` et `Marcher`.
2. **Classe `Poisson`** : Implémente `Nager`.
3. **Classe `Chat`** : Implémente `Marcher` et `Grimper`.

### Exemple de Code en Java

```java
// Interface Voler
interface Voler {
    void voler();
}

// Interface Nager
interface Nager {
    void nager();
}

// Interface Marcher
interface Marcher {
    void marcher();
}

// Interface Grimper
interface Grimper {
    void grimper();
}

// Classe Oiseau
public class Oiseau implements Voler, Marcher {
    private String nom;

    public Oiseau(String nom) {
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

// Classe Poisson
public class Poisson implements Nager {
    private String nom;

    public Poisson(String nom) {
        this.nom = nom;
    }

    @Override
    public void nager() {
        System.out.println(nom + " nage dans l'eau.");
    }
}

// Classe Chat
public class Chat implements Marcher, Grimper {
    private String nom;

    public Chat(String nom) {
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

### Instructions
1. Implémentez les classes avec les comportements spécifiques.
2. Testez les classes dans une classe principale pour vérifier leur fonctionnement.
