# Recursión

----

Antes de ver este tema vamos a revisar un concepto muy importante:

----

### Problema
## Ejemplo

----

```haskell
inf :: Int
inf = 1 + inf
```

----

```haskell
seven :: a -> Int
seven _ = 7

-- seven inf = ??
```

----

```haskell
fst :: (a, b) -> a
fst (x, _) = x

-- fst (0, inf) = ??
```

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

<small>
    Sabemos que (fib 22) cuesta ~1.000.000 reducciones
</small>

----

```haskell
-- cuantas reducciones?
quin (fib 22)
```

----

### Ejemplo 2

```haskell
-- cuantas reducciones
const 3 (quin (fin 22))
```

----

## Y Haskell??

----

# Lazy Evaluation

----

<!-- .slide: style="text-align: left" -->

### Lazy Evaluation

Evaluación normal con **mejora de eficiencia**

-  _recordar_ que las copias de un argumento son el mismo valor, para no replicar trabajo.