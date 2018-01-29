# Premiers pas

## Démarrer Vim

La première étape est, bien sûr, d'apprendre à démarrer Vim.

### Graphiquement

#### Windows

Cliquez sur Démarrer &rarr; Programmes &rarr; Vim 7 &rarr; gVim.

#### Mac OS X

Cliquez sur Finder &rarr; Applications &rarr; MacVim.

#### Linux / BSD

Cliquez sur Applications &rarr; Accessoires &rarr; GVim Text Editor, ou pressez `Alt+F2`, tapez `gvim` et validez avec `entrée`.

### En console

#### Windows

Cliquez sur Démarrer &rarr; Run, tapez `vim` et validez avec `entrée`.

#### Mac OS X

Cliquez sur Finder &rarr; Applications &rarr; Utilities &rarr; Terminal, tapez `vim` et validez avec `entrée`.

#### Linux / BSD

Pressez `Ctrl+T ` ou cliquez sur Applications &rarr; Accessoires &rarr; Terminal, ou pressez `Alt+F2`, tapez `konsole`/`gnome-terminal` et vamidez avec `entrée`.
Puis tapez `vim` et pressez `entrée`.

### Résumé

A partir de maintenant quand on dira 'ouvrez vim', utilisez la méthode ci-dessus qui vous conviens le mieux.

> REMARQUE: En démarrant Vim, vous avez sûrement constaté que vous ne pouviez pas immédiatement taper du texte. Ne paniquez pas, tout sera expliqué dans un petit instant.

## Environnement graphique ou dans le terminal?

La version graphique de Vim possède des menus dans le haut et tout autant d'options variées accessible par la souris, mais notez que tout cela est complètement optionnel. Vous pouvez toujours accéder à toutes les fonctionnalités de Vim en n'utilisant *que* le clavier.

Pourquoi est-ce si important? Parce que lorsqu'une personne devient efficiente en tapant, n'utiliser que le clavier la rend encore plus rapide et moins sujette aux erreurs, contrairement à l'usage de la souris. C'est parce que le mouvement nécessaire pour passer du clavier à la souris est lent et qu'un changement de contexte estnécessaire dans l'esprit de la personne lorsqu'elle déplace la main entre le clavier et la souris. Si nous prenons l'habitude d'utiliser le clavier autant que possible, nous économisons un précieux mouvement de la main.

Bien sûr, c'est subjectif. Certains préfèrent la souris et d'autres le clavier. Je vous encourage à utiliser le clavier autant que possible pour faire l'expérience du véritable pouvoir de Vim.

## Introduction aux Modes

Imaginez vous un samedi après-midi, lassé des programmes télé. Vous voulez regarder votre bon vieux film préféré à la place. Donc, vous *basculez la TV en mode vidéo* afin d'avoir accès au lecteur DVD à la place des chaines du cable. Notez que la télévision permet toujours l'affichage de la vidéo, mais vous avez changé le contexte pour savoir si voulez regarder un DVD ou une chaîne en direct.

De façon similaire, Vim a des modes. Par exemple, Vim a un mode pour écrire du texte, un mode pour exécuter des commandes, etc. 
Ils sont tous dédiés à l'objectif principal d'éditer du texte, mais vous changez le contexte selon que vous voulez simplement taper quelque chose, ou si vous voulez exécuter une commande sur le texte.

N'est-ce pas la simplicité même?

Traditionnellement, le concept des modes est la raison la plus souvent citée par les débutants sur le pourquoi ils trouvent Vim «déstabilisant». Je compare cela à la bicyclette - vous allez trébucher plusieurs fois, mais une fois que vous avez pris le coup, vous vous demanderez où était le problème.

Alors pourquoi Vim a-t-il des modes? Pour rendre les choses aussi simples que possible, même si son utilisation peut sembler "étrange" au premier abord.

Qu'est-ce que je veux dire par là? Prenons un exemple - l'un des objectifs clés de Vim est de le rendre totalement accessible depuis le clavier sans jamais avoir besoin d'utiliser une souris (vous pouvez toujours utiliser la souris si vous le souhaitez mais c'est strictement optionnel). Dans un tel scénario, comment distingueriez-vous le texte que vous voulez écrire et les commandes que vous voulez exécuter? La solution de Vim est d'avoir un mode "normal" où vous pouvez exécuter des commandes et un mode "insertion" où vous écrivez simplement du texte. Vous pouvez basculer entre les deux modes à tout moment. Par exemple, si vous appuyez sur `i`, Vim passe en mode insertion et si vous appuyez sur `Echap`, Vim revient en mode normal.


Comment les éditeurs traditionnels réalisent-ils cette distinction entre les commandes et l'écriture de texte? En utilisant des menus graphiques et des raccourcis clavier. Le problème est que cela n'est pas adapté. Premièrement, si vous avez des centaines de commandes, créer des menus pour chacune de ces commandes serait insenséet source de confusion. Deuxièmement, personnaliser l'utilisation de chacune de ces commandes serait encore plus difficile.

Prnons un exemple spécifique. Supposons que vous vouliez changer toutes les occurrences du mot "aller" au mot "venir" dans un document. Dans un éditeur traditionnel, vous pouvez exécuter une commande du menu comme Modifier &rarr; Remplacer (ou utiliser un raccourci clavier comme `Ctrl-r`) puis entrer le mot 'aller' et le mot 'venir' puis cliquer sur 'Remplacer'. Ensuite, vous devez encore cocher l'option 'Remplacer tout'. Dans Vim, il suffit d'exécuter `:%s/aller/venir/g` en mode normal. Le `:s` est la commande "remplacer" (substitute). Vous visualisez comment c'est plus simple?

