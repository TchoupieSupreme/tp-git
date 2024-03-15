Passion Johan

## B1-Git - Partie 1 : Création du dépôt et _commits_

- Ouvrir un terminal (terminal _Git Bash_ à privilégier)

- Créer, en ligne de commande, un répertoire `tp-git`
git init tp-git
- Se déplacer dans le répertoire
cd tp-git
- Vérifier qu'on est dans le bon répertoire en affichant le chemin du répertoire courant
pwd
- Initialiser un dépôt Git
fait avec le git init
- Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s'assurer que le répertoire `.git` à été créé
ls -a (il y a bien le fichier .git)
- Ouvrir ce répertoire sous VS Code
fait
- Exécuter `git status` et copier/coller la sortie
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

no changes added to commit (use "git add" and/or "git commit -a")
- Créer le fichier `fichier1.md` avec un contenu quelconque et l'enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)
touch fichier1.md
  - Attention, il s'agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.

- Créer le fichier `fichier2.md` avec un contenu quelconque et l'enregistrer
echo "text" > fichier2.md
- Exécuter `git status` et copier/coller la sortie
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ficher1.md
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")

- Ajouter `fichier1.md` à l'index de Git (zone de _Staging_)
git stage fichier1.md 
- Exécuter `git status` et copier/coller la sortie
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   ficher1.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

- Créer un _commit_ avec pour message : "Ajout de fichier1.md"
git commit -m "ajout fichier1.md"
- **_VALIDATION PROF01_**

- Exécuter `git status` et copier/coller la sortie
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md


- Modifier `fichier1.md` et enregistrer
vi fichier1.md, i, test, echap, :wq!
- Exécuter `git status` et copier/coller la sortie
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md
        modified:   reponses.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")

- Ajouter `fichier1.md` et `fichier2.md` à la zone de _Staging_
git stage fichier1.md fichier2.md

- Créer un _commit_ "Ajout de fichier2.md et modification de fichier1.md"
$ git commit -m "Ajout de fichier2.md et modification de fichier1.md"

- Exécuter `git status` et copier/coller la sortie
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

no changes added to commit (use "git add" and/or "git commit -a")

- Copier/coller l'ID des deux premiers _commits_ (utiliser `log`) :

  - ID _commit_ 1 : f5b1ab74ad284cdcda783b0443e116d5f61d1bcb
  - ID _commit_ 2 : 4c9ab6df5302bb3d36f223244929164aa74cf2b4

