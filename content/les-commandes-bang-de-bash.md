Title: Les commandes Bang de Bash
Date: 2016-02-01
Category: linux
Tags: bash
Slug: les-commandes-bang-de-bash

En CLI, nous utilisons souvent les mêmes commandes, et les mêmes arguments. Voici des trucs simples pour augmenter votre rapidité et votre efficacité avec Bash. 

!!
--

Cette commande va exécuter la dernière commande à nouveau. Voici un exemple pratique:

`apt-get update`

Nous donnera le résultat suivant, n'ayant pas les accès nécessaires :

    E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
    E: Unable to lock directory /var/lib/apt/lists/
    E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
    E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Donc pour exécuter la commande précédente avec *sudo* :

`sudo !!`

!chaine
-------

Cette commande va exécuter la dernière commande commençant par *chaine*. Exemple pour exécuter la dernière commande avec whois:

`!whois`

!$
--

Cette commande retourne le dernier argument de la commande précédente. Voici un exemple :

`whois birkoss.com`

Et ensuite :

`host !$`

Cette commande est la même chose que *host birkoss.com*, étant donné que c'est le dernier argument de la commande précédente.

^trouve^remplace
-----------------

Cette commande, permet de remplacer un texte dans la dernière commande et de l'exécuter à nouveau. Voici un exemple:

`tra -zcvf backup.tar.gz dossier`

Il y a une erreur avec *tar* vers *tra*. Au lieu de répéter la commande précédente, on peut simplement faire :

`^tra^tar`

Et cette commande va créer l'archive correctement.
