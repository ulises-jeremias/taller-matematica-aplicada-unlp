>module Conjuntos  where

0- Creando un conjunto. Para este taller podemos pensar a los conjuntos como listas identificadas por las proposiciones que cumplen sus
elementos. En general vamos a tomar los numeros naturales y escupir los numero que cumplen con la preposicion

>crearConjuntoConUnaPrep :: (Int -> Bool) -> [Int]
>crearConjuntoConUnaPrep p = [ x | x <- [1..], p x]

crearConjunto :: [(a -> Bool)] -> [a]


1- Pertenencia a un Conjunto

>pertenece :: (Eq a) => a -> [a] -> Bool
>pertenece a xs = foldr (\x acc -> (x == a) || acc) False xs

>pertenece' a xs = [x == a | x <- xs, x == a] /= []

Estamos yendo uno por uno, para ver si la está en la lista
Pero nosotros en realidad queremos ver si a cumple con un predicado
Cualquier conjunto podemos pensarlo como aquellos elementos que cumplen una proposicion


>conjuntoConPreposicion p xs = [ x | x <- xs, p x ]

De acá podemos ver que en realidad lo que nos interesa es que un elemento a satisfaga una preposición para ver si pertence o no

CÓMO HACEMOS PARA TRABAJAR CON TODOS LOS NATURALES DE FORMA INFINITA



2- Demostración de inclusión
Hacer la función implica para poder ir viendo que cada paso es verdadero

>implica :: (a -> Bool) -> (a -> Bool) -> a -> Bool
>implica p q x = (not (p x)) || (q x)





3 - Operaciones entre conjuntos

>interseccion :: (Eq a) => [a] -> [a] -> [a]
>interseccion [] _ = []
>interseccion _ [] = []
>interseccion xs ys = [ x | x <- xs, elem x ys ]




