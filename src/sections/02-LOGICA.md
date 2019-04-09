# Lógica

----

## Fundamento básicos
### Repaso

----

<!-- .slide: style="text-align: left" -->

### Proposición

Oración declarativa a la cual se le puede asignar un valor verdad: _**verdadera (V)**_ o _**falsa (F)**_. 

Las proposiciones serán simbolizadas mediantes letras minúsculas: $p$, $q$, $r$, ...

----

### Ejercicios de repaso

----

_Determinar si los siguientes enunciados son proposiciones._

  - Siete es mayor que doce.
  - Si 6 > 4 entonces 6 > 2. <!-- .element: class="fragment" -->
  - Ella es inteligente. <!-- .element: class="fragment" -->
  - Quı́en es? <!-- .element: class="fragment" -->
  - En otros planetas del sistema solar hay diversos tipos de seres vivos. <!-- .element: class="fragment" -->
  - De 2 + 3 ≥ 5 + 4 se deduce 3 > 4. <!-- .element: class="fragment" -->
  - Estudiaré música o canto. <!-- .element: class="fragment" -->
  - Cualquier rectángulo tiene cuatro lados. <!-- .element: class="fragment" -->
  - x > 2. <!-- .element: class="fragment" -->

----

<!-- .slide: style="text-align: left" -->

### Función proposicional

Dada una variable $x$ perteneciente al conjunto universal, se define una **función proposicional**, $p$, en la variable $x$, como un proceso que recibe $x$ y _**devuelve una proposión**_.

Una _proposición_ es una oración declarativa, _ó afirmación_, con un valor de verdad asociado.

----

<!-- .slide: style="text-align: left" -->

En los lenguajes de programación no trabajamos con _"oraciones"_ como tal, sino que utilizamos directamente sus valores de verdad, es decir, Verdadero o Falso, _True_ o _False_, un **booleano** (Bool).

----

<!-- .slide: style="text-align: left" -->

### Veamos unos ejemplos

-  2 es par
   **Verdadero** <!-- .element: class="fragment" -->
-  5 es par <!-- .element: class="fragment" -->
   **Falso** <!-- .element: class="fragment" -->
-  1 es par <!-- .element: class="fragment" -->
   **Falso** <!-- .element: class="fragment" -->


<div data-markdown>
    <br />

    <!-- .element: class="fragment" -->
    $p(x) = x$ es par, es una **función proposicional**. Por qué?
    
    <br />
    <br />

    El objetivo del taller es poder llevar los temas de la materia al ámbito de la computación. Para eso vamos a usar un lenguaje en particular, llamado **Haskell**.

    <br />
    <br />
</div>

----

## Introducción a Haskell

----

<!-- .slide: style="text-align: left" -->

### Haskell

- Es un **lenguaje de programación funcional puro**.
- Lo utilizamos en el taller dado que presenta mayor relación con la matemática.
  - A diferencia de lenguajes imperativos como R-Info o Pascal.
- Esto permite escribir las ideas expresadas matemática, ó naturalmente, _directamente_ en el lenguaje de programación.

----

### ¿Cómo se expresan estas ideas?

Definiendo funciones.

----

Aunque después vamos a ver el concepto de función más formalmente en la materia, podemos dar una definición más natural:

<small class="fragment">
  Una _**función**_ es una caja que recibe uno, o más, elementos de un cierto _tipo_ y devuelve una sóla cosa de algún otro _tipo_. Es importante el concepto de que sólo se devuelve un elemento.
</small>

----

En Haskell es muy útil e importante declarar las funciones, así como en R-Info se definían variables. Veamos como se declaran y definen paso a paso.

Note: Mostrar en el pizarron paso a paso como declarar y definir una función.

----

<small>
  Esta función recibe un número entero (Int) y retorna el doble de ese número (Int).
</small>

```haskell
-- | double 2 = 4
-- | double 3 = 6
-- | double 4 = 8
-- | double (double 2) = ?
double :: Int -> Int
```

----
Luego de declarar una función la definimos. Para esto podríamos decir cuánto vale la función para cada posible valor. Es importante que sólo podemos tener un resultado para un valor dado. Por ejemplo:

