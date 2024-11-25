### Composition et Agrégation en UML et Java

### **1. Composition**

#### Diagramme UML : Composition entre `House` et `Room`

```plaintext
+----------------+
|     House      |
+----------------+
| - rooms: List  |
+----------------+
| + addRoom()    |
| + displayRooms()|
+----------------+
         ◆
         │
+----------------+
|     Room       |
+----------------+
| - name: String |
+----------------+
```

#### Code Java

```java
import java.util.ArrayList;
import java.util.List;

// Classe représentant une pièce
class Room {
    private String name;

    public Room(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

// Classe représentant une maison
class House {
    private List<Room> rooms;

    public House() {
        rooms = new ArrayList<>();
    }

    // Ajoute une pièce à la maison
    public void addRoom(String roomName) {
        Room room = new Room(roomName); // La maison crée directement l'objet Room
        rooms.add(room);
    }

    // Affiche toutes les pièces de la maison
    public void displayRooms() {
        System.out.println("Rooms in the house:");
        for (Room room : rooms) {
            System.out.println("- " + room.getName());
        }
    }
}

// Classe principale
public class Main {
    public static void main(String[] args) {
        House house = new House();

        // Ajout de pièces à la maison
        house.addRoom("Living Room");
        house.addRoom("Bedroom");
        house.addRoom("Kitchen");

        // Affichage des pièces
        house.displayRooms();

        // Une fois la maison détruite, les pièces n'existent plus.
    }
}
```

---

### **2. Agrégation**

#### Diagramme UML : Agrégation entre `Classroom` et `Student`

```plaintext
+----------------+
|   Classroom    |
+----------------+
| - students: List|
+----------------+
| + addStudent() |
| + displayStudents()|
+----------------+
         ◇
         │
+----------------+
|    Student     |
+----------------+
| - name: String |
+----------------+
```

#### Code Java

```java
import java.util.ArrayList;
import java.util.List;

// Classe représentant un étudiant
class Student {
    private String name;

    public Student(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

// Classe représentant une salle de classe
class Classroom {
    private List<Student> students;

    public Classroom() {
        students = new ArrayList<>();
    }

    // Ajoute un étudiant existant à la classe
    public void addStudent(Student student) {
        students.add(student); // La salle de classe n'est pas responsable de la création des étudiants
    }

    // Affiche tous les étudiants de la classe
    public void displayStudents() {
        System.out.println("Students in the classroom:");
        for (Student student : students) {
            System.out.println("- " + student.getName());
        }
    }
}

// Classe principale
public class Main {
    public static void main(String[] args) {
        // Création d'étudiants indépendamment de la classe
        Student student1 = new Student("Alice");
        Student student2 = new Student("Bob");
        Student student3 = new Student("Charlie");

        // Création d'une salle de classe
        Classroom classroom = new Classroom();

        // Ajout des étudiants à la classe
        classroom.addStudent(student1);
        classroom.addStudent(student2);

        // Affichage des étudiants
        classroom.displayStudents();

        // L'étudiant existe indépendamment de la salle de classe
        System.out.println("Student " + student3.getName() + " is not in the classroom.");
    }
}
```

---

### Tableau comparatif : Composition vs Agrégation

| **Aspect**            | **Composition**                         | **Agrégation**                          |
|------------------------|------------------------------------------|------------------------------------------|
| **Cycle de vie**       | Les parties dépendent entièrement du tout. Si le tout est détruit, les parties sont également détruites. | Les parties peuvent exister indépendamment du tout. |
| **Représentation UML** | Losange **plein** (◆)                   | Losange **vide** (◇)                    |
| **Responsabilité**     | La classe contenant est responsable de créer les parties. | La classe contenant utilise des parties créées ailleurs. |
| **Exemple**            | Une `House` contient des `Room`.        | Une `Classroom` contient des `Student`. |
| **Couplage**           | Relation étroitement couplée.           | Relation faiblement couplée.            |

---
