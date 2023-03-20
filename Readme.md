# Boucle **non** bloquante

Cet exemple corrige l'erreur conceptuelle est ses effets négatifs sur l'ergonomie de l'application présentée dans l'exemple *Boucle bloquante*.

## Analyse

Après avoir cliqué sur le bouton `Démarrer`, la sortie de l'application (journal) affiche l'incrémentation des valeurs de la variable `i`. La barre de progression est fonctionnelle sur toutes les plateformes (Windows, Linux, MacOS) et l'interface graphique répond. Il serait possible de déclencher un autre traitement ou d'interrompre le traitement en cours.

Contrairement à son contre-exemple, dans celui-ci les itérations sont effectuées en passant des appels sur la run-loop. Ainsi, au lieu d'effectuer `n` itérations en un bloc ininterruptible, ce sont `n` appels qui sont passés successivment à la run-loop et le traitement est fluidifié au travers de celle-ci.

Il devient alors possible d'interrompre le traitement en ajoutant un booléen qui serait vérifié avant chaque appel à la fonction `QTimer::singleShot()`.

