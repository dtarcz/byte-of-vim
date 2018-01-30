# Les bases de l'édition de texte

Apprenons les commandes d'édition de base dans Vim pour lire/écrire des fichiers, couper/copier/coller, annuler/rétablir et rechercher.

## Lire et écrire des fichiers

### Tampons

Quand vous éditez un fichier, Vim pose le texte de ce fichier dans la mémoire vive (RAM) de l'ordinateur. Cela signifie qu'une copie du fichier est stockée dans la mémoire de l'ordinateur et que toute modification apportée est modifiée dans la mémoire de l'ordinateur et immédiatement affichée. Une fois que vous avez fini d'éditer le fichier, vous pouvez enregistrer le fichier, ce qui signifie que Vim réécrit le texte de la mémoire de l'ordinateur dans le fichier sur le disque dur. La mémoire de l'ordinateur utilisée ici pour stocker temporairement le texte est appelée "tampon". Notez que ce même concept est la raison pour laquelle nous devons "sauvegarder" les fichiers dans tous les éditeurs ou traitements de texte que nous utilisons.

Maintenant, ouvrez Vim, écrivez les mots `Hello World` et enregistrez-le sous le nom de fichier `hello.txt`. Si vous avez besoin de vous rappeler comment faire, veuillez vous référer au chapitre [Premiers pas](./first_steps.md#write-file).

### Swap

Vous remarquerez maintenant qu'un autre fichier a été créé dans le même répertoire que ce fichier, le fichier pourrait se nommer quelque chose comme `.hello.txt.swp`. Exécutez `:swapname` pour trouver le nom exact du fichier.

C'est quoi ce fichier? Vim maintient une sauvegarde de la mémoire tampon dans un fichier qu'elle enregistre régulièrement sur le disque dur afin qu'en cas de problème (comme un arrêt brutal de l'ordinateur ou même un crash de Vim), vous ayez une sauvegarde des modifications que vous avez faites depuis votre dernier enregistrement du fichier original. Ce fichier s'appelle un "fichier swap (d'échange - NDT)" parce que Vim garde le contenu du tampon dans la mémoire de l'ordinateur avec le contenu de ce fichier sur le disque dur. Voir `:help swap-file` pour plus de détails.

### Enregistrer mon fichier

Maintenant que le fichier a été chargé, procédons à une modification mineure. Appuyez sur la touche ~ pour changer la casse du caractère sur lequel le curseur est positionné. Vous remarquerez que Vim marque maintenant le fichier qui a été changé (par exemple un signe `+` apparaît dans la barre de titre de la version GUI de Vim). Vous pouvez ouvrir le fichier actuel dans un autre éditeur et vérifier qu'il n'a pas encore changé, c'est-à-dire que Vim n'a modifié que le tampon et ne l'a pas encore enregistré sur le disque dur.

Nous pouvons réécrire le tampon dans le fichier d'origine sur le disque dur en exécutant `:write`.

> REMARQUE: Si vous souhaitez sauvegarder facilement, ajoutez les lignes suivantes dans votre fichier vimrc:
> <br>
> ``` viml
> " Pour sauvegarder avec Ctrl+s
> nmap <c-s> :w<CR>
> imap <c-s> <Esc>:w<CR>a
> ```
> <br>
> Maintenant vous pouvez simplement taper `Ctrl+s` pour enregistrer le fichier.

### Travailler dans mon répertoire

Vim démarre avec votre dossier personnel comme répertoire par défaut et toutes les opérations seront effectuées dans ce dossier.

Pour ouvrir les fichiers situés dans d'autres dossiers, vous pouvez utiliser les chemins complets ou relatifs tels que:

``` viml
:e ../tmp/test.txt
:e C:\\achats\\monday.txt
```

Ou vous pouvez basculer Vim dans ce répertoire:

``` viml 
:cd ../tmp
```

`:cd` est un raccourci pour  'c'hange 'd'irectory.

Pour savoir dans quel répertoire Vim va ouvrir les fichiers:

``` viml
:pwd
```

`:pwd` est un raccourci pour  'w'orking 'd'irectory.

