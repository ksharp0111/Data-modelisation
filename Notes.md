# pour créé des schemat en md utiliser Mermaid

# Fonctionnement modélisation 
- recueil d'info
- etude des docu interne
- etude des docu externe
- types d'info
- info elementaire

l'info doit etre atomique

 '34, rue de la paix, 75000 Paris'

 3 info elementaires:
 - adressse    => 34, rue de la paix
 - code postal => 75000
 - ville       => Paris

 une valeur prise par une info est une occurence (une donnée)


 ## approche nivelée 
 4 niveaux de Merise pour effectuer la conception d'un SI

 - niveau conseptuel
 - niveau organisationnel
 - niveau logique
 - niveau physique

![alt text](/IMG/image-1.png)
#### Le niveau conceptuel
Permet de modéliser les données de l'entreprise. On va utiliser le modèle conceptuel de données (MCD) pour modéliser les données de l'entreprise, et le MCT pour modéliser les traitements effectués sur ces données.

#### Le niveau organisationnel
Permet d'integrer a l'analyse precedente toutes les notions de temporalite, de chronologie des operations, de contraintes geographique, niveau d'acces. On va utiliser le modele organisationnel des traitements (MOT) et le modele organisationnel des donnees (MOD) pour modéliser les traitements de l'entreprise.

En resume on se pose les questions suivantes a partir des donnees recueillies au niveau conceptuel :

Quand les traitements sont-ils effectues ?
Où les traitements sont-ils effectues ?
Par qui les traitements sont-ils effectues ?

#### Le niveau logique:   
Permet de modéliser les données de l'entreprise en utilisant le modèle logique de données (MLD) et les traitements de l'entreprise en utilisant le modèle logique des traitements (MLT).

Le MLD est independant des langages de programmation et des SGBD (Systeme de Gestion de Base de Donnees).

On repond a la question : Avec Quoi les traitements sont-ils effectues ?

#### Le niveau physique
Il s'agit de l'organisation réelle des données. On va utiliser le modèle physique de données (MPD) et le modèle physique des traitements (MPT).

Ici, on apporte les solutions techniques de stockage des données et de traitement des données.

On repond a la question : Comment les traitements sont-ils effectues ?


![alt text](/IMG/image.png)
suite a la collecte des doccument on peut y remplir un dictionnaire de données 

dictionnaire de données
![alt text](/IMG/image-2.png)

### Dependances fonctionnelles:
est une relation entre deux attributs d'une table. 
A dépend fonctionnellement d'une donnée B

