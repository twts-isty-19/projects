# Projets ISTY 2019

Vous trouverez ci-dessous la liste des projets possibles pour le module. Les projets
sont à réaliser exclusivement **en binômes**.

Chaque projet peut vous permettre d'obtenir la note maximum. Le barème suivra à
peu près le schéma suivant (ceci est complètement indicatif et approximatif,
mais vous donnera une idée):
* projet fonctionnel, sans faille de sécurité, design minimaliste: 9/20
* point précédent avec un travail sur le style et l'erognomie: 11/20
* point précédent avec un ou deux bonus "faciles": 15/20
* point précédent avec un plusieurs bonus réalisés (ou un "très difficile"): 18/20
* qualité du code: modificateur entre -3 et +3.

## Note sur la sécurité
Nous avons vu en cours plusieurs attaques (rudimentaires) possibles et quels
outils utiliser pour les contrer efficacement. Les failles présentées en cours sont parmi les plus évidentes et sont les premières à être testées par les pirates informatiques. Il
est donc inconcevable que le site que vous allez produire soit vulnérable à ces
attaques.

Ainsi un projet vulnérable à ces attaques ne pourra pas atteindre la moyenne.

Vous n'avez pas à faire des choses spécifiques pour "sécuriser votre application",
vous devez *juste* utiliser les outils et pratiques que nous avons vu ensemble,
cela suffit la majorité du temps.

S'il s'avère que votre site expose une faille non traitée dans le cours, nous
le signalerons le jour de la soutenance (si nous la voyons 😊 ) mais ne vous
sanctionnerons pas.

N'oubliez pas: **never trust user input!**

## Note sur le design
Ce cours n'est pas un cours de design. C'est pourquoi un projet au design
minimaliste voir inexistant pourra presque accrocher la moyenne.

En revanche un site juste "beau" mais sans fonctionnalités ou comportant des
failles de sécurité évidentes ne dépassera 5/20.

Cependant, CSS fait partie des technologies à connaître dans l'élaboration d'un
site web, il vous faudra donc en faire usage &ndash; de façon intelligente et en suivant les pratiques modernes bien sûr (*e.g.* Flexbox) &ndash; si vous espérez décrocher une bonne note.

Lorsque vous voudrez vous vendre ou produire une application commerciale, il
faudra bien sûr passer du temps sur le design et l'ergonomie. C'est une activité
chronophage, demandant des compétences et des techniques que nous ne voyons pas
pendant ce cours (ce n'est pas pour rien que "designer" est un métier). Par
conséquent, ne cherchez pas à avoir un "super design", contentez-vous d'un design
"acceptable" et s'il vous reste du temps, passez le à réfléchir à votre code,
à son architecture ; tentez de le simplifier au maximum pour qu'il soit le plus
compréhensible possible !

En bref, les enseignants de ce module sont des programmeurs, ils vous évalueront
et pourront vous faire progresser essentiellement sur votre code et relativement
peu sur l'aspect visuel de votre site.

## Conseils pour réaliser votre projet

Nous vous conseillons pour réaliser votre projet
de suivre approximativement ces étapes (ce qui est valable pour n'importe quel
projet informatique) :
<ol start="0">
<li> Défnissez *ensemble* une fonctionnalité (qui vous paraît) facile que vous voudriez
   ajouter à votre code.
</li><li> Définissez *ensemble* les (types de) données que vous allez utiliser :
    quelle structure de
    tables SQL, quelle structure de donnée en Python, quel type en Elm, ...
</li><li> Réfléchissez *ensemble* aux interactions avec ces données : qui a le droit de faire quoi ?
   tel traitement est-il effectué côté serveur ou côté client ? Quelles données
   vont être transférée ? Les traitements
   qu'on veut effectuer sont-ils immédiats à réaliser avec la structure de
   données choisie ? Si non, ne pas hésiter à revenir au point 1.

   Si cela semble trop complexe, revenir à l'étape 0. et découper la
   fonctionnalité en plusieurs fonctionnalités plus simples.

   **N'hésitez pas à en discuter avec les enseignants, même (et surtout !)
   avant d'avoir commencé à coder.**
</li><li> Coder ce à quoi vous venez de réfléchir en gardant l'affichage
   le plus minimaliste possible (pas de CSS ni d'images à ce stade). Par exemple
   pour un jeu, afficher juste les coordonnées des personnages et des objets
   présents suffit à valider le bon fonctionnement du code.

   Si les étapes 1 et 2
   ont été correctement réalisées, vous devriez pouvoir vous séparer le travail:
   un travaillant sur le côté "serveur", l'autre sur le côté "client".
</li><li> Relire le code de votre binôme ; vous *devez* être capable de le lire et le
   comprendre. Si ce n'est pas le cas: soit votre binôme a écrit du code "sale" ;
   soit vous êtes passé à côté des points important du cours.

   Prenez le temps de *discuter* entre vous du code que vous avez écrit, et
   n'hésitez pas à reboucler les étapes 1., 2. et 3. jusqu'à ce que vous soyez
   tous deux satisfaits.

   *Note:* on peut avoir l'impression d'être "bloqué" pour écrire le côté
   "client" tant qu'on n'a pas les données du côté serveur. En Elm, on peut
   déjà faire beaucoup de choses et s'assurer que tout fonctionne grâce au
   compilateur.
</li>
<li> (Optionnel, vous pouvez développer plusieurs fonctionnalités, PUIS vous occuper du design) Maintenant que tout fonctionne, occupez-vous "d'habiller votre site" en
   utilisant du CSS, des images, du contenu...
</li><li> Ajoutez une nouvelle fonctionnalité en reprenant les étapes précédentes.
</li>
</ol>
Les structures de données que vous utilisez sont réellement la clef de voûte
de votre code. Si vous choisissez les bonnes, votre code sera simplissime à
écrire et à
lire. Dans le cas contraire, vous vous retrouverez rapidement avec du code
pénible à écrire et très difficile à maintenir.

Les étapes 1. et 2. peuvent être assez rapides (15-20 minutes peuvent suffire)
mais sont essentielles si vous voulez être efficaces par la suite. Les
développeurs expérimentés peuvent réaliser cette étape "de tête" sur des petites
fonctionnalités et on peut avoir l'impression qu'ils sautent cette étape ; mais
non, cette gymnastique est juste devenue une seconde nature pour eux et ils font
quand même cette étape.

Vous remarquerez que "coder" n'intervient qu'à l'étape 3. et que je vous invite
à faire des aller-retours dans les étapes. Votre code n'est pas au patrimoine
mondial de l'UNESCO: il doit vivre, évoluer, être refactorisé au fur et à mesure
que votre projet progresse.

# Projets proposés

Sont listés ici les projets proposés cette année. Les technologies à utiliser
sont celles vues en cours : Python/Flask côté serveur, Elm côté client (avec si
besoin un peu de JS via des "ports" pour utiliser une fonctionnalité native non
supportée par Elm) ou simplement HTML/CSS s'il n'y a pas d'interactivité sur la
page.

* [Trello](trello.md) ⭐
* [Calendar](calendar.md) ⭐
* [Bataille navale](bataille.md) ⭐⭐
* [Bomberman](bomeberman.md) ⭐⭐⭐