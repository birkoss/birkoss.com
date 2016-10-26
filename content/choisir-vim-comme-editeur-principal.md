Title: Choisir Vim comme éditeur principal
Date: 2016-10-25
Category: webdev
Tags: vim
Slug: choisir-vim-comme-editeur-principal

L'avant Vim
-----------

Avant Vim, j'ai essayé plusieurs éditeurs sans trouver ce qui me convenait. Ayant commencé avec Dreamweaver, pour ensuite trouver PhpEd, j'ai ensuite été avec Sublime pendant un bon moment. Quand Atom est sorti, je l'ai essayé et étant OpenSource, je l'ai adopté pendant un moment.

J'utilisais Vim parfois, principalement par SSH. Étant capable de fonctionner de base, je savais l'utiliser sans bien comprendre toute sa puissance.

Je suis tombé sur des vidéos dans Youtube, d'un programmeur qui utilisait Vim et qui nous montrait ce qu'il peut faire avec. En quelque touche, il pouvait tout faire ce que je fesais avec des racourcis claviers et ma souris, et ce, sans éloigner ses mains de son clavier. On dirait de la magie!

Les avantages de Vim
--------------------

* Vim est installé sur pratiquement tous les serveurs, le maitriser est un plus.
* Vim permet de naviguer dans le document, sans déplacer les doigts de son clavier. Plus besoin d'aller chercher la souris pour se déplacer, remplacer du texte.
* Vim est configurable à sa guise, on choisit exactement son fonctionnement et ses capacités
* Vim permet ce que les autres IDEs offrent: Complétion de code, modifier plusieurs fichiers, utilisation de plugins, compiler son application directement dans l'éditeur, et bien plus.
* Vim est gratuit et OpenSource. Il est encore en constant changement, même s'il a plus de 30 ans.

Les désavantages de Vim
-----------------------

* La courbe d'apprentissage est grande et assez imposante! On peut parler de mur plutôt que d'une courbe. Cependant, c'est possible d'y aller par étapes, à notre rythme. Au début, quand on voit les différentes fonctions et leurs touches, c'est assez difficile de tout absorber.
* Si on modifie Vim (chose que tout le monde fait), quand on tombe dans un Vim de base, c'est parfois mélangeant. C'est pourquoi les modifications qu'on y apporte devrait être esthétique, ou pour faciliter notre édition. Le fonctionnement de base devrait rester sensiblement le même.

Comment Vim fonctionne
----------------------

Vim est un éditeur de mode. Cela signifie qu'il fonctionne à l'aide de différents modes au lieu d'être un éditeur normal. Il y a plusieurs modes :

* Mode normal: C'est le mode par défaut, et celui par lequel on navigue dans les documents et qu'on effectue plusieurs opérations d'édition de texte.
* Mode insertion: C'est le mode ou on ajoute du texte dans le document. Ce mode est fait pour être utilisé par brève instance, une fois le texte ajouté, on devrait toujours retourné en mode normal.
* Mode visual: C'est le mode pour faire des sélections de texte
* Mode commande
* Mode ex

Les commandes sous Vim fonctionne, pour la plupart sous la syntaxe suivante :

Compteur + Opérateur + Mouvement

Le *compteur* est optionel, et signifie la répétion de la commande.

Voici quelques opérateurs parmis les plus importants :

* d pour effacer
* c pour changer
* y pour copier


Jusqu'ici, ça va. C'est le concept du mouvement qui est souvent le plus difficile à comprendre. Si on veut effacer une ligne, on appuie sur **d** et rien ne se passe. C'est normal!

Vim est en mode d'attente **d** n'est pas un opérateur qui est utilisable sans mouvement, Vim sait qu'on veut effacer, mais effacer quoi, et jusqu'ou?

Prenons exemple du texte suivant (mon curseur est représenté par **#**) :

Lorem ipsum dolor sit amet, consectetur adipiscing **#**elit. Nunc quis posuere metus.

Si je veux effacer de mon curseur, jusqu'à la lettre *p* du mot posuere, je vais utiliser la lettre **t** suivi de la lettre jusqu'à laquelle je veux effacer, ici **p**. La commande sera **dtp** qui se lit (en anglais), comme suit : Delete unTil P.

C'est la même chose si on veut remplacer le texte du curseur jusqu'à la lettre **p**, on va utiliser la commande **ctp**. Ceci va effacer le texte et nous mettre en mode insertion.

Prenons l'exemple suivant : (on curseur est représenté par le **#**) :

echo 'Ceci est un**#** texte';

Si je veux changer le texte entre guillemets, peu importe ou je suis situé entre les guillemets, je peux faire **ci'** et le texte sera enlevé et on sera en mode insertion prêt à mettre le nouveau texte. Seulement 3 touches, sans déplacer les mains de son clavier!

Certains mouvements, comme **G** pour la fin du fichier, peut être utiliser seul pour aller à la fin du fichier, mais utilisé avec l'opérateur **d** qui donne **dG** effacera à partir du curseur jusqu'à la fin du fichier.

La force ultime de Vim réside dans ce concept. Il y a toujours façon d'améliorer les opérations qu'on fait en utilisant le moins de touche possible. Aucun autre éditeur ne me rend aussi fier de passer d'une commande de 5 touches vers une commande de 3.
