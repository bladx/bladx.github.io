---
title: Ma Ludothèque
author: xavier
date: 2022-11-01 23:23:00 +0200
categories: [Projet personnel, Programmation]
tags: [réalisation]
---

## Présentation

Aujourd'hui je vais vous parler de ma toute dernière [#réalisation](/tags/réalisation/) : Ma Ludothèque, ou plutôt mon site personnel qui recense tous nos jeux de sociétés.
Celui-ci est d'ailleurs accessible ici, si vous souhaitez voir le résultat : [misteur.fr](https://misteur.fr).

Cela fait un moment que je souhaitais refaire mon site personnel de jeux de société.
Je l'avais fait à l'époque en utilisant PHP et JQuery, plus ou moins imposés par les limitations des serveurs managés chez mon précédent hébergeur Ionos (anciennement 1&1).
Et bien évidemment je désirais m'en débarrasser pour aller vers des technologies plus modernes.
De plus l'édition, comme l'ajout de nouveaux jeux, avait lieu directement depuis la base de données.
Et les déploiements se faisaient à la main, grâce à un drag&drop dans Filezilla.
Bref, c'était à l'époque mon tout premier vrai [projet personnel](/categories/projet-personnel/) et il y avait énormément de choses améliorables.

Aussi, j'ai pris la décision de réaliser ce projet comme s'il s'agissait d'un réel projet professionnel.

## Architecture

Mon projet se découpe en 4 parties :

- La **base de données** qui stocke l'ensemble des informations
- Le **serveur** qui communique avec la base de données et est appelable via une API
- Le **Back Office** qui n'est autre que le dashboard d'édition (privé/protégé)
- Le **Front Office** qui est le site web public que vous voyez en allant sur mon site

![Architecture](/assets/img/posts/ma-ludothèque/architecture.jpg)
_Architecture_

## Technologies

Fini PHP et JQuery ; voici, sans rentrer trop dans le détail, les technologies sur lesquelles je suis parti.

### Hébergement

Etant bien trop limité par un serveur managé, j'ai décidé de partir de chez Ionos afin d'aller chez un hébergeur concurrent qui offre des serveurs dédiés pas chers.
J'ai choisi [Scaleway](https://www.scaleway.com/fr/) qui est à la fois simple d'utilisation, peu cher, propose des services comme des _buckets S3_ et surtout sans problème de disponibilité (contrairement à kimsufi où la mise à disposition de nouveaux serveurs est rare).

Certes, cela implique de tout devoir configurer soi-même.
Aussi bien la configuration de la machine, que le setup initial, la partie sécurité et l'installation des divers services.
Mais d'un autre côté, cela offre une liberté totale sur ce qu'on peut faire tourner dessus !

De plus, la facture est détaillée à la fois par service et au sein même d'un service.
Cela offre une transparence totale sur comment est calculé le coût total chaque mois. 

### DevOps

Pour toute la partie devOps, étant donné que ce n'est pas mon métier, je me suis basé sur les tutoriels très bien construits de Digital Ocean.
Ainsi j'ai suivi ces différentes étapes pour être bien sûr de ce que je faisais :