- Que signifie qu'un fichier est "_tracked_" ou "_untracked_" ?
tracked = il à était commit au moins une fois
untracked = git ne la jamais vu car il n'a jamais était commit, il n'est sauvegardé qu'en local
- Pourquoi doit-on passer les fichiers par la zone de _Staging_ (l'index) avant de les committer ?
Pour choisir ce que l'on veut commit ou pas, histoire de ne pas surcharger git
- **_VALIDATION PROF02_**







PART 2




## B1-Git - Partie 2 : Gestion de branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- Créer une branche `fonctionnalite1`
git branch fonctionnalite1
- Lister les branches
git branch 
- Se déplacer sur la branche `fonctionnalite1`
git checkout fonctionnalite1
- Lister les branches
git branch
- Que représente l'étoile à côté des noms des branches ?
La branche ou l'on se trouve
- Créer un nouveau fichier `fichier3.md`
touch fichier3.md
- Modifier le fichier `fichier2.md`
vi fichier2.md, i,eeee, echap, :wq!
  - Comment utiliser VS Code pour qu'il nous montre les différences entre l'ancienne version de `fichier2.md` et la version courante que l'on vient d'éditer ?

- Committer ces deux modifications : "Fonctionnalité 1 - première phase"
git add fichier2.md fichier3.md, git commit -m "fonctionnalité 1 - première phase"
- Créer un nouveau fichier `fichier4.md`
touch fichier4.md
- Modifier de nouveau le fichier `fichier2.md`
echo > fichier2.md
- Committer ces deux modifications : "Fonctionnalité 1 - terminée"
git add fichier2.md fichier4.md, git commit -m "Fonctionnalité 1 - Terminée"
- **_VALIDATION PROF03_**

- Afficher la liste des fichiers du répertoire
ls
- Se déplacer sur la branche `master`
git checkout master
- Afficher la liste des fichiers du répertoire
ls
- Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?
Parce que les fichiers modifié dans la branch fonctionnalite1 sont affiché que si on est dans celle ci, les fichiers n'ont pas disparu
- Créer une nouvelle branche `fonctionnalite2`
git branch fonctionnalite2
  - Cette branche ne va pas avoir toutes les données incluses dans `fonctionnalite1`. Pourquoi ? parce que c'est pas la même branch elle n'aura que ceux dans la branche actuelle
  - Qu'aurait-il fallu faire si on avait souhaité démarrer la branche `fonctionnalite2` en intégrant les modifications récentes de `fonctionnalite1` ?
    Etre dans la branche 1 quand on l'a crée
- Se déplacer sur la nouvelle branche `fonctionnalite2`
git checkout fonctionnalite2
- Créer un nouveau fichier `fichier5.md`
touch fichier5.md
- Faire un _commit_ intégrant cette ajout : "Ajout fichier5.md"
git add fichier5.md, git commit -m "ajout fichier5.md"
- Entrer la commande `git log --oneline --decorate --graph --all` pour visualiser, sur le terminal, le graphe des _commits_ sur toutes les branches

  - Noter la « déviation » entre les deux branches, à partir de la branche `master` (schématisée sous forme de traits)
  - l'option `--all` permet de visualiser toutes les branches, pas seulement celle sur laquelle on est
  - l'option `--oneline` affiche les _commits_ sur une seule ligne
  - l'option `--graph` affiche le log sous forme de graphe
  - (utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et `Q` pour quitter)

- Installer l'extension VS Code _Git Graph_ et visualiser le graphe actuel des _commits_ à l'aide de cette extension

  - Sur cette représentation, que représente les points ?
  - Comment voit-on sur quelle branche on est actuellement ?

- **_VALIDATION PROF04_**

## Partie 3 - Fusionner des branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- On considère que la branche originale (`master` ou `main`) est la branche d'intégration, c'est-à-dire celle qui va contenir l'historique de toutes les modifications développées au fur et à mesure dans les branches annexes

- Se déplacer sur la branche `master`
git checkout master
  - Noter le changement dans l'onglet _Git Graph_
On voit le changement de branche
- On va maintenant intégrer la branche `fonctionnalite1`, qui est terminée, dans la branche d'intégration (ça s'appelle une _fusion_, ou un _merge_) : fusionner avec la branche `fonctionnalite1`
git merge fonctionnalite1
- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Fast-forward_ indiquée par la sortie de la commande ?
Les branches se rejoignent 
- On veut maintenant fusionner `fonctionnalite2` dans la branche d'intégration (`master`). Effectuer cette fusion.
git merge fonctionnalite2
- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Merge made by the ... strategy_ indiquée par la sortie de la commande ?
C'est la stratégie de merge par défaut de git mais ne peux merge qu'une branche à 2 tête
- Quelle est la différence fondamentale avec la fusion précédente ?
elle peut merge 2 tête contraiment à fast forward
- Créer une nouvelle branche `fonctionnalite3`, se déplacer dessus, et modifier le fichier `fichier1.md` en y ajoutant une ligne de texte. Committer : "Modification fichier1 pour fonctionnalité 3"
git stage fonctionnalite3, git commit -m "message"
  - Comment utiliser _Git Graph_ pour qu'il nous montre les différences entre l'ancienne version de `fichier1.md` et la version courante que l'on vient de committer ?
on clique sur le message de commit et ensuite sur le nom du fichier modifié (fichier1) et on voit deux éditeurs avec les différences entres les deux
- Repartir sur `master`, et modifier `fichier1.md` en y ajoutant aussi une ligne (différente de celle qu'on a ajoutée sur l'autre branche) ; ajouter à l'index et _commit_
fait
- Tenter de fusionner la branche `fonctionnalite3` avec `master`
Conflit entre les fichiers
  - Que se passe-t-il et pourquoi ?
