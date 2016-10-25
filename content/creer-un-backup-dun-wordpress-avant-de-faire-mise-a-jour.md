Title: Créer un backup d'un wordpress avant de faire mise à jour
Date: 2016-02-02
Category: webdev
Tags: wordpress
Slug: creer-un-backup-dun-wordpress-avant-de-faire-mise-a-jour

Voici comment créer un backup des fichiers de Wordpress avant une mise à jour. Habituellement, je ne backup pas le dossier *wp-content/uploads/* car il est souvent trop lourd, et il ne sera pas modifié lors de la mise à jour.

Si votre site Web est dans le dossier *public_html*, une commande du genre :

`tar -pczf backup.tar.gz public_html/ --exclude "public_html/wp-content/uploads"`

Vous fera une archive du site, et c'est beaucoup moins lourd qu'un backup complet. Avec cela et un backup de la base de données, il ne vous manquera rien pour remettre le site fonctionnel s'il y a un problème avec la mise à jour.
