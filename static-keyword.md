En Java, le mot-clé **`static`** est utilisé pour indiquer qu’un membre (variable, méthode, ou bloc) appartient à la classe elle-même plutôt qu’à une instance spécifique de cette classe. Cela signifie que vous n'avez pas besoin de créer un objet pour accéder à un membre `static`.

Voici une explication avec des exemples pour mieux comprendre :

---

### 1. **Variable `static`**
Une variable `static` est partagée par toutes les instances de la classe. Elle appartient à la classe et non aux objets individuels.

#### Exemple :
```java
class ExampleStatic {
    static int count = 0; // Variable static partagée par toutes les instances

    ExampleStatic() {
        count++; // Incrémentation chaque fois qu'un objet est créé
    }

    void displayCount() {
        System.out.println("Nombre d'objets créés : " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        ExampleStatic obj1 = new ExampleStatic();
        ExampleStatic obj2 = new ExampleStatic();
        ExampleStatic obj3 = new ExampleStatic();

        obj1.displayCount(); // Affiche 3
        obj2.displayCount(); // Affiche 3
    }
}
```
**Explication** : La variable `count` est partagée, donc sa valeur est la même pour toutes les instances de la classe.

---

### 2. **Méthode `static`**
Une méthode `static` appartient également à la classe. Elle peut être appelée directement avec le nom de la classe, sans créer d'objet.

#### Exemple :
```java
class MathUtil {
    static int add(int a, int b) {
        return a + b;
    }

    static int multiply(int a, int b) {
        return a * b;
    }
}

public class Main {
    public static void main(String[] args) {
        // Appel direct des méthodes static
        System.out.println("Somme : " + MathUtil.add(5, 3));
        System.out.println("Produit : " + MathUtil.multiply(5, 3));
    }
}
```
**Explication** : Les méthodes `add` et `multiply` sont appelées directement avec `MathUtil`, sans qu'il soit nécessaire de créer un objet.

---

### 3. **Bloc `static`**
Un bloc `static` est exécuté une seule fois lorsque la classe est chargée en mémoire. Il est utile pour initialiser des données `static`.

#### Exemple :
```java
class ExampleStaticBlock {
    static int value;

    // Bloc static pour initialisation
    static {
        value = 42; // Initialisation
        System.out.println("Bloc static exécuté.");
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("Valeur : " + ExampleStaticBlock.value);
    }
}
```
**Explication** : Le bloc `static` est exécuté une seule fois, avant que vous n'accédiez à des membres statiques de la classe.

---

### 4. **Membres `static` et `non-static`**
Les membres `static` ne peuvent pas accéder directement aux membres non-statiques, car les membres `static` n'appartiennent pas à une instance.

#### Exemple :
```java
class Test {
    static int staticVar = 10;
    int instanceVar = 20;

    static void staticMethod() {
        System.out.println("Variable static : " + staticVar);
        // System.out.println("Variable instance : " + instanceVar); // Erreur
    }

    void instanceMethod() {
        System.out.println("Variable static : " + staticVar); // Accessible
        System.out.println("Variable instance : " + instanceVar); // Accessible
    }
}

public class Main {
    public static void main(String[] args) {
        Test.staticMethod(); // Appel direct de la méthode static

        Test obj = new Test();
        obj.instanceMethod(); // Appel de la méthode d'instance
    }
}
```
**Explication** : Les méthodes `static` ne peuvent pas accéder aux variables d'instance sans une référence d'objet.

---

### Points clés à retenir :
1. **Variable `static`** : Partagée par toutes les instances.
2. **Méthode `static`** : Appelée avec le nom de la classe, pas besoin d'objet.
3. **Bloc `static`** : Exécuté une seule fois lors du chargement de la classe.
4. **Limitation** : Les membres `static` ne peuvent pas utiliser directement les membres non-statiques.

