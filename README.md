# Modélisation non paramétrique par des fonctions B-spline

Projet de modélisation statistique - Comparaison de méthodes non paramétriques (B-splines, P-splines) pour prédire un prix immobilier à partir de variables non linéaires.

## Le projet

Étude sur le jeu de données `WarsawApts` (prix de vente d'appartements à Varsovie, Pologne), visant à prédire le prix au m² (`areaPerMzloty`) à partir de :

* La date de construction
* La surface
* Le nombre de pièces et l'étage
* Le district (variable qualitative)

L'objectif est de montrer, via l'analyse des résidus d'un modèle linéaire classique, que la relation entre ces variables n'est pas linéaire et de comparer plusieurs approches non paramétriques pour mieux la modéliser.

## Méthodes utilisées

* **Partie 1 - Modèles univariés** : ajustement par B-splines (`bs()`), choix du nombre de noeuds K par validation croisée à 5 couches, comparaison avec la régression polynomiale et les P-splines (pénalisées)
* **Partie 2 - Modèles multivariés** : modèles additifs généralisés (GAM) avec plusieurs prédicteurs, sélection de la dimension de base k par validation croisée
* **Partie 3 - Variable qualitative × quantitative** : test d'interaction entre le district et l'année de construction, comparaison de modèles emboîtés par test ANOVA et critère AIC, sélection du modèle final par la règle de Ruppert et al. (2002)

Toutes les comparaisons de modèles s'appuient sur l'erreur quadratique moyenne (MSE) et l'AIC.

## Résultat principal

Le modèle final retenu combine une interaction entre le district et l'année de construction (base P-spline `"ps"`) avec un effet global et non linéaire de la surface, validé par test ANOVA et vérification des résidus (QQ-plot, homoscédasticité).

## Structure du projet

* `Projet_splines.Rmd` : script R Markdown avec l'ensemble des analyses
* `Projet_splines.pdf` : rapport complet du projet en PDF

## Lancer l'analyse

1. Cloner le projet ou télécharger les fichiers
2. Installer les packages nécessaires

```r
install.packages(c("HRW", "dplyr", "mgcv", "splines", "knitr", "ggplot2"))
```

3. Ouvrir `Projet_splines.Rmd` dans RStudio et compiler (Knit)

## Auteur

Clara GAMBARDELLO
Projet de Modélisation non paramétrique (2025)
