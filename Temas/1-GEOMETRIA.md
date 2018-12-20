# Geometría

> Introducción a Haskell

Haskell es un **lenguaje de programación funcional puro** el cual vamos a utilizar en este taller ya que, a diferencia de lenguajes imperativos (como pueden ser Pascal o R-info), haskell presenta una mayor relación con las matemática. Esto nos permite escribir las *ideas* expresadas matemática, ó naturalmente, directamente en el lenguaje de programación.

* * *

En las últimas teorías comenzaron a estudiar Geometría. Ya trabajaremos con eso, pero antes, queremos seguir explorando Haskell así podemos utilizarlo para resolver problemas. Para ello vamos a reforzar la idea de Función en Haskell

Todas las funciones necesitan declararse. Recordemos el ejemplo del encuentro anterior

```haskell
r :: Int -> Bool
```
Primero aclaramos qué función vamos a declarar y luego indicamos qué cosas recibe, y qué cosas devuelve. En este caso recibe algo de **Tipo** u y devuelve algo de **Tipo** Bool. Pero... ¿Qué es un **Tipo**? Cuando decimos que algo es de un cierto tipo, nos referimos vamos a recibir un valor qué pertenece a un determinado conjunto. Por ejemplo, cuando decimos que 'x' es de tipo Entero (Int de haskell), nos referimos a que los valores que puede tomar 'x' son valores enteros, es decir, 'x' pertenece al conjunto de los Enteros (Z matemático). 

Luego se define la función

```haskell
r :: Int -> Bool
r x = x > 0
```

En este caso estamos diciendo que `r` es una función que dado un `x` entero devuelve un booleano que es verdadero, si `x > 0`. 

**¿Cómo usamos esta función?** La aplicamos. La aplicación es una de las operaciones que podemos realizar con una función. En haskell lo expresamos con un espacio `' '`. Por ejemplo, lo que en matemática haríamos de esta forma, `r(2)`, en haskell es como sigue:

```haskell
r 2
-- True
```

En el ejemplo anterior, aplicamos la función `r` a un valor entero, `2`, obteniendo un valor de salida booleano, `True`.

En terminos generales, podemos aplicar una función cualquiera a un valor cuyo **Tipo** sea el mismo que el **tipo de entrada** de la función. Y el resultado de la aplicación tendrá el tipo de salida de la misma. En el ejemplo anterior, el tipo de `r 2` es:

```haskell
r 2 :: Bool
```

