# BVG-7003---Devoir-1---Genefinder
Outil pour identifier des gènes spécifiques à partir de données transcriptomiques
# BVG-7003 : Devoir 1 - CannabisSexDeterminator

## Cas d'utilisation
Cet outil permet d'analyser l'expression des marqueurs géniques spécifiques (REM16 et FT1) pour déterminer le sexe des plantes de cannabis. Il compare les niveaux d'expression entre les échantillons mâles et femelles, fournissant ainsi une méthode fiable pour le sexage des plantes.

## Données d'entrée
Le script nécessite les éléments suivants :
- **Jeu de données d'expression génique** : un fichier CSV nommé `2_Data_RNASeq_Cannabis_Sex.csv`, contenant des données d'expression pour les gènes d'intérêt (REM16 et FT1). Le fichier doit avoir les gènes en lignes et les échantillons en colonnes.

## Résultats
Le script génère les résultats suivants :
- **Graphiques d'expression génique** :
  - Boxplot des niveaux d'expression de REM16 par sexe.
  - Boxplot des niveaux d'expression de FT1 par sexe.
  - Boxplot combiné des niveaux d'expression de REM16 et FT1 par sexe.
- Les figures générées seront sauvegardées dans le répertoire courant avec les noms suivants :
  - `REM16_expression_by_sex.png`
  - `FT1_expression_by_sex.png`
  - `Combined_expression_by_sex.png`

## Instructions
1. **Charger les bibliothèques nécessaires** :
   Assurez-vous d'avoir installé les bibliothèques R nécessaires (`ggplot2`, `reshape2`) avant d'exécuter le script.

   ```r
   install.packages(c("ggplot2", "reshape2"))
2. Charger les données : Préparez votre fichier CSV (2_Data_RNASeq_Cannabis_Sex.csv) et placez-le dans le même répertoire que le script.
3. Exécuter le script : Copiez et collez le script R suivant dans votre environnement R et exécutez-le : # Charger les bibliothèques nécessaires
library(ggplot2)
library(reshape2)

# Charger les données
data <- read.csv("2_Data_RNASeq_Cannabis_Sex.csv", row.names = 1)

# Extraire les données d'expression pour REM16 et FT1
rem16_data <- data["LOC115699937", ]
ft1_data <- data["LOC115696989", ]

# Créer un DataFrame pour les graphiques
expression_data <- data.frame(
  Sample = colnames(data),
  REM16 = as.numeric(rem16_data),
  FT1 = as.numeric(ft1_data),
  Sex = ifelse(grepl("XX", colnames(data)), "Female", "Male")
)

# Graphiques d'expression
ggplot(expression_data, aes(x = Sex, y = REM16)) +
  geom_boxplot() +
  ggtitle("Expression de REM16 par sexe") +
  theme_minimal()
ggsave("REM16_expression_by_sex.png")

ggplot(expression_data, aes(x = Sex, y = FT1)) +
  geom_boxplot() +
  ggtitle("Expression de FT1 par sexe") +
  theme_minimal()
ggsave("FT1_expression_by_sex.png")

data_melted <- melt(expression_data, id.vars = c("Sample", "Sex"), measure.vars = c("REM16", "FT1"))
ggplot(data_melted, aes(x = Sex, y = value, fill = variable)) +
  geom_boxplot() +
  ggtitle("Expression combinée de REM16 et FT1 par sexe") +
  theme_minimal()
ggsave("Combined_expression_by_sex.png")

4. Interpréter les résultats :
Examinez les fichiers d'image générés pour visualiser les niveaux d'expression des marqueurs REM16 et FT1 entre les sexes.
Les boxplots vous aideront à comparer facilement les différences d'expression entre les échantillons mâles et femelles.
