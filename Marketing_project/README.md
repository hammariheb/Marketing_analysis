# Analyse des Campagnes Marketing
## Introduction
Ce projet vise à analyser l'efficacité des récentes campagnes marketing afin de comprendre leurs performances et de proposer des solutions basées sur les données.

## Objectif Général:
Faire une étude exploratoire afin d'identifier les problèmes et suggérer des améliorations.

## Nettoyage et Transformation des Données
Nettoyage des Noms de Colonnes :

Standardiser et nettoyer les noms de colonnes pour une meilleure lisibilité et manipulation.
Transformation de Colonnes Sélectionnées au Format Numérique :

Transformer la colonne Income en format float.
## Analyse Exploratoire des Données (EDA)
Valeurs Nulles et Valeurs Aberrantes
Valeurs Nulles :

Identifier les caractéristiques contenant des valeurs nulles :
La caractéristique Income contient 24 valeurs nulles.
Visualiser cette caractéristique pour identifier la meilleure stratégie d'imputation :
La plupart des revenus sont distribués entre 0 et 100,000 euros, avec quelques valeurs aberrantes.
Imputer les valeurs nulles avec la valeur médiane pour éviter les effets des valeurs aberrantes sur la valeur d'imputation.
Valeurs Aberrantes :

Identifier les caractéristiques contenant des valeurs aberrantes :
Plusieurs caractéristiques contiennent des valeurs aberrantes, mais celles qui indiquent probablement des erreurs de saisie de données sont Year_Birth <= 1900.
Imputer les valeurs nulles dans Income en utilisant la valeur médiane pour éviter le biais de la moyenne dû aux valeurs aberrantes.
Supprimer les lignes où Year_Birth <= 1900.
Transformations de Variables
Vérifier les Types de Données :
La colonne Dt_Customer doit être transformée au format datetime.
Transformer Dt_Customer en Format Datetime :
Ingénierie des Caractéristiques
Examiner une liste des noms de caractéristiques pour en créer de nouvelles :
Le nombre total de personnes à charge dans le foyer (Dependents) peut être calculé à partir de la somme de Kidhome et Teenhome.
L'année de fidélisation client (Year_Customer) peut être calculée à partir de Dt_Customer.
Le montant total dépensé (TotalMnt) peut être calculé à partir de la somme de toutes les caractéristiques contenant le mot-clé Mnt.
Le nombre total d'achats (TotalPurchases) peut être calculé à partir de la somme de toutes les caractéristiques contenant le mot-clé Purchases.
Le nombre total de campagnes acceptées (TotalCampaignsAcc) peut être calculé à partir de la somme de toutes les caractéristiques contenant les mots-clés Cmp et Response (la dernière campagne).
Détection de Modèles et d'Anomalies
Identifier les Corrélations entre les Caractéristiques :

Les corrélations positives entre les caractéristiques apparaissent en rouge, les corrélations négatives apparaissent en bleu, et aucune corrélation apparaît en gris dans la heatmap ci-dessous.

À partir de cette heatmap, nous pouvons observer les clusters suivants de caractéristiques corrélées :

Cluster "Haut Revenu" :

Le montant dépensé (TotalMnt et autres caractéristiques Mnt) et le nombre d'achats (TotalPurchases et autres caractéristiques Num...Purchases) sont positivement corrélés avec Income.
Les achats en magasin, sur le web ou via le catalogue (NumStorePurchases, NumWebPurchases, NumCatalogPurchases) sont positivement corrélés avec Income.
Cluster "Avoir des Enfants et des Adolescents" :

Le montant dépensé (TotalMnt et autres caractéristiques Mnt) et le nombre d'achats (TotalPurchases et autres caractéristiques Num...Purchases) sont négativement corrélés avec Dependents (avec un effet plus fort des enfants par rapport aux adolescents).
Les achats de promotions (NumDealsPurchases) sont positivement corrélés avec Dependents (enfants et/ou adolescents) et négativement corrélés avec Income.
Cluster "Campagnes Publicitaires" :

L'acceptation des campagnes publicitaires (AcceptedCmp et Response) est fortement positivement corrélée entre elles.
Une faible corrélation positive des campagnes publicitaires est observée avec le cluster "Haut Revenu", et une faible corrélation négative est observée avec le cluster "Avoir des Enfants et des Adolescents".
Anomalies :

De manière surprenante, le nombre de visites du site web au cours du dernier mois (NumWebVisitsMonth) n'est pas corrélé avec une augmentation du nombre d'achats sur le web (NumWebPurchases).
Au lieu de cela, NumWebVisitsMonth est positivement corrélé avec le nombre d'achats de promotions (NumDealsPurchases), suggérant que les promotions sont un moyen efficace de stimuler les achats sur le site web.
Visualisations
Illustrer l'Effet des Hauts Revenus sur les Dépenses :

Limiter le revenu à moins de 200000 pour supprimer les valeurs aberrantes.
Illustrer l'Effet Négatif d'Avoir des Enfants et des Adolescents sur les Dépenses :

Illustrer l'Effet Positif d'Avoir des Enfants et des Adolescents sur le Nombre d'Achats de Promotions :

Illustrer l'Effet Positif du Revenu et Négatif d'Avoir des Enfants et des Adolescents sur l'Acceptation des Campagnes Publicitaires :

Limiter le revenu à moins de 200000 pour supprimer les valeurs aberrantes.
Investigation de l'Anomalie :

Le nombre de visites du site web au cours du dernier mois n'est pas positivement corrélé avec le nombre d'achats sur le web.
Au lieu de cela, il est positivement corrélé avec le nombre d'achats de promotions, suggérant que les promotions sont un moyen efficace de stimuler les achats sur le site web.

## Conclusion
Cette analyse des campagnes marketing a révélé plusieurs points clés et possibilités d'amélioration. Les données ont été soigneusement nettoyées et transformées pour garantir leur qualité, notamment en standardisant les noms de colonnes et en convertissant Income en format numérique. Les valeurs nulles dans Income ont été imputées avec la médiane pour éviter l'influence des valeurs aberrantes, et les enregistrements incohérents, tels que Year_Birth inférieur ou égal à 1900, ont été supprimés. L'ingénierie des caractéristiques a permis de créer des variables significatives comme Dependents, Year_Customer, TotalMnt, TotalPurchases, et TotalCampaignsAcc. Les corrélations entre les caractéristiques ont été analysées pour identifier des clusters significatifs, mettant en lumière des modèles tels que la corrélation positive entre les revenus et les dépenses, ainsi que l'effet des enfants et des adolescents sur les achats promotionnels. Enfin, des anomalies comme la corrélation positive entre les visites de sites web et les achats promotionnels ont été mises en évidence, suggérant que les promotions sont un moyen efficace de stimuler les achats en ligne. Ces insights fournissent une base solide pour optimiser les futures campagnes marketing et maximiser leur efficacité.
