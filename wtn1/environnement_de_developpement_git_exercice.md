### Projet : Bibliothèque Open Source

#### Objectif

Créer une bibliothèque open source qui permet de gérer une collection de livres. Les utilisateurs pourront ajouter, modifier et supprimer des livres, ainsi que collaborer sur le projet via des branches et des pull requests.

#### Étapes du Projet

1. **Création du Projet**
   - Utilisez des commandes bash pour créer un dossier nommé `bibliotheque` et naviguez à l'intérieur.
   - Créez un fichier `README.md` pour décrire le projet et son objectif.

   ```bash
   mkdir bibliotheque
   cd bibliotheque
   touch README.md
   echo "# Bibliothèque Open Source" >> README.md
   ```

2. **Initialisation du Repository Git**
   - Initialisez un repository Git dans le dossier `bibliotheque`.
   - Ajoutez le fichier `README.md` au repository et effectuez un premier commit.

   ```bash
   git init
   git add README.md
   git commit -m "Initial commit: ajout du README"
   ```

3. **Création de la Structure de Dossiers**
   - Créez un dossier `livres` pour stocker les fichiers des livres.
   - À l'intérieur de `livres`, créez un fichier pour chaque livre (par exemple, `livre1.md`, `livre2.md`, etc.) avec des informations comme le titre, l'auteur, et une brève description.

   ```bash
   mkdir livres
   touch livres/livre1.md
   echo "Titre: Le Petit Prince\nAuteur: Antoine de Saint-Exupéry\nDescription: Un conte poétique et philosophique." >> livres/livre1.md
   ```

4. **Ajout de Livres et Modifications**
   - Ajoutez plusieurs fichiers de livres avec des informations variées.
   - Modifiez un fichier de livre pour corriger une erreur ou ajouter des informations.

   ```bash
   touch livres/livre2.md
   echo "Titre: 1984\nAuteur: George Orwell\nDescription: Un roman dystopique sur un futur totalitaire." >> livres/livre2.md
   git add livres/livre1.md livres/livre2.md
   git commit -m "Ajout de livres"
   ```

5. **Création d'une Branche pour une Nouvelle Fonctionnalité**
   - Créez une branche nommée `ajout-auteurs` pour ajouter des informations sur les auteurs.
   - Modifiez les fichiers de livres pour inclure une section sur l'auteur.

   ```bash
   git checkout -b ajout-auteurs
   echo "Biographie: Antoine de Saint-Exupéry était un écrivain et aviateur français." >> livres/livre1.md
   git add livres/livre1.md
   git commit -m "Ajout de la biographie de l'auteur pour Le Petit Prince"
   ```

6. **Pull Request et Collaboration**
   - Poussez la branche `ajout-auteurs` vers GitHub.
   - Créez une pull request pour fusionner les modifications dans la branche principale.
   - Invitez un camarade à examiner votre pull request et à faire des commentaires.

7. **Résolution de Conflits**
   - Pendant que vous travaillez sur la branche `ajout-auteurs`, un camarade modifie le même fichier dans la branche principale.
   - Lorsque vous essayez de fusionner, un conflit se produit. Résolvez le conflit en choisissant les modifications appropriées.

   ```bash
   git checkout main
   git pull origin main
   git merge ajout-auteurs
   # Résoudre les conflits dans le fichier concerné
   git add livres/livre1.md
   git commit -m "Résolution de conflit"
   ```

8. **Mise en Place d'une Pipeline CI/CD**
   - Configurez un fichier de configuration pour une pipeline CI/CD (par exemple, avec GitHub Actions) qui vérifie la syntaxe des fichiers markdown à chaque push.
   - Créez un fichier `.github/workflows/ci.yml` avec une configuration de base.

   ```yaml
   name: CI

   on: [push]

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - name: Vérifier le code
           run: |
             echo "Vérification des fichiers markdown..."
             # Ajoutez des commandes pour vérifier la syntaxe des fichiers markdown
   ```
