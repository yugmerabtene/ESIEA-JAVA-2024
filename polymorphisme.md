### Structure du Projet

```
src/
├── polymorphisme_soustypage/
│   ├── User.java
│   ├── Administrator.java
│   ├── Subscriber.java
│   └── MainSousTypage.java
├── polymorphisme_parametrique/
│   ├── User.java
│   ├── Administrator.java
│   ├── Subscriber.java
│   └── MainParametrique.java
├── polymorphisme_inclusion/
│   ├── User.java
│   ├── Administrator.java
│   ├── Subscriber.java
│   └── MainInclusion.java
├── polymorphisme_dynamique/
│   ├── User.java
│   ├── Administrator.java
│   ├── Subscriber.java
│   └── MainDynamique.java
├── polymorphisme_interface/
│   ├── User.java
│   ├── AdministratorAuth.java
│   ├── SubscriberAuth.java
│   ├── Authenticable.java
│   └── MainInterface.java
└── polymorphisme_adhoc/
    ├── User.java
    ├── Administrator.java
    ├── Subscriber.java
    └── MainAdHoc.java
```

### Explication et Code pour chaque Package

#### 1. Package `polymorphisme_soustypage`

##### Description

Le polymorphisme de sous-typage en Java repose sur l'héritage. Il permet aux sous-classes d'implémenter leurs propres versions des méthodes héritées de la classe parent. En utilisant une référence de type `User`, nous pouvons appeler la méthode `login()` sur des instances de `Administrator` et `Subscriber`, et Java exécutera la méthode correspondante dans la sous-classe.

##### Code

**Classe `User.java`**
```java
package polymorphisme_soustypage;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }
}
```

**Classe `Administrator.java`**
```java
package polymorphisme_soustypage;

public class Administrator extends User {
    @Override
    public void login() {
        System.out.println("Administrator logged in with elevated privileges.");
    }
}
```

**Classe `Subscriber.java`**
```java
package polymorphisme_soustypage;

public class Subscriber extends User {
    @Override
    public void login() {
        System.out.println("Subscriber logged in with limited privileges.");
    }
}
```

**Classe `MainSousTypage.java`**
```java
package polymorphisme_soustypage;

public class MainSousTypage {
    public static void main(String[] args) {
        User[] users = { new User(), new Administrator(), new Subscriber() };
        
        for (User user : users) {
            user.login(); // Appelle la méthode login() spécifique à chaque type d'objet
        }
    }
}
```

**Explication**:  
Dans cet exemple, chaque sous-classe redéfinit la méthode `login()` pour afficher un message différent selon le type de l'utilisateur. La méthode est appelée dynamiquement, déterminée à l'exécution en fonction du type réel de l'objet, malgré l'utilisation d'une référence de type `User`.

#### 2. Package `polymorphisme_parametrique`

##### Description

Le polymorphisme paramétrique utilise des classes génériques pour manipuler des types d'objets variés dans une même structure. Ici, `ArrayList<User>` stocke des instances de `User`, `Administrator`, et `Subscriber`, ce qui permet de manipuler les objets de manière homogène.

##### Code

**Classe `User.java`**
```java
package polymorphisme_parametrique;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }
}
```

**Classe `Administrator.java`**
```java
package polymorphisme_parametrique;

public class Administrator extends User {
    @Override
    public void login() {
        System.out.println("Administrator logged in with elevated privileges.");
    }
}
```

**Classe `Subscriber.java`**
```java
package polymorphisme_parametrique;

public class Subscriber extends User {
    @Override
    public void login() {
        System.out.println("Subscriber logged in with limited privileges.");
    }
}
```

**Classe `MainParametrique.java`**
```java
package polymorphisme_parametrique;

import java.util.ArrayList;

public class MainParametrique {
    public static void main(String[] args) {
        ArrayList<User> users = new ArrayList<>();
        users.add(new User());
        users.add(new Administrator());
        users.add(new Subscriber());

        for (User user : users) {
            user.login();
        }
    }
}
```

**Explication**:  
Dans cet exemple, la liste `users` contient des objets de types variés (User, Administrator, Subscriber) mais tous sont manipulés en tant que `User`. Le polymorphisme permet de gérer des types variés dans une structure générique sans connaître les types spécifiques au moment de la compilation.

#### 3. Package `polymorphisme_inclusion`

##### Description

Le polymorphisme d'inclusion permet de traiter des objets d'une sous-classe comme des instances de la classe parent, grâce à l'assignation de sous-classes à des références de type parent.

##### Code

**Classe `User.java`**
```java
package polymorphisme_inclusion;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }
}
```

**Classe `Administrator.java`**
```java
package polymorphisme_inclusion;

public class Administrator extends User {
    @Override
    public void login() {
        System.out.println("Administrator logged in with elevated privileges.");
    }
}
```

