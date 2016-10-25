Title: Enlever le "Guest Session" dans Ubuntu 16.04
Date: 2016-03-06
Category: linux
Tags: ubuntu
Slug: enlever-le-guest-session-dans-ubuntu-16-04

C'est sensiblement la même chose que pour Ubuntu 14.04, il faut modifier le fichier suivant :

    /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

Pour ajouter la ligne suivante à la fin :

    allow-guest=false

Voici un exemple de mon fichier au complet :

    [Seat:*]
    user-session=ubuntu
    allow-guest=false
