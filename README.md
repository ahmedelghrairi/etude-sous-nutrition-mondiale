# Sous-nutrition dans le monde : une étude FAO (2013-2017)

Rejoindre une équipe de chercheurs de la FAO pour continuer une étude sur l'alimentation mondiale, avec un objectif précis : comprendre pourquoi la sous-nutrition persiste alors que la production alimentaire mondiale semble suffisante. Marc, chercheur en économie de la santé, m'a confié la partie historique de l'analyse, 2013 à 2017, à partir de quatre sources FAO à nettoyer, harmoniser et croiser.

Étude de cas complète, avec démarche et recommandations : [voir sur mon portfolio](https://ahmedelghrairi.github.io/projets/sous-nutrition.html)

## Contenu du dépôt

- `notebook_sous_nutrition.ipynb` : nettoyage des quatre sources et l'ensemble des analyses
- `data/` : les quatre fichiers sources (population, disponibilité alimentaire, aide alimentaire, sous-nutrition)
- `requirements.txt` : bibliothèques utilisées

## Les données

Quatre fichiers FAO, chacun avec sa propre unité à harmoniser avant de pouvoir les croiser : la population par pays et par année (en milliers, ramenée en individus), la disponibilité alimentaire par pays et par produit sur 18 colonnes (kcal, kg, grammes de protéines et de matières grasses par personne, plus les volumes en milliers de tonnes convertis en kg), l'aide alimentaire par pays, année et produit (en tonnes, ramenée en kg), et la sous-nutrition par période de trois ans (les valeurs "<0,1" ont été interprétées comme quasi nulles et ramenées à 0 pour permettre les calculs).

## La démarche

Chaque source est explorée avant nettoyage : dimensions, types de colonnes, décompte des valeurs présentes. Les valeurs manquantes de la disponibilité alimentaire sont remplacées par 0, une donnée absente signifiant ici qu'un pays ne consomme pas ce produit plutôt qu'une non-réponse à traiter à part.

Les jointures se font sur la colonne Zone, avec une vigilance particulière sur les années : la sous-nutrition est mesurée par période de trois ans quand la population est annuelle, une jointure directe sur l'année aurait donc perdu des lignes. La période 2016-2018 est retenue comme référence de l'année 2017, cohérente avec la population de cette même année.

## Quelques résultats

- 535,7 millions de personnes en sous-nutrition en 2017, soit 7,1 % de la population mondiale.
- La disponibilité alimentaire mondiale permettrait théoriquement de nourrir 8,37 milliards de personnes, davantage que la population mondiale de l'époque : la faim n'est pas un problème de production globale.
- Les produits d'origine végétale, à eux seuls, suffiraient à nourrir 6,9 milliards de personnes, 92 % de la population mondiale.
- Sur la disponibilité intérieure totale (9,85 billions de kg), 42,75 % des céréales disponibles vont à l'alimentation humaine contre 36,29 % à l'alimentation animale, un partage qui pèse directement sur la disponibilité réelle pour les populations les plus vulnérables.
- Haïti (48,3 %) et la Corée du Nord (47,2 %) affichent les taux de sous-nutrition les plus élevés en 2017, très loin devant l'Afghanistan (28,9 %), dixième du classement.
- La corrélation entre disponibilité alimentaire par habitant et taux de sous-nutrition est de -0,59, une liaison modérée mais incomplète : la disponibilité seule n'explique pas tout, la répartition, les pertes et l'accès jouent un rôle tout aussi déterminant.
- Cas de la Thaïlande sur le manioc : une production élevée, majoritairement exportée, qui contribue peu à l'alimentation nationale malgré un taux de sous-nutrition du pays de 8,96 %, un exemple concret que production et sécurité alimentaire nationale ne se confondent pas.

## Outils

Python, pandas pour l'analyse, matplotlib pour les visualisations.

Ahmed El Ghrairi, 2026.
