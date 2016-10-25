Title: Effacer les fichiers plus vieux que 30 jours
Date: 2016-02-01
Category: linux
Tags: bash
Slug: effacer-les-fichiers-plus-vieux-que-30-jours

Cette commande effacera les fichiers plus vieux que 30 jours, dans le dossier en cours :

`find . -mtime +30 -exec rm {} \;`

Le signe devant le 30 indique la comparaison à faire:

* **+30** = Supérieur à 30 jours
* **-30** = Inférieur à 30 jours
* **30** = Exactement 30 jours

La syntaxe de l'argument exec peut sembler étrange, mais elle remplacera les parenthères {} par les noms de fichiers trouvés.

On peut aussi combiner avec le paramètre -size pour trouver les fichiers plus gros que qu'une taille précise :

`find . -mtime +30 -size +1024 -exec rm {} \;`

Ceci effacera les fichiers plus vieux que 30 jours, et plus gros que 1mo.

Le signe devant la valeur est identique à celui pour *-mtime*.
