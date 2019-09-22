# Bataille navale ⭐⭐

Le but de ce projet est de réaliser un jeu de bataille navale en ligne
multi-utilisateur.


### Description du jeu

On rappelle le principe de la bataille navale.

- Deux joueurs disposent chacun d'une grille de jeu (par ex., de 10×10
  cases).

- Chaque joueur dispose du même nombre de navires. Les navires peuvent
  occuper une, deux, trois ou quatre cases.

- Avant de commencer la partie, chaque joueur dispose ses navires sur
  sa grille.

- À tour de rôle, un joueur décide de frapper une case sur la grille
  du joueur adverse. S'il touche un navire, l'adversaire lui annonce
  « touché », sinon il lui annonce « manqué ». Lorsque toutes les
  cases d'un même navire ont été touchées, le joueur annonce « coulé ».

- Gagne le joueur qui en premier coule tous les navires de
  l'adversaire.

### Description du projet

Le projet doit comporter :

- Une page permettant de s'enregistrer,
- Une page présentant la liste des utilisateurs en ligne, leur nombre
  de parties gagnées/perdues, et autres informations éventuelles,
- Un mécanisme pour se connecter,
- Un mécanisme permettant de défier un adversaire,
- Une interface permettant de jouer le jeu.

L'interface du jeu doit être réalisée en Elm :

- Les navires sont disposés aléatoirement ;
- Chauque joueur voit les deux grilles :
  - Sur sa propre grille toutes les informations sont affichées :
	disposition des navires, navires touchés/coulés, cases frappées ;
  - Sur la grille de l'adversaire, uniquement les cases frappées,
    touchées, coulées sont affichées, mais pas les bateaux.
- Le joueur doit pouvoir sélectionner la case à frapper en cliquant
  dessus.
- L'affichage montre clairement si la frappe a manqué/touché/coulé.
- Lorsqu'un joueur a coulé tous les navires de son adversaire, le jeu
  déclare le joueur gagnant.

### Ressources


- [La page wikipedia du jeu de la bataille navale](https://fr.wikipedia.org/wiki/Bataille_navale_%28jeu%29).

**Interface**

Pour l'interface de jeux vous avez plusieurs choix :

- Une interface minimaliste, avec une grille de jeux représentée par
  un tableau HTML ou similaire.

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


- Créez une interface qui permet aux joueurs de placer leurs navires
  avant le début de la partie.

- Faites une version multi-joueurs du jeu : les joueurs sont séparés
  en deux équipes, qui essaient de collaborer pour vaincre les
  adversaires.
