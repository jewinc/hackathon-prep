# Préparation Hackathon


Ce projet Git a pour but de préparer l'équipe Innovaite pour le hackathon Start'in saclay 2026.
Il traitera des bases pour mener à bien et en toute sérénnité le hackathon (Git, Environnement Python, usage LLM)


# Git

Git sert à versioner tout un répertoire contenant le code d'un projet et ses fichiers.
Les points importants sont : branches, commit et HEAD.

Les branches sont composés d'une succession de commit, c'est une certaine version des différents fichiers.
Un commit décrits des changements apportés aux fichiers.

La branche `main` est crée par défaut et doit contenir une version fonctionnelle en permanence mais on pourra passer outre cette règle pour la hackathon vu le temps qu'on a.
HEAD est le pointeur vers un commit, par défaut c'est le commit le plus récent de la branche.


**Contribuer à Git avec les différents scénarios :**
    
**Toujours être à jour avant de faire vos modifications sinon ça complique les choses.**

Se mettre à jour avec le répertoire distant : 
- git fetch origin
- git pull origin <branch-name>


Contribuer au projet : 
    - Créer une branche : git checkout -b <branch-name> | Charger une branche déjà existante : git checkout <branch-name>
    - Faire des modifications : modifier le fichier git_tuto.py
    - Ajouter les modifs à soumettre : git add <file_path>|. (pour tous les fichiers modifiés)
    - Ajouter à l'historique de la branche : git commmit -m "msg"
    - Envoyer les modifications au répertoire distant : git push <dist-repo-name> <branch-name>, dist-repo-name=origin (par défaut)

Gérer les conflits :



conflict