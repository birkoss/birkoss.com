Title: Générer un certificat SSL avec LetsEncrypt sur une machine distante
Date: 2016-01-31
Category: linux
Tags: ssl
Slug: generer-un-certificat-ssl-avec-letsencrypt-sur-une-machine-distante

Installer Letsencrypt
---------------------

Étant donner l'état actuel de LetsEncrypt: Encore en beta, et demande l'accès root pour générer des certificats à distance, je préfère l'utiliser dans une machine virtuelle.

Une fois dans la machine virtuel, il suffit d'aller chercher la dernière version sur GitHub comme ceci:

`git clone https://github.com/letsencrypt/letsencrypt`

Générer le certificat SSL
------------------------

Dans le dossier de letsencrypt, il faut utiliser la commande suivante pour commencer le processus de génération du certificat :

`./letsencrypt-auto certonly -d DOMAINE.com --manual`

La première fois que cette commande est exécutée sur la machine, letsencrypt va demander le mot de passe root pour compléter l'installation et installer plusieurs autres dépendances comme *libssl*, *libpython-dev*, etc.

Ensuite, votre courriel vous sera demandé dans un fenêtre similaire à ceci :

![](/images/8e5df579-fa23-4802-af5c-fc5317e5d3a3.png)

Ensuite, il faudra accepter les conditions de LetsEncrypt :

![](/images/037cbdd7-3dfc-4ad9-9fa1-fd229e7a0703.png)

Ces deux écrans ne seront plus visibles par la suite, ils ne le sont qu'à l'installation.

Un message d'avertissement vous indiquera que votre adresse IP sera loggué, comme nous somme en mode manuel :

![](/images/2cd1d8b3-d965-4399-9057-1da4a1586fd0.png)

Ensuite, LetsEncrypt va être en mode d'attente en affichant ceci :

    Make sure your web server displays the following content at
    http://DOMAINE.com/.well-known/acme-challenge/V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc before continuing:

    V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc.gfvUNPMI3XZctLkUftzOR21ObQbzhVdXzg41xfoaV9Y

     If you don't have HTTP server configured, you can run the following command on the target server (as root):

    mkdir -p /tmp/letsencrypt/public_html/.well-known/acme-challenge
    cd /tmp/letsencrypt/public_html
    printf "%s"     V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc.gfvUNPMI3XZctLkUftzOR21ObQbzhVdXzg41xfoaV9Y > .well-known/acme-challenge/V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc
    # run only once per server:
    $(command -v python2 || command -v python2.7 || command -v python2.6) -c \
    "import BaseHTTPServer, SimpleHTTPServer; \
    s = BaseHTTPServer.HTTPServer(('', 80), SimpleHTTPServer.SimpleHTTPRequestHandler); \
    s.serve_forever()" 
    Press ENTER to continue

Letsencrypt reste en attente, il vous laisse le temps de créer le fichier demandé dans le dossier *.well-known/acme-challenge/* de votre serveur. Ce fichier, va assurer LetsEncrypt que vous êtes bien le propriétaire du domaine.

Dans l'exemple plus haut, il faudrait créer le fichier : 

    .well-known/acme-challenge/V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc

contenant le texte suivant : 

    V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc.gfvUNPMI3XZctLkUftzOR21ObQbzhVdXzg41xfoaV9Y

Ensuite, par précaution, il faut vérifier qu'on peut bien accéder au fichier avec un navigateur, et qu'il affiche le bon texte: 

    http://DOMAINE.com/.well-known/acme-challenge/V6xK80Z6w9WYLPNfC51HjZwZW3gh_gf1fqB4lg9jvpc

Lorsque cela est fait, on peut appuyer sur **ENTER** dans la fenêtre de LetsEncrypt.

Si tout va bien, un message similaire va apparaître :

    - Congratulations! Your certificate and chain have been saved at
    /etc/letsencrypt/live/DOMAINE.COM/fullchain.pem. Your cert
    will expire on 2016-04-30. To obtain a new version of the
    certificate in the future, simply run Let's Encrypt again.

Les fichiers seront dans le dossier : /etc/letsencript/live/DOMAINE.COM/, il y aura :

* cert.pem
* chain.pem
* fullchain.pem
* privkey.pem

Ces fichiers vous serviront à installer le certificat sur votre site Web.

Le certificat va expirer dans 3 mois, cette opération sera à refaire, mais le processus est beaucoup plus simple pour le renouveller.

Erreurs possibles
-----------------

Si vous voyez une fenêtre comme celle-ci :

![](/images/667e2d2b-3ca1-4f75-95d4-be9c5f116660.png)

Il faut bien lire le message d'erreur, les raisons les plus probables sont que le fichier de validation n'est pas accessible ou que le domaine ne peut être contacter depuis les serveurs de LetsEncrypt.
