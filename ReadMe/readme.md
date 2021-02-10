##Grille de Sudoku

###Énoncé :
La société "La Française des Jeux" souhaite diffuser en direct sur une chaîne télévisée les résultats de son dernier jeu : le super SODUKO avec une cagnotte de 1.000.000 €.
Pour cela, vous devez traiter l'ensemble des grilles des jeux fournies et afficher les gagnants dans un délai de 60 secondes maximum

####Logique applicative :
Dans Symfony :

* Création d'entities (et donc des repositories) :
  
`* Joueur`
  
`* Grille`
  
`* relation OneToOne entre Joueur et Grille, avec ajout d'une propriété "idJoueur dans l'entity Grille"`
  
*Création du controller :

`* GrilleControlleur`

`* Création d'un CRUD pour gérer les données des grilles dans la bdd (connexion à la bdd depuis Symfony dans le fichier .env`

*A part de GrilleController :

`* Récupération des données des grilles sous forme de tableaux à 2 dimensions`

`* Fonction qui parcours les données du tableau  :`

    --> Si une valeur est nulle (case égale à 0) : retourne "false" et break de la fonction
    --> Sinon pour toutes les lignes du tableau (on part d'une ligne i=1, on incrémente de 1, jusqu'à i=9):
        --> Si la somme des valeurs de la ligne n'est pas strictement égale à 45 : break de la fonction
        --> Si la somme des valeurs de la ligne est strictement égale à 45 : continue
            -->Lorsque toutes les lignes sont parcourus et que les sommes des lignes sont égales à 45 chacune => stockage du tableau dans une variable $gagnante et envoie (render) à un fichier twig

*Dans le fichier twig :

`*Pour la variable $gagnante avec un rang de 3, boucle qui affiche la grille gagnante et son joueur`
