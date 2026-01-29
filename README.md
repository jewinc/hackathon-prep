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


## **Contribuer à Git avec les différents scénarios :**

**Toujours être à jour avant de faire vos modifications sinon ça complique les choses.**

### Se mettre à jour avec le répertoire distant : 
- git fetch origin
- git pull origin <branch-name>

### Commandes utiles : 
- git branch (permet de voir toutes les branches)
- git branch -d <branch-name> (supprime une branche)
- git log (liste tous les commits d'une branche avec leur hash)
- git status (liste tous les fichiers modifiers a ajouté avec git add)
- git restore --staged <file-path> (annule un fichier qui a été ajouter avec git add)

### Contribuer au projet : 
    - Créer une branche : git checkout -b <branch-name> | Charger une branche déjà existante : git checkout <branch-name>
    - Faire des modifications : modifier le fichier git_tuto.py
    - Ajouter les modifs à soumettre : git add <file_path>|. (pour tous les fichiers modifiés)
    - Ajouter à l'historique de la branche : git commmit -m "msg"
    - Deux choix ici pour rappatrier ces modifs vers la branche principale : 
      - Avec les pull request (meilleur pratique car permet les reviews, formattage etc... si c'est implémenté)
        - Envoyer les modifications au répertoire distant : git push <dist-repo-name> <branch-name>, dist-repo-name=origin (par défaut), j'utiliserais origin par la suite
        - Faire une pull request depuis l'interface WEB de Github : <target-branch> <- <current-branch>
      - Avec Rebase (merge ou squash possible aussi), <target-branch> est la branche principale, <current-branch> est la branche avec les modifications :
        - Aller à la branch cible : git checkout <target-branch>
        - Mettre à jour la branch : git pull origin <target-branch>
        - Rappatrier les modifs : git rebase <current-branch>
        - Mettre à jour le repo distant : git push origin <target-branch>


### Gérer les conflits :

Un conflit peut arriver si une des deux branches divergent (nombre de commit différent) et que des fichiers ont été modifié dans les deux branches.
Exemple : si deux personnes différentes travaillent sur le même fichier.

Simulons un conflit (on modifiera git_tuto.py) :
- Crée une nouvelle branche <conflict> et ajouter un commit (ajoutez print("c1 prime"), git add ., git commit)
- Dans la branche <main> : ajouter deux commit (ajoutez print("c1") et print("c2), git add ., git commit)
- On se retrouve dans cette sitution : 
  - <main> : c -> c+1 -> c+2
  - <conflict> : c -> c+1
- On va vouloir rappatrier les modifications de la branche <conflict> à main mais les branches divergent et le même fichier a été modifié
- On rappatrie : git rebase <conflict>
- On doit résoudre les conflits (dans VS code, il y a une interface dédié= merge editor), n'oubliez pas de sauvegarder le fichier (CTRL+S) une fois les conflits gérés.
- Une fois les conflits résolus : git add . et git rebase --continue
- Pour cette démo, vous pouvez nettoyer : git reset --hard HEAD~2 et git branch -d <conflict>

### Détruire un commit : 
On l'a juste au dessus, on peut annuler des commit de l'historique d'une branche avec git reset.
Quelques arguments important : git reset --hard|--soft HEAD^|HEAD~x
--hard si vous ne voulez pas conserver les modifications après avoir enlevé le commit, --soft si on vous voulez les garder
HEAD : pointeur du commit actuel, ^ c'est le commit juste avant, ~x c'est le commit numéro x avant HEAD
On peut aussi faire git reset <commit-hash>, cela annule les commits jusqu'a atteindre le commit en question.



# Python

Une bonne pratique avant de commencer à développer est de créer un environnement python, cela évite de polluer votre interpréteur python gobale à la machine.

Pour ce faire, assurez vous d'avoir au moins python d'installer : 
- Aller dans le répertoire ou vous souhaitez créer l'environnement
- Créer l'environnement : python|python3 -m venv .venv
- Activer l'environnement à votre terminal : source .venv/bin/activate (sur linux) | .venv/Scripts/activate (sur windows)
- Installer les packages que vous voulez : pip install -r requirements.txt

Si vous êtes sur VS Code et linux (à voir si ça fonctionne pareil avec d'autre éditeurs), vous pouvez utiliser cet environnement comme kernel jupyter pour les notebooks avec ces étapes : 
- pip install ipykernel
- python -m ipykernel install --user --name=venv --display-name "Nom du venv"
- ls ~/Library/Jupyter/kernels/


# Snowflake 

Pour faire tourner le notebook et les fichiers python de démo, il faudra copier et configurer le fichier .env-template.
Vous trouverez l'account id dans l'url de l'interface web (ex: https://app.snowflake.com/ggspbsl/tl37311/#/homepage, a pour account-idf : ggspbsl-tl37311)
Le User et Password correspondent aux identifiants utilisés pour vous connecter à l'interface web.
Quelques exemple de ce qui est possible de faire se trouve dans le notebook demo_snowflake.ipynb.