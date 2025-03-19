Exercice1:
1.1 Commandes utilisées :

# Création d'un dépôt Git
mkdir tp3
cd tp3
git init

# Création du fichier README.md
echo "# Projet d'exercice" > README.md
echo "Version initiale du projet" >> README.md
git add README.md
git commit -m "Premier commit : création du README"

# Création et affichage des branches
git branch feature-1
git branch feature-2
git branch  # Vérifier la liste des branches

# Déplacement sur feature-1
git checkout feature-1

# Modification du README
echo "Modification dans feature-1" >> README.md
git add README.md
git commit -m "Ajout d'une modification dans feature-1"

# Retour sur main
git checkout main
cat README.md  
1.2 Réponses aux questions :
Que se passe-t-il si vous essayez de supprimer une branche sur laquelle vous êtes ?
→ Git affiche une erreur :


error: Cannot delete branch 'feature-1' checked out at ...
Il faut changer de branche avant de la supprimer avec :


git checkout main
git branch -d feature-1
Comment voir les différences entre les branches main et feature-1 ?


git diff main..feature-1












Exercice 2 : Fusion simple
2.1 Commandes utilisées :

# Création et passage sur la branche dev
git checkout main
git branch dev
git checkout dev

# Création du fichier notes.txt
echo "Notes importantes" > notes.txt
git add notes.txt
git commit -m "Ajout du fichier notes.txt"

# Retour sur main et fusion
git checkout main
git merge dev

# Vérification
ls  

# Suppression de la branche dev
git branch -d dev







 Exercice 3 : Gestion des conflits
3.1 Commandes utilisées :

# Modification du README dans main
git checkout main
echo "# Projet d'exercice - Version Main" > README.md
git commit -am "Modification du README dans main"

# Création de conflit-test et modification du README
git checkout -b conflit-test
echo "# Projet d'exercice - Version Test" > README.md
git commit -am "Modification du README dans conflit-test"

# Retour sur main et tentative de fusion
git checkout main
git merge conflit-test

Édite README.md pour obtenir :

# Projet d'exercice - Version Main et Test
Puis termine la fusion :


git add README.md
git commit -m "Résolution du conflit entre main et conflit-test"







 Exercice 4 : Rebase
4.1 Commandes utilisées :

# Création de la branche feature-rebase
git checkout -b feature-rebase

# Ajout d'un fichier et commits
echo "Contenu du fichier feature" > feature.txt
git add feature.txt
git commit -m "Ajout du fichier feature.txt"
echo "Deuxième modification" >> feature.txt
git commit -am "Deuxième commit sur feature-rebase"

# Modifications sur main
git checkout main
echo "Mise à jour dans main" > update.txt
git add update.txt
git commit -m "Ajout d'une mise à jour dans main"

# Rebase de feature-rebase sur main
git checkout feature-rebase
git rebase main

# Vérification de l'historique
git log --oneline --graph --all




 Exercice 5 : Branches et historique
5.1 Commandes utilisées :

# Création des branches
git checkout main
git branch feature-a
git branch feature-b
git branch feature-c

# Travail sur chaque branche
git checkout feature-a
echo "Travail sur A" > a.txt
git add a.txt
git commit -m "Ajout de A"

git checkout feature-b
echo "Travail sur B" > b.txt
git add b.txt
git commit -m "Ajout de B"

git checkout feature-c
echo "Travail sur C" > c.txt
git add c.txt
git commit -m "Ajout de C"

# Fusion des branches dans main
git checkout main
git merge feature-a
git merge feature-b
git merge feature-c

# Affichage de l’historique
git log --all --decorate --oneline --graph
git branch -v
git branch --merged
git branch --no-merged





 Rendu du TP
6.1 Commandes utilisées :

# Création du fichier reponses.md
nano reponses.md  # Ajouter toutes les réponses et enregistrer

# Ajout et commit
git add reponses.md
git commit -m "Solution TP3"

# Ajout du dépôt distant
git remote add origin <URL_GIT>

# Push de la branche principale avec forçage
git push origin HEAD --force

# Push des autres branches
git push origin conflit-test
git push origin feature-rebase
git push origin feature-a
git push origin feature-b
git push origin feature-c
