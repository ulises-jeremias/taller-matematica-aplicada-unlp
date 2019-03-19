# Logica

**Utilizar sección 1.1 del libro de Algebra y Matemática Discreta de Liliana Alcon. Hasta operadores lógicos. Un par de ejemplos**

Una proposición es una oración declamativa a la cual se le puede asignar un valor
verdad: verdadera (V) o falsa (F). Las proposiciones serán simbolizadas mediantes
letras minúsculas: p, q, r, etc.

**Problemas: (Ejericios para resolver entre todes. Luego mostrar las respuestas correctas)**

- Determinar si los siguientes enunciados son proposiciones.

  - Siete es mayor que doce.
  - Si 6 > 4 entonces 6 > 2
  - Ella es inteligente.
  - Quı́en es?
  - En otros planetas del sistema solar hay diversos tipos de seres vivos
  - De 2 + 3 ≥ 5 + 4 se deduce 3 > 4.
  - Estudiaré música o canto.
  - Cualquier rectángulo tiene cuatro lados.
  - x > 2.

> Definir funcion proposicional

Dada una variable x perteneciente al conjunto universal, se define una **función proposicional**, _p_, en la variable x, como un proceso
que recibe x y devuelve una proposión. Una _proposición_ es una oración declarativa, _ó afirmación_, con un valor de verdad asociado.

En los lenguajes de programación no trabajamos con "oraciones" como tal, sino que utilizamos directamente sus valores de verdad,
es decir, Verdadero o Falso, True o False, un booleano (Bool).

**Veamos un ejemplo**

-  2 es par `Verdadero`
-  5 es par `Falso`
-  1 es par `Falso`

`p(x) = x es par` es una función proposicional. Por qué?

El objetivo del taller es poder llevar los temas de la materia al ámbito de la computación. Para eso vamos a usar un lenguaje en particular, llamado Haskell

> Introducción a Haskell

Haskell es un **lenguaje de programación funcional puro** el cual vamos a utilizar en este taller ya que, a diferencia de lenguajes imperativos (como pueden ser Pascal o R-info), haskell presenta una mayor relación con la matemática. Esto nos permite escribir las *ideas* expresadas matemática, ó naturalmente, directamente en el lenguaje de programación.

> Funciones

¿Cómo se expresan estas ideas? Definiendo funciones. Aunque después vamos a ver el concepto de función más formalmente en la materia, podemos dar una definición más natural.
Una función es una caja que recibe uno más elementos de un cierto *tipo* y devuelve una sóla cosa de algún otro *tipo*. Es importante el concepto de que sólo se devuelve un elemento.


**PROBLEMA**

¿Una función proposicional? ¿qué tipo devuelve? ¿qué recibe?

> Declaración de funciones

En Haskell es muy útil e importante definir las funciones, así como en R-info definían variables. Veamos la sintaxis

**MOSTRAR EN PIZARRON** Paso por paso. Nombre de función. :: tipos, flechas y finalmente el tipo que se devuelve

```haskell
p :: u -> Bool -- u es conjunto universal
```
u representa al conjunto universal
-> Bool quiere decir que devolveremos un valor de verdad, un booleano, es decir que puede ser True o False. (En R-Info lo llamamos V y F)

> Definición de funciones

Luego de declarar una función la definimos. Para eso podríamos decir cuánto vale la función para cada posible valor. Es importante que *sólo podemos tener un resultado para un valor dado* 
Por ejemplo sea:

```haskell
aMayus :: Char -> Char
```
Ésta función recibe un char y un char (en particular, si recibe algo en minúsula, lo devuelve a mayúsucula). Si queremos decir qué valor devuelve para el valor 'a' y para 'b', por ejemplo, escribimos

```haskell
aMayus 'a' = 'A'
aMayus 'b' = 'B'
```

y así podríamos seguir. Lo que estaría **mal** sería definir esto:

```haskell
aMayus 'a' = 'A'
aMayus 'a' = '#'
```

No sólo porque no tiene ningún sentido si no por lo que mencionamos antes **Una función no puede tener dos resultados distintos para la misma entrada**. Claramente, este trabajo de dar el valor para cada posible entrada es tedioso, así que lo escribinos así

```haskell
aMayus x = toUpper x 
```

Analicémoslo. Para referirse a "Cualquier elemento que entre" podemos utilizar una letra cualquiera, en este caso x. Del otro lado del igual estamos llamando a una **expresión**, particularmente, el resultado de usar la función toUpper  (está bien, hicimos trampa).

*nombreDeFunción* *parámetro* = *expresión*

una expresión es algo que puede tomar un valor. Por ejemplo 'c', 2, 1.4 o True. Cuando *aplicamos* una función, ésta nos da un valor. **No se preocupen, vamos a volver a estos conceptos**

> Volviendo a funciones proposicionales

Para definir, e.g., la funcion proposional `r(x): x es mayor que 0` lo hacemos de la siguiente forma:

```haskell
r :: Int -> Bool
r x = x > 0

-- donde x es cualquier valor perteneciente a los Enteros, (Z), (Int).
```

**Equivalencia** (aclarar que llamamos Equivalencia a como definimos en haskell las cosas que ya conociamos en matematica)

En las definicion anterior se pueden observar aspectos de haskell que iremos profundizando a medida que transcurre la materia.

**MOSTRAR COMO SON LOS OPERADORES BOOLEANOS EN HASKELL**

#### Problemas

```
p(n): n es par
q(x): x es divisible por 2
r(x): x es igual 0
c(x): x es la letra 'c'
d(y): y no es la letra 'c'
t(x, y): la suma entre x e y es igual a cero
w(a, b): a es el opuesto de b
h(n, m): n es igual a 0 y m no es la letra 'c'
a(x) : 'x' es la letra 'x' #Esta es una función constante
```

**SOLUCIONES**

```haskell
divide :: (Int, Int) -> Bool
divide (d, x) = x `mod` d == 0

esPar :: Int -> Bool
esPar x = divide (2, x)

p :: Int -> Bool
p n = esPar n

q :: Int -> Bool
q x = divide (2, x)

r :: Int -> Bool
r x = x == 0

c :: Char -> Bool
c x = x == 'c

d :: Char -> Bool
d x = not (c x)
```
