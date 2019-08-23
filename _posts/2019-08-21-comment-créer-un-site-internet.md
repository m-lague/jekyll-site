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

Ce n'est que la solution que j'utilise actuellement. Il y en a beaucoup d'autre.
Pour ce site
>j'utilise le générateur de site statique [Jekyll].

après avoir installé [Jekyll] j'ai fait

```zsh
$ jekyll new my-blog
```
dans ma console. Le générateur créer une arboresence de fichier mais aussi des fichier de configuration. Parce qu'en fait on ne fait plus des pages html *en dur* comme avant. (av 2000 !)

Toute la puissance des générateurs comme [Jekyll] ou [Middleman] est que l'on peut construire un site statique comme un site dynamique. On peut utiliser des layouts, des bouts de code qu'on peut rappeler par la suite sans avoir à tout réécrire. C'est un gain de temps et donc d'argent pour le client. On doit pour celà connaitre un langage de template pour [Jekyll] c'est le [Liquid]. C'est un langage compilé qui permet d'utiliser des variables, des fonctions, etc... Par exemple pour récupérer le titre de la page actuelle pas besoin d'écrire du html comme ceci

```html
<title>Le titre de la page</title>
```

en Liquid ça donnera ça

```liquid
{{ page.title }}
```

Imaginez que vous ayez 50 pages dans votre site, en html il faudrait réécrire 50 fois `<title>le titre de la page</title>`. En liquid on l'écrit 1 fois et on met ce code dans un layout que toutes les pages appeleront. Sympa non?
>J'utilise aussi d'autres langage de template comme [Erb], [Slim], [Haml]

Lorsque tout est fait il faut compiler le site. En fait c'est le serveur qui s'en occupe.
Une fois la compilation faite toutes les pages du sites sont générées et stockées en fichier html sur le serveur. A partir de là le serveur ne fera plus qu'envoyer les pages demandées.

Un autre point très intéressant c'est qu'on trouve des hébergements gratuits pour des pages statiques.
>Ce site est hébergé sur [GitHub Pages].

Conclusion un gain de temps à la conception et un gain sur le coût de l'hébergement.

Par contre un inconvénient survient quand il faut ajouter un article par exemple. Il faut créer un fichier html ou un fichier texte écrit en [Markdown]. Il n'est pas prévu d'éditeur de type wysiwyg. Pour un non initié c'est un gros frein à la création d'un tel site et c'est aussi pourquoi la majorité des blogs ou sites d'entreprises sont créés avec Wordpress et donc sont des sites dynamiques.

## Comment créer un site dynamique

Je préfère parler d'application web qui sont de véritable programme avec de l'intelligence du coté du serveur. Par exemple pour un blog du type Wordpress on écrit un article dans un éditeur wysiwyg on publie.

Le serveur reçoit l'article l'envoi à la base de donnée qui l'enregistre. Puis pour afficher l'article vous allez sur la page de l'article, le serveur reçoit la demande de la page, va demander à la base de donnée de lui fournir cet article, la base de données va rechercher puis renvoyer l'article au serveur qui va compiler la page en html puis vous la renvoyer.

L'intérêt est de pouvoir afficher des chosees différentes suivant l'utilisateur ou les droits d'accès. Sur AirBnB dans la liste de vos appartements vous ne pouvez voir que vos appartements, ça semble logique.

On voit avec ce principe que ça prendra forcément plus de temps pour afficher une page qu'avec un site statique. Mai son pourra faire beaucoup plus de choses.

L'inconvénient c'est qu'il y a des coûts serveur et de développement car il faut gérer ce qu'on appelle le *back-end*. C'est toute la logique qui sera hébergé sur le serveur.

>Je réalise les **applications web** à l'aide de [Ruby on Rails] ou [Sinatra]

[Ruby on Rails] est framework pour le développement web. On peut quasiment tout faire avec pour seule limite notre imagination. Je réalise des **applications web** avec [Ruby On Rails] pour des startup qui ont besoin d'un prototype fonctionnel rapidement. Ce peut être des places de marchés comme [AirBnB], des applications pour héberger des documents comme [GitHub] ou [Dropbox], de sites comme [Groupon], des sites de news comme [Bloomberg], des applications de gestion de projet comme [Basecamp], des réseaux sociaux comme [Twitter] etc... la liste est très longue...

Pour utiliser [Ruby on Rails] ou [Sinatra] il faut connaitre le langage Ruby. de plus on peut utiliser des languages de template pour le coté front-end ( [Erb], [Slim], [Haml]) avec les mêmes avantages que dans les générateurs de sites statiques.

## Comment rendre dynamique un site statique

*en cours de rédaction*




[Jekyll]: 'https://jekyllrb.com/'
[Middleman]: 'https://middlemanapp.com'
[GitHub pages]: 'https://pages.github.com'
[Liquid]: 'https://shopify.github.io/liquid/'
[Markdown]: 'https://fr.wikipedia.org/wiki/Markdown'
[Ruby on Rails]: 'https://rubyonrails.org'
[Erb]: 'https://ruby-doc.org/stdlib-2.6.3/libdoc/erb/rdoc/'
[Slim]: 'http://slim-lang.com'
[Haml]: 'http://haml.info'
[Sinatra]: 'http://sinatrarb.com/'
[AirBnB]: 'https://www.airbnb.fr'
[Dropbox]: 'https://www.dropbox.com'
[Groupon]: 'https://www.groupon.fr/'
[Bloomberg]: 'https://www.bloomberg.com/europe'
[Basecamp]: 'https://basecamp.com/'
[Twitter]: 'https://twitter.com/MathieuLAGUE'
[GitHub]: 'https://github.com/m-lague/'