1. [Initial Server Setup with Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04)
2. [How to Set Up SSH Keys on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-22-04)
3. [How To Install and Use Docker on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04) (steps 1 & 2)
4. [How To Install and Use Docker Compose on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-22-04)
5. [How To Install Nginx on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04)
6. [How To Secure Nginx with Let's Encrypt on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04)

#### Docker

[Docker](https://www.docker.com/) est la **plateforme de conteneurs** la plus populaire et la plus utilisée.
Un conteneur étant le regroupement d’un logiciel/service avec toutes ses dépendances (librairies, code source, fichiers de configuration, etc.) empaquetées au même endroit.

Voici les principaux avantages de Docker :

- **Flexible** : n'importe quelle application peut être transformée en conteneur
- **Portable** : la création, le déploiement ainsi que le démarrage d'un conteneur ne dépendent pas de la machine ou de l'OS
- **Indépendant** : chaque conteneur est indépendant, ce qui permet d'en modifier un sans devoir se préoccuper des autres
- **Légère** : les conteneurs sont semblables aux machines virtuelles sauf qu'ils se partagent le même noyau du système d'exploitation
- **Sécurisé** : Docker offre une sécurité de base en termes d'isolement de processus

#### NGINX

[NGINX](https://www.nginx.com/) est un reverse proxy qui permet d'améliorer les performances d'hébergement.
Autrement dit, il permet d'**optimiser les redirections d'une URL vers l'un de vos conteneurs Docker**.
C'est le concurrent direct d'Apache, si ce n'est qu'il est plus performant dans le cas de grosses charges.
De plus, il a besoin de bien moins d'espace de stockage par connexion client.

Mon choix s'est donc porté vers ce service, nouveau pour moi, très facile à prendre en main.

### Serveur

Pour la partie back-end, j'ai utilisé NestJS qui est à ce jour la technologie avec laquelle j'ai préféré travailler.
J'ai également choisi MySQL pour la gestion et le stockage des données.
Avec TypeORM pour faire la jonction entre ces deux éléments.

#### NestJS

[NestJS](https://nestjs.com/) est un framework, basé sur ExpressJS (NodeJS), que je résume souvent personnellement par la phrase :

> NestJS est au JavaScript ce que Spring est au Java.

C'est à dire qu'il permet de créer un **serveur web** facilement et de manière propre grâce, entre autres choses, aux annotations ou à son architecture inspirée d'Angular.
Il est, bien entendu, compatible avec TypeScript et offre tous les avantages de NodeJS, comporte un bon nombre de modules natifs et permet d'inclure aisément n'importe laquelle des innombrables modules NPM.

Il existe un superbe tutoriel : [NestJS Zero to Hero - Modern TypeScript Back-end Development](https://www.udemy.com/course/nestjs-zero-to-hero/) sur Udemy qui permet d'apprendre comment créer un projet en utilisant ce framework.

> A noter que ce cours est régulièrement gratuit.<br>
    L'auteur l'annonce en général sur le subreddit [/r/node](https://www.reddit.com/r/node/).
{: .prompt-tip }

### TypeORM

[TypeORM](https://typeorm.io/) est sûrement le **mapping objet-relationnel** (ORM) le plus mature dans l'écosystème de NodeJS.
De plus, le fait qu'il soit écrit directement en TypeScript fait qu'il est préconisé dans la documentation NestJS.
En effet, ils offrent un module natif dédié `@nestjs/typeorm` ainsi que sa [page](https://docs.nestjs.com/recipes/sql-typeorm#sql-typeorm) associée.

Moa décision a donc été relativement évidente quant au choix de l'ORM.
Surtout que le tutoriel avec lequel je me suis formé explique également comment implémenter toute cette partie.

#### MySQL

Plus besoin de présenter [MySQL](https://www.mysql.com/), qui n'est autre que le système de gestion de **bases de données relationnelles** le plus connu et répandu.
C'est la seule technologie que j'ai conservée avec la version initiale.
Mon projet nécessite une base de données relationnelles et j'ai plus l'habitude de MySQL que PostgreSQL ou encore MariaDB qui sont très proches.

### Back Office

Mon Back Office, ou encore dashboard d'édition, repose principalement sur une seule technologie qui est le framework React Admin.
Celui-ci permet de générer un site statique qui peut ensuite être stocké sur un _bucket S3_.

#### React Admin

[React Admin](https://marmelab.com/react-admin/) est un framework open source qui permet d'avoir rapidement une **interface d'édition pour gérer les données** de votre site.
En d'autres termes, il s'agit d'un CMS qui utilise React et qui est déjà pré-construit et facilement personalisable, à la condition d'avoir une API standard en amont.
Leur [site](https://marmelab.com/react-admin/Readme.html) dispose d'une vidéo de présentation, ainsi qu'un site de démonstration.

Pour un projet qui n'a pas besoin de trop de personnalisation, comme des formulaires spécifiques, cette technologie permet de faire gagner un temps précieux.
Qui plus est, l'interface utilisateur (UI), c'est-à-dire le design, est basique mais amplement suffisante.

Pour mon projet, je n'ai eu besoin de faire qu'un seul composant custom.
Un champ d'ajout, remplacement et suppression d'image qui gère l'upload sur un bucket S3 afin d'envoyer uniquement l'URL finale au serveur qui la stockera alors en base de données.
Cela permet de ne pas envoyer le fichier directement avec les autres champs du formulaire, garder une API REST simple et profiter des avantages d'un bucket S3 que nous allons aborder dans la prochaine section.

> J'ai effectué 2 contributions à ce projet, en faisant des pull requests (PR) qui ont depuis été merged.
{: .prompt-info }

#### Bucket S3

Ce service, créé initialement par Amazon, est un service de **stockage de fichiers**.
Cela veut dire que vous pouvez stocker toutes formes d'objet (fichier) comme vous le feriez sur un Google Drive par exemple.

Ce service présente les avantages suivants :

- **Economique** : vous ne paierez qu'un petit prix qui dépend de la taille des fichiers stockés ainsi que de leur fréquence d'utilisation
- **Facile d'utilisation** : une interface web simple et clair à la façon d'un File Explorer permet de gérer son bucket, ou encore à l'aide d'une interface en ligne de commande (CLI)
- **Disponible en permanence** : fiable, rapide et dupliqués sur divers serveurs ; le risque de panne est inférieur à 0.01%
- **Sécurisé** : vous définissez les règles d'accès aux fichiers de chaque bucket, ainsi que la visibilité publique ou privée
- **Simple à migrer** : très simple à migrer, soit en ligne de commande soit en import/export, et de nombreux services compatibles chez tous les services d'hébergement

> Le service que j'utilise n'est d'ailleurs pas [Amazon S3 bucket](https://aws.amazon.com/fr/s3/), mais l'[object storage](https://www.scaleway.com/en/object-storage/) de Scaleway qui est similaire et **compatible avec le SDK** d'AWS.
{: .prompt-warning }

Pour mon projet, je dispose de 2 buckets :

1. Le stockage des images (pour chacun de mes jeux)
2. Le stockage de mon Back Office, sous la forme de site web statique

### Front Office

La partie pulbique du site, appelée Front Office, s'appuie principalement sur la librairie React.
Une surcouche Next.js permet d'optimiser la rapidité avec notamment un rendu côté serveur.
Tailwind, quant à lui, facilite grandement la gestion du style.
Et enfin, Storybook offre la possibilité de travailler nos composants graphiques en les isolant.

Voyons tout cela plus en détail.

#### React

[React](https://reactjs.org/) est une librairie JS, créée par Facebook en 2013, qui permet de faciliter la **création d'application web monopage** (SPA).
Son principe est simple : décomposer nos pages en un ensemble de composants indépendants les uns des autres.
Chacun ayant ses propres propriétés et son état qui peut évoluer en fonction des interactions de l'utilisateur.

C'est l'une des librairies front-end les plus connues/utilisées, avec Angular et Vue.js.
Mais React est loin en tête avec des acteurs majeurs comme Netflix, Yahoo, Atlassian ou bien sûr Facebook.
Il se démarque des autres par sa grande flexibilité ainsi que ses performances.

#### Next.js

[Ce framework](https://nextjs.org/) se base sur la technique de **rendu des pages web côté serveur** ainsi que la **génération de pages statiques**.
Cela permet donc d'optimiser une application web monopage grâce à la génération hybride de pages web et incrémentale des pages.

Ainsi lors de la phase de _build_ de votre projet, Next.js va construire les différentes pages de votre site de manière statique.
C'est à dire que derrière la page `/article/foo`, il aura au préalable cherché les données depuis une API afin de construire la page HTML finale correspondante.
Mais si vous ajoutez, après le _build_, un article `bar` en base ; alors Next.js va construire dynamiquement cette page et la stocker pour les prochains utilisateurs.
C'est ce procédé qui permet d'accélérer au maximum le rendu du site .

#### Tailwind

Aussi appelé, [Tailwind CSS](https://tailwindcss.com/), ce framework permet justement de **se débarrasser de la partie style (CSS) d'un site web**.
En effet, il utilise des noms de classe qui correspondent à une propriété CSS.
Et en additionnant ces classes vous pouvez définir le CSS d'une balise HTML.

Ainsi, contrairement à Bootstrap, vous n'aurez pas de classes toutes faites ; mais bien un ensemble de classes à utiliser comme bon vous semble pour obtenir le style de votre choix.
Par exemple si vous souhaitez faire un bouton, vous utiliserez alors `py-1 px-2 bg-blue-500 text-white hover:bg-blue-800` qui se décompose comme suit :

- `py-1`: `padding-top: 0.25rem; padding-bottom: 0.25rem;`
- `px-2`: `padding-left: 0.5rem; padding-right: 0.5rem;`
- `bg-blue-500`: `background-color: rgb(59 130 246);`
- `text-white`: `color: rgb(255 255 255);`
- `hover:bg-blue-800`: `background-color: rgb(30 64 175);`

Vous aurez remarquez que vous pouvez utiliser toutes les pseudo-classes, comme`hover:` dans cet exemple qui permet de définir le style quand le composant est survolé.
Il est également possible d'utiliesr le préfixe `dark:` pour le dark mode ou encore les traditionnels `xs:`, `sm:`, etc. pour le côté responsive design.
Vous pouvez aussi créer vous-mêmes des classes que vous aurez définies au préalable.

> A noter que Tailwind se charge d'optimiser la taille finale en ne générant que les classes que vous avez utilisées dans votre projet.
{: .prompt-info }

#### Storybook

[Cette librairie](https://storybook.js.org/) est très utile dans le **développement de l'interface utilisateur (UI)**.
En effet, cet outil permet d'isoler tel ou tel composant, facilitant alors la modification graphique sans avoir à se préoccuper du reste.

Fini la perte de temps où vous devez lancer tout votre projet pour voir le rendu d'un composant graphique.
Grâce à Storybook, vous trouverez au même endroit, tous les composants que vous avez définis, organisés selon une hiérarchie simple et claire.
Et il sera facile de modifier les propriétés/état d'un composant pour voir ses différents rendus.

Couplé avec des données mockées, vous pourrez alors concevoir votre site web avant même de posséder l'API qui vous fournira les données.