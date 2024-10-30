### 1. **Concept de l'encapsulation en Java**


L'encapsulation est un principe fondamental de la programmation orientée objet, qui consiste à **cacher les détails internes** d'une classe pour protéger ses données et restreindre l'accès direct depuis l'extérieur. En Java, cela se réalise en :
- Déclarant les attributs de la classe avec des modificateurs d'accès adaptés pour limiter leur visibilité.
- Fournissant des méthodes (getters et setters) pour accéder et modifier ces attributs de manière contrôlée.

L'encapsulation améliore la sécurité et la maintenance du code, en permettant de changer l'implémentation interne sans affecter les autres parties du programme.

### 2. **Les Modificateurs d'Accès en Java**

Les modificateurs d'accès permettent de définir la **visibilité** des classes, attributs et méthodes. En Java, il en existe quatre principaux : **`public`**, **`private`**, **`protected`**, et l'absence de modificateur (appelé *package-private*). 

#### a. `public`
- Un membre déclaré `public` est **accessible depuis n'importe quel endroit** dans le programme, que ce soit dans la même classe, un autre package, ou une autre classe.
- Utilisé pour les méthodes que l’on souhaite rendre accessibles partout.

#### b. `private`
- Un membre `private` est **accessible uniquement depuis la classe où il est défini**.
- Utilisé pour cacher les données d'une classe afin de protéger ses attributs et de contrôler leur accès via des getters et setters.

#### c. `protected`
- Un membre `protected` est **accessible dans la même classe, dans les sous-classes (même si elles sont dans un autre package), et dans les classes du même package**.
- Souvent utilisé dans le cas de l'héritage pour permettre l’accès aux attributs aux classes dérivées tout en limitant l'accès pour les autres.

#### d. Aucun Modificateur (Package-Private)
- Lorsque l'on n'ajoute pas de modificateur d'accès, le membre est dit "package-private". Il est accessible **dans toutes les classes du même package**, mais pas en dehors.
- Il est rarement utilisé intentionnellement sauf si l’on veut restreindre l’accès aux classes du même package uniquement.

### 3. **Mise en Pratique de l'Encapsulation avec un Exercice Complet**

#### Exemple de Classe : `Personne`

Pour illustrer ces concepts, prenons une classe `Personne`. Elle va contenir trois attributs : `nom`, `age` et `adresse`, et des méthodes pour y accéder et les modifier.

```java
public class Personne {
    // Attributs privés
    private String nom;
    private int age;
    protected String adresse; // Accessible dans la même classe, sous-classes et même package

    // Constructeur public pour créer une instance de Personne
    public Personne(String nom, int age, String adresse) {
        this.nom = nom;
        this.age = age;
        this.adresse = adresse;
    }

    // Getter pour le nom (accesseur public)
    public String getNom() {
        return nom;
    }

    // Setter pour le nom (mutateur public)
    public void setNom(String nom) {
        this.nom = nom;
    }

    // Getter pour l'âge
    public int getAge() {
        return age;
    }

    // Setter pour l'âge avec vérification
    public void setAge(int age) {
        if (age >= 0) {  // Vérification pour ne pas accepter un âge négatif
            this.age = age;
        }
    }

    // Getter pour l'adresse (utilisation de protected)
    protected String getAdresse() {
        return adresse;
    }

    // Setter pour l'adresse
    protected void setAdresse(String adresse) {
        this.adresse = adresse;
    }
}
```

#### Explication des Composants :
1. **Attributs :**
   - `nom` et `age` sont privés (`private`) : ils sont cachés de l’extérieur et accessibles uniquement via les méthodes publiques (getters et setters).
   - `adresse` est `protected`, permettant l'accès aux sous-classes et aux classes du même package, mais pas à l’extérieur.
   
2. **Constructeur :**
   - Le constructeur `Personne` est public (`public`) pour pouvoir créer des instances de `Personne` à partir d'autres classes.

3. **Méthodes (Getters et Setters) :**
   - **Getters** : `getNom()`, `getAge()` et `getAdresse()` renvoient les valeurs des attributs respectifs.
   - **Setters** : `setNom()`, `setAge(int age)`, et `setAdresse(String adresse)` permettent de modifier les valeurs. Le setter de `age` inclut une vérification pour éviter les âges négatifs.

### 4. **Utilisation des Accesseurs et Modificateurs dans le Main**

Voici un exemple de code utilisant cette classe dans un programme principal :

```java
public class Main {
    public static void main(String[] args) {
        // Création d'une instance de Personne
        Personne personne = new Personne("Alice", 25, "Paris");

        // Accès aux attributs via les accesseurs (getters)
        System.out.println("Nom : " + personne.getNom());
        System.out.println("Âge : " + personne.getAge());
        
        // Tentative de modification via les mutateurs (setters)
        personne.setNom("Bob");
        personne.setAge(30);

        // Utilisation de l'accès protégé (protected) dans une sous-classe
        // Impossible d'accéder directement à l'attribut adresse car il est protégé
        System.out.println("Nouvel âge : " + personne.getAge());
        System.out.println("Nom mis à jour : " + personne.getNom());
    }
}
```

### 5. **Le Mot Clé `protected` et l'Héritage**

Si nous créons une sous-classe de `Personne`, nous aurons accès aux membres `protected`. Voici un exemple :

```java
public class Employe extends Personne {
    private String poste;

    public Employe(String nom, int age, String adresse, String poste) {
        super(nom, age, adresse); // Appel du constructeur de la classe parente
        this.poste = poste;
    }

    public String getPoste() {
        return poste;
    }

    public void setPoste(String poste) {
        this.poste = poste;
    }

    // Méthode pour afficher les informations de l'employé, y compris l'adresse (protected)
    public void afficherInfos() {
        System.out.println("Nom : " + getNom());
        System.out.println("Âge : " + getAge());
        System.out.println("Adresse : " + getAdresse()); // Accessible car protected
        System.out.println("Poste : " + poste);
    }
}
```

### Récapitulatif

- **Public** : accessible partout.
- **Private** : accessible uniquement dans la classe d'origine.
- **Protected** : accessible dans la classe d'origine, dans ses sous-classes et dans les classes du même package.
  
L’encapsulation permet de protéger les données et de mieux structurer votre code, en limitant l’accès aux membres d’une classe et en fournissant des méthodes contrôlées pour y accéder.
