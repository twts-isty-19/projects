# Bomberman ⭐⭐⭐

Le but de ce projet est de développer un jeu à deux joueurs en temps
réel. On va choisir l'*arcade* très populaire
[*Bomberman*](https://en.wikipedia.org/wiki/Bomberman).

### Description du jeu

Bomberman se joue de deux a quatre joueurs. Les joueurs démarrent aux
coins opposés d'une une grille 11×11.

Les joueurs peuvent se déplacer librement dans la grille. Toutes les
cases de coordonnées paires de la grille sont inaccessibles, formant
ainsi des couloirs pour les joueurs.

Les joueurs disposent d'un nombre illimité de bombes à retardement,
qu'ils peuvent placer dans une case libre. Les bombes explosent après
un nombre prédéterminé de secondes. Aucun joueur ne peut déposer plus
d'une bombe en même temps.

Lorsqu'une bombe explose, son explosion frappe dans quatres
directions, jusqu'à une distance préderminée. Un joueur frappé par une
explosion est éliminé du jeu.

Une [vidéo](https://www.youtube.com/watch?v=DZNcCowQKRQ) va expliquer
mieux que mille mots.

### Description du projet

Vous devez réaliser un jeu de Bomberman en ligne. Il doit comporter :

- Une page permettant de s'enregistrer,
- Une page présentant la liste des utilisateurs en ligne,
- Un mécanisme pour se connecter,
- Un mécanisme permettant de défier un adversaire,
- Une interface permettant de jouer le jeu.

L'interface du jeu doit être réalisée en Elm. Pour faire
simple, limitez vous à un jeu basique :

- Uniquement deux joueurs;
- Pas de murs autres que les murs indestructibles;
- Pas d'*upgrades*;
- Pas de temps limite.

Les joueurs peuvent contrôler leur personnage avec le clavier: flèches
pour se déplacer, espace pour déposer une bombe.

Le serveur devra gérer plusieurs parties simultannées. On pourra stocker l'état
des parties dans une variable globale dans un premier temps.


**Note pratique:** le rôle du client sera essentiellement d'afficher les données
du jeu envoyées par le serveur et  de transmettre au serveur les actions de
l'utilisateur ; le gros de la logique sera traité par le serveur.

**Note légale:** on vous rappelle que le jeu Bomberman est un copyright de
Konami. Si vous avez droit de développer le jeu dans un but
pédagogique, mettre votre application à disposition du public aurait
des implications légales fâcheuses.


### Ressources


**Évènements claviers**

Vous aurez besoin de capturer les évènements clavier en Elm, pour cela il vous
faut utiliser [ce package](https://package.elm-lang.org/packages/elm/browser/latest/Browser-Events#keyboard). Il s'agit d'une souscription, vous devrez donc
utiliser ces fonctions dans la fonction `subscriptions`. Lisez également [cette
page de documentation](https://github.com/elm/browser/blob/1.0.0/notes/keyboard.md).

Vous pouvez également consulter (cet exemple)[https://elm-lang.org/examples/first-person] pour apprendre à gérer le clavier (vous pouvez ignorer la partie
sur WebGL, concentrez vous sur les types, les messages, les fonctions `update`,
`updateKeys` et `subscriptions`).

**Interface**

Pour l'interface de jeux vous avez plusieurs choix :

- Une interface minimaliste, avec une grille de jeux représentée par
  un tableau HTML ou similaire, et où les personnages
  sont positionnés avec un `display: absolute`.

- Une interface plus fluide, utilisant la balise `<canvas>` pour
  dessinner avec des primitives graphiques. En Elm, vous pouvez utiliser
  [ce package](https://package.elm-lang.org/packages/joakin/elm-canvas/latest/),
  dont [vous pouvez trouver un exemple
  d'utilisation sur Ellie](https://ellie-app.com/62Dy7vxsBHZa1) (notez que vous
  avez besoin d'inclure un fichier Javascrip externe &ndash; voir le code HTML
  du Ellie).
- Utiliser [du WebGL](https://package.elm-lang.org/packages/elm-community/webgl/latest)
  afin de tirer parti de la carte graphique (évidemment, c'est beaucoup
  plus dur que les deux autres points, je ne vous conseille de l'essayer que!).



### Parties optionnelles

- Utiliser Redis à la place d'une variable globale pour ne pas avoir de soucis
  de concurrence. Vous pouvez créer un compte gratuitement sur [RedisLabs](https://app.redislabs.com) puis créez une "base de données". Voir le [glitch
  suivant](https://glitch.com/edit/#!/flask-redis-example) pour utiliser avec
  Flask.

  C'est vraiment le premier "bonus" à réaliser, on ne peut pas sérieusement
  prétendre gérer du temps réel et utiliser une variable globale comme nous
  l'avons expliqué dans les TDs; la mise en
  place ne devrait pas poser de soucis majeurs.

  *Note:* Redis stocke tout sous forme de chaînes de caractères. L'exemple mis
  à disposition utilise une classe "maison" afin d'automatiquement sérialiser
  les valeurs Python lors de l'enregistrement dans la base de données puis de
  les désérialiser lorsque vous récupérer les données. L'utilisation de cette
  classe n'est pas du tout obligatoire.

- Permettre des parties jusqu'à 4 joueurs.

- Ajouter des caractéristiques du jeu original, ou de votre crû : murs
  destructibles, *upgrades*, etc.

- Proposer un "éditeur de maps" pour construire des terrains de jeu
  personnalisés.

- Permettre de contrôler le personnage à la souris : clic gauche pour
  se déplacer, clic droit pour déposer une bombe. Quel parcours
  choisir lorsque le déplacement ne peut pas se faire en ligne droite ?
