![image](https://github.com/user-attachments/assets/c33c2f49-b653-4964-96f3-0895edd6ccc9)


### 1. **Dépendance (Dependency)**
**Définition** : Une classe utilise une autre classe de manière temporaire. La dépendance est faible.

```java
class A {
    void useB() {
        B b = new B();
        b.display();
    }
}

class B {
    void display() {
        System.out.println("Class B is being used by Class A");
    }
}

public class DependencyExample {
    public static void main(String[] args) {
        A a = new A();
        a.useB(); // A utilise B temporairement
    }
}
```

**Explication** : La classe `A` crée une instance locale de la classe `B` dans sa méthode `useB`, montrant une relation de dépendance.

---

### 2. **Agrégation (Aggregation)**
**Définition** : Une classe contient une autre classe comme un attribut. Les deux peuvent exister indépendamment.

```java
class A {
    private B b;

    public A(B b) {
        this.b = b;
    }

    void show() {
        b.display();
    }
}

class B {
    void display() {
        System.out.println("Class B is aggregated in Class A");
    }
}

public class AggregationExample {
    public static void main(String[] args) {
        B b = new B();  // B peut exister seul
        A a = new A(b); // B est "agrégé" dans A
        a.show();
    }
}
```

**Explication** : La classe `A` a une instance de `B` passée en tant que paramètre dans le constructeur. L'objet `B` peut être utilisé ailleurs.

---

### 3. **Composition**
**Définition** : Une classe possède une autre classe comme attribut, mais leur cycle de vie est lié (si A est détruit, B est détruit).

```java
class A {
    private B b = new B();

    void show() {
        b.display();
    }
}

class B {
    void display() {
        System.out.println("Class B is owned by Class A");
    }
}

public class CompositionExample {
    public static void main(String[] args) {
        A a = new A();
        a.show();
        // B est détruit quand A est détruit
    }
}
```

**Explication** : Ici, la classe `A` crée l'objet `B` directement dans son attribut. La relation est plus forte que l'agrégation.

---

### 4. **Héritage (Inheritance)**
**Définition** : Une classe dérivée hérite des propriétés et méthodes d'une classe de base.

```java
class A {
    void display() {
        System.out.println("Class A: Parent class");
    }
}

class B extends A {
    @Override
    void display() {
        super.display();
        System.out.println("Class B: Child class");
    }
}

public class InheritanceExample {
    public static void main(String[] args) {
        B b = new B();
        b.display(); // Méthode héritée et surchargée
    }
}
```

**Explication** : La classe `B` hérite de `A` et peut utiliser ses méthodes tout en les redéfinissant grâce à l'annotation `@Override`.

---

### 5. **Réalisation (Realization)**
**Définition** : Une classe implémente les méthodes d'une interface.

```java
interface A {
    void display();
}

class B implements A {
    @Override
    public void display() {
        System.out.println("Class B realizes interface A");
    }
}

public class RealizationExample {
    public static void main(String[] args) {
        A a = new B(); // Interface utilisée comme type
        a.display();
    }
}
```

**Explication** : La classe `B` réalise (implémente) l'interface `A`, obligeant `B` à fournir une implémentation pour les méthodes de `A`.

---

![image](https://github.com/user-attachments/assets/933c3cb6-ead1-4aa1-bcee-a82a2768072f)  



### Multiplicité :   


![image](https://github.com/user-attachments/assets/bdcafd2f-0129-4fae-a074-470fcc5e8160)



### Exemple de code
```java
import java.util.ArrayList;
import java.util.List;

// Classe représentant une entreprise
class Company {
    private String name;
    private List<Person> employees; // Une entreprise peut avoir plusieurs personnes (1..*)

    public Company(String name) {
        this.name = name;
        this.employees = new ArrayList<>();
    }

    // Ajouter une personne à l'entreprise
    public void addEmployee(Person person) {
        if (person.getCompany() != null) {
            System.out.println("Cette personne est déjà associée à une autre entreprise.");
        } else {
            employees.add(person);
            person.setCompany(this); // Liaison bidirectionnelle
        }
    }

    public String getName() {
        return name;
    }

    public List<Person> getEmployees() {
        return employees;
    }
}

// Classe représentant une personne
class Person {
    private String name;
    private Company company; // Une personne est associée à une seule entreprise (1)

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public Company getCompany() {
        return company;
    }

    public void setCompany(Company company) {
        if (this.company == null) { // Une personne ne peut être associée qu'à une seule entreprise
            this.company = company;
        } else {
            System.out.println("Cette personne est déjà employée par " + this.company.getName());
        }
    }
}

// Exemple d'utilisation
public class Main {
    public static void main(String[] args) {
        // Création d'une entreprise
        Company company = new Company("TechCorp");

        // Création de personnes
        Person person1 = new Person("Alice");
        Person person2 = new Person("Bob");

        // Ajout de personnes à l'entreprise
        company.addEmployee(person1); // Alice rejoint TechCorp
        company.addEmployee(person2); // Bob rejoint TechCorp

        // Affichage des employés de l'entreprise
        System.out.println("Les employés de " + company.getName() + " :");
        for (Person p : company.getEmployees()) {
            System.out.println("- " + p.getName());
        }

        // Tentative de réaffectation d'une personne à une autre entreprise
        Company anotherCompany = new Company("OtherCorp");
        anotherCompany.addEmployee(person1); // Cela échouera car Alice est déjà employée par TechCorp
    }
}
```

### Explications :
1. **Multiplicité `1` pour `Person -> Company`** :
   - Une personne ne peut être associée qu'à une seule entreprise grâce à la vérification dans la méthode `setCompany`.

2. **Multiplicité `1..*` pour `Company -> Person`** :
   - Une entreprise peut avoir plusieurs employés. La liste `employees` dans la classe `Company` permet de gérer cette relation.

3. **Relations bidirectionnelles** :
   - Lorsqu'une personne est ajoutée à une entreprise, l'entreprise est aussi définie comme employeur pour la personne.





