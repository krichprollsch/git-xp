<!-- 
Titre : Introducing APIHours
Date : 03/07/2013
Événement : APIHour #X
Auteur : Julien Maupetit
-->

#### Retour d'experience : git en entreprise
# De rien à git

----

## Pierre Tachoire

Développeur web chez ITNetwork

[@krichprollsch](https://twitter.com/krichprollsch)

----

# Contexte

---
![ITNetwork](http://www.itnetwork.fr/_itn/img/itnetwork.png)

* Fondée en 1996
* Agence web => SSII

---
![ITNetwork](http://www.itnetwork.fr/_itn/img/itnetwork.png)

* ~15 salariés
* 7 développeurs
* 3 intégrateurs
* 1 admin système

> Dont 6 développeurs sous windows.

----

# Une vie avant git ?

---
* mode : `web agency`
* combo `ftp` + edition en prod

> on est réactifs

---

* 1 projet par personne
* chacun code dans son coin
* chacun avec ses techniques, son style

---

* pas d'annulation automatique
* deploiement manuel
* accès aux espaces web/bdd dispersés 
* pas de partage de code interne

---

## ça passe encore.

Note: quels sont les fichiers à mettre à jour ? ITNetwork à tenu plus de 10 ans ainsi

---

## On signe un plus gros projet ?

---

> On va développer en équipe, ça ira plus vite

---

* Création d'un espace de dev "commun" sur un serveur
* Comment on règle les conflits ?

---

```
- je fais le module de gestion des users tu t'occupes des documents
- pourquoi tu as touché à ce fichier ?
- qui à écrasé mes 2 semaines de travail ?
```

---

## On a trouvé une solution ultime

---

[capture word edition des fichiers]

---



![](http://33.media.tumblr.com/tumblr_m8f7q8kgNr1qhxacso1_500.gif)

> les devs cassent tout et se barrent en we

> je dois pouvoir mettre en prod mes modifs

> un dev ne doit pas toucher au serveur

----

# Git ?

---

## Automatiser les déploiements
---

* impulsion de l'admin sys
* création d'un projet pilote
* environnements de dev, de test, de recette, de prod
* injection de conf 

---
 
### ne plus *JAMAIS* avoir accès à la prod

---


### `Git` : la pierre angulaire du process

----

## Projet pilote

---

* 1 seul développeur pilote
* mise en place de deploiements avec admin sys
* reflexion/documentation

---

### Objectifs :

* préparer les choses en amont pour éviter les blocages des
projets
* pouvoir faire le support en interne en ayant de l'avance sur l'apprentissage
* sans pour autant maitriser tout git.

----

## Formation et généralisation

---

> c'est rigolo ta ligne de commande...

> mais j'installe quoi comme logiciel sérieusement ?

---

* une formation est nécessaire
* on donne des logiciels graphiques
* montrer que la ligne de commande est plus utile

---

### Ne pas mettre la pression sur les développeurs

* commencer que sur les nouveaux projets
* généralisation sur les anciens petit à petit

----

## Les premiers pas avec git

---

```
git commit -am 'woot \o/'
```

* les premiers pas, on est fous-fous.
* Travail individuel tout est ok.

---

### On ne se préoccupe ni de workflow ni de l'historique.

----

## Deploiements
---

### On garde la réactivité.

* Ce sont les développeurs qui déploient.
* Ils sont pas dépendants de l'admin sys.

---

### Introduction de qualité 

* pas de deploiement si les testent echouent
* système de migration de bdd

----

## Les branches

---

Expliquer la puissance des branches et l'utilité de switcher.

---

* on ne mélange plus son travail
* une tâche par branche
* on peut faire des essais et se tromper
* on fait des petits commits
---

### Toujours donner des bonnes pratiques

----

## Les premiers blocages

---


* Premiers conflits difficiles à gérer
* Accompagnement nécessaire pour rassurer et ne pas se tromper 
* Aider à configurer un mergetool graphique

---

Git est verbeux, la solution est très souvent dans le message, il faut juste faire l'effort de le lire...

---

### git a supprimé mon fichier !

---

* Analyser avec le développeur l'historique
* Comprendre et expliquer ce qui s'est passé et la logique.

---

### Apprendre à faire confiance à git

----

## Premier workflow
---

On s'appuie sur [nvie]()

---

* une branche `master` de référence : le développement le plus avancé
* une branche par fonctionnalité qui est mergée dans `master`
* une branche de `qa` pour deploiement et test
* une branche de `production`
* une branche `hotfix` dérivant de production

---


`git merge --no-ff`

* Fusion dans master en creant un commit de merge
* Permettre de mieux suivre l'historique des branches dans `master`.

---

Récupération des hotfixes dans master via `cherry-pick`

----

## Et les dépendances ?

---

`git submodule`

Utilisé dans quelques projets pilotes pour des dépendances privées.

Abandonné depuis.

---

* utilisation n'est pas toujours bien compris
* le changement de dépôt est compliqué

---

![getcomposer](https://getcomposer.org/img/logo-composer-transparent.png)

[Composer](http://getcomposer.org) règle le problème dans les projets php en
offrant plus de souplesse et de simplicité pour le développeur.

----

> Finalement la ligne de commande c'est pas mal

---

Donner envie d'utiliser git à travers de linux :

* prompt git
* couleurs
* diff
* log

----

# Tirer parti de git

---

## Comprendre le code

---

`git log`

* pourquoi est-ce codé ainsi ?
* quand est-ce que ça à été fait/modifié
* qui à travailler dessus ?

---

* Permettre la communication entre développeurs
* faciliter la recherche d'informations
* mieux prévoir les impacts d'une modifications

---

`git bisect` 

* outil ultime pour trouver l'origine d'un bug rapidemment.

----

## On fait encore des erreurs

---

`git push -f`

> j'annule juste une modifs

* Expliquer les cas possibles
* Pas toujours bien compris et trop souvent trouvé sur le net.

----

## le serveur pirate

---

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
