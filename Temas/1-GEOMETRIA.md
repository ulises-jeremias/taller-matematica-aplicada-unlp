# Geometría

> Introducción a Haskell

Haskell es un **lenguaje de programación funcional puro** el cual vamos a utilizar en este taller ya que, a diferencia de lenguajes imperativos (como pueden ser Pascal o R-info), haskell presenta una mayor relación con la matemática. Esto nos permite escribir las *ideas* expresadas matemática, ó naturalmente, directamente en el lenguaje de programación.

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

aplicamos la función `r` a un valor entero, `2`, obteniendo un valor de salida booleano, `True`.

En terminos generales, podemos aplicar una función cualquiera a un valor cuyo **Tipo** sea el mismo que el **tipo de entrada** de la función. Y el resultado de la aplicación tendrá el tipo de salida de la misma. En el ejemplo anterior, el tipo de `r 2` es:

```haskell
r 2 :: Bool
```

* * *

Nosotros hasta ahora habiamos visto el operador `::` al momento de declarar el tipo de las funciones. Sin embargo, en el ejemplo anterior, utilizamos `::` para indicar el tipo de `r 2`. Qué pasó? **INSERTE MEME AQUÍ**

Esto sucede ya que en Haskell, al igual que en matemáticas, no diferenciamos lo que son funciones de lo que son los valores. Es decir, una función es un valor que, al igual que el resto de los valores que vemos, _tiene un **tipo**_. En este caso, cuando indicamos `r :: Int -> Bool` estamos diciendo que el tipo de `r` es `Int -> Bool`.

Más adelante vamos a ver como podemos sacarle el jugo a esta hermosa propiedad.

## Don Cartesiano

Existen situaciones en las cuales es conveniente expresar un problema a traves de un plano coordenado. Este se compone de dos ejes que representan dos variables. Precio de un terreno en funcion de su tamaño. **INSERTAR IMAGEN**. Crecimiento de población en función del tiempo. En resumen, cualquier par de datos del mundo real donde una depende de la otra.

> Se quiere saber, dada la longitud de una pared, que superficie tendrá una habitación cuadrada con dicha longitud.

* * *

Sabemos que un punto en un dato en el plano al cual le podemos atribuir un valor, por lo tanto, podemos definir funciones como las siguientes:

```haskell
abscisa :: (Float, Float) -> Float
abscisa (x, y) = x

ordenada :: (Float, Float) -> Float
ordenada (x, y) = y
```
Supongamos que queremos sumar dos puntos. La suma entre dos puntos la definiremos de la siguiente forma:

```
Sean P = (a, b), Q = (c, d),

P + Q = (a + c, b + d)
```

1.  Necesitamos buscar las forma de poder enviar dos puntos como parámetros de la función. **PREGUNTAR SI SE LES OCURRE COMO**

2.  Producto por un escalar

> Podemos recibir parámetros de dos tipos? **Como siempre, proponer que den el tipo de la funcion**

3.  Región en el plano

> Hacer una función que diga si un punto está en una región dada. Pero, que es una región?

4.  Funciones con rectas

> Una recta es una relación entre dos valores, uno del eje X y otro del eje Y. Entonces es una función y por lo tanto podemos aplicar todas las propiedades que venimos trabajando hasta ahora.

5.  Evaluar si un punto pertenece a la recta

6.  Let in y Where

7.  Funciones en rectas

> Pasemos una recta como parámetro
