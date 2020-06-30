# Ynov - B1 - PHP - Rattrapage

## Mode de rendu

Lien vers votre dépôt Git, que je pourrai clôner.

## Critères d'évaluation

- Utilisation de l'inclusion de fichiers
- Séparation de templates
- Création de fonctions pour mieux séparer / organiser / réutiliser votre code
- Utilisation de PDO pour effectuer des requêtes (préparées ou non) vers la base de données
- Utilisation des sessions

## Questions théoriques

Répondez à ces questions dans le `README` de votre projet.

- Quelles sont les 2 méthodes HTTP utilisables dans un formulaire en PHP ?
- Quelle est la différence entre `include`, `include_once`, `require` et `require_once` ?
- Quelle fonction devez-vous appeler pour utiliser les sessions dans votre application ?
- Qu'est-ce qu'un DSN et à quoi sert-il dans le cadre de PDO ?
- Quelle est la différence entre une requête préparée et une requête non préparée ?
- Quelle est la différence entre la méthode `GET` et la méthode `POST` ?

## Projet

Vous allez réaliser un site simple présentant des produits, qu'un utilisateur pourra ajouter à un panier.

### Arborescence

- Page d'accueil
- Page de liste de produits
- Page fiche produit
- Page de contact
- Page panier

> Il n'y aura pas d'utilisateur à gérer, donc pas d'authentification ni de table utilisateur. N'importe quel utilisateur arrivant sur le site pourra commencer à ajouter des produits à son panier

### Interface

Vous utiliserez [Bootstrap](https://getbootstrap.com/).

L'interface contiendra :

- Un header
- Une zone de contenu
- Un footer

## Structure de la base de données

### Table : produit

| Champ | Type | Commentaire |
|---|---|---|
| ID | INT | PRIMARY KEY AUTO_INCREMENT |
| nom | VARCHAR(255) | |
| picture | VARCHAR(255) | Contiendra le chemin vers l'image du produit (utilisez un site fournissant des images, comme [Unsplash](https://unsplash.com/))  |
| description | TEXT | |
| promo | TINYINT(1) | 1 si le produit est en promotion, 0 sinon |

### Table : contact

| Champ | Type | Commentaire |
|---|---|---|
| ID | INT | PRIMARY KEY AUTO_INCREMENT |
| email | VARCHAR(255) | |
| subject | VARCHAR(255) | |
| message | TEXT | |

## Page d'accueil

La page d'accueil présentera une liste des produits en promotion.

Par ailleurs, un champ de recherche (texte) permettra de rechercher un produit directement depuis la page d'accueil.

> La cible du formulaire de recherche sera la page de liste des produits. Cela signifie que votre page de liste des produits devra pouvoir accepter un paramètre `GET` servant à rechercher un produit par son nom

## Page de liste de produits

La page de liste de produits présentera tous les produits présents en base de données.
Pour chaque produit, on affichera son nom, son image, et un indicateur visuel, comme une icône, pour indiquer s'il est en promotion ou pas.

Pour chaque produit, on pourra cliquer sur le nom ou l'image pour accéder à sa fiche individuelle.

> Il ne sera pas nécessaire de remettre un champ texte pour la recherche de produits dans cette page. Pour ce sujet, on ne pourra faire une recherche que depuis la page d'accueil. Donc pour résumer, dans la page de liste de produits, si on détecte un paramètre `GET` de recherche (appelez-le comme vous voulez), on va filtrer la requête SQL. Sinon, on affiche tous les produits

## Fiche produit

La fiche produit affichera toutes les informations relatives au produit dont l'ID sera passé en paramètre `GET` (nom, image, description, promotion ou pas).

Par ailleurs, un bouton supplémentaire permettra d'ajouter ou supprimer le produit de son panier.

> Le panier sera géré en **session**, pas en base de données
>
> Lorsque vous ajouterez un produit au panier présent en session, vous pourrez ajouter son ID uniquement
>
> Vous veillerez à éviter les doublons de produits. Par ailleurs, il n'est pas nécessaire de gérer une quantité pour un produit donné : on l'ajoute une et une seule fois, on pourra le supprimer ensuite

## Page contact

La page de contact contiendra un formulaire simple reprenant la structure de la table `contact` présente en base de données.

Pour chaque validation de formulaire, une nouvelle demande de contact sera enregistrée dans la table `contact`.

## Page panier

La page panier affichera l'ensemble des produits ajoutés au panier, sous forme de liste.

Si aucun produit n'est présent dans le panier, un message sera prévu pour indiquer à l'utilisateur que son panier est vide.

Chaque produit pourra être supprimé du panier grâce à un bouton.

Un bouton global permettra de vider son panier.
