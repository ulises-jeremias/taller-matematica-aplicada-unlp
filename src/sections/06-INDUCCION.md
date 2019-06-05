# Inducción

----

En los últimos encuentros estuvimos creando funciones recursivas que nos pueden dar mucha potencia. Pero también vimos que pueden existir problemas con ellas.

----

**Ejemplo**

```haskell
fact 0 = 1
fact n = n * fact (n - 1)
```

-  ¿Siempre termina? <!-- .element: class="fragment" -->
-  ¿Como podemos asegurarlo? <!-- .element: class="fragment" --> 

Note: ¿QUÉ PREGUNTAS SURGEN SOBRE ELLA? ¿CUÁL ES LA PESADILLA?

----

**Ejemplo**

```haskell
sumatoria f 0 = 0
sumatoria f i = f 0 + (sumatoria f (i - 1))

sumatoria' f 0 = 0
sumatoria' f i = (sumatoria f (i - 1)) + (f 0)
```

-  ¿Hacen lo mismo? <!-- .element: class="fragment" -->
-  ¿Cómo podemos decirlo? <!-- .element: class="fragment" -->

Note: ¿QUÉ NOS ENCANTARÍA DECIR DE ESTAS DOS FUNCIONES?

----

Usando **Inducción** no sólo vamos a construir funciones recursivas _**sabiendo**_ que terminan, si no que además vamos a poder decir un montón de propiedades más sobre ellas.

----

### Definición Matemática
## Repaso

Note: USTEDES VIERON INDUCCIÓN CON EL FIN DE HACER CIERTAS DEMOSTRACIONES SOBRE LOS NUMEROS NATURALES

----

En la teoría vieron un conjunto de axiomas, sobre los cuales se basan los fundamentos para hacer inducción. Uno de ellos es el siguiente:

----

<!-- .slide: style="text-align: left" -->

### Axioma Inductivo

Sea $A \subseteq \mathbb{N}$, si se cumple que:

-  $1 \in A$
-  Cualquiera sea $x$, si $x \in A$, entonces $x + 1 \in A$

Entonces $A = \mathbb{N}$

Note: Hablar del conjunto de Verdad V(P) asociado a un p(n)
----

Con ésto se puede decir que si un conjunto de _Verdad_ satisface éstas reglas, entonces ese conjunto de verdad es $\mathbb{N}$. Pero, _¿Qué tienen de especiales éstas reglas para permitir decir algo tan fuerte?_

Note: aclarar que vamos a mirar estas reglas de otra manera
----

<!-- .slide: style="text-align: left" -->

### Conjuntos Inductivos

Un conjunto se dice **Inductivo**, o *definido* **inductivamente**, si se define en base a una colección de reglas que se separan en dos tipos:

- **Reglas Base** Anuncian qué elementos están *incondicionalemente* en el conjunto.

- **Reglas Inductivas** Anuncian que un elemento está en el conjunto si otros lo están.

Note: Es una forma más de definir conjuntos. Así como estaba por extensión y por comprensión, está ésta forma. Notar que pueden haber varias de cada una

----

### Ejemplo

Definamos el conjunto $\mathcal{A}$ que está compuesto por todas las cadenas que tienen **n** caracteres *S*, y al final una *Z*. Pediremos el conjunto que satisfaga las siguientes reglas:

- *Z* $\in \mathcal{A}$.
 <!-- .element: class="fragment" -->

- Si **e** $\in \mathcal{A}$, entonces S**e** $\in \mathcal{A}$.
 <!-- .element: class="fragment" -->

- $\mathcal{A}$ es el **menor** (con la relación de inclusión) conjunto que satisface las reglas anteriores.
 <!-- .element: class="fragment" -->

Note: hacer los dibujos de los posibles conjuntos $\mathcal{A}$

----

¿Qué propiedades tiene éste conjunto?

Tiene infinitos elementos 
<!-- .element: class="fragment" -->

Todos sus elementos satisfacen una u otra de las reglas
<!-- .element: class="fragment" -->

Todos sus elementos son finitos
<!-- .element: class="fragment" -->

----

Otra propiedad a destacar es: Todo elemento $w \in \mathcal{A}$ se forma a partir de otra cadena $w'$, y una cadena de elementos ordenados de ésta forma siempre termina

En el caso anterior, _Z_ es parte de _SZ_ es parte de _SSZ_ es parte de _SSSZ_.
<!-- .element: class="fragment" -->

Cualquier cadena de ésta forma, termina en Z.
<!-- .element: class="fragment" -->

Note: Bueno genial ¿y con ésto qué? ¿Qué significa ésto? ¿Qué es éste conjunto? Nada, es pura sintaxis.

----

### Ejemplo
# Listas

----

Dado un tipo cualquier **a**, definimos inductivamente el conjunto `[a]` con las siguientes reglas:

-  _[] :: [a]_
<!-- .element: class="fragment" -->

-  si _x :: a_ y _xs :: [a]_ entonces _x:xs :: [a]_
<!-- .element: class="fragment" -->

----

```haskell
len :: [a] -> Int
len [] = ...
len (x:xs) = ... len xs ...
```

----

```haskell
len :: [a] -> Int
len [] = 0
len (x:xs) = 1 + len xs
```

----

<!-- .slide: style="text-align: left" -->

### Observaciones

