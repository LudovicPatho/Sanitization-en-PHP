# Sanitization-en-PHP

    $options = array(
    'name' 			=> FILTER_SANITIZE_STRING,
    'lastName' 		=> FILTER_SANITIZE_STRING,
    'mail' 			=> FILTER_VALIDATE_EMAIL,
    'gender' 		=> FILTER_SANITIZE_STRING,
    'country' 		=> FILTER_SANITIZE_STRING,
    'subject' 		=> FILTER_SANITIZE_STRING,
    'message' 		=> FILTER_SANITIZE_STRING);

Ensuite on créé une variable avec la fonction filter_input_array.   

    $result = filter_input_array(INPUT_POST, $options);
    
Si on 

## Sources

* Vous trouverez tous les filtres disponnibles ici :
http://php.net/manual/fr/filter.filters.sanitize.php

* La documentation sur la fonction filter_input()
http://php.net/manual/fr/function.filter-input.php

* La documentation sur la fonction filter_input_array()
http://php.net/manual/fr/function.filter-input.php 
