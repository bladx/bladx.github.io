---
title: Puzzle games quotidiens
author: xavier
date: 2022-10-18 13:34:00 +0200
categories: [Vie quotidienne, Routine]
tags: [réflexion]
---

## Introduction

Tous les matins, j'aime commencer ma journée avec une petite routine en mode [#réflexion](/tags/réflexion/).
Celle-ci consiste à résoudre de petits puzzle games rapides, générés chaque jour.

Voici l'ordre dans lequel je les fais :

## 1 - Nerdle

[Nerdle](https://nerdlegame.com/) est un jeu du style _Mastermind_ mais qui utilise l'arithmétique.

### Règles

C'est-à-dire que vous avez maximum 6 essais pour trouver la bonne opération sur 8 cases.
Où chaque case peut être soit un chiffre (0-9), soit un symbole mathématique à savoir : `+`, `-`, `*`, `/` ou `=`.
Il n'y a obligatoirement qu'un seul symbole `=`.
Et il ne peut y avoir que des chiffres à droite de l'égalité.
Bien entendu, l'ordre des opérations est respecté.
Ainsi un `+` ou un `/` prend l'ascendant sur un `+` ou un `-`.
Et enfin la commutativité, à savoir le fait d'inverser 2 côtés de l'opération, est acceptée.
Ce qui veut dire que `12*23` est équivalent à `23*12`.

Au départ, vous n'avez aucun indice.
Il faut alors tenter une combinaison afin d'avoir des informations sur l'opération recherchée.
A chaque tentative, vous obtenez l'une des 3 couleurs différentes :

- Case **verte** : Le chiffre/symbole est correctement placé
- Case **rouge** : Le chiffre/symbole est mal placé mais il est présent dans l'opération
- Case **noire** : Le chiffre/symbole ne figure à aucun endroit du résultat final

### Exemple

![Nerdle](/assets/img/posts/puzzle-games-quotidiens/nerdle-1.jpg){: width="450" height="450" }
_Nerdle (partie en cours)_

Dans cet exemple, avec la deuxième ligne nous obtenons les informations suivantes :

- L'opération possède au moins un `9` et un `7` mais pas en première et deuxième position (respectueusement)
- La troisième case est forcément un `-`
- Le résultat final ne possède ni `8` ni `5`
- La fin de l'opération n'est autre que `=12`

La partie se termine lorsque toutes les cases sont vertes en cas de victoire.
Cela signifie que tous les chiffres/symboles sont bel et bien positionnés.
Ou bien après la sixième tentative en cas de défaite.

![Nerdle](/assets/img/posts/puzzle-games-quotidiens/nerdle-2.jpg){: width="450" height="450" }
_Nerdle (partie finie)_

### Modes

Nerdle est un jeu quotidien.
Pour ma part, je me contente de toujours résoudre l'opération du jour et uniquement celle-ci.
Mais sachez que d'autres modes sont proposés avec de petites variantes relativement sympathiques.
Aussi, si un seul puzzle arithmétique ne vous suffit pas, vous pourrez compléter les autres modes tels que :

- mini
- micro
- bi
- mini bi
- speed
- instant

## 2 - Sutom

[Sutom](https://sutom.nocle.fr/) suit le même principe que Nerdle, à la différence qu'il utilise non pas l'arithmétique mais plutôt le vocabulaire français.
Les plus perspicaces auront remarqué que Sutom c'est Motus à l'envers.
Et effectivement, il s'agit là du même procédé.

### Règles

Vous disposez de 6 essais pour tenter de deviner le mot du jour qui comporte entre 6 et 9 lettres.
Le mot qu'il faut trouver est un mot commun, qui se trouve dans le dictionnaire et qui n'est pas conjugué/accordé.
Il peut s'agir d'un nom commun, d'un verbe ou encore d'un adjectif.
Aussi vous pouvez tenter n'importe quel mot qui existe, même conjugué/accordé.
Seuls les noms propres ne sont pas acceptés.

Dès le début, vous avez connaissance de la première lettre imposée (et non modifiable).
Puis à la suite de chaque tentative vous obtenez de nouveaux indices :

- Une carré **rouge** indique que la lettre est à la bonne place
- Un rond **jaune** signifie que la lettre existe dans le mot mais n'est pas correctement placée
- Une lettre qui reste sur fond bleu indique que cette lettre n'existe pas dans le mot à trouver

### Exemple

![Sutom](/assets/img/posts/puzzle-games-quotidiens/sutom-1.jpg){: width="450" height="450" }
_Sutom (partie en cours)_

Avec la seconde ligne de cet exemple, on peut aisément comprendre que :

- Le mot que l'on cherche commence par un `F`, il s'agit de la lettre imposée
- Le résultat ne contient ni un deuxième `L` (le premier étant en dernière position), ni de `O`
- Il y aura un `R` dans le mot mais ni en troisième (grâce à la première ligne) ni en quatrième position
- La solution finit par `AL`

La partie se termine une fois que toutes les cases sont rouges, ou après 6 essais en cas d'échec.
C'est-à-dire quand le mot a été correctement identifié.

![Sutom](/assets/img/posts/puzzle-games-quotidiens/sutom-2.jpg){: width="450" height="450" }
_Sutom (partie finie)_

> Après ma 100ème partie, ma moyenne est de **3.81** essais avant de trouver
{: .prompt-tip }

### Alternatives

De nombreuses alternatives existent.
La plus connue est certainement [Tusmo](https://www.tusmo.xyz/) qui s'appuie sur le même principe.
A la différence près que le mot recherché peut être conjugué ou accordé.
C'est sur ce point que je préfère Sutom à Tusmo.

Toutefois, Tusmo a le mérite de proposer un mode _Suite quotidienne_ qui vous invite à trouver un mot de 6 puis 7 puis 8 et enfin 9 lettres.
Avec pour chaque mot, le moins d'essais possibles.

## 3 - 0h n0

[0h n0](https://0hn0.com/) est différent des deux autres.
En effet, il ne s'agit pas d'un jeu où il faut deviner une séquence en un certain nombre d'essais.
Mais d'une grille qu'il faut remplir de façon logique avec soit des ronds bleus soit des rond rouges.

> Personellement, j'utilise directement l'[application Android](https://play.google.com/store/apps/details?id=com.q42.ohno&hl=fr&gl=FR).<br>
    Mais le site web possède exactement les mêmes options.
{: .prompt-info }

### Règles

A la façon d'un sudoku, la grille de départ est remplie avec plusieurs chiffres qui donnent les premiers indices.
Tous ces chiffres sont donnés sous la forme de ronds bleus.
Il est également possible d'avoir des ronds rouges, vides, qui donnent eux aussi des informations.

Voici comment interpréter les différents indices dont vous disposez :

- Un rond **bleu** voient tous les ronds bleus présents dans sa ligne ou dans sa colonne
- Un rond **rouge** bloque la vue à tous les ronds bleus qui se trouvent, une fois encore, sur sa ligne/colonne
- Les **chiffres**, toujours présents dans un rond bleu, indiquent combien de ronds bleus celui-ci peut voir

Il faut donc remplir le reste de la grille en mettant soit des ronds bleus soit des ronds rouges afin que tous les ronds bleus de départ, contenant des chiffres, voient le bon nombre de ronds bleus.

- Pour placer un nouveau rond bleu, il suffit de cliquer une fois sur une case vide.
- Pour un rond rouge, il faut cliquer une seconde fois sur un rond bleu vide.

### Exemple

> Attention !
    Cet exemple explique des techniques de base que vous pourriez vouloir trouver par vous même.<br>
    Il s'agit seulement des concepts expliqués dans le tutoriel officiel, mais sait-on jamais.
{: .prompt-danger }

![0h n0](/assets/img/posts/puzzle-games-quotidiens/0hn0-1.jpg){: width="450" height="450" }
_0h n0 (grille de départ)_

Dans cette grille de départ, nous disposons de plusieurs informations qui nous permettent de passer à l'étape suivante :

1. Les deux `3` en bas à droite de la grille voient déjà 3 autres ronds bleus.<br>
    Il faut donc placer 4 ronds rouges afin qu'ils n'en voient pas plus.
2. Le `1` dans le coin en haut à droite se retrouve donc avec un rond rouge à sa gauche.<br>
    Il n'a alors plus d'autres choix que de voir un rond bleu directement en dessous de lui.
3. Après avoir ajouté ce rond bleu, le `4` de droite voit tous ses ronds bleus.<br>
    Plaçons donc un rond rouge à sa gauche.
4. Enfin, le `5` tout en bas à droite a dans tous les cas un rond bleu à gauche de lui.
    Car même s'il possède un rond bleu à sa droite, il lui en manquera alors toujours un autre.

![0h n0](/assets/img/posts/puzzle-games-quotidiens/0hn0-2.jpg){: width="450" height="450" }
_0h n0 (partie en cours)_

La partie prend fin une fois que la grille est correctement remplie.
De plus, les ronds bleus vides se voient attribuer une valeur comme sur l'exemple ci-dessous.

![0h n0](/assets/img/posts/puzzle-games-quotidiens/0hn0-3.jpg){: width="450" height="450" }
_0h n0 (partie finie)_

### Taille de grilles

Dans le mode _puzzles quotidiens_, une grille de chaque taille est générée.
Ainsi, il vous faudra résoudre les tailles suivantes :

- 4 * 4
- 5 * 5
- 6 * 6
- 7 * 7
- 8 * 8
- 9 * 9

La plus petite taille demande à peine une dizaine de secondes.
Mais pour la plus grande, cela peut prendre plusieurs minutes.

Un mode _libre_ existe également si vous souhaitez jouer à d'avantages de grilles générées alors aléatoirement.