# Geometría

----

## Repaso
### Introducción a Haskell

<!-- .slide: style="text-align: left" -->

Esta sección del taller corresponde a la parte de Geometría de la materia. Sin embargo, por el momento vamos a seguir explorando Haskell así podemos utilizarlo para resolver problemas.

----

Para ello vamos a reforzar la idea de **Función** en _Haskell_.

----

Todas las funciones necesitan declararse. 

```haskell
-- Fahrenheit to Celsius
ftc :: Float -> Float
```

Primero aclaramos qué función vamos a declarar y luego indicamos qué cosas recibe, y qué cosas devuelve.

----

En este caso recibe algo de Tipo _**Int**_ y devuelve algo de Tipo _**Float**_. Pero...

----

### ¿Qué es un Tipo?

Cuando decimos que **algo es de un cierto tipo**, nos referimos a que ese _"algo"_ es un **valor qué pertenece a un determinado conjunto**. 

<small>
    Por ejemplo, cuando decimos que $x$ es de tipo Entero (_Int_ de Haskell), nos referimos a que los valores que puede tomar $x$ son valores enteros, es decir, $x$ pertenece al conjunto de los Enteros ($\mathcal{Z}$ matemático).
</small>

Note: Anticipar idea de expresión indicando lo importante que es cómo _denotar_ un valor.

----

Las **expresiones** son formas de denotar un valor. Es decir el valor es una idea de lo que queremos representar, mientras que una expresión es la manera en la que _hablamos_ de ese valor. 

Note: Anotar en el pizarrón a las expresiones apuntando a los valores que pertenecen a un cierto tipo

----

Luego, se define la función $ftc$ como sigue:

```haskell
ftc :: Float -> Float
ftc x = (x - 32) * 5 / 9
```

<small>
    En este caso estamos diciendo que $ftc$ es una función que dado un $x$ flotante devuelve un flotante, que es la temperatura en celsius para la entrada x en fahrenheit.
</small>

----

### ¿Cómo usamos esta función?

La aplicamos.

----

La aplicación es una de las operaciones que podemos realizar con una función. En haskell lo expresamos con un espacio `" "`.

----

Por ejemplo, lo que en matemática haríamos de esta forma, $ftc(82)$, en haskell es como sigue:

```haskell
r 82.0
-- 27.77777777777778
```

<small>
    aplicamos la función $ftc$ a un valor entero, $82$, obteniendo un valor de salida flotante, _27.77777777777778_.
</small>

----

En terminos generales, podemos aplicar una función cualquiera a un valor cuyo **Tipo** sea el mismo que el **tipo de entrada** de la función. Y el resultado de la aplicación tendrá el tipo de salida de la misma.

----

En el ejemplo anterior

```haskell
ftc 82.0 :: Float
```

----

Como se habrán dado cuenta, el símbolo :: lo hemos utilizado para declarar una función, pero también para decir el tipo de _2.0_ , 'C', o incluso _ftc 2.0_ ¿Qué nos sugiere esto?

----

En haskell, al igual que en matemática, no diferenciamos lo que son funciones de los que son los valores. Es decir, una **función es un valor** que, al igual que el resto de los valores, tiene un **tipo**.

----

En este caso, cuando indicamos 

```haskell
ftc :: Float -> Float
```

estamos diciendo que el **tipo** de $ftc$ es _Float -> Float_ ¿Y esto qué implica? Si las funciones son "procesos" que reciben algo de un cierto tipo y devuelven otra cosa de un cierto tipo, y las funciones tienen un tipo, tiene sentido que una función pueda **recibir una función como parámetro de entrada**. Veamos cómo nos ayuda esto en la siguiente sección.


----
<!-- .slide: style="text-align: left" -->

### Repaso
## Problemas

Escribir expresiones que tengan los siguientes tipos

-  (Int, Int)
-  Float
-  Char
-  Int -> Int
-  Bool -> (Bool, Bool)

----

## Geometría

<small>
    Existen situaciones en las cuales es conveniente expresar un problema a traves de un plano coordenado. Este se compone de dos ejes que representan dos variables. Por ejemplo el crecimiento de una población en función del tiempo.
</small>

<img src="../static/worldGrowth.png" alt="Imagen poblacion" width="250" height="250">

Caso de estudio: _Tenemos una variable, cuyo valor depende de otra variable_.

----

Expresemos, por ejemplo, la superficie de un terreno en función de uno de sus lados.

Note: Escribir el problema matemáticamente, y después en Haskell

----

Sabemos que un punto es un dato en el plano al cual le podemos atribuir un valor, por lo tanto, podemos definir funciones como las siguientes:

```haskell
abscisa :: (Float, Float) -> Float
```

```haskell
abscisa (x, y) = x
```
<!-- .element: class="fragment" -->

```haskell
ordenada :: (Float, Float) -> Float
```

```haskell
ordenada (x, y) = y
```
<!-- .element: class="fragment" -->

Note: preguntar cómo es

----

Supongamos que queremos sumar dos puntos. La suma entre dos puntos la definiremos de la siguiente forma:

```
Sean P = (a, b), Q = (c, d),

P + Q = (a + c, b + d)
```

Note: Hablar sobre recibir varios parámetros en una función

----

Cuando querramos recibir varios parámetros declararemos la función de la siguiente manera: 

*a0 -> a1 -> a2*

Donde *a0* y *a1* son los tipos de entrada, y *a2* es el tipo de salida. _En general_, siempre el último tipo indicado es el tipo de salida. Pero ¿No era que las funciones recibían una cosa y devolvían otra? ¿Una función puede recibir más de una cosa? *Ya veremos...*

----

### Regiones en el plano

Hagamos una función que nos diga si un punta dado *p* pertenece a una cierta región *r*.

----

### Rectas

Una recta es una relación entre dos valores, uno del eje X y otro del eje Y. Entonces es una función y por lo tanto podemos aplicar todas las propiedades que venimos trabajando hasta ahora. 

Note: Hacer que definan una función que me diga si un punta dado está en la recta

----

A veces nos da mayor legibilidad guardar ciertas ideas en variables. 

**Equivalencia**: Así como en matémica decimos "Sea x una variable real" o "Donde f es una función" en haskell tenemos las cláusulas _**let in**_ y _**where**_

Note: Habría que explicar el _let in_, y el _where_

----

**let in**

Cláusula con la forma general:

```haskell
let x1 = e1
    x2 = e2
--  ...
--  xn = en
in expresionQueUsaLasVariables
```

----

**where**

Cláusula con la forma general:

```haskell
expresionQueUsa x1 x2 ... xn
	where x1 = e1
	      x2 = e2
	      ...
	      xn = en
```

----
