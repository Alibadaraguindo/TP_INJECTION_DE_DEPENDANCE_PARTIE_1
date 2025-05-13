GUINDO BADARA ALIOU
2100000017
MASTER SDIA FSM



TP Injection de Dépendances – PARTIE 1
Objectif

L’objectif de cette première partie est de mettre en œuvre différentes méthodes d’injection de dépendances en Java,
avec et sans Spring Framework.
Cela permet de démontrer l’importance du couplage faible et les avantages des frameworks comme Spring pour la gestion automatique des dépendances.

 Structure du projet

Le projet est organisé en plusieurs packages :
net.ali/
├── dao/ --> Interface IDao et son implémentation DaoImpl
├── ext/ --> Autre implémentation de IDao : DaoImplV2
├── metier/ --> Interface IMetier et sa classe MetierImpl
├── pres/ --> Classes de présentation :
│ - Pres1 (injection manuelle)
│ - Pres2 (injection via réflexion)
│ - presSpringXML (injection Spring XML)
│ - presSpringAnnotation (injection Spring annotations)
└── resources/ --> Fichiers de configuration :
- config.txt (pour Pres2)
- config.xml (pour Spring XML)

Chaque méthode d'injection est testée dans une classe différente.

Interfaces et Implémentations

- `IDao` : interface contenant la méthode `getData()`.
- `DaoImpl` : première implémentation (retourne une valeur simulée de base de données).
- `DaoImplV2` : deuxième implémentation (retourne une valeur simulée d’un capteur).
- `IMetier` : interface contenant la méthode `calcul()`.
- `MetierImpl` : classe métier qui dépend de `IDao`, avec injection via :
  - constructeur
  - setter
  - annotations Spring (`@Autowired`, `@Qualifier`)
    ![image](https://github.com/user-attachments/assets/f0aae4f7-5cbc-478f-b5cb-649abdeeaea5)
 Injection des dépendances – Méthode 1 : Manuelle (Statique)

La classe `Pres1.java` illustre une injection manuelle des dépendances via le **constructeur** :
![image](https://github.com/user-attachments/assets/fc327f4f-50e7-4def-88d1-08f0eceeb2c9)

Injection des dépendances – Méthode 2 : Dynamique (Réflexion)

La classe `Pres2.java` utilise la **réflexion Java** pour lire les noms des classes depuis un fichier `config.txt`, les instancier dynamiquement, et injecter la dépendance :
![image](https://github.com/user-attachments/assets/d28150f7-2248-4f7a-ba7a-296c54617223)

![image](https://github.com/user-attachments/assets/b565cb89-8206-45d7-b13f-48042feb7881)

Injection avec Spring – Méthode 3 : Fichier XML

La classe `presSpringXML.java` utilise le framework Spring pour injecter les dépendances définies dans un fichier `config.xml` :
![image](https://github.com/user-attachments/assets/e3855ea5-c1cf-4ff9-ac4f-d5513ed764c2)
![image](https://github.com/user-attachments/assets/7dae9370-abf7-4b67-ab8f-84c66133251a)
![image](https://github.com/user-attachments/assets/81c80b7e-e409-408d-a5a8-79c8b9f4d4e6)
![image](https://github.com/user-attachments/assets/2ddac10a-ccaa-4c18-9b3b-877956b05f72)

 Injection avec Spring – Méthode 4 : Annotations

La classe `presSpringAnnotation.java` illustre l’utilisation des **annotations Spring** (`@Component`, `@Autowired`, `@Qualifier`) pour configurer automatiquement les dépendances sans fichier XML.

![image](https://github.com/user-attachments/assets/187a3750-2b2f-4000-a0ed-165fc83e9e32)
![image](https://github.com/user-attachments/assets/dfc69fad-571f-4bc4-9059-aee02e302149)

Conclusion

Ce travail pratique a permis d'explorer différentes méthodes d'injection de dépendances en Java, en partant des approches les plus simples jusqu’à l’utilisation du framework Spring. Plusieurs objectifs pédagogiques ont été atteints au fil des étapes :

- **Compréhension du couplage fort vs couplage faible** : les premières approches (manuelle par instanciation directe, ou par setter) ont mis en évidence les limites d’un couplage fort entre les composants, qui rend le code rigide et difficile à maintenir.
  
- **Découverte de la réflexion en Java** : l’injection dynamique via la lecture d’un fichier de configuration (`config.txt`) a introduit une forme d’inversion de contrôle rudimentaire. Cette solution permet de rendre le code plus souple, mais reste complexe à maintenir à grande échelle.
  
- **Introduction au framework Spring** :
  - L’utilisation d’un fichier XML (`config.xml`) a permis de déclarer les dépendances de manière déclarative, sans modifier le code source.
  - L’approche par annotations (`@Component`, `@Autowired`, `@Qualifier`) a ensuite permis une configuration encore plus légère et moderne, en exploitant le **scanning de packages** et l’**injection automatique** des composants.

Ces différentes méthodes illustrent l’évolution des pratiques de développement vers une architecture modulaire, flexible, et maintenable. Le framework Spring se révèle particulièrement adapté pour les projets de taille moyenne à grande, grâce à sa capacité à gérer les dépendances, réduire le couplage entre les classes, et améliorer la testabilité du code.

L’ensemble du TP offre ainsi une base solide pour comprendre les principes de l’**Inversion de Contrôle (IoC)** et de **l’Injection de Dépendances (DI)**, piliers de l’architecture logicielle moderne.