La même ligne est modifiée mais différemment
- Lancer un `git status`
On branch master
Your branch is ahead of 'origin/master' by 10 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   fichier1.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   reponses.md

  - Que doit-on faire si on veut annuler la fusion en cours ? (**ne pas lancer la commande**)
git merge --abort
- On veut résoudre le conflit. Plusieurs possibilités :

  - Conserver uniquement les modifications faites dans `fonctionnalite3`
  - Conserver uniquement les modifications faites dans `master`
  - Conserver les deux modifications
  - Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement

- Git nous laisse totalement la main et ne va pas essayer d'imposer l'un de ces choix pour nous, ni nous assister dans l'application automatique de l'un d'entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

- Ouvrir le fichier en question sous VS Code

  - La chaîne `<<<<<<<<<<` marque le début du conflit
  - La chaîne `>>>>>>>>>>` marque la fin du conflit
  - La chaîne `==========` sépare les deux versions

- Éditer le fichier pour faire en sorte d'intégrer les deux modifications ; à la fin de l'édition :
accept both change
  - Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c'est-à-dire pas de `<<<<<<<<<<`, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu'il doit apparaître dans le _commit_ de fusion, avec les conflits résolus manuellement
  - Sauvegarder

- Ajouter les modification à l'index et committer
git stage fichier1.md git commit -m "conflit résoud"
- NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

- NB : les conflits de fusion sont fréquents lorsqu'on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

- Les branches créées n'ont plus de raison d'exister

  - Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d'intégration
  - On va vouloir nettoyer le dépôt en les supprimant
  - Cela ne va bien sûr pas supprimer tous les _commits_ qui y sont associés
  - Attention cependant d'éviter en général de supprimer une branche qui n'a pas encore été intégrée à la branche d'intégration, sauf si on souhaite vraiment abandonner le développement de cette branche
  - Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
  - Nouvelle tâche ? => nouvelle branche à partir d'un _commit_ de la branche d'intégration (en général le plus récent)
  - Tâche terminée ? => fusion dans la branche d'intégration et suppression de la branche

- Supprimer les trois branches `fonctionnalitex` (attention : on ne peut pas supprimer une branche sur laquelle on est)
git branch -d fonctionnalitex



## Partie 4 - Travailler avec un dépôt distant (_remote_)

- Faire un _fork_ du dépôt https://github.com/rose-line/sio1-2024-java-grpb (pas par commande Git, c'est sur l'interface GitHub)

- Cloner localement votre _fork_ (**ne pas cloner le dépôt original**)

  - Quelle est la différence entre un _fork_ et un clonage ?
  Un fork c'est une copie du dépot source vers un dépot à votre nom avec les fichiers actuels, un clonage c'est une copie du dépot sur votre machine
  - Indiquer dans quelles circonstances on voudrait _forker_ et/ou cloner un dépôt
  forker c'est pour travailler sur un dépot tout en gardant le dépot original, et cloner c'est plus pratique pour travailler sur un projet mais dans le même dépots

- Modifier le fichier `README.md` à la racine du dépôt en ajoutant une ligne quelconque
salut salut
- On veut maintenant envoyer cette modification vers le dépôt distant

  - Il faut d'abord faire un _add/commit_ local
  - Puis utiliser la commande qui « pousse » les modifs sur le dépôt GitHub (_push_)
  - Vérifier directement sur GitHub que le _push_ a bien fonctionné
ça à bel et bien fonctionné
- Trouver la commande qui affiche le nom du ou des dépôt(s) distant(s) relié(s) avec le dépôt local : cela permet de savoir si le dépôt courant est synchronisé avec un dépôt en ligne ou non
git remote -v
- On va faire un _merge_ en local puis *push* :

  - Créer une branche locale `bugfix1`, se déplacer dessus, créer un nouveau fichier `ok.java` à la racine du dépôt
  - Ajouter `ok.java` à l'index et faire un _commit_
  - Retourner sur `master`, créer le fichier `ajout.java`, ajouter à l'index et committer
  - Fusionner la branche `bugfix1` dans la branche `master`
  - Afficher le log des *commits* ; noter les emplacements des trois branches différentes, en local et en remote
  - Faire un _push_
  - Refaire un affichage du log ; `origin/master` a bougé : que représente cette branche ?
  la branche principale
  
