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