---
title: Créer une base de données relationnelle
date: 1er semestre 2022-2023
author: Sébastien Biay
---

Plan :

1. [Introduction](#t1)
	1. [À quoi sert une base de données ? ](#t1-1)
	2. [Principe fondamental ](#t1-2)
	3. [Premiers pas : trier et filtrer des données ](#t1-3)
2. [Concevoir une nouvelle base de données](#t2)
	1. [Récolter des images dans les collections numériques ](#t2-1)
	2. [Élaborer un modèle conceptuel de données ](#t2-2)
	3. [Éditorialiser les données ](#t2-3)
	4. [Créer une table secondaire ](#t2-4)

[comment]: <> (FINET)


<a id='t1'/>

# Introduction
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## À quoi sert une base de données ? 

### <2>

- Traiter des données en masse
- Les exploiter : statistiques
- Les publier : partager les données de la recherche
- Les visualiser : collections virtuelles, cartographies, diagrammes


<a id='t1-2'/>

## Principe fondamental 

### <3>

Beaucoup de données sont exposées sur le web sous la forme de **documents** au format **Json**, comme les ouvrages numérisés sur Gallica (un exemple [**ici**](https://gallica.bnf.fr/iiif/ark:/12148/btv1b60000317/manifest.json)).

Mais la pierre angulaire du monde des bases de données, c'est le **modèle tabulaire**.


<a id='t1-3'/>

## Premiers pas : trier et filtrer des données 

### <4>

On démarre avec des données très simples à télécharger [**ici**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=278086)

Un tableau présente trois éléments :

1. **Attributs** : chaque colonne est un « attribut »
2. **Enregistrements** : chaque ligne est un « enregistrement »
3. **Valeurs** : une valeur est l'information correspondant à un attribut et à un enregistrement


### <5>

La puissance du tableau réside notamment dans la possibilité de **trier selon un ou plusieurs attributs**

**Attention !** Avant de trier, on doit s'assurer de ne trier que les valeurs et pas les **étiquettes des colonnes** (leur titre).

- Dans le menu principal : **Données** > Trier > Option
- Vérifier que « La plage contient des étiquettes de colonne » est **bien coché**


### <6>

Ajoutons un attribut : la **période** de spécialisation des personnes

Il comporte quatre valeurs possibles :

1. antique
2. médiévale
3. moderne
4. contemporaine


### <7>

Si je veux trier les modernistes par ordre alphabétique, je dois appliquer un tri à plusieurs critères :

- Dans le menu principal : **Données** > Trier
- **Critères de tri** :
	- Clé de tri 1 : Période
	- Clé de tri 2 : Nom


### <8>

Si maintenant je veux appliquer un **filtre** pour ne visualiser que les enregistrements ayant comme attribut « Période » et comme valeur « médiévale »

- Dans le menu principal : **Données** > Autofiltre
- Cliquer sur le menu de l'attribut « Période »
- Sélectionner la valeur pertinente


<a id='t2'/>

# Concevoir une nouvelle base de données
[comment5]: <8> (TITRE1)


<a id='t2-1'/>

## Récolter des images dans les collections numériques 

### <9>

Nous allons concevoir une base de données sur le chat dans l'histoire de l'art. Chacun-e va remplir une mission de son choix (liste [**ici**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=278106)) :

1. Fouiller des collections numériques en utilisant les **filtres ou facettes**, pour récolter **5 œuvres**
2. Repérer le **permalien** (s'il existe) : une URL courte qui se termine par un identifiant pérenne
3. Télécharger une image (si possible !)

Il peut être utile de télécharger l'extension pour Firefox [**Dezoomify**](https://addons.mozilla.org/en-US/firefox/addon/dezoomify/) pour télécharger en HD si le site le ne propose pas.

[comment7]: <9> (Exemple d'une recherche dans les collections du Met avec le mot-clé « cat », puis le filtre sur la période 1400-1600.)

[comment8]: <9> (L'URL contient dans sa chaîne de requêtes les arguments de ma recherche)

[comment9]: <9> (Le permalien est court)

[comment10]: <9> (British Museum : cliquer sur Use this image)


### <10>

Ce qu'il faut faire avec les données :

1. Ajouter les permaliens dans le tableau partagé [**base.ods**](https://docs.google.com/spreadsheets/d/1jB7TmDyQ3jfdU1t5gppX3tuWLvry1_13vn-0OlHHLoc/edit#gid=87305927)

2. Renommer les images téléchargées par l'identifiant de l'item (`01.jpg`, `02.jpg`)

3. Placer le fichier de l'image dans le dossier virtuel du Moodle [**envoyer-images-drive**](https://pedag.u-picardie.fr/moodle/upjv/mod/url/view.php?id=278088)


<a id='t2-2'/>

## Élaborer un modèle conceptuel de données 

### <11>

Le but de cette base de données est d'**analyser l'iconographie du chat à travers les époques de l'art**.

Quels **attributs** seraient nécessaires pour décrire les objets que l'on a récoltés et les représentations du chat qu'ils proposent ?

En bref, combien de **colonnes** avec quels intitulés faut-il ajouter à notre tableau pour cela ?


<a id='t2-3'/>

## Éditorialiser les données 

### <12>

Il faut maintenant commencer à renseigner les colonnes.

Prenons la **date de création** des œuvres.

Par exemple « 1750-1800 (circa) (circa) » pour [**cette œuvre**](https://www.britishmuseum.org/collection/object/A_1999-1202-0-4-19).

Pour rendre mes enregistrements triables par date, il faut décomposer l'information en trois attributs :

1. Date de début
2. Date de fin
3. circa ?


### <13>

Les valeurs que contiendra notre tableau sont de trois types :

1. Texte (ou chaînes de caractères)
2. Nombres
3. Booléens[^1] : type « vrai »/« faux »

[^1]: Du nom de l'inventeur de ce type de variable : George Boole (1815-1864).


### <14>

Passons au **lieu de conservation** des œuvres

Remplir à l'avenant la colone « Lieu de conservation » conduit immanquablement à écrire différemment le même nom, et donc à brouiller les données.

**Comment s'assurer que l'on renseigne toujours de la même manière le même nom ?**

Il faut des méthodes pour être sûr que la saisie des données soit homogène tout au long du travail.


### <15>

**Niveau de sécurité n^o^ 1**

Copier-coller plutôt que saisir les informations manuellement.

Pour rechercher dans la colonne « Lieu de conservation » si le nom à saisir existe déjà :

- Sélectionner toute la colonne en faisant un **clic gauche sur la lettre** de cette colonne
- **Ctrl ou Cmd + H**
- Cocher **Sélection active seulement**
- Cliquer sur **Rechercher le suivant**


### <16>

**Niveau de sécurité n^o^ 2**

Faire appel à un **référentiel d'autorités**

La BnF est particulièrement soucieuse de publier ce genre de référentiel ; elle couvre très bien les noms d'institutions patrimoniales.

Le site dédié est **Data-BnF** : [https://data.bnf.fr](https://data.bnf.fr)

Voir par exemple la notice du Metropolitan Museum [**ici**](https://data.bnf.fr/fr/11870475)


<a id='t2-4'/>

## Créer une table secondaire 

### <17>

**Niveau de sécurité n^o^ 3**

Si l'on est amené à avoir beaucoup de données et des données variées, il est utile de **les déporter dans une table secondaire**

Dans cette table secondaire :

- On attribue une **clé** à chaque lieu (par exemple `1`, `2`, etc.)
- On place le **label** ou intitulé correspondant dans la colonne suivante

Dans la table principale :

- On crée une colonne « Clé lieu conservation » pour saisir les clés de la table secondaire, dites **clés étrangères**
- On crée une colonne « Label lieu conservation » où l'on **appellera** automatiquement les labels de la table secondaire


### <18>

Une fois les clés étrangères renseignées :

- Télécharger la feuille et l'ouvrir dans LibreOffice Calc
- Dans la case **F2** qui correspond au premier enregistrement et à l'attribut « Label lieu conservation », coller la formule suivante : **`=RECHERCHEV(E:E;$Feuille2.A:Z;2;0)`**
	- `=RECHERCHEV()` signifie que l'on écrit une fonction de Recherche Verticale
	- `E2` est le **critère de recherche** ; il signifie : « on cherche la clé dans la case E2 »
	- `$Feuille2.A:Z` est la **matrice** ; cela signifie : « l'info recherchée se trouve dans la Feuille2 entre les colonnes À et Z »
	- `2` est l'**index** ; cela signifie : « l'info que je recherche est dans la 2^e^ colonne de la matrice »
	- `0` est un booléen… peu importe !


### <19>

**Choisir des identifiants**

- Ils peuvent être très **abstraits**, comme `1`, `2`
- On peut aussi les rendre **parlants**, en codant par exemple le nom du pays, de la ville et de l'institution sous forme de groupes de lettres :
	- British museum. Londres : `GB-LON-BMU`
	- Metropolitan museum of art. New York, N.Y. : `US-NYO-MET`

Cela permet de classer les enregistrements selon leur identifiant.

**Attention** : il est toujours dangereux de changer les clés primaires d'une table ! Mieux vaut ajouter de nouveaux attributs dans cette table pour la trier selon de nouveaux critères.

[comment14]: <19> (Pour la suite du cours : d'autres référentiels, pour les champs à utiliser, pour les techniques artistiques, etc.)

[comment15]: <19> (Si je veux diviser le contenu de la colonne lieu de conservation, je peux le faire en fonciton du séparateur **point** : Données, Texte en colonnes.)
