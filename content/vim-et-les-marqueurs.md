Title: Vim et les marqueurs
Date: 2016-10-25
Category: webdev
Tags: vim
Slug: vim-et-les-marqueurs

Les marquers (markers) sont en quelque sorte, des marques pages dans les documents.

Créer un marqueur
-----------------

Pour créer un marqueur, en mode normal, il faut appuyer sur **m** suivi d'une lettre. Il y a une différence entre les majuscules et les minuscules: les majuscules sont utilisés globalement dans Vim, et sont associés à un fichier précis. Les lettres minuscules sont locales par fichier. Si vous avez 10 fichiers d'ouvert, chaque fichier peut utiliser la lettre *a*, alors qu'un seul pourra utiliser la lettre *A*.

Le marqueur sera créé à la position du curseur.

Si on utilise une lettre déjà utilisé, l'ancienne référence sera écrasée.

Retourner à un marqueur existant
--------------------------------

En mode normal, il faut appuyer sur **'** suivi de la lettre défini lors de sa création. Ceci va retourner au début de la ligne ou le marqueur a été créé.

Encore en mode normal, on peut appuyer sur **`** suivi de la lettre défini pour retourner directement à l'endroit ou le curseur était lors de la création du marqueur.
