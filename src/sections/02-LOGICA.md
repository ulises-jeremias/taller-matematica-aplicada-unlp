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
    <!-- .element: class="fragment" -->
    $p(x) = x$ es par, es una **función proposicional**. Por qué?
    
    <br />
    <br />

    Para responder analicemos lo siguiente:

    <br />
    <br />
</div>

<div data-markdown>
    <!-- .element: class="fragment" style="text-align: center" -->

    **VEAMOS EL PIZARRÓN**
</div>

----

## Equivalencias

----

### Función proposicional

Una funcion proposicional en Haskell debe declararse,

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

En las definicion anterior se pueden observar aspectos de haskell que iremos profundizando a medida que transcurre el taller.

----

### Operadores lógicos

----

## Problemas

Dadas las siguientes funciones proposicionales,

```haskell
-- Evalúa si un número divide a otro
-- divide (2, 4) == True
-- divide (3, 4) == False
divide :: (Int, Int) -> Bool

-- Evalúa si un número es par
-- esPar 2 == True
-- esPar 3 == False
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
- $a$($x$): 'x' es la letra 'x'

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
```