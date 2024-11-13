### Exercice : Interfaces et Implémentation de Classes avec Encapsulation et Accesseurs

#### Interfaces
1. **Interface `Voler`** : Méthode `void voler()`.
2. **Interface `Nager`** : Méthode `void nager()`.
3. **Interface `Marcher`** : Méthode `void marcher()`.
4. **Interface `Grimper`** : Méthode `void grimper()`.

#### Classes qui implémentent ces interfaces
1. **Classe `Oiseau`** : Implémente `Voler` et `Marcher`.
2. **Classe `Poisson`** : Implémente `Nager`.
3. **Classe `Chat`** : Implémente `Marcher` et `Grimper`.

### Exemple de Code en Java avec Encapsulation

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

// Classe Poisson
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

// Classe Chat
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

// Classe principale pour tester
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

### Instructions
1. **Encapsulation** : Les attributs `nom` sont privés, et des méthodes getter et setter sont fournies pour accéder et modifier ces attributs.
2. **Classe principale `Main`** : Instancie des objets de chaque classe et utilise leurs méthodes pour vérifier le fonctionnement.
3. **Résultat attendu** : Les détails des comportements (`voler`, `marcher`, `nager`, `grimper`) et la mise à jour des noms doivent être affichés dans la console.
