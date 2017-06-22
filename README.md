# Sanitization-en-PHP

Il arrive parfois qu'on ait besoin de traiter un nombre important d'entrées dans un formulaire. Dans ce cas, il est sans doute préférable de faire la sanitization avec la fonction filter_input_array.  

    $options = array(
    'name' 		=> FILTER_SANITIZE_STRING,
    'lastName' 		=> FILTER_SANITIZE_STRING,
    'mail' 		=> FILTER_VALIDATE_EMAIL,
    'phone' 		=> FILTER_SANITIZE_NUMBER_INT,
    'url' 		=> FILTER_SANITIZE_URL,
    'subject' 		=> FILTER_SANITIZE_STRING,
    'message' 		=> FILTER_SANITIZE_STRING);

Ensuite on créé une variable avec la fonction filter_input_array. Comme son nom l'indique, la fonction va retourner un Array(). 

    $result = filter_input_array(INPUT_POST, $options);
    
En cas de problème, la fonction retourne un NULL si la variable est vide et un FALSE si il y a eu une erreur.

     if ($result != null AND $result!= FALSE) 
	 {
        echo "Tous les champs ont été néttoyé !";
     } 
     else
     {
        echo "Un champs est vide ou n'est pas correcte!";
     }
     
Pour afficher les résultats, on fait une boucle foreach avec la variable $result :     
     
     foreach($options as $key => $value) 
	 {
        echo $result[$key];
     }

    
## Sources

* Vous trouverez tous les filtres disponnibles ici : http://php.net/manual/fr/filter.filters.sanitize.php

* La documentation sur la fonction filter_input() : http://php.net/manual/fr/function.filter-input.php

* La documentation sur la fonction filter_input_array() : http://php.net/manual/fr/function.filter-input-array.php
