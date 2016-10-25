Title: Modifier les liens dans Wordpress pour passer vers HTTPS
Date: 2016-02-01
Category: webdev
Tags: ssl, wordpress
Slug: modifier-les-liens-dans-wordpress-pour-passer-vers-https

Si vous utilisez des fichiers venant de votre serveur n'ayant pas de HTTPS, vous n'aurez pas le beau cadenas vert qui indique que la connexion est sécurisée. Et nous voulons tous ce cadenas :)

C'est possible facilement, de corriger les liens vers nos fichiers/pages à l'aide de de votre thème enfant de Wordpress directement avec le filtre sur *the_content*.

Voici un exemple à mettre dans le fichier de votre thème:

    function child_theme_the_content($content) {
        $content = str_replace('http://'.basename(get_site_url()), 'https://'.basename(get_site_url()), $content);
        return $content;
    }
    add_filter( 'the_content', 'child_theme_the_content' );

Ce filtre va remplacer tous les appels de votre site actuel vers HTTPS (images, liens, etc.).
