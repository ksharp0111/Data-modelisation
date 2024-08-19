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


![alt text](/IMG/image.png)
suite a la collecte des doccument on peut y remplir un dictionnaire de données 

dictionnaire de données
![alt text](/IMG/image-2.png)

1 Dependances fonctionnelles:
est une relation entre deux attributs d'une table. 
A dépend fonctionnellement d'une donnée B

Pour formaliser une dependance fonctionnelle on utilise la notation suivante :   
Numero adherent (Nom, prenom, code postal, ville, telephone, date d'adhesion, mail)

La partie gauche (numero adherent) est la source de la dependance fonctionnelle. La partie droite desgine le but de la dependance.


2 Dependances fonctionnelles composées

Si une dependance fonctionnelle fait intervenir plus de deux attributs (source) on parle de dependance fonctionnelle composee.  
Exemple: Pour connaitre le temps d'un coureur sur une etape donnee il nous faut son numero ou son nom ainsi que le nom ou le numero de l'etape.          
Formalisation:  
(numero coureur, numero etape) (temps)

### Modele Conceptuel de Données MCD

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

