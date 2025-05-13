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
