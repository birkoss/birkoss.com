Title: Redirection HTTP vers HTTPS avec le fichier .htaccess
Date: 2016-02-01
Category: webdev
Tags: rewrite
Slug: redirection-http-vers-https-avec-le-fichier-htaccess

Voici un exemple pour faire une redirection du domaine de http://domaine.com vers https://domaine.com avec un fichier .htaccess :

    RewriteEngine On
    RewriteCond %{HTTP_HOST} ^DOMAINE\.COM [NC]
    RewriteCond %{SERVER_PORT} 80
    RewriteRule ^(.*)$ https://DOMAINE.COM/$1 [R=301,L]

La ligne *RewriteCond %{HTTP_HOST} ^DOMAINE\.COM [NC]* n'est pas essentiel si vous n'avez pas d'autres sous-domaines dans le même compte.

Cet exemple, ma rediriger toutes les appels vers des fichiers sur le port 80 (HTTP) vers vos fichiers en HTTPS.

Voici des explications sur les différents *flags* d'Apache utilisé :

* **NC** = Insensible à la casse
* **R=301** = Redirection 301
* **L** = Indique à Apache d'arrêter l'interprétation des autres règles dans le .htacces
