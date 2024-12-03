La **composition** est une technique où une classe utilise une autre classe comme attribut. C'est une alternative à l'héritage qui favorise une relation de type **"A a un B"** (has-a) plutôt que **"A est un B"** (is-a).

### Exemple de composition
Voici un exemple simple pour illustrer la composition :

#### Classe utilisée dans la composition
```java
public class Adresse {
    private String rue;
    private String ville;

    public Adresse(String rue, String ville) {
        this.rue = rue;
        this.ville = ville;
    }

    public String getRue() {
        return rue;
    }

    public void setRue(String rue) {
        this.rue = rue;
    }

    public String getVille() {
        return ville;
    }

    public void setVille(String ville) {
        this.ville = ville;
    }

    @Override
    public String toString() {
        return rue + ", " + ville;
    }
}
```

#### Classe principale qui utilise la composition
```java
public class Personne {
    private String nom;
    private int age;
    private Adresse adresse; // Composition : "Une personne a une adresse"

    public Personne(String nom, int age, Adresse adresse) {
        this.nom = nom;
        this.age = age;
        this.adresse = adresse;
    }

    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Adresse getAdresse() {
        return adresse;
    }

    public void setAdresse(Adresse adresse) {
        this.adresse = adresse;
    }

    @Override
    public String toString() {
        return nom + ", " + age + " ans, habite à : " + adresse.toString();
    }
}
```

#### Classe principale pour tester
```java
public class Main {
    public static void main(String[] args) {
        Adresse adresse = new Adresse("12 rue des Lilas", "Paris");
        Personne personne = new Personne("Jean Dupont", 30, adresse);

        System.out.println(personne);

        // Modification de l'adresse via la composition
        personne.getAdresse().setRue("15 avenue des Champs");
        System.out.println(personne);
    }
}
```

### Sortie
```
Jean Dupont, 30 ans, habite à : 12 rue des Lilas, Paris
Jean Dupont, 30 ans, habite à : 15 avenue des Champs, Paris
```

### UML  

![image](https://github.com/user-attachments/assets/92b6f2bd-52aa-42e7-9f81-25f6cb75f1b6)


### Avantages de la composition
1. **Flexibilité** : Permet de réutiliser des classes sans les surcharger.
2. **Encapsulation** : Les détails d'implémentation sont masqués.
3. **Évolutivité** : Plus simple à maintenir et à étendre comparé à l'héritage.

Si tu as besoin d’un exemple plus avancé ou dans un contexte particulier, fais-le-moi savoir ! 😊
