Title: Raccourcis pour ouvrir rapidement des connexions SSH sous Ubuntu
Date: 2015-07-29
Category: linux
Tags: ubuntu
Slug: raccourcis-pour-ouvrir-rapidement-des-connexions-ssh-sous-ubuntu

Voici ma méthode pour avoir un accès rapide à mes différentes connexions SSH sous Ubuntu. Plusieurs de mes serveurs ont des noms d'usager différents, ou des ports différents. Cette méthode me permet de ne plus avoir à me souvenir des différentes informations à chaque fois, en plus de me faire gagner du temps.

Voici un exemple du résultats:

![]({filename}/images/a28bec3e-a414-4c58-9728-c549a5dfaf27.jpg)

Cette méthode permet aussi de partager les informations de vos connexions entre vos machines sans la nécessité d'installer un logiciel, ou d'enregistrer des informations sensibles.

Création du fichier
------------------

Il faut créer un fichier avec l'extension **.desktop** dans le dossier **~/.local/share/applications/**, exemple: **~/.local/share/applications/terminal.desktop**.

Voici le contenu du fichier qui permet d'avoir l'exemple plus haut:

    [Desktop Entry]
    Name=Terminal
    Comment=Use the command line
    Exec=gnome-terminal
    Icon=utilities-terminal
    Type=Application
    Categories=GNOME;GTK;Utility;TerminalEmulator;
    StartupNotify=true
    Actions=<strong>New;Server1;Server2;

    [Desktop Action New]
    Name=New Terminal
    Exec=gnome-terminal
    OnlyShowIn=Unity

    [Desktop Action Server1]
    Name=server-name.com
    Exec=gnome-terminal -x ssh SERVER-NAME.com -p1221
    OnlyShowIn=Unity;

    [Desktop Action Server2]
    Name=user@server-name.com
    Exec=gnome-terminal -x ssh USER@SERVER-NAME.com
    OnlyShowIn=Unity;

Il faut ajouter dans l'option **Actions**, chaque nouvel action que vous voulez créer et ensuite, ajouter l'entrée **[Desktop Action NAME]** correspondante.

Ajouter le raccourcis dans le launcher
--------------------------------------

Il suffit de glisser le fichier **terminal.desktop** dans le launcher pour ajouter le raccourcis.
