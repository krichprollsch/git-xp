# retour d'experience : git en entreprise

## Le contexte

* ITNetwork, agence web / service info

~15 salariés, 7 dévs, 3 intégrateurs, 1 admin sys

6 devs sous windows...

## Une vie avant git ?

malheureusement oui...
mode web agency old school

combo ftp + edition en prod

Live coding sans bretelles

:|

> on est réactifs

c'est sûr, mais avec des soucis...

1 projet par personne, chacun code dans son coin, chacun avec ses techniques, son style.

* pas d'annulation automatique
* pas de recetage client
* deploiement manuel
* accès aux espaces web/bdd dispersés 

C'est loin d'être top, mais ça passe encore.

## On signe une plus gros projet ?

> On va développer en équipe, ça ira plus vite

Création d'un espace de dev "commun"

Le ftp c'est cool, on garde.

> je fais le module de gestion des users
> tu t'occupes des documents

> pourquoi tu as touché à ce fichier ?

> qui à écrasé mes 2 semaines de travail ?

## On a trouvé une solution ultime

[capture excel edition des fichiers]

hum :|

Et un système de versionning, ca pourrait pas aider ? 

> c'est quoi ?

## Arthur, c'est la gueurre !

> les devs cassent tout et se barrent en we

> je dois pouvoir mettre en prod mes modifs

> un dev ne doit pas toucher au serveur

# Bon va falloir changer les choses

## On doit automatiser les déploiements

* impulsion de ladmin sys
* création d'un projet pilote
* utilisation d'environnements de dev, de test, de recette, de prod
* injection de conf : le dev ne doit plus JAMAIS avoir accès aux infos de prod

> il est où mon phpmyadmin ?

Git est la pierre angulaire du process

## c'est rigolo ta ligne de commande...

Mais j'installe quoi comme logiciel sérieusement ?

FORMATION

## woot je peux commiter des modifs

les priemiers par, on est fous-fous.
Travail individuel tout est ok.

## travail à plusieurs sur master

C'est quoi un conflit ?

## des branches ?

L'historique est pas hyper clair.
Je ne comprends pas ce qui se passe...

Tu peux m'aider ?

## Finallement la ligne de commande c'est pas mal

déjà ça fait "barbu"

> à ouais c'est vachement mieux dans ton linux

## on commence un workflow



## le serveur pirate

## release manager et revue de code

vous avez dit `rebase` ?

## vous avez dit intégration continue ?

Ah faut faire des tests ?

## Ouvrir notre code à des développeurs extérieurs ?

> Mais il vons tout casser !

# conclusion 

* libére le développeur
* permet des expérimentations
* permet tout les workflow
* outil central des projets
* permet de faciliter le travail à plusieurs
* permet de s'entraider
