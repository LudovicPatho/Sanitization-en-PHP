# Sanitization-en-PHP

Il arrive parfois qu'on ait besoin de traiter un nombre important d'entrées dans un formulaire. Dans ce cas, il est sans doute préférable de faire la sanitization avec la fonction filter_input_array(). Cette fonction est utile pour récupérer plusieurs valeurs sans avoir à appeler plusieurs fois la fonction filter_input().

## Description 
    mixed filter_input_array ( int $type [, mixed $definition [, bool $add_empty = true ]] )
Comme on peut le voir la fonction peut accepter des variables mixes, comme "string", "int" etc.
Si un champs est vide, elle retournera un "NULL". Si il y a une erreur lors de la sanitization, la fonction retournera un "FALSE". 
    
## Exemple :
Imaginons que nous avons un formulaire avec les inputs suivants :

    <form>
		<input type="text" name="first_name" >
		<input type="text" name="last_name" >
		<input type="email" name="mail">
		<input type="tel" name="phone">
		<input type="url" name="url">
		<input type="text" name="subject">
		<input type="text" name="message">
    </form>

Dans un premier temps, nous allons créer un tableau qui contient les filtres dont nous avons besoin. Vous trouverez tous les filtres ici : http://php.net/manual/fr/filter.filters.sanitize.php. Pour les clés du tableau, il est important de conserver les noms de vos inputs. 

    $options = array(
    'first_name' 	=> FILTER_SANITIZE_STRING,
    'last_Name' 	=> FILTER_SANITIZE_STRING,
    'mail' 		=> FILTER_VALIDATE_EMAIL,
    'phone' 	=> FILTER_SANITIZE_NUMBER_INT,
    'url' 		=> FILTER_SANITIZE_URL,
    'subject' 	=> FILTER_SANITIZE_STRING,
    'message' 	=> FILTER_SANITIZE_STRING);

Ensuite on créé une variable $result avec la fonction filter_input_array. Comme son nom l'indique, la fonction va également retourner un Array() qui sera associatif. Cette onction doit recevoir au moins deux arguments. Ici INPUT_POST pour récupérer les valeurs encodées dans le champs et la variable $option pour appliquer les filtres.

    $result = filter_input_array(INPUT_POST, $options);
    
Et voilà, tous vos champs ont été sanitizé ! En cas de problème, la fonction retourne un NULL si la variable est vide et un FALSE si il y a eu une erreur.

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
