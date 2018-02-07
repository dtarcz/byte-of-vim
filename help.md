# Aide

Vim possède diverses liste de commandes, de raccourcis clavier, de tampons, etc. Il est impossible de retenir leur fonctionnement à tous. En fait, il n'est même pas utile de tous les connaître. Le mieux c'est de savoir comment rechercher certaines fonctionnalités dans Vim quand vous en avez besoin.

Par exemple, vous voulez éviter d'avoir à taper un nom long à chaque fois, vous vous souvenez soudainement qu'il y a une fonctionnalité d'abréviations dans Vim qui vous aidera à faire cela, mais ne vous souvenez pas comment l'utiliser. Que pouvez-vous faire?

Voyons les différentes façons de trouver de l'aide sur la façon d'utiliser Vim.

## La commande `:help`

Le premier et plus important endroit où chercher de l'aide est la documentation intégrée et Vim a l'un des manuels d'utilisation les plus complets et compréhensible que j'ai jamais vus.

Dans notre cas, exécutez simplement `:help abbreviation` et vous serez amené à l'aide pour les abréviations et vous pourrez lire comment utiliser les commandes `:ab` and `:iab`.

Parfois, cela peut être aussi simple que cela. Si vous ne savez pas ce que vous cherchez, alors vous pouvez lancer `:help user-manual` et parcourir la liste du contenu de l'ensemble du manuel d'utilisation et lire le chapitre qui vous semble pertinent pour ce que vous essayez de faire.

## Comment lire le sujet `:help`

Prenons un échantillon du texte de `:help abbreviate`:

```
    :ab[breviate] [<expr>] {lhs} {rhs}
                add abbreviation for {lhs} to {rhs}.  If {lhs} already
                existed it is replaced with the new {rhs}.  {rhs} may
                contain spaces.
See |:map-<expr>| for the optional <expr> argument.
```

Notez qu'il existe une manière standard d'écrire dans l'aide de Vim pour nous aider à trouver les parties qui nous sont nécessaires au lieu d'essayer de comprendre l'ensemble de la commande.

La première ligne explique la syntaxe, c.-à-d. comment utiliser cette commande.

Les crochets dans `:ab[breviate]` indiquent que la dernière partie du nom complet est facultative. Le minimum que vous devez taper est `:ab` pour que Vim reconnaisse la commande. Vous pouvez également utiliser `:abb` ou `:abbr` ou `:abbre` et ainsi de suite jusqu'au nom complet `:abbreviate`. La plupart des gens ont tendance à utiliser la forme la plus courte possible.

Les crochets dans `[<expr>]` indiquent à nouveau que la dite 'expression' est facultative.

Les accolades dans `{lhs} {rhs}` indiquent que ce sont des espaces réservés pour des arguments à fournir. Ce sont des abbréviations pour 'côté gauche' et 'côté droit' respectivement.

Après la première ligne le paragraphe indenté explique brièvement ce que fait cette commande.

Notez le deuxième paragraphe qui vous indique des informations supplémentaires. Vous pouvez positionner le curseur sur le texte entre les deux symboles pipe et appuyer sur `Ctrl+]` pour suivre le "lien" vers la rubrique `:help` correspondante. Pour revenir en arrière, appuyez sur `Ctrl+o`.

## La commande `:helpgrep`

Si vous ne connaissez pas le nom du sujet, vous pouvez rechercher une phrase dans toute la documentation en utilisant `: helpgrep`. Supposons que vous vouliez savoir comment rechercher le début d'un mot, alors lancez simplement `:helpgrep beginning of a word`.

Vous pouvez utiliser `:cnext` et `:cprev` pour passer à la partie suivante et précédente de la documentation où se trouve cette phrase. Utilisez `:clist` pour voir toute la liste de toutes les occurrences de la phrase.

## Aide rapide

Copiez le texte suivant dans un fichier dans Vim, puis exécutez-le:

``` viml
:let &keywordprg=':help'
```

Maintenant, placez votre curseur n'importe où sur le mot `keywordprg` et appuyez simplement sur `K`. Vous serez immédiatement amené à l'aide pour ce mot. Ce raccourci évite d'avoir à taper `:help keywordprg`.

## Liste de diffusion

Si vous n'arrivez toujours pas à bien comprendre comment faire ce que vous voulez réaliser, le mieux à faire c'est d'approcher les autres utilisateurs de Vim pour vous aider. Ne vous inquiétez pas, c'est très facile et c'est épatant comme d'autres Vimmers sont prêts à vous aider.

Recherchez dans les archives de la liste de diffusion Vim pour voir si quelqu'un a déjà répondu à votre question. Allez simplement sur la [page de recherche du groupe Vim](http://groups.google.com/group/vim_use), puis entrez les mots-clés de votre question. La plupart du temps, de nombreuses questions communes seront déjà traitées, car il s'agit d'une liste de diffusion à fort trafic, c.-à-d. que beaucoup de personnes posent des questions et donnent des réponses dans ce groupe.

Si vous ne trouvez pas de réponses pertinentes, alors posez votre question dans cette même liste de diffusion.

## Résumé

Il y a une mine d'informations sur la façon de faire les choses avec Vim, et nombre de Vimmers vous aideront volontiers. La communauté Vim est l'une des plus grandes forces de l'éditeur Vim, alors assurez-vous d'utiliser toutes les ressources et rejoignez la communauté grandissante.

> Le vrai plaisir est dans *la découverte* plutôt que dans le *savoir*.
> -- Isaac Asimov
> The true delight is in the *finding out* rather than in the *knowing*.
> -- Isaac Asimov
