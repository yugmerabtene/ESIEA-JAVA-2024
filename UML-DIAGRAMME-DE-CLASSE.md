## 1. **Héritage** (`extends`)
- **Relation :** Une classe hérite d'une autre (relation "is-a").
- **Flèche UML :** **Triangle plein** à l'extrémité.
- **Code UML :**
  ```
  Dog ---► Animal
  ```
- **Exemple en Java :**
  ```java
  class Animal {
      void eat() {
          System.out.println("This animal eats food.");
      }
  }

  class Dog extends Animal {
      void bark() {
          System.out.println("The dog barks.");
      }
  }
  ```

---

## 2. **Implémentation** (`implements`)
- **Relation :** Une classe concrète implémente une ou plusieurs interfaces.
- **Flèche UML :** **Triangle vide** à l'extrémité.
- **Code UML :**
  ```
  Dog ---▷ Canine
  ```
- **Exemple en Java :**
  ```java
  interface Canine {
      void run();
  }

  class Dog implements Canine {
      public void run() {
          System.out.println("The dog runs fast.");
      }
  }
  ```

---

## 3. **Association**
- **Relation :** Un lien générique entre deux classes. Peut être unidirectionnel ou bidirectionnel.
- **Flèche UML :** **Ligne simple** avec ou sans multiplicités.
- **Code UML avec multiplicité :**
  ```
  Person 1 ------ * Car
  ```
- **Multiplicité détaillée :**
  - **1 :** Exactement une instance.
  - **0..1 :** Aucune ou une seule instance (optionnel).
  - **1..* :** Au moins une instance.
  - **0..* :** Aucune ou plusieurs instances.
- **Exemple en Java :**
  ```java
  class Car {
      String model;
      Car(String model) {
          this.model = model;
      }
  }

  class Person {
      List<Car> cars = new ArrayList<>();
      void addCar(Car car) {
          cars.add(car);
      }
  }
  ```

---

## 4. **Agrégation**
- **Relation :** "Part-of" faible. La partie peut exister sans le tout.
- **Flèche UML :** **Ligne avec un losange vide** côté conteneur.
- **Code UML :**
  ```
  Team ◇------ Player
  ```
- **Exemple en Java :**
  ```java
  class Player {
      String name;
      Player(String name) {
          this.name = name;
      }
  }

  class Team {
      List<Player> players = new ArrayList<>();
      void addPlayer(Player player) {
          players.add(player);
      }
  }
  ```

---

## 5. **Composition**
- **Relation :** "Part-of" forte. La partie dépend du tout pour exister.
- **Flèche UML :** **Ligne avec un losange plein** côté conteneur.
- **Code UML :**
  ```
  House ◆------ Room
  ```
- **Exemple en Java :**
  ```java
  class Room {
      Room() {
          System.out.println("Room created.");
      }
  }

  class House {
      List<Room> rooms = new ArrayList<>();
      House() {
          rooms.add(new Room());
          rooms.add(new Room());
      }
  }
  ```

---

## 6. **Dépendance**
- **Relation :** Une classe dépend temporairement d'une autre (relation faible).
- **Flèche UML :** **Ligne en pointillés avec flèche**.
- **Code UML :**
  ```
  Printer - - - > Document
  ```
- **Exemple en Java :**
  ```java
  class Document {
      String content;
      Document(String content) {
          this.content = content;
      }
  }

  class Printer {
      void print(Document doc) {
          System.out.println("Printing: " + doc.content);
      }
  }
  ```

---

## 7. **Généralisation**
- **Relation :** Représente un lien générique (relation "is-a").
- **Flèche UML :** **Triangle plein**.
- **Code UML :**
  ```
  Rectangle ---► Shape
  ```
- **Exemple en Java :**
  ```java
  abstract class Shape {
      abstract void draw();
  }

  class Rectangle extends Shape {
      void draw() {
          System.out.println("Drawing a rectangle.");
      }
  }
  ```

---

## 8. **Réalisation**
- **Relation :** Une classe réalise un contrat défini par une interface.
- **Flèche UML :** **Ligne en pointillés avec un triangle vide**.
- **Code UML :**
  ```
  Car - - ▷ Drivable
  ```
- **Exemple en Java :**
  ```java
  interface Drivable {
      void drive();
  }

  class Car implements Drivable {
      public void drive() {
          System.out.println("The car is driving.");
      }
  }
  ```

---

## Multiplicité en détail :
La **multiplicité** définit le nombre d'instances qui peuvent exister dans une relation entre deux classes. Elle est représentée par des nombres ou des plages (ex. `0..*`).

| **Symbole** | **Description**                              | **Exemple UML**       |
|-------------|----------------------------------------------|-----------------------|
| `1`         | Exactement une instance                     | `Person 1 ------ 1 Car` |
| `0..1`      | Aucune ou une seule instance (optionnel)     | `Person 0..1 ------ 1 Address` |
| `1..*`      | Une ou plusieurs instances                  | `Person 1..* ------ Book` |
| `0..*`      | Aucune ou plusieurs instances (optionnel)   | `Person 0..* ------ Phone` |

### Exemple UML avec multiplicité :
```
Person 1 ------ * Car
```
Cela signifie :
- Une personne (`Person`) possède **au moins une voiture** (`Car`).

---

### Exemple Java avec multiplicité :
#### Multiplicité 1:
```java
class Person {
    Car car; // Exactement une voiture.
}
```

#### Multiplicité 1..*:
```java
class Person {
    List<Car> cars = new ArrayList<>(); // Une ou plusieurs voitures.
}
```

#### Multiplicité 0..1:
```java
class Person {
    Car car; // Optionnel : aucune ou une voiture.
}
```

#### Multiplicité 0..*:
```java
class Person {
    List<Car> cars = new ArrayList<>(); // Optionnel : aucune ou plusieurs voitures.
}
```

---
