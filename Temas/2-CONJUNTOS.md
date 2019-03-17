# Conjuntos

* * *

> Listas

Las listas son una de las estructuras más básicas de la computación, lo cual no las hace poco útiles, si no todo lo contrario. Vamos a repasar y reforzar los conceptos de conjuntos a través de listas. Aunque está definido el tipo Set en Haskell ("conjunto"), vamos a estar usando listas 


¿Qué es una lista? Se trata de una serie de elementos ordenados. Esto quiere decir que una lista tiene un comienzo y un final, no necesariamente sus elementos están ordenados


**PREGUNTA**
¿Cuál sería la diferencia entre una lista y un conjunto?


> Creando listas

Se usan [] para crear listas literales
['a', 'b', 'c']
[10,9,2,1, 2, 9]
[True, False]
["Entre comillas"]

Para agregar un elemento a la cabeza de la lista usamos :
1:[10,9,2,1]
"Esto está":["Entre comillas"]

No podemos agregar un sólo elemento al final de la lista pero si podemos agregar otra lista al final de una lista con la operación ++

[10,9,2,1] ++ [0]
['a', 'b'] ++ ['c', 'd']
[True, False] ++ []

¿qué fue eso último? No cambió nada, porque [] representa a una lista vacía. Esto es un concepto importante. Es análogo a la idea de Conjunto vacío. En listas tiene varios usos. Para empezar, en realidad una lista consiste en concatenar elementos a una lista vacía

1:[] == [1]
2:1:[] == [2,1]
'e':'s':'t':'o':' ':'e':'s':' ':'u':'n':'a':' ':'l':'i':'s':'t':'a':[]

¡qué forma más incómoda de escribir un String! Esperá, ¿eso fue un string? ¿No era una lista? Tadan, un string es una lista de Chars. Esto veremos que es muy útli

c:"lavo"

Ya que la lista tiene un orden (principio y final) podemos hacer operaciones con estas partes

head ["CABEZA", "COLA", "COLA", "FINAL"]
last ["No, ", "quiero"]

init
tail
!!

Ahora, veamos funciones útiles para hacer cosas con estas listas

elem
filter
any
all
map


