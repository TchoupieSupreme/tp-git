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