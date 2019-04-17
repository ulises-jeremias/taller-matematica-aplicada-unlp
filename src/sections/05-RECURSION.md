# Recursión

----

Antes de ver este tema vamos a revisar un concepto muy importante:

----

## Ejemplo

----

```haskell
inf :: Int
inf = 1 + inf
```
<!-- .element: contenteditable="true" -->
----

```haskell
seven :: a -> Int
seven _ = 7

-- seven inf = ??
```
<!-- .element: contenteditable="true" -->
----

```haskell
fst :: (a, b) -> a
fst (x, _) = x

-- fst (0, inf) = ??
```
<!-- .element: contenteditable="true" -->
----

## Qué pasa??

----

### Denotacional vs Operacional
# Reducción

----

La reducción es un _sistema de reescritura_. Se usa en distintos ámbitos, pero la esencia es la misma: **Reemplazar subtérminos de una fórmula (o expresión) con otros términos**.

----

En nuestro caso queremos utilizar reducciones para llegar al valor de un expresión. En otras palabras, queremos **reducir** una *expresión* a su *valor*.

----

## Cómo hacemos?

----

### Hasta donde lo hacemos?
## Se reduce infinitamente?!

----

Veamos el siguiente como reduce la expresión:

```haskell
seven inf
```
<!-- .element: contenteditable="true" -->
----

<!-- .slide: style="text-align: left" -->

## Formas de Reducción

-  Forma normal

-  Formal aplicativa

----

## Cual tiene haskell?

Ninguna <!-- .element: class="fragment" -->

----

Para entender las decisiones de implementación del lenguaje vamos a definir unos conceptos claves:

----

## Reducción

-  Redex (reducible expression)
  -  subexpresión que coincide con una instancia del lado izquierdo de una ecuación

-  Forma normal
  Expresión que no contiene redexes

-  Mecanismo de Reducción
    1.  Localizar un redex
    2.  Reemplazarlo
    3.  Repetir hasta que la expresión esté en forma normal

----

-  Normalización
-  La forma normal es única?
-  Ordenes de reducción
    -  Hay una única forma de reducir? Todas equivalentes?

----

## Normalización

-  Forma normal
    -  Expresión que no se puede reducir
    -  _Valor_

-  No toda expresión tiene forma normal!
    -  e.g. **inf**
    -  Valor denotacional, _Bottom_
    -  Valor operacional

----

## Bottom

```haskell
bottom :: a
bottom = bottom
```
<!-- .element: contenteditable="true" -->
----

## Bottom y Funciones

-  Funciones Estrictas
-  Funciones NO Estrictas

----

## Funciones No Estrictas

```haskell
const :: a -> b -> a
const x _ = x

-- const 7 inf = ??
```
<!-- .element: contenteditable="true" -->
<small>
    Si la función precisa el valor de los parámetros para dar un resultado, entonces
    es estricta.
</small>

----

## Orden de Evaluación

----

<!-- .slide: style="text-align: left" -->

### Orden APLICATIVO

Primero los redexes internos

-  Es decir, primero los argumentos y luego la aplicación
-  TODAS LAS FUNCIONES SON ESTRICTAS

----

<!-- .slide: style="text-align: left" -->

### Orden NORMAL

Primeros los redexes externos

-  Primero la aplicación y, si aún están, los argumentos
-  Hay funciones estrictas y no estrictas

----

## Ejemplos

----

### Ejemplo 1

```haskell
quin x = x + x + x + x + x
```
<!-- .element: contenteditable="true" -->
<small>
    Sabemos que (fib 22) cuesta ~1.000.000 reducciones
</small>

----

```haskell
-- cuantas reducciones?
quin (fib 22)
```
<!-- .element: contenteditable="true" -->
----

### Ejemplo 2

```haskell
-- cuantas reducciones
const 3 (quin (fin 22))
```
<!-- .element: contenteditable="true" -->
----

## Y Haskell??

----

# Lazy Evaluation

----

<!-- .slide: style="text-align: left" -->

### Lazy Evaluation

Evaluación normal con **mejora de eficiencia**

-  _recordar_ que las copias de un argumento son el mismo valor, para no replicar trabajo.

----

#### Ejemplo

```haskell
ones = 1:ones

-- take 10 ones = ??
```
<!-- .element: contenteditable="true" -->
----

# Currificación

----

```haskell
inc :: Int -> Int
inc x = 1 + x

suma :: Int -> Int -> Int
suma x y = x + y

-- inc x = suma 1 x ??
```
<!-- .element: contenteditable="true" -->
----

# Funciones Lambda

----

-  Necesita una función que no vamos a referenciar, tener un nombre??
-  Si queremos devolver una función como valor de retorno
    -  Necesita estar previamente definida??

----

### Ejemplo

```haskell
inc :: Int -> Int
-- inc x = 1 + x
inc = \x -> 1 + x
```
<!-- .element: contenteditable="true" -->
----

# Recursión

----

```haskell
let list = [1, 2, 5, 8, 0, 10]

list !! 3
-- 8
```
<!-- .element: contenteditable="true" -->
----

```haskell
let fibs = 0 : 1 : [ n | x <-[2..], let n = ((fibs !! (x-1)) + (fibs !! (x-2))) ]

fib :: Int -> Int
fib x = fibs !! x
```
<!-- .element: contenteditable="true" style="font-size: 17px" -->
----

```haskell
-- Analizar
fibs' a b = a:fibs' b (a+b)
-- fibs = fibs' 0 1 ??
```
<!-- .element: contenteditable="true" -->
----

Con recursión,

```haskell
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib n = ... ??
```

----

```haskell
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib n = fib (n-1) + fib (n-2)
```