- Étudier le résultat sur GitHub, en examinant _commits_ et branches (bouton _drop-down_ sur la page du dépôt pour voir les branches) : qu'est-ce qui est différent de la version locale ?
Qu'on est 4 commit plus loin que le dépot original
- Le bug est corrigé et intégré ; que doit-on faire de la branche `bugfix1` maintenant ?
On peut la supprimer
- **_VALIDATION PROF06_**

- Supposons que l'on veuille effectivement publier sur le _remote_ une branche sur laquelle on travaille (pour sauvegarde ou pour que d'autres puissent l'utiliser)

  - Créer une nouvelle branche `partage`
  - Aller sur la branche
  - Ajouter un fichier `partage.md`
  - L'inclure dans l'index
  - Faire un _commit_
  - _Push_
  - Que se passe-t-il ? The current branch partage has no upstream branch.
  - Exécuter la bonne commande pour sauvegarder la branche sur le remote git push --set-upstream origin partage
  - Vérifier sur GitHub que la branche apparaît bien
  
- La branche `partage` n'a pas été fusionnée avant le *push* ; on va utiliser un autre moyen offert par GitHub pour fusionner une branche en *remote* : la **_Pull Request_**

  - La _Pull Request_ est très utilisée en collaboration : elle permet à l'intégrateur du projet d'examiner les demandes de _merge_ au niveau du _remote_ avant de les accepter (ou non)

- Sur GitHub, cliquer sur le bouton _Compare & pull request_, qui apparaît directement sur la page du dépôt depuis le dernier _push_ qui a ajouté la branche (voir ci-dessus).

- À gauche, la branche d'intégration (« *base* », qui reçoit le _merge_) ; à droite, la branche à fusionner (« *compare* »)

  - On doit fusionner `partage` dans `master`
  - Attention, il faut bien choisir le repo de base qui est sur votre propre compte (pas le compte du dépôt d'origine que vous avez _forké_)
  - On peut ajouter d'autres informations : titre et commentaire de la _pull request_, et même upload de fichiers annexes, liens éventuels... Également, on peut ajouter des labels pour étiquetter la _pull request_ et lui affecter un _reviewer_, qui va officiellement être en charge
  - Valider en cliquant sur le bouton _Create pull request_

- La page résultante informe sur les branches source et cible, sur les _commits_ concernés, les fichiers qui ont été modifiés...

- On peut aussi y démarrer une conversation notamment entre l'émetteur de la _pull request_ et l'intégrateur

- On voit que l'intégrateur (possesseur du compte cible) peut accepter la _pull request_ en cliquant sur le bouton _Merge pull request_ (ou refuser en cliquant sur _Close pull request_).

- En discutant de la _pull request_, on se rend compte que certaines choses devraient être modifiées

  - Repartir en local pour effectuer une modification sur `partage.md` et ajouter `precision.md`
  - _Commit_ des deux modifs
  - _Push_
  - Observer la *pull request* : que s'est-il passé ? ça fonctionne
  - Finalement, faire le _merge_ sur la page de la _pull request_ 
  - Noter que l'interface nous propose alors de supprimer la branche devenue inutile ; supprimer la branche

- Dans un contexte de travail en collaboration sur un même dépôt, donner un _workflow_ (façon de travailler) possible qui va permettre à tous les intervenants de viser des ajouts à la branche d'intégration, d'en discuter, et ceci sans danger pour la branche d'intégration, avant que finalement l'intégrateur (probablement propriétaire du dépot) accepte les changements.
travailler sur des branches différentes avant de demander à les merge à l'intégrateur
- **_VALIDATION PROF07_**