Pour formaliser une dependance fonctionnelle on utilise la notation suivante :   
Numero adherent (Nom, prenom, code postal, ville, telephone, date d'adhesion, mail)

La partie gauche (numero adherent) est la source de la dependance fonctionnelle. La partie droite desgine le but de la dependance.


### Dependances fonctionnelles composées

Si une dependance fonctionnelle fait intervenir plus de deux attributs (source) on parle de dependance fonctionnelle composee.  
Exemple: Pour connaitre le temps d'un coureur sur une etape donnee il nous faut son numero ou son nom ainsi que le nom ou le numero de l'etape.          
Formalisation:  
(numero coureur, numero etape) (temps)

## Modele Conceptuel de Données MCD

le MCD est un schemat conceptuel qui permet de représenté données d'une entreprise

- les propriétés
- les entitées
- les relations

#### les entités ou objets
les entitées sont un ensemeble de propriétés qui déctivent un objet du SI. Elles sont représenté par un rectangle.
![alt text](/IMG/image-3.png)

#### l'identifiant 
![alt text](/IMG/image-5.png)

#### les relations ou associations
les relations permettent de relier les entités entre elles. Par exemple:
![alt text](/IMG/image-4.png)

#### les cardinalités
une cardinalite exprime le nombre de fois ou l'occurence d'une entité participe aux occurences de la relation:
- Combien de fois au minimum peut-il commander un article
- Combien de fois au maximum peut-il commander un article

![alt text](/IMG/image-6.png)

pour obtenir la cardinalité suivante on se pose les memes questions, mais cette fois-ci pour l'entite n article
![alt text](/IMG/image-7.png) 

Exemple
![alt text](/IMG/image-8.png)

les cadinalités:

- Une mère peut élever un ou plusieurs enfants
- Un enfant peut etre élever par une et une seule mère


#### Les relations porteuse
Une relation est dite porteuse si elle possède des propriétés.
Imaginons que nous voulont faire apparaitre la quantité d'articles commandés par un client. Nous allons donc ajouter une propriété à la relation.
![alt text](/IMG/image-9.png)

ci dessus nous avons une relation qui fait intervenir deux entités: c'est unne relation binaire. une relation qui fait intervenir trois entités est une relation terniere
![alt text](/IMG/image-10.png)

#### Les relations reflective
Une relation est dite reflexive si elle relie une entité à elle même.
![alt text](/IMG/image-11.png)
ici un employer peut Diriger zéro ou n (employer) et peut etre dirigé uniquement par un employer.

#### Quelques regles de conception
- 1 toute entité doit foicement avoir un identifiant
- 2 toute les propriété de l'entite dependent fonctionnellement de l'identifiant
- 3 le nom d'une propriété ne doit apparaitre qu'une seule fois le MCD (utilisation de préfixe camelcase ou undescore)

#### Notion d'entité forte et d'entité faible
- 1 Une entite forte qui ne depend pas d'autre entité pour exister 
- 2 Au contraire une entité faible dépénd forcement d'une entité forte pour exister

#### Contrainte d'intégrité fonctionnelle (CIF)
une CIF est définit par le fait qu'une des entités de l'association est completement déterminée par la connaissance d'une ou de plusieurs entites participant a l association



## Modele logique de données (MLD)
Le MLD est la suite du processus Merise, on se rapproche un peu plus de la base de données.
#### Exemple 
![alt text](/IMG/image-14.png)

#### Cas simple de MLD
![alt text](/IMG/image-8.png)

Nous arrivons au MLD suivant :
![alt text](/IMG/image-20.png)

L'entite qui possede la cardinalite 1,1 ou 0,1 absorbe l'identifiant de l'entite la plus forte (0,n ou 1,n). Cet identifiant devient alors une cle etrangere.

#### Cas (0,n), (0,n) ou (1,n), (1,n)
Parlons du MCD suivant:
![alt text](/IMG/image-13.png)
l'entité qui possede la cadinnalité maximale egale a 1 recevra le ou les identifiants des entités ayant les cardianalités maximale les plus fortes

Dans le cas ou la cardinalité max est n des deux cotés, on cree une entité intermédiaire qui va contenir les deux clés étrangeres des deux entités.  
![alt text](/IMG/image-12.png)


Continuons avec le MCD suivant :   
![alt text](/IMG/image-23.png)

On obtient le MLD suivant en suivant la meme logique:                    
![alt text](/IMG/image-24.png)                                       

#### Cas d'une relation reflexive
Partons du MCD suivant :   
![alt text](/IMG/image-25.png)
![alt text](/IMG/image-26.png)


## Modele physique des donnees (MPD)
Le MPD est la suite du MLD, il permet de passer du modele logique des donnees au modele physique des donnees.
Voici le schema relationnel correspondant au MLD precedent:
Diplômes (Diplomes)
Possède (#NumEmployé, #Diplôme, Date d'obtention)
Employés (NumEmployé, Nom, Prénom, Adresse, Code Postal, Ville, Téléphone)
Tables (NumTable, Capacité)
Date (Date)
Service (TypeService, Désignation)
Boissons Diverses (NumBoissons, Désignation, Prix de vente)
Contenir (#NumCommande, #NumBoissons, Quantité)
Commande (NumCommande, #Numemployé, #Date, #TypeService, #NumTable)
Comprend (#NumMenu, #NumCommande, Quantité)
Menus (NumMenu, Libellé, Prix de vente)
Constitué (#NumMenu, #NumPlat)
Constituer (#NumCommande, #NumPlat, Quantité)
Sélectionner (#NumCommande, #NumVin, Quantité)
Carte des vins (NumVin, Nom du vin, Millesime, Prix de vente)

traduit en script sql:
```SQL
CREATE TABLE CARTE_DES_VINS
   (
   NUMVIN INTEGER(2) NOT NULL ,
   NOM_DU_VIN CHAR(40)   ,
   MILLESIME INTEGER(2)  ,
   PRIX_DE_VENTE REAL(5,2)
,
    PRIMARY KEY (NUMVIN) CONSTRAINT PK_CARTE_DES_VINS
   );

CREATE TABLE BOUTEILLES
   (
   NUMVITICULTEUR INTEGER(2) NOT NULL ,
   NUMVIN INTEGER(2) NOT NULL ,
   NUMBOUTEILLE INTEGER(2) NOT NULL ,
   DATE_ACHAT DATE(8) ,
   PRIX_D_ACHAT REAL(5,2)
,
    PRIMARY KEY (NUMVITICULTEUR, NUMVIN, NUMBOUTEILLE) CONSTRAINT
PK_BOUTEILLES
   );


CREATE TABLE VITICULTEUR
   (
   NUMVITICULTEUR INTEGER(2) NOT NULL ,
   NOM_VITICULTEUR CHAR(20) ,
   PRÉNOM_VITICULTEUR CHAR(20) ,
   ADRESSE_VITICULTEUR CHAR(40) ,
   CODE_POSTAL CHAR(5) ,
   VILLE CHAR(40) ,
   TÉLÉPHONE CHAR(15)
,
    PRIMARY KEY (NUMVITICULTEUR) CONSTRAINT PK_VITICULTEUR
   );
```



