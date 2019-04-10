# CONJUNTOS

----

<!-- .slide: style="text-align: left" -->

## Conjunto

Un **conjunto** es una colección de elementos con características similares considerada en sí misma como un objeto.

Se dice que un elemento (o miembro) pertenece al conjunto si está definido como incluido de algún modo dentro de él.

----

Un conjunto suele definirse mediante una **propiedad que todos sus elementos poseen**. Por ejemplo, para los _números naturales_, si se considera la propiedad de ser un número primo, el conjunto de los números primos es:

$P = \{2, 3, 5, 7, 11, 13, \ldots \}$

----

Conocer las distintas propiedades y operaciones que se pueden aplicar a conjuntos nos permite introducir el siguiente concepto de Haskell.

----

# Listas

Note: Mostrar operaciones básicas como funciones.

----

En esta clase vamos a ver algunos de los conceptos más importantes del taller:

-  Bases sobre las listas
-  Cadenas de texto
-  **Listas**

----

En Haskell, las listas son una estructura **homogénea**. Almacena varios elementos del mismo tipo. 

<small>
    Esto significa que podemos crear una lista de enteros o una lista de caracteres, pero no podemos crear una lista que tenga unos cuantos enteros y otros cuantos caracteres.
</small>

----

```haskell
ghci> let lostNumbers = [4, 8, 15, 16, 23, 42]
ghci> lostNumbers
[4, 8, 15, 16, 23, 42]
```

<small>
    Las listas se definen mediante corchetes y sus valores se separan por comas.
</small>

----

En general, se escribe entre '[' y ']' y sus elementos separados por ','

```haskell
[1, 2, 3]
[True,  True, False]
['y', 'o', 'l', 'o']
```

----

```haskell
[1, 2, 'a', 3, 'b', 'c', 4]
```

<small>
    Si intentáramos crear una lista como esta Haskell nos avisaría que los caracteres no son números.
</small>

----

Las cadenas de texto son listas de caracteres.

```haskell
"hello"
['h', 'e', 'l', 'l', 'o']
```

----

Tipo de una lista

```haskell
[2,3,4] :: [Int]
['a', 'b', 'c'] :: [Char]
```

----

## Tipo de [ ] ??

`[] :: [a]` <!-- .element: class="fragment" -->

----

Dos operaciones básicas que podemos realizar con ellas son:

```haskell
(++) :: [a] -> [a] -> [a]
-- función que concatena dos listas

(:) :: a -> [a] -> [a]
-- función que agrega un elemento al principio de la lista
```

----

### Concatenación

```haskell
ghci> [1,2,3,4] ++ [9,10,11,12]
[1,2,3,4,9,10,11,12]
ghci> "hello" ++ " " ++ "world"
"hello world"
ghci> ['w','o'] ++ ['o','t']
"woot"
```

----

### Cons

```haskell
ghci> 'U':"n gato negro"
"Un gato negro"
ghci> 5:[1,2,3,4,5]
[5,1,2,3,4,5]
```

----

`[1,2,3]` es una alternativa sintáctica de `1:2:3:[]`. 

-  `[]` es una lista vacía. Si anteponemos 3 a ella con `:`, obtenemos `[3]`, y si anteponemos 2 a esto obtenemos `[2,3]`.

Note: Desambiguar listas vacias

----

`[], [[]] y [[],[],[]]`

----

## Funciones básicas sobre listas

----

### Head

Toma una lista y devuelve su cabeza. La cabeza de una lista es básicamente el primer elemento.

```haskell
ghci> head [5, 4, 3, 2, 1]
5
```

----

### Tail

Toma una lista y devuelve su cola. En otros palabras,  corta la cabeza de la lista.

```haskell
ghci> tail [5, 4, 3, 2, 1]
[4, 3, 2, 1]
```

----

### Last

Toma una lista y devuelve su último elemento.

```haskell
ghci> last [5, 4, 3, 2, 1]
1
```

----

### Init

Toma una lista y devuelve toda la lista excepto su último elemento.

