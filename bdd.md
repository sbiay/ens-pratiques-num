---
title: Créer une base de données relationnelle
date: 1^er^ semestre 2023-2024
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
	4. [Écrire une formule pour concaténer plusieurs champs ](#t2-4)
	5. [Élaborer un thésaurus personnel ](#t2-5)
	6. [Tables secondaires et tables de relation ](#t2-6)

[comment]: <> (FINET)


<a id='t1'/>

# Introduction
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## À quoi sert une base de données ? 

### <2>

- Les organiser : traiter des données en masse
- Les exploiter : statistiques, cartographies, diagrammes
- Les publier : partager les données de la recherche
- Les valoriser : collections virtuelles


<a id='t1-2'/>

## Principe fondamental 

### <3>

Beaucoup de données sont exposées sur le web sous la forme de **documents** au format **Json**, comme les ouvrages numérisés sur Gallica (un exemple [**ici**](https://gallica.bnf.fr/iiif/ark:/12148/btv1b60000317/manifest.json)).

Mais la pierre angulaire du monde des bases de données, c'est le **modèle tabulaire**.


<a id='t1-3'/>

## Premiers pas : trier et filtrer des données 

### <4>

On démarre avec des données très simples à télécharger [**ici**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=344777)

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

Ajoutons un attribut : la **période** de spécialisation

Il comporte quatre valeurs possibles :

1. Antique
2. Médiévale
3. Moderne
4. Contemporaine


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

Nous allons concevoir une base de données sur le chat dans l'histoire de l'art.
Chacun.e va remplir une mission de son choix (liste [**ici**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=321309)) :

1. Fouiller des collections numériques en utilisant les **filtres ou facettes**, pour récolter **5 œuvres**
2. Repérer le **permalien** (s'il existe) : une URL courte qui se termine par un identifiant pérenne
3. Télécharger une image (si possible !)

Il peut être utile de télécharger l'extension pour Firefox [**Dezoomify**](https://addons.mozilla.org/en-US/firefox/addon/dezoomify/) pour télécharger en HD si le site ne le propose pas.

[comment7]: <9> (Exemple d'une recherche dans les collections du Met avec le mot-clé « cat », puis le filtre sur la période 1400-1600.)

[comment8]: <9> (L'URL contient dans sa chaîne de requêtes les arguments de ma recherche)

[comment9]: <9> (Le permalien est court)

[comment10]: <9> (British Museum : cliquer sur Use this image)


### <10>

Ce qu'il faut faire avec les données :

1. Ajouter les permaliens dans le tableau partagé [**base.ods**](https://docs.google.com/spreadsheets/d/1jB7TmDyQ3jfdU1t5gppX3tuWLvry1_13vn-0OlHHLoc/edit#gid=87305927)

2. Renommer les images téléchargées par l'identifiant de l'item (`01.jpg`, `02.jpg`)

3. Placer le fichier de l'image dans le [**drive**](https://drive.google.com/drive/folders/1sH30BKL2uREnLs9z3BxrNioxAkM9nuup)


<a id='t2-2'/>

## Élaborer un modèle conceptuel de données 

### <11>

Le but de cette base de données est d'**analyser l'iconographie du chat à travers les époques de l'art**.

Quels **attributs** seraient nécessaires pour décrire les objets que l'on a récoltés et les représentations du chat qu'ils proposent ?

En bref, combien de **colonnes** avec quels intitulés faut-il ajouter à notre tableau pour cela ?


### <12>

La base **Agorha** de l'INHA est un excellent modèle francophone pour définir la liste et les noms des attributs (voir une statuette égyptienne [**ici**](https://agorha.inha.fr/ark:/54721/64706557-e7ad-4e92-8361-3427c89882b0) ou un tableau du XVI^e^-XVII^e^ s.
[**là**](https://agorha.inha.fr/ark:/54721/14f34326-2b28-493e-89be-31f2f5830311)) :

- Identification :
	- Type d'œuvre (voir le thésaurus [**ici**](https://thesaurus.inha.fr/thesaurus/page/ark:/54721/8e09cc44-abef-4f14-9761-6c9cb3f63b2d))
	- Titre : il faudra le donner ***en français***

- Localisation :
	- Lieu de conservation
	- Cote


### <13>

- Description :
	- Matérialité (th^us^ [**ici**](https://thesaurus.inha.fr/thesaurus/page/ark:/54721/2275eb81-6e47-4c3c-b1ee-96795edb046c)) :
		- Matériau
		- Technique
	- Dimension
	- Commentaire descriptif
- Création / exécution :
	- Date de création
	- Période de création (th^us^ [**ici**](https://thesaurus.inha.fr/thesaurus/page/ark:/54721/b9fff2ce-220d-4bcc-858d-776f21e2cd61))
	- Lieu de création
	- Personne liée à l'œuvre
	- Rôle : voir notamment « degré d'attribution » (th^us^ [**ici**](https://thesaurus.inha.fr/thesaurus/page/ark:/54721/284089a5-2287-47e2-b107-79c704802630))

Pour retrouver tous les thésaurus de l'INHA, voir [**ici**](https://thesaurus.inha.fr/thesaurus/page/vocabulaires).


<a id='t2-3'/>

## Éditorialiser les données 

### <14>

Il faut maintenant commencer à renseigner les colonnes.

Prenons la **date de création** des œuvres.

Par exemple « 1750-1800 (circa) (circa) » pour [**cette œuvre**](https://www.britishmuseum.org/collection/object/A_1999-1202-0-4-19).

**Comment rendre mes enregistrements triables par dates** malgré la diversité des formats de données proposés ?


### <15>

**Règle d'or**

Pour pouvoir exploiter les données,\
il faut les rendre **nucléaires**

![<a date='sans'/>](img/demos_nucleaire.jpg)

1. Date de début
2. Date de fin
3. *circa *?


### <16>

Les valeurs que contiendra notre tableau sont de trois types :

1. Texte (ou chaînes de caractères)
2. Nombres
3. Booléens[^1] : type « vrai »/« faux »

[^1]: Du nom de l'inventeur de ce type de variable : George Boole (1815-1864).


### <17>

Passons au **lieu de conservation** des œuvres.

Remplir à l'avenant la colonne « Lieu de conservation » conduit immanquablement à écrire différemment le même nom, et donc à brouiller les données.

**Comment s'assurer que l'on renseigne toujours de la même manière le même nom ?**

Il faut des méthodes pour être sûr que la saisie des données soit homogène tout au long du travail…


### <18>

**Niveau de sécurité n^o^ 1**

Copier-coller plutôt que saisir les informations manuellement.

Pour rechercher dans la colonne « Lieu de conservation » si le nom à saisir existe déjà :

- Sélectionner toute la colonne en faisant un **clic gauche sur la lettre** de cette colonne
- **Ctrl ou Cmd + H**
- Cocher **Sélection active seulement** sur LibreOffice Calc (« Plage particulière » dans Google Sheets)
- Cliquer sur **Rechercher le suivant**


### <19>

**Niveau de sécurité n^o^ 2**

Faire appel à un **référentiel d'autorités**

La BnF est particulièrement soucieuse de publier ce genre de référentiel ; elle couvre très bien les noms d'institutions patrimoniales.

Le site dédié est **Data-BnF** : [https://data.bnf.fr](https://data.bnf.fr)

Voir par exemple la notice du Metropolitan Museum [**ici**](https://data.bnf.fr/fr/11870475)

**C'est à vous !** Renseignez le lieu de conservation de votre premier enregistrement selon la forme donnée par Data-BnF. 


### <20>

Le format de données fourni par Data-BnF pose un problème.

On doit séparer le nom de l'institution et le nom de la ville pour rendre les données nucléaires.


### <21>

**Niveau de sécurité n^o^ 3**

Si l'on est amené à avoir beaucoup de données et des données variées, il est utile de **les déporter dans une table secondaire**.

On verra cela plus loin…


[comment13]: <21> (Fin de la 2^e^ séance)


### <22>

**Si je veux y voir plus clair, je masque** les colonnes qui vont me gêner. Dans LibreOffice Calc :

- Cliquer droit sur la lettre d'une colonne > Masquer la colonne (par exemple **H** et **I**)

Pour faire réapparaître les colonnes masquées :

- Sélectionner les colonnes qui encadrent la ou les colonnes masquées
- Cliquer droit sur la lettre d'une colonne de la sélection > Afficher les colonnes


### <23>

**Noms d'artistes**

Il peuvent poser des problèmes d'homonymie.

- Chercher un nom dans le référentiel du Getty Institute, **Union List of Artist Names** accessible [**ici**](https://www.getty.edu/research/tools/vocabularies/ulan/) ou en cherchant du Google "getty ulan"

- Inscrire le numéro d'identification dans la colonne **H**


<a id='t2-4'/>

## Écrire une formule pour concaténer plusieurs champs 

### <24>

On va composer des **légendes** pour nos futures illustrations grâce à l'écriture de **formules**

Si j'écris `R2` dans une case, la case affiche… `R2` ("bof")

Si j'écris `=R2` dans une case, la case affiche le contenu de la case F2 ("wouahou")

- Écrire dans la colonne **E**, à la ligne de votre première œuvre, le contenu de la colonne **R**


### <25>

Pour « concaténer » le contenu des colonnes **R** (ville) et **P** (institution), dans la colonne **E**, j'écris, par exemple pour la ligne 2 : **`=R2&P2`**


### <26>

Il me faut un séparateur entre les deux données.

Il s'écrit entre **guillemets ""**.

La formule devient pour la ligne 2 : **`=R2&", "&P2`**

Continuons à écrire la légende en ajoutant la date, en format texte (colonne **L**) entre parenthèses.
Essayez d'abord sans regarder la solution (diapo suivante)


### <27>

La solution était : **`=R2&", "&P2&" ("&L2&")"`**

Ajoutons à présent au début de notre formule : 

- **Auteur** (colonne **G**) suivi d'une virgule ;
- **Titre** (colonne **F**) suivi d'une virgule ;
- **Type d'œuvre** (colonne **J**) suivi d'une virgule


### <28>

La solution était : **```=G2&", "&F2&", "&J2&", "&R2&", "&P2&" ("&L2&")"```**

**Problème** : en l'absence de donnée, j'ai un **séparateur inutile**.


### <29>

On efface le début de la formule pour revenir à **```=" ("&L2&")"```**

On utilise la fonction **TEXTJOIN**, qui s'appelle **JOINDRE.TEXTE** dans LibreOffice Calc.

- Juste après le égal, on écrit **TEXTJOIN(**
- On définit d'abord le délimiteur : `", "`
- On tape **`;`** pour séparer les paramètres
- **`1`** signifie **vrai** pour le paramètre **ignorer si vide** (en effet on veut ignorer les cases vides)
- Puis on définit chaque case à appeler : pour la ligne 2 : **`G2;F2;J2;R2;P2`** (attention, ici ne pas utiliser `F:F;Q:Q`…)
- On ferme la parenthèse et on ajoute **`&`** pour concaténer avec la suite de la formule


### <30>

Pour la ligne 2 du tableau, la formule serait :\
**`=TEXTJOIN(", ";1;G2;F2;J2;R2;P2)&" ("&L2&")"`**


### <31>

Autre solution : **créer une fonction de condition**

- On se dit la phrase suivante : *Si le contenu de la colonne F est égal à rien alors je veux afficher rien ; dans le cas contraire, je veux afficher la colonne F suivie de virgule espace*

- Sa traduction en formule est : **`SI(G2="";"";G2&", ")`**

Pour enchaîner **G** et **F** :\
**`=SI(G2="";"";G2&", ")&F2`**


<a id='t2-5'/>

## Élaborer un thésaurus personnel 

### <32>

L'intérêt de monter sa propre base de données réside surtout dans la possibilité de **forger des catégories d'analyse**.
Ce sera le cas pour le contenu iconographique de notre base.

Le thésaurus **Iconclass** constitue un modèle intéressant (voir [**ici**](https://iconclass.org/help/outline)) avec sa structure en arborescence.

Si l'on cherche « cat », on le trouve en plusieurs endroits du thésaurus.
Son entrée principale ([**ici**](https://iconclass.org/34B12)) ne présente pas assez de variété pour couvrir tous nos besoins : il faut donc élaborer notre propre thésaurus.


### <33>

Essayons de concevoir un ensemble de valeurs (ou catégories) qui décrivent dans nos objets *ce que les chats font* ou *comment ils sont représentés*.

1. Cartographier les concepts (diagramme « patates »)
2. Structurer les concepts en arborescence
3. Transposer cette arborescence dans une feuille de tableur


### <34>

**Étape 1 : cartographier les concepts**

![Dégager des thèmes de plus en plus englobant](img/demos_20230103_180332.jpg)


### <35>

**Étape 2 : structurer les concepts en arborescence**

Pour structurer une arborescence sous forme de liste, **LibreOffice Writer** peut faire l'affaire avec ses **listes ordonnées** (raccourci : F12).

Pour changer de niveau de numérotation : 

- Menu pricipal : **Format** > Listes
- **Abaisser d'un niveau**

Pour changer les numérotations des niveaux :

- Menu pricipal : **Format** > Puces et numérotation

Voir la liste à plusieurs niveaux [**ici**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=279130).


### <36>

**Étape 3 : Transposer cette arborescence dans une feuille de tableur**

Voir le tableau [**là**](https://pedag.u-picardie.fr/moodle/upjv/mod/resource/view.php?id=279142).


<a id='t2-6'/>

## Tables secondaires et tables de relation 

### <37>

On va a présent appeler les informations du thésaurus **sujets** dans le tableau des œuvres.

Dans la table principale :

- On crée une colonne « Sujet-clé » en **U** pour saisir les clés de la table secondaire, dites **clés étrangères**
- On crée une colonne « Sujet-code » en **V** et une colonne « Sujet-label » en **W** où l'on **appellera** automatiquement les labels de la table secondaire


### <38>

Il faut a présent remplir manuellement la colonne **U** : les clés étrangères des sujets.

Pour aller chercher, dans la colonne **V**, les codes correspondants (qui se trouvent dans la 2^e^ colonne de la feuille `sujets`), il faut inscrire la formule suivante, par exemple pour la ligne 2 : 

- Sous Google Sheets : **`=RECHERCHEV(U3;sujets!A:C;2;0)`**
- Sous LibreOffice Calc : **`=RECHERCHEV(E:E;$sujets.A:C;2;0)`**


### <39>

On vient donc d'associer notre table des œuvres (`Feuille1`) à une **table secondaire** (`sujets`).

On peut ainsi associer *à chaque œuvre un sujet unique*.

Les tables secondaires offrent une vraie **sécurité** aux données : je peux mettre à jour les labels et les codes sans risque pour la cohérence de mes données.


### <40>

**Comment faire si une œuvre doit avoir plusieurs sujets ?**

C'est ce que dans le jargon des bases de données on appelle la **cardinalité** (voir définition sur Wikipédia [**ici**](https://fr.wikipedia.org/wiki/Cardinalit%C3%A9_(programmation)).

Quand on élabore une base de données, et qu'il faut concevoir des tables secondaires, il faut toujours se poser ce type de question :

- Une œuvre peut-elle avoir plusieurs…
	- Lieu de conservation ?
	- Sujet ?
	- Titre ?
	- Auteur ?
	- Etc.


### <41>

Chaque fois que la réponse est "plusieurs", il faut élaborer une **table de relation**

Créons donc une nouvelle feuille intitulée **`relation-oeuvres-sujets`** avec les colonnes suivantes :

- **A** : Sujet-clé
- **B** : Sujet-code : `=RECHERCHEV(A2;sujets!A:C;2;0)`
- **C** : Sujet-label : `=RECHERCHEV(A2;sujets!A:C;3;0)`
- **D** : Oeuvre-clé : 
- **E** : Oeuvre-légende : `=RECHERCHEV(D2;Feuille1!A:Z;5;0)`