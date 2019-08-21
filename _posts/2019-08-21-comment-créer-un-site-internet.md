---
layout: post
title: "Comment créer un site internet"
date: 2019-08-21 13:12:50
image: '/assets/img/html.jpg'
description: Site statique ou site dynamique
category: 'developpement web'
tags:
- site statique
- site dynamique
- WebApp
twitter_text:
introduction: Quelles méthodes pour créer un site internet ou mieux une application web.
comments: true
---

Vous vous êtes surement déjà posé la question
> Comment faire pour créer un site web ou une application web?


Plusieurs manières existent mais dans cet article je vais vous présenter comment je procède et les outils que j'utilise, en terme plus technique on appelle ça la *stack*.

Avant de se lancer dans le code tête baissée il faut savoir ce qu'on va créer! Nous faut il un site statique ? un site dynamique ? un mix des deux ? Faut-il des fonctionnalités avancées (login , gestion et interaction d'utilisateurs, ...)

## Site statique vs Site dynamique

On trouve beaucoup de définitions différentes sur internet. La limite entre les deux devient de plus en plus floue avec les avancées techniques ces derniers temps. Ce sont donc plus des interprétations que des définitions gravées dans le marbre.

Je vais donc y aller de mon interprétation sur la question.

Pour moi un site statique est site dan sle lequel il n'y a pas d'intelligence coté serveur. Je m'explique: le serveur stocke uniquement des pages html qui ne changent pas. Lorsque vous cliquez sur [about](https://mathieu.lague.me/about/) dans le menu de ce site la page renvoyée par le serveur est toujours la même. Il renvoit bêtement un fichier texte (que le navigateur comprend et déchiffre).

Un site dynamique à contrario a de l'intelligence coté serveur. Il effectue donc des fonctions qui ont été écrites pas le développeur du site. Il a aussi très souvent une base de données pour stocker toutes les données. Le serveur reçoit donc une demande de page comme pour le site statique mais il n'a pas cette pas ou ce fichier stocké sur son disque dur. Il doit donc créer la page demandée en temps réel. Puis renvoi un fichier html (la page du site) qui a été demandée.

L'avantage d'un site dynamique c'est que l'on peut intéragir avec l'utilisateur. Par exemple on peut afficher les derniers articles lus ou par ordre de création. L'utilisateur pourra effectuer des actions de suppression ou d'édition par exemple. En fait ce sont la majorité des sites ou services qui sont dynamiques à l'heure actuelle.
Tous les sites Wordpress sont des sites dynamiques ; au sens exposé précédemment.
Même les sites vitrines, qui ne sont pas vouer à changer souvent,  sont des sites dynamiques!
> et alors pourquoi ne pas faire que des sites dynamiques si ça marche bien?
>> et bien c'est une excellente question!!

Dans bien des cas il serait plus simple et plus rapide de faire des sites statiques. Par exemple ce site est un site statique!
J'ai une page [home](https://mathieu.lague.me/), une page [about](https://mathieu.lague.me/about/), une page [contact](https://mathieu.lague.me/contact/) et page par article. Et c'est tout!

## Comment faire un site statique

Là encore ce n'est que la solution que j'utilise actuellement. Il y en a beaucoup d'autre.
Pour ce site j'ai utilisé le générateur de site statique [Jekyll].

après avoir installé Jekyll j'ai fait

```zsh
$ jekyll new my-blog
```
dans ma console. Le générateur créer une arboresence de fichier mais aussi des fichier de configuration. Parce qu'en fait on ne fait plus des pages html *en dur* comme avant. (av 2000 !)

Toute la puissance des générateurs comme [Jekyll] ou [Middleman] est que l'on peut construire un site statique comme un site dynamique. On peut utiliser des layouts, des bouts de code qu'on peut rappeler par la suite sans avoir à tout réécrire. C'est un gain de temps et donc d'argent pour le client.

Lorsque tout est fait il faut compiler le site. En fait c'est le serveur qui s'en occupe.
Une fois la compilation faite toutes les pages du sites sont générées et stockées en fichier html sur le serveur. A partir de là le serveur ne fera plus qu'envoyer les pages demandées.

Un autre point très intéressant c'est qu'on trouve des hébergements gratuits pour des pages statiques. Ce


[Jekyll]: 'https://jekyllrb.com/'
[Middleman]: 'https://middlemanapp.com'