**Classe `Subscriber.java`**
```java
package polymorphisme_inclusion;

public class Subscriber extends User {
    @Override
    public void login() {
        System.out.println("Subscriber logged in with limited privileges.");
    }
}
```

**Classe `MainInclusion.java`**
```java
package polymorphisme_inclusion;

public class MainInclusion {
    public static void main(String[] args) {
        User user1 = new Administrator();
        User user2 = new Subscriber();

        user1.login();
        user2.login();
    }
}
```

**Explication**:  
Ici, les instances de `Administrator` et `Subscriber` sont assignées à des variables de type `User`, ce qui démontre le polymorphisme d'inclusion. Bien que référencés comme des `User`, ces objets conservent leur comportement propre lors de l'appel de `login()`.

#### 4. Package `polymorphisme_dynamique`

##### Description

Le polymorphisme dynamique utilise la résolution tardive des méthodes, où la méthode appelée dépend du type réel de l'objet à l'exécution. 

##### Code

**Classe `User.java`**
```java
package polymorphisme_dynamique;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }
}
```

**Classe `Administrator.java`**
```java
package polymorphisme_dynamique;

public class Administrator extends User {
    @Override
    public void login() {
        System.out.println("Administrator logged in with elevated privileges.");
    }
}
```

**Classe `Subscriber.java`**
```java
package polymorphisme_dynamique;

public class Subscriber extends User {
    @Override
    public void login() {
        System.out.println("Subscriber logged in with limited privileges.");
    }
}
```

**Classe `MainDynamique.java`**
```java
package polymorphisme_dynamique;

public class MainDynamique {
    public static void main(String[] args) {
        User user = getUserType();
        user.login();
    }

    public static User getUserType() {
        return new Administrator(); // Peut retourner un Administrator ou un Subscriber
    }
}
```

**Explication**:  
Dans ce cas, la méthode `login()` appelée dépend de l'objet instancié par `getUserType()` au moment de l'exécution. Cela montre la résolution dynamique des méthodes, où le type de la classe spécifique est déterminé au runtime.

#### 5. Package `polymorphisme_interface`

##### Description

Le polymorphisme avec interfaces permet de manipuler différents types d'objets qui implémentent une même interface, sans héritage direct.

##### Code
## Package polymorphisme_interface

**Classe User.java**
```java
package polymorphisme_interface;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }
}

```


**Interface `Authenticable.java`**
```java
package polymorphisme_interface;

public interface Authenticable {
    void authenticate();
}
```

**Classe `AdministratorAuth.java`**
```java
package polymorphisme_interface;

public class AdministratorAuth extends User implements Authenticable {
    @Override
    public void authenticate() {
        System.out.println("Administrator authenticated.");
    }
}
```

**Classe `SubscriberAuth.java`**
```java
package polymorphisme_interface;

public class SubscriberAuth extends User implements Authenticable {
    @Override
    public void authenticate() {
        System.out.println("Subscriber authenticated.");
    }
}
```

**Classe `MainInterface.java`**
```java
package polymorphisme_interface;

public class MainInterface {
    public static void main(String[] args) {
        Authenticable admin = new AdministratorAuth();
        Authenticable subscriber = new SubscriberAuth();

        admin.authenticate();
        subscriber.authenticate();
    }
}
```

**Explication**:  
Les classes `AdministratorAuth` et `Subscriber

Auth` implémentent `Authenticable`, ce qui permet de les manipuler via l'interface. On peut donc appeler `authenticate()` indépendamment du type de chaque objet, tant qu'il implémente l'interface.

#### 6. Package `polymorphisme_adhoc`

##### Description

Le polymorphisme ad hoc ou statique consiste à surcharger des méthodes pour offrir plusieurs versions de la même méthode avec des signatures différentes.

##### Code

**Classe `User.java`**
```java
package polymorphisme_adhoc;

public class User {
    public void login() {
        System.out.println("User logged in.");
    }

    public void login(String userType) {
        System.out.println(userType + " logged in.");
    }
}
```

**Classe `Administrator.java`**
```java
package polymorphisme_adhoc;

public class Administrator extends User {
    @Override
    public void login() {
        System.out.println("Administrator logged in with elevated privileges.");
    }
}
```

**Classe `Subscriber.java`**
```java
package polymorphisme_adhoc;

public class Subscriber extends User {
    @Override
    public void login() {
        System.out.println("Subscriber logged in with limited privileges.");
    }
}
```

**Classe `MainAdHoc.java`**
```java
package polymorphisme_adhoc;

public class MainAdHoc {
    public static void main(String[] args) {
        User user = new User();
        user.login();
        user.login("Administrator");
    }
}
```

**Explication**:  
Dans cet exemple, `login()` est surchargée dans `User`, permettant d'appeler des versions différentes de la même méthode selon les paramètres fournis. C'est une forme de polymorphisme statique où la méthode à appeler est déterminée au moment de la compilation.
