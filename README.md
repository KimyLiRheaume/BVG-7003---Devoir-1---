# BVG-7003 : Devoir 1 - CannaGenix

## Cas d'utilisation
Cet outil interactif est conçu pour analyser les différences d'expression génique des marqueurs spécifiques REM16 et FT1 afin de déterminer le sexe des plantes de cannabis. Grâce à une interface conviviale, les chercheurs peuvent identifier rapidement et efficacement le sexe des plantes en comparant les niveaux d'expression de ces marqueurs entre les échantillons mâles et femelles. 

L'application permet aux utilisateurs de charger facilement leurs propres fichiers CSV ou d'utiliser un jeu de données par défaut, offrant ainsi une solution flexible pour le sexage des plantes.

## Données d'entrée
L'application nécessite les éléments suivants :
- **Jeu de données d'expression génique** : un fichier CSV que les utilisateurs peuvent charger. Ce fichier doit respecter les conditions suivantes :
  - **Format** : Le fichier doit être au format CSV, avec les gènes en lignes et les échantillons en colonnes.
  - **Colonnes** : Chaque colonne doit représenter un échantillon et inclure les niveaux d'expression des gènes pour chaque échantillon.
  - **Lignes** : Les lignes doivent contenir les IDs de gènes (par exemple, `LOC115699937` pour REM16 et `LOC115696989` pour FT1). Les utilisateurs doivent s'assurer que les IDs de gènes dans leur fichier correspondent à ceux utilisés dans l'application.

## Résultats
L'application génère les résultats interactifs suivants :

-**Un tableau** : présentant le nom des échantillons, le niveau d'expression du marqueur REM16 et de FT1 et le sexe de l'échantillon.
- **Graphiques d'expression génique** :
  - **Expression de REM16 par sexe** : Un boxplot montrant les niveaux d'expression du marqueur REM16 pour les échantillons mâles et femelles.
  - **Expression de FT1 par sexe** : Un boxplot représentant les niveaux d'expression du marqueur FT1 entre les sexes.
  - **Expression combinée de REM16 et FT1 par sexe** : Un boxplot combiné illustrant les niveaux d'expression des deux marqueurs pour chaque sexe.
  
  Les figures générées peuvent être téléchargées en format HTML.
  
## Protocole pour la Détermination du Sexe
Un protocole détaillé pour la détermination du sexe des plantes de cannabis est fourni avec ce projet. Ce protocole décrit les étapes utilisées pour extraire l'ARN et analyser les niveaux d'expression des marqueurs géniques REM16 et FT1.

## Instructions
1. **Charger l'application :** Ouvrez le fichier "20241104BVG_7003_Devoir1KLR" RMarkdown dans RStudio présent dans le répertoire appelé "files_data".
2. **Exécuter l'application :** Knit le Document :** Cliquez sur "Knit" pour lancer l'interface Shiny.
3. **Charger des données :** Glissez-déposez votre fichier CSV ou cliquez sur "Charger le jeu de données par défaut" pour utiliser un fichier préétabli.
4. **Générer des graphiques :** Cliquez sur "Générer Graphiques" pour visualiser les résultats.
5. **Télécharger les résultats :** Utilisez les boutons fournis pour télécharger les tableaux et graphiques au format HTML.

## Dépendances
Assurez-vous d'avoir installé les bibliothèques R suivantes :

```r
install.packages(c("shiny", "shinythemes", "ggplot2", "reshape2", "ggpubr", "knitr", "kableExtra", "tidyverse", "htmlwidgets", "plotly", "DT"))
```

## Contenu des documents de ce GitHub :
-Tableaux : Tableau de résultats attendus obtenus à partir du jeu de données par défaut
-Files_Data : Jeu de données par défaut en format zip et le script permettant d'ouvrir l'application,
-Graphiques générés à partir du jeu de données par défaut : Graphique 1 : Expression du marqueur de REM16, Graphique 2 : Expression du marqueur de FT1, Graphique 3 : Combiné de l'expresion de REM16 et FT1






