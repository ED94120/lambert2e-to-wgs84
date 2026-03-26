# Lambert II étendu vers Latitude / Longitude

Accès à l’utilitaire :

https://ed94120.github.io/lambert2e-to-wgs84/

## Objet

Cet utilitaire web convertit des coordonnées en Lambert II étendu vers des coordonnées géographiques Latitude / Longitude pour la France métropolitaine.

Le code est conçu pour fonctionner directement dans un navigateur web.

## Fonction principale

L’application permet de :

- saisir des coordonnées X et Y en Lambert II étendu
- convertir ces coordonnées en Latitude / Longitude
- utiliser une grille de transformation géodésique `.gsb`
- comparer le résultat calcule avec une latitude et une longitude de référence
- calculer les écarts en mètres :
- Delta X
- Delta Y
- DeltaDistance
- copier la latitude calculée dans le presse papier
- copier la longitude calculée dans le presse papier
- choisir le séparateur décimal affiche :
- point
- virgule

## Système géodésique utilise

Le système source est :

- Lambert II étendu
- datum historique NTF

Le système de sortie est :

- Latitude / Longitude en WGS84

Pour améliorer la précision, la transformation s’appuie sur une grille `.gsb` chargée dans le navigateur avec Proj4js.

Cette approche permet d’obtenir un résultat plus proche des outils de référence qu’une simple transformation `towgs84` a 3 paramètres.

## Contenu du dépôt

Le dépôt contient en principe :

- `index.html`
- `ntf_r93.gsb`
- `README.md`

## Fonctionnement général

1. l’utilisateur saisit X et Y
2. le programme vérifie que les valeurs sont numériques
3. le programme convertit les coordonnées Lambert II étendu en Latitude / Longitude
4. si une latitude ou une longitude de comparaison est saisie, le programme calcule les écarts
5. les deltas sont affiches en mètres

## Logique des deltas

Les deltas sont calcules selon la convention suivante :

- Delta X = calcule - compare
- Delta Y = calcule - compare

Interprétation :

- Delta X positif : le point calcule est plus a l’est
- Delta X négatif : le point calcule est plus a l’ouest
- Delta Y positif : le point calcule est plus au nord
- Delta Y négatif : le point calcule est plus au sud

Comportement :

- si seule la latitude de comparaison est renseignée, seul Delta Y est calcule
- si seule la longitude de comparaison est renseignée, seul Delta X est calcule
- si les deux sont renseignées, Delta X, Delta Y et DeltaDistance sont calcules

## Saisie des nombres

Les champs d entrée acceptent :

- le point comme séparateur décimal
- la virgule comme séparateur décimal

Le programme convertit automatiquement la saisie dans un format exploitable pour le calcul.

## Affichage

Le séparateur décimal des résultats peut être choisi dans une liste déroulante :

- point
- virgule

Ce réglage agit sur :

- Latitude
- Longitude
- Delta X
- Delta Y
- DeltaDistance

## Boutons disponibles

- `Convertir` : lance la conversion
- `Effacer` : efface toutes les zones
- `Copier Latitude` : copie la latitude calculée
- `Copier Longitude` : copie la longitude calculée

## Bibliothèque utilisée

Le projet utilise :

- `Proj4js`

Cette bibliothèque assure :

- la définition des projections
- le chargement de la grille `.gsb`
- la conversion des coordonnées

## Limites et précision

La précision dépend de plusieurs facteurs :

- qualité de la coordonnée source
- exactitude du système d’origine
- qualité de la grille utilisée
- méthode géodésique employée par l’outil de comparaison

Cet utilitaire est destiné a fournir une conversion géographique précise pour des usages techniques courants.

Pour des usages critiques, il est recommandé de vérifier aussi :

- la qualité de la donnée source
- le système géodésique réel du fichier d’origine
- la cohérence avec les outils géodésiques de référence

## Publication

Ce projet est publié via GitHub Pages.

La page publique est accessible à l’adresse indiquée en tête de ce document.

