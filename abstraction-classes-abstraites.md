Les **classes abstraites** en Java jouent un rôle spécifique et offrent des avantages qui se situent entre les classes normales et les interfaces. Voici une explication claire et concise pour bien comprendre leur utilité :

### 1. **Classes normales** :
   - Une classe normale peut être instanciée (créée sous forme d'objet).
   - Elle contient des attributs et des méthodes concrètes.
   - Elle est utilisée pour représenter des entités complètes.

### 2. **Interfaces** :
   - Une interface ne contient que des méthodes abstraites (jusqu'à Java 7) et des constantes. Depuis Java 8, elle peut contenir des méthodes par défaut et des méthodes statiques.
   - Les classes qui implémentent une interface s'engagent à fournir une implémentation pour toutes ses méthodes abstraites.
   - Une classe peut implémenter plusieurs interfaces (héritage multiple), mais elle ne peut hériter que d'une seule classe.

### 3. **Classes abstraites** :
   Une classe abstraite combine certains aspects des classes normales et des interfaces :
   - **Elle peut contenir des méthodes abstraites** : méthodes sans corps (déclaration uniquement), obligatoires à implémenter dans les sous-classes.
   - **Elle peut aussi contenir des méthodes concrètes** : avec une implémentation.
   - **Elle peut avoir des attributs** (comme une classe normale).
   - Une classe abstraite ne peut pas être instanciée directement.

---

### **Quand utiliser une classe abstraite ?**
1. **Lorsque vous voulez définir un comportement de base commun à toutes les sous-classes, tout en permettant des variations spécifiques.**
   - Exemple : une classe `Animal` avec une méthode concrète `respirer()` et une méthode abstraite `crier()`.

2. **Quand vous voulez partager du code entre plusieurs classes liées.**
   - Contrairement aux interfaces, les classes abstraites permettent de fournir des méthodes avec une implémentation partielle.

3. **Si une relation d'héritage est naturelle.**
   - Exemple : `Voiture` hérite de `Véhicule`.

---

### **Différences principales entre interfaces et classes abstraites :**

| **Aspect**                     | **Interface**                            | **Classe abstraite**                    |
|---------------------------------|------------------------------------------|-----------------------------------------|
| Héritage                       | Une classe peut implémenter plusieurs.   | Une classe ne peut hériter que d'une seule. |
| Méthodes                       | Méthodes abstraites ou par défaut.       | Méthodes abstraites et concrètes.       |
| Attributs                      | Uniquement constants (static final).     | Attributs normaux et constants.         |
| Instanciation                  | Impossible.                              | Impossible.                             |
| Usage                         | Sert à définir un contrat.               | Sert à définir un comportement commun et partiel. |

---

## exemple UML : 
Est défini avec {classe abstraite}

![image](https://github.com/user-attachments/assets/e90a947b-10ec-4f90-ae63-625b367a8583)





