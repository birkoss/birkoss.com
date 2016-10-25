Title: Afficher la taille des sous-dossiers en ordre de poids
Date: 2016-02-01
Category: linux
Tags: bash
Slug: afficher-la-taille-des-sous-dossiers-en-ordre-de-poids

Commande très pratique pour afficher la taille des sous-dossiers du dossier en cours, en ordre de poids :

`du -h --max-depth=1 | sort -h`

Voici un exemple du résultat :

    4.0K	./Atom Crashes
    4.0K	./.com.google.Chrome.4A1OpU
    4.0K	./.ICE-unix
    4.0K	./luwzdil1.tmp
    4.0K	./orbit-standish
    4.0K	./.org.chromium.Chromium.nkpRKz
    4.0K	./.X11-unix
    8.0K	./.vbox-standish-ipc
    8.0K	./.wine-1000
    76K     ./sni-qt_spotify_29748-a20ORe
    76K     ./sni-qt_spotify_30617-KYbMyy
    76K     ./sni-qt_spotify_5356-z6QGNv
    80K     ./skype-2340
    280K	./fz3temp-1
    17M     .
