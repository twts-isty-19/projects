# Trello ⭐

Le but du projet est de créer une version simplifiée d'un trello,
permettant à plusieurs utilisateurs de s'organiser dans la réalisation
d'un projet.

### Description de l'application

Un tableau trello est constitué de plusieurs colonnes (par exemple "À faire", "Travail en cours" et "Terminé") et de tâches (par exemple "Faire le projet
AWS"), chaque tâche étant affectée à une colonne.

Les utilisateurs peuvent créer:
* des tâches dans chacune des colonnes ;
* changer une tâche de colonne ;
* créer une nouvelle colonne en lui donnant un nom ;
* changer le titre du tableau.

### Description du projet

Vous devez réaliser un site hébergeant un clone de Trello. Il doit comporter :

- Une page permettant de s'enregistrer,
- Un mécanisme pour se connecter,
- Un mécanisme permettant de créer une colonne,
- Un mécanisme permettant de créer une tâche,
- Un mécanisme permettant de changer une tâche de colonne.

Il est de votre responsabilité de gérer le cas où l'utilisateur crée deux
colonnes du même nom: soit refuser la création de la colonne, soit en créer une
colonne du même nom.

Si vous voulez vous mettre en confiance, vous pouvez ne créer qu'un seul tableau
que tous les utilisateurs peuvent voir et modifier. Si vous vous sentez à
l'aise, vous pouvez dès le début concevoir l'application pour qu'elle gère
plusieurs tableaux.

Ce projet est réalisable de façon satisfaisante sans utiliser
d'interactivité côté client. Nous
vous conseillons "d'assurer" et de produire dans un premier temps une version
utilisant uniquement du templating côté serveur. Cependant, vous serez plafonnés
à 11/20 si la page se recharge entièrement à chaque création de tâche ou changement de colonne.

### Conseils d'implémentation

#### Base de données
En base de données, une "colonne" contient un champ "utile":
* son nom.
On rappelle qu'en SQLite, une colonne "rowid" est implicitement créée et sert
de remplacement à une colonne en "AUTO INCREMENT".

Une "tâche" contiendra deux champs:
* la description de la tâche,
* un clef étrangère vers la colonne à laquelle elle appartient.

Si vous autorisez plusieurs tableaux, il faudra une table "tableaux"
avec son nom. Il faudra également rajouter une clef étrangère à la table
"colonne" vers la table tableaux.


#### Routes

Vous êtes libres de structurer la logique de l'application comme vous
le souhaitez. Nous proposons ici un exemple de découpage en
gestionnaires :
- Route `/` : présentant la page d'accueil principale. On peut envisager une
  redirection vers `/login/` si l'utilisateur n'est pas loggé.
- Route `/signup/` : permettant de créer un nouvel utilisateur.
- Route `/login/` : permettant de se connecter. Redirige vers `/` après
  un login réussi.
- Route `/logout/` : permettant de se déconnecter. Redirige vers `/` après
  un logout réussi.
- Route `/add-column/` : permettant d'ajouter une colonne
  - Si AJAX, renvoie un code de succès/erreur.
  - Si non-AJAX, redirige vers `/` après un ajout réussi.
- Route `/column/<columnid>/add-task/` : permettant de créer une tâche sur la
  colonne `<columnid>`.
  - Si AJAX, renvoie un code de succès/erreur.
  - Si non-AJAX, redirige vers `/` après un ajout réussi.
- Route `/task/<taskid>/move/` : pour changer la colonne où est affectée la
  tâche `<taskid>`.

### Parties optionnelles

- Permettre la création de plusieurs tableaux ; le créateur d'un tableau peut
  ajouter des membres existants à son tableau, ce qui permettra à ces membres
  de consulter et/ou modifier le tableau.

  Le créateur d'un tableau pourra également lui donner un nom afin de le
  retrouver aisément.
- Ajouter des rôles aux membres de tableaux. Par exemple "admin" (tous les
  droits, y compris ajouter/retirer des membres), "éditeur" (modification des
  des colonnes et tâches) et "visiteur" (lecture seule).

  Vous pouvez pousser ce système d'autorisations plus loin en donnant la
  possiblité de définir des permissions pour chaque action.

- Permettre d'affecter une tâche à une personne.
- Ajouter la possibilité aux membres de définir un avatar personnalisé. Stocker
  des images peut-être un peu délicat, vous pouvez utiliser un encodage en
  base64 afin de vous libérer de cette contrainte (penser à limiter la taille
  des avatars!).

  Vous pouvez définir un avatar par défaut en utilisant un service similaire à
  [http://avatars.adorable.io/](http://avatars.adorable.io/).
- Mettre à jour automatiquement le tableau d'un utilisateur A lorsqu'un
  utilisateur B effectue une action en utilisant une websocket.

