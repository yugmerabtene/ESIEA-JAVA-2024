En Java, **l'agrégation** est un type particulier de composition où une classe inclut une autre classe comme attribut, mais sans posséder le cycle de vie de cet attribut. En d'autres termes, l'objet contenu peut exister indépendamment de l'objet conteneur.

C'est une relation de type **"has-a"** (a une), mais où les deux objets sont moins fortement couplés. L'agrégation est souvent représentée avec un losange vide dans les diagrammes UML.

### Exemple d'agrégation

#### Classe utilisée dans l'agrégation
```java
public class Departement {
    private String nom;

    public Departement(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    @Override
    public String toString() {
        return nom;
    }
}
```

#### Classe principale qui utilise l'agrégation
```java
import java.util.List;

public class Universite {
    private String nom;
    private List<Departement> departements; // Agrégation

    public Universite(String nom, List<Departement> departements) {
        this.nom = nom;
        this.departements = departements;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    public List<Departement> getDepartements() {
        return departements;
    }

    public void setDepartements(List<Departement> departements) {
        this.departements = departements;
    }

    @Override
    public String toString() {
        return "Université " + nom + " avec départements : " + departements.toString();
    }
}
```

#### Classe principale pour tester
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        Departement informatique = new Departement("Informatique");
        Departement mathematiques = new Departement("Mathématiques");

        Universite universite = new Universite("Université Paris-Sud", Arrays.asList(informatique, mathematiques));
        System.out.println(universite);
    }
}
```

### Sortie
```
Université Université Paris-Sud avec départements : [Informatique, Mathématiques]
```

### Différence entre composition et agrégation
- **Composition** : L'objet contenu dépend de l'objet conteneur. Si le conteneur est détruit, le contenu est aussi détruit.
- **Agrégation** : L'objet contenu peut exister indépendamment du conteneur.

#### Exemple : Si l'université est supprimée, les départements existent toujours indépendamment. Par contre, avec une composition stricte, les départements seraient détruits avec l'université.

![image](https://github.com/user-attachments/assets/d929bcbb-1c96-4696-b1ba-67594fc08b4b)
