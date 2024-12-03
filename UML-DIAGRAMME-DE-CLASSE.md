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


