Title: Se connecter sans mot de passe sur un serveur par SSH 
Date: 2015-04-02
Category: linux
Tags: ssh
Slug: se-connecter-sans-mot-de-passe-sur-un-serveur-par-ssh 

Générer une clé publique et privée
----------------------------------

Cette étape est optionnelle si vous avez déjà généré une clé sur votre ordinateur.

Ouvrez un terminal, et entrez la commande suivante pour créer des clés RSA de 2048 bit.

`ssh-keygen -t rsa`

Vous devrez entrer le fichier ou enregistrer votre clé privée:

    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/birkoss/.ssh/id_rsa):

Vous pouvez laisser la valeur par défaut en appuyer sur **ENTRÉE**.

Ensuite, vous devrez entrer le mot de passe de votre clé. C'est ce mot de passe qui sera utilisé pour utiliser votre clé. Il faut aussi confirmer le mot de passe.

    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:

C'est possible de laisser le mot de passe vide pour ne pas avoir à entrer de mot de passe du tout, mais c'est très insécure. Si quelqu'un a accès à votre clé privée, il aura accès à tous les systèmes ou la clé est installée.

Avec la plupart des distributions Linux, et même sous OSX, il existe un utilitaire appelé **ssh-agent** qui permet d'entrer le mot de passe de votre clé qu'une seule fois par session.

Ensuite, les clés seront générées:

    Your identification has been saved in /home/birkoss/.ssh/id_rsa.
    Your public key has been saved in /home/birkoss/.ssh/id_rsa.pub.
    The key fingerprint is:
    05:55:c5:3e:7b:58:05:4d:07:89:aa:c1:6d:e3:61:8c birkoss@Thinkpad
    The key's randomart image is:
    +--[ RSA 2048]----+
    |        .....++*o|
    |         .  . o +|
    |       . +.. .  .|
    |        E.O   o .|
    |        S* o   = |
    |        . .   o .|
    |               . |
    |                 |
    |                 |
    +-----------------+

Vous pouvez voir que votre clé privée (**id_rsa**) et votre clé publique (**id_rsa.pub**) sont bien générés avec la commande suivante:

    birkoss@Thinkpad:~$ ls -lh ~/.ssh/
    total 12K
    -rw------- 1 birkoss birkoss 1.8K Jul 29 10:23 id_rsa
    -rw-r--r-- 1 birkoss birkoss  404 Jul 29 10:23 id_rsa.pub
    -rw-r--r-- 1 birkoss birkoss  444 Jul 29 08:04 known_hosts
    birkoss@Thinkpad:~$

Copier votre clé publique sur le serveur
---------------------------------------

Il faut ajouter la clé publique dans le fichier **~/.ssh/authorized_key** du compte sur le serveur que vous voulez accéder. Cette étape peut se faire manuellement, mais il existe une commande pour le faire plus rapidement: **ssh-copy-id**.

`ssh-copy-id -i ~/.ssh/id_rsa.pub USER@SERVER.com`

On peut aussi spécifier le port avec le paramêtre **-p**.

Le serveur demandera le mot de passe du compte que vous voulez accéder:

    birkoss@Thinkpad:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub USER@SERVER.com -p1221
    /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
    /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
    USER@SERVER.com's password:

Une fois le mot le mot de passe entré, le serveur devrait vous indiquer que la clé est bien ajoutée:

    Number of key(s) added: 1

    Now try logging into the machine, with:   "ssh -p '1221' 'SERVER.com'" and check to make sure that only the key(s) you wanted were added.

    birkoss@Thinkpad:~$ 

Se connecter sur le serveur sans mot de passe
----------------------------------------------

C'est de la même façon qu'on se connecte sur le serveur, mais cette fois, aucun mot de passe ne sera demandé.

Si par hasard, vous voyez le message d'erreur suivant:

    Agent admitted failure to sign using the key.

et que vous devez entrer le mot de passe quand même, vous pouvez fermer et ouvrir la session à nouveau, ou bien entrer la commande suivante:

`ssh-add`
