# Calendar ⭐

Le but du projet est de définir une application permettant de gérer un
calendrier personnel, un peu comme Google Calendar.

### Description

Un calendrier est une suite d'événements, qui **ne doivent jamais se
chevaucher ou se superposer**.  Un événement a au moins :

* un titre,
* une date et heure de début,
* une date et heure de fin,
* un créateur.

Ces champs sont reflétés dans une table SQL. Une autre table SQL
sera utilisée pour stocker les utilisateurs et leurs mots de passe.

L'application est composée de deux *vues* :

- Une page pour enregistrer un nouvel utilisateur. Vous pouvez suivre
  le modèle déjà utilisé en TD.

- Une page principale, présentant le planning de la semaine, et :
  - soit un formulaire de login, si l'utilisateur n'est pas connecté,
  - soit un lien de déconnexion, si l'utilisateur est connecté.

#### La page principale

Sur la page principale, le planning de la semaine courante apparaît
sous la forme d'une grande table, avec **une colonne par jour**. En
première approximation, vous pouvez découper chaque jour en **48 cases
d'une demie heure** chacune.

Les évènements sont représentés en colorant les plages horaires
occupées, par exemple en rouge. Utilisez des classes CSS pour
distinguer les cases libres des cases occupées. La première case d'un
évènement doit contenir le titre et le créateur de l'évènement.

Des boutons/menus permettent de naviguer dans les semaines.

**Note :** Il existe d'autres solutions, que de diviser le jour en 48
plages. Par exemple vous pouvez utiliser du positionnement CSS et des
hauteurs fixes. Les possibilités sont nombreuses, et permettent de
réaliser des grains plus fin que la demie heure. Libre à vous de les
explorer.

#### Ajout d'un nouvel évènement

Uniquement les utilisateurs connectés ont droit de modifier le
calendrier. Il vont faire cela en interagissant avec le tableau de la
semaine.

Un clic sur une case déjà occupé ne fait aucune action, ou donne un
message d'erreur, au choix.

Un clic sur une case libre ouvre une interface (une "modale" semble
le plus adapté), permettant de préciser le
titre de l'évènement, de modifier les heures de début et de fin, et
éventuellement d'autres informations (couleur, description,
etc...). Après validation, une requête est envoyée au serveur et
l'événement est inséré dans la base de données.  Si l'insertion
s'effectue avec succès, le nouvel évènement est affiché dans le
tableau.

Une interaction de type AJAX et préférable pour cette action, bien que
tout soit réalisable avec du templating côté seveur. Cependant, vous serez
plafonnés à 11/20 si la page se recharge entièrement à chaque action.

**Attention :** prêtez attention à vérifier la validité d'un évènement
(format des dates, non-chevauchement, etc.) du côté serveur, et pas
uniquement du côté client.  Si plusieurs utilisateurs modifient en
même temps le calendrier, rater cette vérification peut amener à des
conflits. Affichez un message d'erreur significatif lorsque cette
étape de validation ne passe pas.

#### Suppression d'un évènement

En plus d'afficher les informations décrites ci-dessus, uniquement
pour les évènements créés par l'utilisateur connecté, donner un moyen
(bouton, lien, croix, ...) de supprimer l'évènement.  Demander
confirmation avant de supprimer. Lorsque l'utilisateur confirme,
envoyer une requête, mettre à jour la base de données, et actualiser
l'affichage en cas de succès.

#### Routes

Vous êtes libres de structurer la logique de l'application comme vous
le souhaitez. Nous proposons ici un exemple de découpage en
gestionnaires :

- Route `/` : présentant la page principale.
- Route `/signup/` : permettant de créer un nouvel utilisateur.
- Route `/login/` : permettant de se connecter. Redirige vers `/` après
  un login réussi.
- Route `/logout/` : permettant de se déconnecter. Redirige vers `/` après
  un logout réussi.
- Route `/add/` : permettant d'ajouter un évènement.
  - Si AJAX, renvoie un code de succès/erreur.
  - Si non-AJAX, redirige vers `/` après un ajout réussi.
- Route `/remove/` : permettant d'éliminer un évènement.
  - Si AJAX, renvoie un code de succès/erreur.
  - Si non-AJAX, redirige vers `/` après un ajout réussi.
- Route `/list/` : renvoyant la liste des événements au format JSON
  (ou XML, ou autre), pour un traitement chez le client. Uniquement si
  AJAX.

### Ressources

Si vous voulez diviser votre journée en parties plus fines que des
demies-heures, vous aurez probablement besoin de savoir exactement où
l'utilisateur a cliqué. Vous pouvez pour cela utiliser la bibliothèque suivante:
[mpizenberg/elm-pointer-events](https://package.elm-lang.org/packages/mpizenberg/elm-pointer-events/latest).


### Parties optionnelles

* Ajouter la possibilité de modifier ses propres évènements.

* Gérer les clics glissés (clics qui commencent sur une case et qui
  terminent sur une autre). Les heures de début et de fin seront
  respectivement la plus petite et la plus grande parmi les deux
  cases. Utiliser des classes CSS pour visualiser la plage
  sélectionnée pendant le glissement.

* Définir quatre niveaux d'accès au calendrier : création,
  modification, effacement, administration. Les administrateurs ont
  droit de modifier/effacer les évènements de tout le monde. Ajouter
  une page d'administration, accessible uniquement aux
  administrateurs, pour donner/enlever ces droits aux utilisateurs.

  Créer un utilisateur spécial *guest*, qui correspond aux droits des
  utilisateurs non-connectés.

* Gérer plusieurs calendriers : dans ce cas, chaque calendrier a un
  identifiant (par exemple toto, et sera accessible à l'adresse
  <http://serveur-calendrier/toto>).

* Réaliser un affichage qui s'adapte à la taille de l'écran, notamment
  aux écrans mobiles. Ajouter de la gestion d'évènements tactiles, et
  tester avec un téléphone ou tablette.

* Utiliser une base de données No-SQL (par exemple MongoDB) à la place
  de SQL.

* Faire en sorte que 15 minutes avant un évènement, un message
  d'alerte soit affiché sur la page.

* Utiliser AJAX pour ne télécharger de la base de données que les
  évènements de la semaine visualisée.

  Ou, encore mieux : pour rendre l'interface plus fluide, vous pouvez
  télécharger en même temps la semaine courante, la semaine précédente
  et la semaine suivante. Lorsque l'utilisateur navigue dans les
  semaines, vous utilisez la liste d'évènements stockée en cache pour
  afficher la nouvelle semaine immédiatement, et vous lancez une
  nouvelle requête AJAX pour télécharger le contenu du nouveau bloc de
  trois semaines. Gardez à l'esprit que le contenu d'une semaine peut
  avoir changé entre le moment où les données ont été téléchargées, et
  le moment où l'utilisateur demande une navigation.

* Faire en sorte qu'à chaque modification d'événement, tous les
  navigateurs qui affichent le même calendrier soient mis à jour
  automatiquement en utilisant les websockets.