-  Hay una ecuación por cada caso de la definición de [a]
-  Los paréntesis son necesarios; si no dice (len x):xs
-  La función `len` está definida para toda lista (siempre termina y da un valor definido). Esta propiedad está garantizada por la construcción de `len`, y por la naturaleza inductiva de las listas.
-  Se pueden demostrar propiedades de `len` por inducción estructural en la lista argumento.

----

<!-- .slide: style="text-align: left" -->

## Propiedad

Demostrar que para toda lista xs, su longitud es mayor o igual que cero.

----

<!-- .slide: style="text-align: left" -->

## Demostracion

**_Por inducción en la estructura de xs_**

-  **Caso base**: xs = [ ], P([])

```
len [] = 0 [por def. de len], por lo tanto, len [] ≥ 0
```

-  **Caso inductivo**: xs = x:xs', P(xs') $\rightarrow$ P(x:xs')

**HI)** Asumimos len xs' ≥ 0 , (hipótesis inductiva).

```
len (x:xs')
= [por def. de len]
1 + len xs' 
≥ [por HI y aritmética]
1 ≥ 0
```

----

## Siguiente clase!

----

# Tipos de Datos

----

<!-- .slide: style="text-align: left" -->

### Para definir un tipo de datos podemos:

establecer qué forma tendrá cada elemento, y dar un mecanismo único para inspeccionar cada
elemento entonces: **_TIPO ALGEBRAICO_** <br />ó<br /> determinar cuáles serán las operaciones que
manipularán los elementos, SIN decir cuál será la forma exacta de éstos o aquéllas
entonces: **_TIPO ABSTRACTO_**

----

<!-- .slide: style="text-align: left" -->

**Tipos Algebraicos**

- dar la forma de los elementos
- dar un mecanismo único de acceso

**Tipos Abstractos**

- dar sólo las operaciones
- NO dar la forma de elementos ni operaciones

----

<!-- .slide: style="text-align: left" -->

**Tipos predefinidos**

- a->b: tipo abstracto con sintaxis especial
- Bool, (a,b): tipos algebraicos con sintaxis especial
- Int, Float, Char: tipos abstractos con componentes
algebraicos y sintaxis especial

----

# Tipos Algebraicos

----

**¿Cómo damos en Haskell la forma de un
elemento de un tipo algebraico?**

Mediante **constantes** llamadas _constructores_.

----

## Constructores

- nombres con mayúsculas
- no tienen asociada una regla de reducción
- pueden tener argumentos

```haskell
False :: Bool
True :: Bool
```

----

_La cláusula **data**_

- introduce un nuevo tipo algebraico
- introduce los nombres de los constructores
- define los tipos de los argumentos de los constructores

**Ejemplos:**

```haskell
data SensacionTermica = HaceFrio | HaceCalor
data Shape = Circle Float | Rect Float Float
```

----

```haskell
data Shape = Circle Float | Rect Float Float

-- Ejemplos de elementos:
c1 = Circle 1.0
c2 = Circle (4.0-3.0)
r1 = Rect 2.5 3.0

-- Ejemplos de funciones que arman Shapes:
circuloPositivo x = Circle (abs x)
cuadrado x = Rect x x
```

----

**¿Cuál es el mecanismo único de acceso?**

**Pattern matching (correspondencia de patrones (?))**

- Pattern: expresión especial
  - sólo con constructores y variables sin repetir
  - argumento en el lado izquierdo de una ecuación

- Matching: operación asociada a un pattern
  - inspecciona el valor de una expresión 
  - puede fallar o tener éxito
  - si tiene éxito, liga las variables del pattern

----

```haskell
area :: Shape -> Float
area (Circle radio) = pi * radio^2
area (Rect base altura) = base * altura

isCircle :: Shape -> Bool
--isCircle1 (Circle radio) = True
--isCircle1 (Rectangle base altura) = False
isCircle (Circle _) = True
isCircle _ = False
```

----

<!-- .slide: style="text-align: left" -->

### Tipos Algebraicos

**Podemos clasificarlos en:**

- **Enumerativos** (SensacionTermica, Bool)
  - Sólo constructores sin argumentos
- **Productos** (Complex, Tuplas, registros)
  - Un único constructor con varios argumentos
- **Sumas** (Shape, Maybe, Either, Helado)
  - Varios constructores con argumentos
- **Recursivos** (Listas, árboles)
  - Utilizan el tipo definido como argumento

----

## Tipos Recursivos

**Un tipo algebraico recursivo**

- tiene al menos uno de los constructores con el tipo que se define como argumento
- es la concreción en Haskell de un conjunto definido inductivamente

----

## Ejemplos?

----

```haskell
data Nat = Zero | Succ Nat
```

----

```haskell
evalN :: Nat -> Int
evalN Zero = ...
evalN (Succ x) = ... evalN x ...
```

----

```haskell
evalN :: Nat -> Int
evalN Zero = 0
evalN (Succ x) = 1 + evalN x
```

----

```haskell
addN :: Nat -> Nat -> Nat
addN Zero m = m
addN (Succ n) m = Succ (addN n m)
```

----

### Practica

Definir las siguientes funciones sobre listas

- any, devuelve True si algún elemento de una lista es True.

- squares, dada una lista de números, devuelve la lista de sus cuadrados.

- order, dada una lista de pares ordenados de números, devuelve la lista de aquellos
cuya primer componente es menor que el triple de la segunda.

----

- moreThan, dada una lista de listas xss y un número n, devuelve la lista de aquellas
listas de xss que tienen longitud mayor que n.

----

Definir el conjunto de Expresiones booleanas (con and y not alcanza). Construir la función necesaria para evaluar.	
