## Organizacion

Somos 2 confirmados, 1 mas puede ser.

Tener con anticipacion la lista de alumnos de Turno 1.
Primer encuentro, explicarles la razon de todo, formulario, etc, etc.
Plantear la necesidad de hacer las PRACTICAS!!

Ir a las comisiones un jueves para una comision y un lunes para la otra ?? 
Ir como ayudantes los lunes y clase de aplicaciones los miercoles <pre-Runco>. !!
Despues de terminar un tema (practica).

Subir material antes y hacer consulta despues.

Pedir dar sucesiones e induccion cuanto antes.

## Temas y propuesta

### Logica

**Utilizar sección 1.1 del libro de Algebra y Matemática Discreta de Liliana Alcon.**

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

Para responder analicemos lo siguiente:

**INSERTE AQUI TECNICA DE RECUADROS**

**Equivalencia** (aclarar que llamamos Equivalencia a como definimos en haskell las cosas que ya conociamos en matematica)

Una funcion proposicional en Haskell antes debe declararse

```haskell
p :: u -> Bool -- u es conjunto universal
```
u representa al conjunto universal
-> Bool quiere decir que devolveremos un valor de verdad, un booleano, es decir que puede ser True o False. (En R-Info lo llamamos V y F)

Para definir, e.g., la funcion proposional `r(x): x es mayor que 0` lo hacemos de la siguiente forma:

```haskell
r :: Int -> Bool
r x = x > 0

-- donde x es cualquier valor perteneciente a los Enteros, (Z), (Int).
```

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