----


Algo que estaría **mal** es lo siguiente:

```haskell
double 2 = 4
double 2 = 3
```

----

No sólo porque no tiene ningún sentido si no que, por lo que mencionamos antes, **Una función NO puede tener dos resultados distintos para el mismo valor de entrada**.

----

### Definimos double

<small>
  Claramente, este trabajo de dar el valor para cada posible entrada es tedioso, así que la definimos como se puede ver a continuación:
</small>

```haskell
double :: Int -> Int
double x = 2 * x
```
<!-- .element: class="fragment" -->

----

### Problema

Una _función proposicional_, **¿qué tipo devuelve?** **¿qué recibe?**

----

### Función proposicional

Una funcion, en este caso proposicional, en Haskell debe declararse,

```haskell
p :: u -> Bool -- u es conjunto universal
```

- **u** representa al conjunto universal
- **-> Bool** quiere decir que devolveremos un valor de verdad, un _booleano_, es decir que los posibles resultados de la función son _True_ o _False_. _(En R-Info lo llamamos V y F)_

----

Para definir, e.g., la funcion proposional

_$r$($x$): $x$ es mayor que $0$_

lo hacemos de la siguiente forma:

```haskell
r :: Int -> Bool
r x = x > 0

-- donde x es cualquier valor perteneciente
-- a los Enteros, (Z), (Int).
```

<small>
  En las definicion anterior se pueden observar aspectos de haskell que iremos profundizando a medida que transcurre el taller.
</small>

----

### Equivalencias
## Operadores en Haskell

----

### Operadores Booleanos

```haskell
True && False   -- | AND lógico
True || False   -- | OR lógico
not True        -- | negación lógica
```

----

### Operadores Aritméticos

```haskell
2 + 3   -- | suma
3 - 2   -- | resta
4 * 2   -- | producto
1 / 2   -- | division
  .
  .
  .
```

----

## Operadores relacionales

```haskell
4 < 6    -- | menos que
3 <= 9   -- | menor o igual que
8 == 7   -- | igualdad
0 /= 1   -- | desigualdad
3 >= 2   -- | mayor o igual que
2 > 3    -- | mas que
```

----

## Problemas

Dadas las siguientes funciones proposicionales,

```haskell
-- Evalúa si un número divide a otro
-- divide (2, 4) = True
-- divide (3, 4) = False
divide :: (Int, Int) -> Bool

-- Evalúa si un número es par
-- esPar 2 = True
-- esPar 3 = False
esPar :: Int -> Bool
```

----

```haskell
divide :: (Int, Int) -> Bool
divide (d, x) = mod x d == 0

esPar :: Int -> Bool
esPar x = divide (2, x)
```

----

### Repasamos cosas de Haskell

```haskell
'c'   :: Char  -- caracter 'c' es de tipo Char
2     :: Int   -- 2 es de tipo Int, es decir, 2 pertenece a Z
True  :: Bool  -- True es de tipo Bool
False :: Bool  -- False es de tipo Bool
```

----

Definir las siguientes funciones

- $p$($n$): $n$ es par
- $q$($x$): $x$ es divisible por $2$
- $r$($x$): $x$ es igual $0$
- $c$($x$): $x$ es la letra 'c'
- $d$($y$): $y$ no es la letra 'c'
- $t$($x$, $y$): la suma entre $x$ e $y$ es igual a cero
- $w$($a$, $b$): $a$ es el opuesto de $b$
- $h$($n$, $m$): $n$ es igual a $0$ y $m$ no es la letra 'c'
- $a$($x$): 'x' es igual a 'x'

----

**SOLUCIONES**

```haskell
p :: Int -> Bool
p n = esPar n

q :: Int -> Bool
q x = divide (2, x)

r :: Int -> Bool
r x = x == 0

c :: Char -> Bool
c x = x == 'c'

d :: Char -> Bool
d x = not (c x)

t :: (Int, Int) -> Bool
t (x, y) = x + y == 0

w :: (Int, Int) -> Bool
w (a, b) = a == -b

h :: (Int, Char) -> Bool
h (n, m) = n == 0 && not (c m)

a :: u -> Bool
a x = True
```