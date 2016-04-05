Supports de formation Osones  ![Build Status](https://travis-ci.com/Osones/formations.svg?token=sy6nX4pitZ2Pksd9gZmW&branch=master)
===============================

Supports de formation (sous forme de slides) écrits en Français et réalisés par Osones (https://osones.com/) pour ses offres de formation.

Sont notamment abordés les sujets suivants : le cloud, sa philosophie, le projet OpenStack, l'utilisation d'OpenStack, le déploiement d'OpenStack, le principe des conteneurs, le projet Docker, l'utilisation de Docker, l'orchestration de conteneurs Docker.

Auteurs :
* Adrien Cunin <adrien.cunin@osones.com>
* Pierre Freund <pierre.freund@osones.com>
* Romain Guichard <romain.guichard@osones.com>
* Kevin Lefevre <kevin.lefevre@osones.com>
* Jean-François Taltavull <jft@osones.com>

Build gérés par la CI (Travis) :
* [Supports PDF](http://formation.osones.com/pdf)
* [Support HTML OpenStack](http://formation.osones.com/openstack.html)
* [Support HTML Docker](http://formation.osones.com/docker.html)

Fonctionnement
--------------

Les supports de formation (slides) sont écrits en Markdown. Chaque fichier dans `cours/` est un module indépendant.

`cours.list` définit les cours à partir des modules.

Il est possible de générer ces slides sous différents formats :
1. HTML / reveal.js
2. PDF à partir du HTML / reveal.js
3. PDF à partir de LaTeX / Beamer

Deux méthodes de build sont disponibles :
* Makefile : supporte 1. et 3.
* .sh : supporte 1. et 2.

Build Makefile
--------------

Le build se fait entièrement en local.
* Voir le header du Makefile pour les dépendances nécessaires.
* Voir `make help` pour l'utilisation.

Quelques exemples :

    make openstack.pdf
    make docker-handout.pdf
    make docker-print.pdf
    make openstack.html

Build .sh
---------

Le build se fait dans des containers Docker.

```
bash build.sh
```

Pour visualiser :

- Lire le(s) fichier(s) cours/output-html/$(cours).html avec votre navigateur
- Les PDF se trouvent dans output-pdf/

OU

```
docker run -d \
            -p 80:8001 \
            -v $PWD/images:/revealjs/images \
            -v $PWD/cours/output-html/$(cours).html:/revealjs/index.html \
            -v $PWD/cours/output-html/revealjs/css/theme/osones.css:/revealjs/css/theme/osones.css \
            vsense/revealjs
```

- Les slides sont ensuite accessibles sur http://localhost

Copyright et licence
--------------------
Tous les contenus originaux (Makefile, scripts, fichiers dans cours/) sont :
* Copyright © 2014-2016 Osones
* Distribués sous licence Creative Commons BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/)

![Creative Commons BY-SA](http://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png)

Les autres fichiers du répertoire images/ sont soumis à leur copyright et licence respectifs.