## Couper, Copier, et Coller

Comme le dit Sean Connery, dans le film [À la rencontre de Forrester (Finding Forrester)](http://www.imdb.com/title/tt0181536/):

> Ne pas penser - ça vient après. Écrivez votre premier brouillon avec votre coeur. Corrigez avec votre tête. La clef fondamentale pour écrire c'est... d'écrire, pas de penser!

Lorsque nous révisons, nous réorganisons fréquemment l'ordre des paragraphes ou des phrases, c'est-à-dire que nous devons être en mesure de couper/copier/coller le texte. Dans Vim, nous utilisons une terminologie légèrement différente:

| Monde du PC | Monde de Vim | Opération |
| --- | --- | --- |
| cut (couper) | delete (supprimer) | `d` |
| copy (copier) | yank (tirer) | `y` | 
| paste (coller) | paste (coller) | `p` |

Dans la terminologie de l'ordinateur de bureau (PC) normale, 'cut' (découper) du texte signifie enlever le texte et le mettre dans le presse-papiers. La même opération dans Vim signifie qu'il supprime le texte du tampon de fichiers et le stocke dans un 'registre' (une partie de la mémoire de l'ordinateur). Puisque nous pouvons choisir le registre où nous pouvons stocker le texte, il y est fait référence en tant qu'opération "supprimer".

De même, dans la terminologie bureautique normale, 'copier' du texte signifie qu'une copie du texte est placée dans le presse-papiers. Vim fait pareil, il "tire" le texte et le place dans un registre.

"Coller" veut dire pareil dans les 2 terminologies.

Nous avons vu comment vous pouvez faire des opérations couper/copier/coller dans Vim. Mais comment spécifiez-vous le texte sur lequel ces opérations devraient fonctionner? Eh bien, nous avons déjà vu cela dans la précédente section [Objets Textes](./moving_around.md#text-objects).

Combiner la notation d'opération et la notation d'objet texte signifie que nous avons d'innombrables manières de manipuler le texte. Voyons quelques exemples.

Ecrivez ce texte dans Vim (exactement comme indiqué):

> Ceci est le mle premier paragraphe. <br>
> Ceci est la deuxième ligne. <br>
> <br>
> Ceci est le second paragraphe. <br>

Placez le curseur à la position la plus en haut à gauche, en appuyant sur `1G` et `|` qui se déplace vers la première ligne et la première colonne respectivement

Voyons le premier cas: Nous avons tapé un 'm' supplémentaire que nous devons supprimer. Tapez `3w` pour avancer de 3 mots.

Maintenant, on doit effacer 1 caractère là où est positionné le curseur.

Remarquez qu'il y a 2 parties à cela:

| Opération | Objet Texte / Mouvement |
| --- | --- |
| Efface | 1 caractère à la position courante du curseur |
| `d` | `l` |

Donc, nous avons juste à taper `dl` et nous effaçons 1 caractère! Notez que nous pouvons utiliser `l` même si c'est un mouvement.

Maintenant on remarque que le mot corrigé est redondant, car on a 2 fois "le". Réfléchissez maintenant attentivement à la combinaison de touche qui serait la plus rapide pour corriger ça?

Prenez un peu de temps pour y penser et comprenez par vous même. Prenez votre temps. Maintenant, lisez la suite.

| Opération | Objet Texte / Mouvement |
| --- | --- |
| Efface | Mot |
| `d` | `w` |

Donc, tapez `dw` et vous effacez un mot. Done! Si simple et si beau. La beauté réside dans le fait que ces concepts simples peuvent être combinés pour offrir une gamme de possibilités infiniment riche.

Comment effectuer la même opération pour les lignes? Et bien, les lignes sont considérées comme spéciales dans Vim parce que les lignes sont notre façon de penser le texte. Vite dit, si vous répétez le nom d'une opération 2 fois, elle agira sur le ligne. Donc `dd` effacera la ligne courante et `yy` copiera la ligne courante.

Notre texte d'exemple dans Vim devrait maintenant ressembler à ceci:

> Ceci est le premier paragraphe. <br>
> Ceci est la deuxième ligne. <br>
> <br>
> Ceci est le second paragraphe. <br>

Allez à la 2me ligne en tapant `j`. Maintenant, tapez `dd` et la ligne sera effacée. Vous devriez maintenant voir:

> Ceci est le premier paragraphe. <br>
> <br>
> Ceci est le second paragraphe. <br>

Voyons voir un cas plus grand: Comment copier le paragraphe courant?

| Opération | Objet Text Objecte / Mouvement |
| --- | --- |
| Copier | Le Paragraphe |
| `y` | `ap` |

Donc, `yap` copierai le paragraphe.

Maintenant qu'on a copié le texte, comment le colle t-on? Juste en le `p`étant.

Maintenant vous devriez avoir sous les yeux:

> Ceci est le premier paragraphe. <br>
> Ceci est le premier paragraphe. <br>
> <br>
> <br>
> Ceci est le second paragraphe. <br>

Notez que la ligne vide a aussi été copiée lorsque nous avons fait yap, donc p ajoute cette ligne vide supplémentaire aussi.

Il y a 2 façons de coller qui peuvent être réalisés de la même façon que les 2 façon d'insérer que nous avons vu précédemment:

==========faire rappel vers https://github.com/dtarcz/byte-of-vim/blob/master/modes.md#insert-mode==========

| Clef | Mnémonique |
| --- | --- |
| `p` | coller après la position courante du curseur |
| `P` | coller avant la position courante du curseur |

En poussant cette idée plus loin, nous pouvons combiner tout cela dans des façon de faire encore plus puissantes.

Comment interchanger 2 caractères? Tapez `xp`.

- `x` &rarr; efface 1 caractère sous le curseur
- `p` &rarr; colle après le curseur
==========continuer==========

How to swap two words? Press `dwwP`.

- `d` &rarr; delete
- `w` &rarr; one word
- `w` &rarr; move to the next word
- `P` &rarr; paste before the current cursor position

The important thing is *not* to learn these operations by rote. These combinations of operations and text objects/motions should be automatic for your fingers, without you needing to put in mental effort. This happens when you make using these a habit.

## Marking your territory

You are writing, and you suddenly realize you have to change sentences in a previous section to support what you are writing in this section. The problem is that you have to remember where you are right now so that you can come back to it later. Can't Vim remember it for me? This can be achieved using marks.

You can create a mark by pressing m followed by the name of the mark which is a single character from `a-zA-Z`. For example, pressing `ma` creates the mark called 'a'.

Pressing `'a` returns the cursor to line of the mark. Pressing <code>`a</code> will take you to the exact line and column of the mark.

The best part is that you can jump to this position using these marks any time thereafter.

See `:help mark-motions` for more details.

## Time machine using undo/redo

Suppose you are rewriting a paragraph but you end up muddling up what you were trying to rewrite and you want to go back what you had written earlier. This is where we can "undo" what we just did. If we want to change back again to what we have now, we can "redo" the changes that we have made. Note that a change means some change to the text, it does not take into account cursor movements and other things not directly related to the text.

Suppose you have the text:

> I have coined a phrase for myself - 'CUT to the G': <br>
> 1. Concentrate <br>
> 2. Understand <br>
> 3. Think <br>
> 4. Get Things Done <br>
> <br>
> Step 4 is eventually what gets you moving, but Steps 2 and 3 are equally important. As Abraham Lincoln once said "If I had eight hours to chop down a tree, I'd spend six hours sharpening my axe." And to get to this stage, you need to do Step 1 which boils down to one thing - It's all in the mind. That's why it's so hard.

Now, start editing the first line:

1. Press `S` to 's'ubstitute the whole line.
2. Type the text `After much thought, I have coined a new phrase to help me solidify my approach:`.
3. Press `<esc>`.

Now think about the change that we just did. Is the sentence better? Hmm, was the text better before? How do we switch back and forth?

Press `u` to undo the last change and see what we had before. You will now see the text `I have coined a phrase for myself - 'CUT to the G':`. To come back to the latest change, press `ctrl-r` to now see the line `After much thought, I have coined a new
phrase to help me solidify my approach:`.

It is important to note that Vim gives unlimited history of undo/redo changes, but it is usually limited by the `undolevels` setting in Vim and the amount of memory in your computer.

Now, let's see some stuff that really shows off Vim's advanced undo/redo functionality, some thing that other editors will be jealous of: Vim is not only your editor, it also acts as a time machine.

For example, `:earlier 4m` will take you back by 4 minutes i.e. the state of the text 4 minutes "earlier".

The power here is that it is superior to all undoes and redoes. For example, if you make a change, then you undo it, and then continue editing, that change is actually never retrievable using simple u again. But it is possible in Vim using the `:earlier` command.

You can also go forward in time: `:later 45s` which will take you later by 45 seconds.

Or if you want the simpler approach of going back by 5 changes: `:undo 5`.

You can view the undo tree using `:undolist`.

See :help `:undolist` for the explanation of the output from this command.

See `:help undo-redo` and `:help usr_32.txt` for more details.

## A powerful search engine but not a dotcom

Vim has a powerful built-in search engine that you can use to find exactly what you are looking for. It takes a little getting used to the power it exposes, so let's get started.

Let's come back to our familiar example:

> I have coined a phrase for myself - 'CUT to the G': <br>
> 1. Concentrate <br>
> 2. Understand <br>
> 3. Think <br>
> 4. Get Things Done <br>
> <br>
> Step 4 is eventually what gets you moving, but Steps 2 and 3 are equally important. As Abraham Lincoln once said "If I had eight hours to chop down a tree, I'd spend six hours sharpening my axe." And to get to this stage, you need to do Step 1 which boils down to one thing - It's all in the mind. That's why it's so hard.

Suppose we want to search for the word "Step". In normal mode, type `/Step<cr>` (i.e. `/Step` followed by `enter` key). This will take you to the first occurrence of those set of characters. Press `n` to take you to the 'n'ext occurrence and `N` to go in the opposite direction i.e. the previous occurrence.

What if you knew only a part of the phrase or don't know the exact spelling? Wouldn't it be helpful if Vim could start searching as and when you type the search phrase? You can enable this by running:

``` viml
set incsearch
```

You can also tell Vim to ignore the case (whether lower or upper case) of the text that you
are searching for:

``` viml
set ignorecase
```

Or you can use:

``` viml
set smartcase
```

When you have `smartcase` on:

- If you are searching for `/step` i.e. the text you enter is in lower case, then it will search for any combination of upper and lower case text. For example, this will match all the following four - "Step", "Stephen", "stepbrother", "misstep."
- If you are searching for `/Step` i.e. the text you enter has an upper case, then it will search for **only** text that matches the exact case. For example, it will match "Step" and "Stephen", but not "stepbrother" or "misstep."

> NOTE: I recommend that you put these two lines in your vimrc file (explained later, but see `:help vimrc-intro` for a quick introduction) so that this is enabled always.

Now that we have understood the basics of searching, let's explore the real power of searching. The first thing to note that what you provide Vim can not only be a simple phrase, it can be a "expression". An expression allows you to specify the 'kinds' of text to search for, not just the exact text to look.

For example, you will notice that /step will take you to steps as well as step and even footstep if such a word is present. What if you wanted to look for the exact word step and not when it is part of any other word? Then you can search using `/\<step\>`. The `\<` and
`\>` indicate the start and end positions of a "word" respectively.

Similarly, what if you wanted to search for any number? Searching for `/\d` will look for a 'digit'. But a number is just a group of digits together. So we specify "one or more" digits together as `/\d\+`. If we were looking for zero or more characters, we can use the `*` instead of the `+`.

There are a variety of such magic stuff we can use in our search patterns. See `:help pattern` for details.

## Summary

We have explored some of the basic editing commands that we will use in our everyday usage of Vim. *It is very important that you go through these concepts again and make them a habit.* It is not important to learn each and every option or nuances of these commands. If you know how to use the command and know how to find out more on it based on what you need, then you're a true Vimmer.

Now, go ahead and start editing!
