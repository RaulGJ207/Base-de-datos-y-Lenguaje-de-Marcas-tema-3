Character Set y Collations  
Ejercicio 1

Mostrar todos los conjuntos de caracteres que contengan la palabra utf.  
SHOW CHARACTER SET LIKE '%utf%';

Ejercicio 2

Muestra todos los collations disponibles para el conjunto de caracteres latin1. ¿Cuál es el collation predeterminado de latin1?

Nota: hay que generar dos consultas: una por cada pregunta.  
SHOW COLLATION WHERE Charset \= 'latin1';

SHOW COLLATION WHERE Charset= 'latin1' ANDDefault \= 'Yes';

Ejercicio 3

Filtra las collations del conjunto utf8mb4 que sean sensibles a acentos (as). Filtra las collations del conjunto utf8mb4 que sean sensibles a mayúsculas (cs).

Nota: hay que generar dos consultas: una por cada pregunta.  
SHOW COLLATION WHERE Charset \= 'utf8mb4' AND Collation LIKE '%\_as%';

SHOW COLLATION WHERE Charset \= 'utf8mb4' AND Collation LIKE '%\_cs%';

Ejercicio 4

Compara si ó es igual a o utilizando el collation utf8mb4\_0900\_ai\_ci. Compara si ó es diferente de o utilizando el collation utf8mb4\_0900\_as\_ci.

Nota: hay que generar dos consultas: una por cada pregunta.  
SELECT 'ó' \= 'o' COLLATE utf8mb4\_0900\_ai\_ci AS Result;

SELECT 'ó' \!= 'o' COLLATE utf8mb4\_0900\_as\_ci AS Result;

Ejercicio 5

Compara si la ñ es igual a n utilizando los collations utf8mb4\_spanish\_ci y utf8mb4\_spanish2\_ci.  
SELECT 'ñ' \= 'n' COLLATE utf8mb4\_spanish\_ci AS Spanish\_CI\_Result, 'ñ' \= 'n' COLLATE utf8mb4\_spanish2\_ci AS Spanish2\_CI\_Result;