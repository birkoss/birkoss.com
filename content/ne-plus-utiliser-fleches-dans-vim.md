Title: Ne plus utiliser les flèches pour se déplacer dans Vim
Date: 2016-10-26
Category: webdev
Tags: vim
Slug: ne-plus-utiliser-les-fleches-dans-vim

Une des choses les plus difficiles dans mon apprentissage de Vim fut de perdre mon habitude de naviguer dans Vim avec les flèches.

Cela nous fait prendre des mauvaises habitudes, comme par exemple la pire, est de rester inutilement en mode insertion en se déplacant avec les flèches au lieu de naviguer avec les différentes méthodes de Vim.

Le mode insertion est fait pour de brève intervention, ensuite on retourne en mode normal. Avec les flèches, c'est beaucoup plus simple de rester en mode insertion que d'apprendre le déplacement dans Vim.

Voici la façon que j'ai utilisé :

Bloquer les touches
-------------------

Aux grands maux, les grands moyens! En bloquant les touches directement dans le fichier de configuration de Vim (~/.vimrc), c'est simple, on aura pas le choix d'utiliser **h j k** et **l** pour se déplacer. Voici les lignes :

	noremap <Up> <NOP>
	noremap <Down> <NOP>
	noremap <Left> <NOP>
	noremap <Right> <NOP>
	inoremap <Up> <NOP>
	inoremap <Down> <NOP>
	inoremap <Left> <NOP>
	inoremap <Right> <NOP>

Ceci va désactiver les touches en mode normal et en mode insertion.

Cela m'a pris environ 2 journées pour complètement être capable de naviguer avec les touches **hjkl**, les premières heures ont été longues...

Quitter le mode insertion dès qu'on a terminé
---------------------------------------------

Quand on commence à annuler les opérations qu'on fait, on se rend vite compte que l'annulation va enlever tout ce qui a été fait en mode insertion (si c'est la dernière opération...). C'est toujours plus pratique d'annuler seulement ce qui est nécessaire plutôt que 3 paragraphes ainsi que du code.

Dans les habitudes que j'ai pris, dès que j'ai terminé une phrase, que j'analyse mon code ou que j'arrête d'écrire, je retourne en mode normal.

Apprendre à bien naviguer dans Vim
----------------------------------

Cette étape est un *work in progress* perpétuel. À chaque semaine, je découvre de différentes façons de naviguer de plus en plus rapide. Voici les opérations qui m'ont beaucoup aidé au début :

* **I** Permet de passer en mode insertion à la fin de la ligne active
* **A** Permet de passer en mode insertion au début de la ligne active
* **o** Permet de créer une nouvelle ligne en bas la ligne active, et de passer en mode insertion
* **O** Permet de créer une nouvelle ligne au dessus de la ligne active, et passe en mode insertion
* **Xgg** Se déplace à la ligne X
* **fX** Cherche le prochain caractère X dans la ligne active
* **FX** Cherche le caractère X précédent dans la ligne active

Une règle avec Vim est que si on utilise la même touche plusieurs fois, on n'utilise pas Vim à sa juste valeur. Si on veut monter de 6 lignes, il ne faut pas appuyer sur **k** 6 fois, mais au minimum de faire **6k** ou de trouver un caractère ou un mot qu'on peut recherche pour y aller plus rapidement.
