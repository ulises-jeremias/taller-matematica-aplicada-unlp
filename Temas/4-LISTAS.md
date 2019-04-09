###LISTAS

Una lista es una estructura de datos **homogénea**, cuya longitud es **mutable**:

*homogénea*: los elementos dentro de la lista son **TODOS** del mismo tipo
*mutable*: la cantidad de elementos puede variar. Puede tener 0 elementos (en cuyo caso es una lista vacía, denotada por []). O puede tener *n*, donde *n* es un natural cualquiera, que puede ir cambiando según si agregamos o sacamos elementos.

Además, tienen un orden. Es decir: tienen primer y último elemento.
----

En general, se escribe entre '[' y ']' y sus elementos separados por ','
```haskell
[1,2,3]
[True, True, False]
['y','o','l','o']
```

----

Dos operaciones básicas que podemos realizar con ellas son:

```haskell
(++) :: [a] -> [a] -> [a]
--función que concatena dos listas

(:) :: a -> [a] -> [a]
--función que agrega un elemento al principio de la lista

```

----

##Ejemplos

Note: hacer ejemplos

----

Como dijimos, tienen orden. 
Al primer elemento, lo obtenemos con la función *head*
Al último elemento, lo obtenemos con la función *last*

Después tenemos las funciones *tail* e *init*. *tail* nos da todo menos la cabeza, e *init* nos da todo menos el último elemento

----

Otras funciones útiles:

*length*
*take*
*minimun*
*sum*
*elem*


----
## Creando listas

Note: rangos y replicate

----

### Comprensión de listas

Esto es algo muy útil que tiene mucha **equivalencia** con la notación que ven en matemática. En lugar de definir los elementos de una lista numerándolos, podemos decir qué deben cumplir para estar en la lista.

Note: No sé si acá se podrá meter algo en latex

----

La forma de escribir esto en haskell sigue la siguiente regla sintáctica

[2 * x | x <- [1..], esDivisible x 2]

[Función de salida | conjunto de donde salen las x, predicados que cumple]

----


