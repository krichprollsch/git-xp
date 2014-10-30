# retour d'experience : git en entreprise

## Pierre Tachoire

Développeur web chez ITNetwork
@krichprollsch

## Le contexte

![ITNetwork](http://www.itnetwork.fr/_itn/img/itnetwork.png)

* ITNetwork, agence web / service info

~15 salariés, 7 dévs, 3 intégrateurs, 1 admin sys

6 devs sous windows

## Une vie avant git ?

mode web agency 

combo ftp + edition en prod

> on est réactifs

c'est sûr, mais avec des soucis...

1 projet par personne, chacun code dans son coin, chacun avec ses techniques,
son style.

* pas d'annulation automatique
* deploiement manuel (quels sont les fichiers à mettre à jour ?)
* accès aux espaces web/bdd dispersés 
* pas de partage de code interne

C'est loin d'être top, mais ça passe encore.

## On signe un plus gros projet ?

> On va développer en équipe, ça ira plus vite

Création d'un espace de dev "commun" sur un serveur

> je fais le module de gestion des users
> tu t'occupes des documents

> pourquoi tu as touché à ce fichier ?

> qui à écrasé mes 2 semaines de travail ?

## On a trouvé une solution ultime

[capture word edition des fichiers]

## Arthur, c'est la gueurre !

> les devs cassent tout et se barrent en we

> je dois pouvoir mettre en prod mes modifs

> un dev ne doit pas toucher au serveur

## On doit automatiser les déploiements

* impulsion de l'admin sys
* création d'un projet pilote
* utilisation d'environnements de dev, de test, de recette, de prod
* injection de conf : le dev ne doit plus JAMAIS avoir accès aux infos de prod

> il est où mon phpmyadmin ?

Git est la pierre angulaire du process

## Projet pilote

* 1 seul développeur pilote
* mise en place de deploiements avec admin sys
* reflexion/documentation

Objectifs :

* préparer les choses en amont pour éviter les blocages des
projets
* pouvoir faire le support en interne en ayant de l'avance sur l'apprentissage
sans pour autant maitriser tout git.

## Formation et généralisation

> c'est rigolo ta ligne de commande...
> mais j'installe quoi comme logiciel sérieusement ?

Une formation est absolument nécessaire.
On donne des logiciels graphiques, mais on fait passer l'idée que la ligne
de commande est plus utile.

Ne pas mettre la pression sur les développeurs

On ne commence que sur les nouveaux projets et on généralise sur les anciens
petit à petit.

# Les premiers pas avec git

```
git commit -am 'woot \o/'
```

les premiers pas, on est fous-fous.
Travail individuel tout est ok.

![first step](https://farm1.staticflickr.com/25/59418536_9052eee2a3_z_d.jpg)

On ne se préoccupe ni de workflow ni de l'historique.

## Deploiements

Ce sont les développeurs qui déploient.
Ils ne sont pas dépendants de l'admin sys.

* pas de deploiement si les testent echouent
* système basique de migration de bdd

On garde la réactivité.

## Les branches

Changer de scope pour expliquer la puissance des branches et l'utilité de
switcher.

* on ne mélange plus son travail
* une tâche par branche
* on peut faire des essais et se tromper
* on fait des petits commits

Toujours donner des bonnes pratiques

## Les premiers blocages

Git est verbeux, la solution est dans le message, il faut juste le lire...

Les premiers conflits à gérer sont difficiles.
Un accompagnement est nécessaire pour rassurer et ne pas se tromper.

Aider les utilisateurs à configurer git, en particulier un mergetool graphique
pour débuter.

## perte de fichier

> git a supprimé mon fichier !

Analyser avec le développeur l'historique afin de trouver l'explication.
Comprendre et expliquer ce qui s'est passé et la logique.

*Faire confiance à git*

# On apprend

## on commence un workflow

On s'appuie sur [nvie]()

* une branche `master` de référence : le développement le plus avancé
* une branche par fonctionnalité qui est mergée dans `master`
* une branche de `qa` pour deploiement et test
* une branche de `production`
* une branche `hotfix` dérivant de production

## workflow

Fusion dans master en creant un commit de merge

```
git merge --no-ff dev-1234
```

Permettre de mieux suivre l'historique des branches dans `master`.

## workflow

Récupération des hotfixes dans master via `cherry-pick`

## Et les dépendances ?

`git submodule`

Utilisé dans quelques projets pilotes pour des dépendances privées.
Abandonné depuis.

* utilisation n'est pas toujours bien compris
* le changement de dépôt est compliqué

[Composer](http://getcomposer.org) règle le problème dans les projets php en
offrant plus de souplesse et de simplicité pour le développeur.

## Finalement la ligne de commande c'est pas mal

> à ouais c'est vachement mieux dans ton linux

Donner envie d'utiliser git à travers de linux :
prompt git, couleurs, diff, historique

# Tirer parti de git

## Comprendre le code

Git permet de faciliter la compréhension du code en aidant à répondre
aux questions :

* pourquoi est-ce codé ainsi ?
* quand est-ce que ça à été fiat/modifié
* qui à travailler dessus ?

```
git log
```
Permettre la communication entre développeurs, faciliter la 
recherche d'informations, mieux prévoir les impacts d'une 
modifications.

## trouver et corriger un bug

`git bisect` est un outil ultime pour trouver l'origine d'un bug rapidemment.

## On fait encore des erreurs

> j'annule juste une modifs

```
git push -f
```

Expliquer dans quel cas c'est possible et dans quels cas ce ne l'est pas.
Pas toujours bien compris et trop souvent trouvé sur le net.

> si git me le permet, c'est que c'est safe

Un grand pouvoir nécessite de grandes responsabilités.

## le serveur pirate

Tirer parti de la souplesse de git pour faire des essais, valider des outils.

Installation d'un serveur [Gitlab]() en plus du serveur [gitosis]() "offciel".

* donner plus de souplesse dans la création de dépots
* les devs gèrent eux-même leur clefs ssh
* changer de workflow

## release manager et revue de code

[Gitlab]() facilite l'introduction du workflow basé sur des merges request

* mise en place d'un release manager
* faire des revues de code

Meilleur suivi du code source des gros projets

Les développeurs peuvent travailler sur plus de projets plus facilement.
Meilleur partage des connaissances

Mise en place de bonnes pratiques et de règles de codage.

## Historique

`git rebase` permet de conserver un historiaue lisible en travaillant avec
de multiples branches.

Mise en place de bonnes pratiques de message de commit, avec référence aux
tickets [Redmine]().

## Intégration continue

Tout comme gitlab, git permet de mettre en place un serveur d'intégration
continu facilement.

L'outil peut être testé sans admin sys pour validation avant généralisation
dans la société :

se tromper/corriger/généraliser

## Ouvrir notre code à des développeurs extérieurs ?

Git et Gitlab permettent de faciliter la collaboration avec des membres exterieurs de la société.

# conclusion 

* libére le développeur
* permet des expérimentations
* permet tout les workflow
* outil central des projets
* permet de faciliter le travail à plusieurs
* permet de s'entraider

* seuls 2 développeurs sont encore sous windows

# Credit photos

[First steps of Maya at 11 months / David Perry](https://www.flickr.com/photos/crazykinux/59418536)
