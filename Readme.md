# Remote meetings planning

Ce projet contient tout les fichiers de build des différents services de doodle

Les fichiers de conf ont été déplacés ici: [quentinlegot/doodle-config](https://github.com/quentinlegot/doodle-config)

Les documents sont build en parellèle lors d'un push

J'ai remplacé mysql par mariadb par il contient un fichier shell qui permet de faire un healthcheck afin d'éviter de lancer l'api si la bdd n'est pas encore prêt car l'api crash au lancement s'il n'arrive pas à se connecter à la bdd