```haskell
ghci> init [5, 4, 3, 2, 1]
[5, 4, 3, 2]
```

----

### Length

Toma una lista y obviamente devuelve su tamaño.

```haskell
ghci> length [5,4,3,2,1]
5
```

----

### Null

Comprueba si una lista está vacía. Si lo está, devuelve True, en caso contrario devuelve False. Usa esta función en lugar de xs == [] (si tienes una lista que se llame xs).

```haskell
ghci> null [1,2,3]
False
ghci> null []
True
reverse pone del revés una lista.
ghci> reverse [5,4,3,2,1]
[1,2,3,4,5]
```
----

### take

Toma un número y una lista y extrae dicho número de elementos de una lista. Observa.

```haskell
ghci> take 3 [5,4,3,2,1]
[5,4,3]
ghci> take 1 [3,9,3]
[3]
ghci> take 5 [1,2]
[1,2]
ghci> take 0 [6,6,6]
[]
```

Si intentamos tomar más elementos de los que hay en una lista, simplemente devuelve la lista. Si tomamos 0 elementos, obtenemos una lista vacía.

----
### Drop

Funciona de forma similar, solo que quita un número de elementos del comienzo de la lista.

```haskell
ghci> drop 3 [8,4,2,1,5,6]
[1,5,6]
ghci> drop 0 [1,2,3,4]
[1,2,3,4]
ghci> drop 100 [1,2,3,4]
[]
```

----

### Maximum y minimun

Maximun toma una lista de cosas que se pueden poner en algún tipo de orden y devuelve el elemento más grande. Minimum devuelve el más pequeño.

```haskell
ghci> minimum [8,4,2,1,5,6]
1
ghci> maximum [1,9,2,3,4]
9
```
----

### sum

Toma una lista de números y devuelve su suma.
product toma una lista de números y devuelve su producto.

```haskell
ghci> sum [5,2,1,6,3,2,5,7]
31
ghci> product [6,2,1,2]
24
ghci> product [1,2,5,6,7,9,2,0]
0
```

----

### Elem

Toma una cosa y una lista de cosas y nos dice si dicha cosa es un elemento de la lista. Normalmente, esta función es llamada de forma infija porque resulta más fácil de leer.

```haskell
ghci> 4 `elem` [3,4,5,6]
True
ghci> 10 `elem` [3,4,5,6]
False
```

----

## Rangos

----

### Ejemplo

```haskell
ghci> [1..20]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
ghci> ['a'..'z']
"abcdefghijklmnopqrstuvwxyz"
ghci> ['K'..'Z']
"KLMNOPQRSTUVWXYZ"
```

----

```haskell
ghci> [2,4..20]
[2,4,6,8,10,12,14,16,18,20]
ghci> [3,6..20]
[3,6,9,12,15,18]
```

----

```haskell
ghci> [0.1, 0.3 .. 1]
[0.1,0.3,0.5,0.7,0.8999999999999999,1.0999999999999999]
```

Consejo: No utilizar rangos con números en coma flotante.

----

## Listas por Comprensión

----

Si quisiéramos escribir esto en Haskell, podríamos usar algo como 

```haskell
take 10 [2, 4 ..]
```

<small>
    Pero, ¿y si no quisiéramos los dobles de los diez primeros número naturales, sino algo más complejo?
</small>

----

```haskell
ghci> [x*2 | x <- [1..10]]
[2,4,6,8,10,12,14,16,18,20]
```

----

**Agregando condiciones**

```haskell
ghci> [x*2 | x <- [1..10], x*2 >= 12]
[12,14,16,18,20]
```

----

```haskell
ghci> [ x*y | x <- [2,5,10], y <- [8,10,11]]
[16,20,22,40,50,55,80,100,110]
```

----

```haskell
ghci> [ x*y | x <- [2,5,10], y <- [8,10,11], x*y > 50]
[55,80,100,110]
```

----

### Length

----

```haskell
length' :: [a] -> Int
length' xs = ...
```

----

```haskell
length' :: [a] -> Int
length' xs = sum [ 1 | _ <- xs ]
```