Que se passe-t-il si vous souhaitez maintenant exécuter cette substitution uniquement dans les 10 premières lignes du texte et que vous souhaitez avoir une confirmation oui/non a chaque remplacement? Dans les éditeurs de texte traditionnels, il est facile d'obtenir la confirmation oui/non en décochant l'option 'Remplacer tout', mais notez que vous devez d'abord rechercher cette option puis utiliser la souris pour cliquer dessus (ou utiliser une longue série de les touches en utilisant le clavier). Mais comment allez-vous exécuter le remplacement juste dans les 10 premières lignes? Dans Vim, vous pouvez simplement lancer `:0,10s/aller/venir/gc`. La nouvelle option `c` que nous utilisons signifie que nous voulons un message de 'c'onfirmation pour chaque remplacement.

En séparant les modes d'écriture (insert) et de commande (normal), Vim nous facilite le changement des deux contextes aisément.

Remarquez comment les premières étapes de l'utilisation de Vim semblent un peu "bizarres", un peu "étranges", mais une fois que vous l'avez vu en action, cela commence à avoir du sens. Le meilleur c'est que ces concepts de base vous aideront à comprendre tout ce que vous devez savoir sur la façon d'utiliser Vim.

Puisque vous comprenez maintenant la différence entre le mode normal et le mode insertion, vous pouvez rechercher les différentes commandes que vous pouvez exécuter en mode normal, et vous pouvez immédiatement commencer à les utiliser. Comparez cela à l'apprentissage de nouvelles commandes dans les éditeurs traditionnels, ce qui signifie généralement avoir à lire beaucoup de documentation, à rechercher dans de nombreux menus, beaucoup d'essais et d'erreurs ou à demander de l'aide à quelqu'un.

Personnellement, je trouve que les noms des modes ne sont pas intuitifs pour les débutants. Je préfère appeler le mode d'insertion mode "écriture" et le mode normal mode "correction", mais nous nous en tiendrons à la terminologie Vim standard pour éviter toute confusion.

> REMARQUE: Toutes les commandes en mode normal doivent se terminer par la touche Entrée pour signaler à Vim que nous avons écrit la commande complète. Donc, quand  verrez écrit: `:help vim-modes-intro`, cela signifie que vous devez taper `:help vim-modes-intro` et appuyer sur la touche Entrée à la fin de la commande.

## Écrire un fichier {#write-file}

1. Ouvrez Vim. ![](img/first_steps_open.png) 
2. Tapez `:edit salut.txt` et pressez la touche entrée. ![](img/first_steps_edit.png) 
3. Pressez `i` pour passer en mode insertion. ![](img/first_steps_insert.png) 
4. Tapez le texte `Salut Monde`. ![](img/first_steps_type.png) 
5. Pressez la touche `<Echap>`. ![](img/first_steps_normal.png) 
6. Tapez `:write` et pressez la touche `entrée`. ![](img/first_steps_write.png) 
7. Fermez Vim en exécutant `:quit`. ![](img/first_steps_quit.png) 

Félicitation! Vous venez juste d'écrire votre premier fichier avec Vim :-).

Est-ce qu'il semble y avoir beaucoup d'étapes? Tout à fait, *au début*. C'est parce que c'est la première fois que nous nous habituons à ouvrir Vim, à écrire un fichier et à fermer Vim. Vous devez garder à l'esprit que cela ne sera qu'une partie mineure de votre temps par rapport au temps réel qui est consacré à la modification du contenu du document.

Voyons ce que font les commandes suivantes.

- `:edit hello.txt` ou simplement `:e hello.txt`
   - Ouvre un fichier pour édition. Si le fichier avec le nom spécifié n'existe pas, il sera créé la première fois que nous "save" (sauvegardons) le fichier.
- Appuyez sur `i`
   - Ceci passe Vim en mode insertion
- Tapez le texte `Hello World`
   - C'est là que vous tapez le texte que vous voulez écrire.
- Appuyez sur `<Échap>`
   - Cela permet à Vim de revenir en mode normal
- `:write` ou simplement `:w`
   - Ceci indique à Vim de *w* enregistrer (écrire) le texte (qui est actuellement stocké dans la mémoire de l'ordinateur) dans le fichier sur le disque dur. Cela signifie que tout ce que nous avons écrit jusqu'ici est maintenant stocké de façon permanente.
- `:quit` ou simplement `:q`
   - Ceci indique à Vim de *q*uitter le fichier dans la "fenêtre" que nous sommes en train d'éditer. S'il n'y avait qu'une seule "fenêtre" ouverte, cela fermera aussi Vim (le Concept des fenêtres sera discuté dans un chapitre ultérieur). <!-- A FAIRE: Convertir ceci en un lien -->

Essayez de répéter ce processus plusieurs fois avec différents noms de fichiers, différents textes, etc. afin de vous familiariser avec les étapes de base de l'utilisation de Vim.

Notez que lorsque vous êtes en mode insertion, Vim affiche `-- INSERTION --` dans le coin inférieur gauche. Lorsque vous passez en mode normal, il n'affiche rien. C'est parce que le mode normal est le mode *par défaut* dans lequel Vim s'exécute.

Prenez le temps de vous imprégner de cette information, c'est probablement la leçon la plus difficile à apprendre sur Vim, le reste est facile :)

Et ne vous inquiétez pas, l'aide n'est pas très loin. En fait, c'est juste la commande `:help`. Par exemple, lancez `:help :edit` et vous verrez la documentation s'ouvrir. Allez-y, essayez.

## Résumé

Nous avons maintenant abordé les concepts de base et la façon d'utiliser Vim. Voir `:help notation` et `:help keycodes` aussi.

Assurez-vous de bien comprendre ces concepts. Une fois que vous commencez à "penser comme Vim", il est aisé de comprendre le reste des fonctionnalités de Vim.
