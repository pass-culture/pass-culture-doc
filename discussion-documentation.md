# Préambule
Suite à la dernière rétro j'ouvre le débat "documentation", on essaie de faire ça de manière asynchrone ici et on voit où ça nous mène et si il faut compléter par un autre medium. 
Avoir la discussion ici plutôt que par mail nous permettra de facilement amender et faire des liens / citation et pourra servir de référence aux éventuelles décisions qui en découleront (mais je suis déjà en train de prêcher pour ma paroisse :blush:)

Je propose de faire des commentaires voir des PR pour, dans un premier temps, lister et développer tous les arguments de manière intelligible (et synthétique)

# Objectifs
L'objectif de cette discussion est de déterminer :

1. Si oui ou non nous écrivons de la documentation
2. Si oui, l'objet : qu'est-ce qui doit être documenté ?
3. Si oui, la forme : comment, où créer la documentation


# Positions

> _**Disclaimer :** Je vais rapporter des points de vue qui ne sont pas les miens et qui ont été échangés il y a plusieurs semaines, toute erreur ou sur-interprétations ne serait que le fruit de ma subjectivité et de ma mémoire déficiente #noOffense_ 

> Les assertions `PROS` sont préfixées et numérotées P1, P2, etc. et les `CONS` C1, C2, etc. afin de permettre une référence succincte dans les discussions

## PROS


### P1 - Le code doit être utilisable sans connaître les détails d'implémentation
C'est particulièrement important pour tout ce qui a vocation à être utilisé par d'autres développeurs (autre que l'auteur du code).

Par exemple il n'est pas nécessaire de lire le code source de React ou de Flask pour utiliser ces librairies.

Les commandes unix ont généralement une entrée de `man` associée et/ou une option `--help` (on imagine pas aller lire le code source de `ls` pour connaitre les options disponibles).


### P2 - La documentation est un contrat d'interface
Écrire la documentation devrait être un préalable au développement, de la même manière qu'on parle de TDD, on pourrait parler de Documentation Driven Dev. ou Documentation First pour les APIs, c'est un peu l'idée derrière [OpenAPI/Swagger](https://www.openapis.org/).
Cela permet :
 * lors de la conception, de se concentrer sur la cohérence de l'API (nommages, arguments) 
 * d'avoir un **contrat d'interface** que le code devra honorer tout au long de sa vie (au moins pour une version majeure donnée) et ce, peut importe les détails d'implémentation interne.
 * le développement de programmes clients sans attendre la fin du développement d'un service.
 * de se passer de specifications fonctionnelles plus formelles dans certains cas


### P3 - L'écrit est un moyen plus efficace et pérenne que l'oral de transmettre la connaissance
S'il est vraiment nécessaire d'argumenter sur ce point mieux vaux renvoyer vers [wikipedia](https://fr.wikipedia.org/wiki/%C3%89criture#Impact_culturel)


### P4 - Soliciter les collaborateurs les freine
Solliciter les collaborateur pose le problème du context switching, attendre qu'il soient disponible n'est pas meilleur pour la productivité


### P5 - Les collaborateurs ne sont pas toujours disponibles
La majorité des contributeurs sont soit au 4/5ème sur le projet et/ou ont régulièrement des événements qui les prive d'une journée dans la semaine (événements Octo ou Beta.gouv).


## CONS

### C1 - Le code doit être auto-documenté
Le code doit être écrit (découpage, nommage) de manière suffisamment claire pour ne pas nécessiter de documentation.
Corollaire : S'autoriser de la documentation diminue l'exigence de qualité du code.
 
### C2 - Les tests doivent fournir suffisamment de documentation

### C3 - Mettre à jour la documentation est couteux

Et redondant avec le travail fait pour l'écriture des tests

### C4 - Solliciter les autres peut permettre de partager plus que ce que contiendrait la documentation

Les tests sont une documentation, mais elle ne saurait être complète ou suffisante pour un nouvel arrivant sur le projet, ou simplement pour quelqu'un qui n'a pas encore manipulé le code dans son ensemble.
Ceci, des tests situés au bon niveau d'abstraction peuvent être très utiles : des tests de routes me renseignements sur les différents status codes, payloads et responses auxquels je peux m'attendre.
Ils constituent donc une documentation exécutable.


### C3 - La documentation, comme les commentaires, a tendance a vieillir plus mal que le code

La documenation, comme les commentaires, constitue une méta-donnée sur le code.
Le problème est qu'on ne dispose d'aucun mécanisme qui permettre de dire si la documentation est correcte, au contraire du code qui dispose des tests automatisés pour cela.
L'erreur est humaine, et ainsi, si une documentation n'est pas mise à jour et qu'on ne s'en aperçoit pas, on a un décalage entre ce que le code fait, et ce que le commentaire / la doc dit que le code fait.
En fin de compte, pour être sûr, on finit toujours par aller voir le code.


### C4 - La documentation complète n'existe pas

Il est extrêmement difficile de représenter l'entiereté d'un système d'information. Au mieux, on ne peut en réprésenter que des vues abstraites et incomplètes :
    + une vue du modèle de donnée
    + une vue sur les fonctionnalités du point de vue des utilisateurs
    + les différents utilisateurs (personas)
    + la structure du code
    + une vue des flux de données entre le système et ses systèmes partenaires
    + une vue d'architecture applicative
    + une vue d'infrastructure logique
    + une vue d'infrastructure technique
    + etc.

Tous ces aspects du SI ne changent pas au même rythme.