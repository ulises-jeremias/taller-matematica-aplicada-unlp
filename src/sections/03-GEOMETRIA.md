## Introducción a Haskell

----

<!-- .slide: style="text-align: left" -->

### Haskell

- Es un **lenguaje de programación funcional puro**.
- Lo utilizamos en el taller dado que presenta mayor relación con la matemática.
  - A diferencia de lenguajes imperativos como R-Info o Pascal.
- Esto permite escribir las ideas expresadas matemática, ó naturalmente, _directamente_ en el lenguaje de programación.

----

<!-- .slide: style="text-align: left" -->

Esta sección del taller corresponde a la parte de Geometría de la materia. Sin embargo, por el momento vamos a seguir explorando Haskell así podemos utilizarlo para resolver problemas.

----

Para ello vamos a reforzar la idea de **Función** en _Haskell_.

----

Todas las funciones necesitan declararse. Recordemos el ejemplo del encuentro anterior

```haskell
r :: Int -> Bool
```

Primero aclaramos qué función vamos a declarar y luego indicamos qué cosas recibe, y qué cosas devuelve.

----

En este caso recibe algo de Tipo **$u$** y devuelve algo de Tipo _**Bool**_. Pero...

----

### ¿Qué es un Tipo?

Cuando decimos que **algo es de un cierto tipo**, nos referimos a que ese _"algo"_ es un **valor qué pertenece a un determinado conjunto**. 

<small>
    Por ejemplo, cuando decimos que $x$ es de tipo Entero (_Int_ de Haskell), nos referimos a que los valores que puede tomar $x$ son valores enteros, es decir, $x$ pertenece al conjunto de los Enteros ($\mathcal{Z}$ matemático).
</small>

----

Luego, se define la función $r$ como sigue:

```haskell
r :: Int -> Bool
r x = x > 0
```

<small>
    En este caso estamos diciendo que $r$ es una función que dado un $x$ entero devuelve un booleano que es verdadero, si $x > 0$.
</small>

----

### ¿Cómo usamos esta función?

La aplicamos.

----

La aplicación es una de las operaciones que podemos realizar con una función. En haskell lo expresamos con un espacio `" "`.

----

Por ejemplo, lo que en matemática haríamos de esta forma, $r(2)$, en haskell es como sigue:

```haskell
r 2
-- True
```

<small>
    aplicamos la función $r$ a un valor entero, $2$, obteniendo un valor de salida booleano, _True_.
</small>

----

En terminos generales, podemos aplicar una función cualquiera a un valor cuyo **Tipo** sea el mismo que el **tipo de entrada** de la función. Y el resultado de la aplicación tendrá el tipo de salida de la misma.

----

En el ejemplo anterior

```haskell
r 2 :: Bool
```

----

Nosotros hasta ahora habiamos visto el operador `::` al momento de declarar el tipo de las funciones. Sin embargo, en el ejemplo anterior, utilizamos `::` para indicar el tipo de _r 2_.

----

### Que pasó??

<small>
    En haskell, al igual que en matemática, no diferenciamos lo que son funciones de los que son los valores. Es decir, una **función es un valor** que, al igual que el resto de los valores, tiene un **tipo**.
</small>

----

En este caso, cuando indicamos 

```haskell
r :: Int -> Bool
```

estamos diciendo que el **tipo** de $r$ es _Int -> Bool_.

**Más adelante vamos a ver como podemos sacarle el jugo a esta hermosa propiedad.** <!-- .element: class="fragment" -->

----

## Geometría