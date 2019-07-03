# Esquemas

----

## Definiciones

```haskell
succl :: [Int] -> [Int]
-- suma uno a cada elemento de la lista

upperl :: [Char] -> [Char]
-- pasa a mayúsculas cada carácter de la lista

test :: [Int] -> [Bool]
-- cambia cada número por un booleano que
-- dice si el mismo es cero o no
```

----

### Esquema de Recursión sobre Listas

```haskell
succl :: [Int] -> [Int]
succl [] = ...
succl (n:ns) = ... n ... succl ns ...

upperl :: [Char] -> [Char]
upperl [] = ...
upperl (c:cs) = ... c ... upperl cs ...

test :: [Int] -> [Bool]
test [] = ...
test (x:xs) = ... x ... test xs ...
```

----

```haskell
succl [] = []
succl (n:ns) = (n + 1) : succl ns

upperl [] = []
upperl (c:cs) = upper c : upperl cs

test [] = []
test (x:xs) = (x == 0) : test xs
```

Alguna similitud en la estructura??
<!-- .element: class="fragment" -->

----

```haskell
succl [] = []
succl (n:ns) = (\n -> n + 1) n : succl ns

upperl [] = []
upperl (c:cs) = (\c -> upper c) c : upperl cs

test [] = []
test (x:xs) = (\n -> n == 0) x : test xs
```

Reescribimos las funciones para que no dependan del contexto.

----

## Esquema de map

Procedemos con la abstracción

```haskell
map :: ??
map ? [] = []
map ? (x:xs) = ? x : map ? xs
```

----

Completamos la definición

```haskell
map :: ??
map f [] = []
map f (x:xs) = f x : map f xs
```

----

Como la usamos??

```haskell
-- succl' = map (\n -> n + 1)
succl' = map (+1)

-- upperl' = map (\c -> upper c)
upperl' = map upper

-- test = map (\n -> n == 0)
test' = map (==0)
```

----

Agregamos el tipo

```haskell
map :: (a -> b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs
```

----

## Mas funciones

```haskell
masQueCero :: [Int] -> [Int]
-- retorna la lista que sólo contiene los números
-- mayores que cero, en el mismo orden

noVacias :: [[a]] -> [[a]]
-- retorna sólo las listas no vacías
```

----

```haskell
masQueCero [] = ...
masQueCero (x:xs) = ... x ... masQueCero xs ...

noVacias [] = ...
noVacias (xs:xss) = ... xs ... noVacias xss ...
```

----

```haskell
masQueCero [] = []
masQueCero (c:cs) = if (c > 0) then c : masQueCero cs
                               else masQueCero cs

noVacias [] = []
noVacias (xs:xss) = if (null xs) then noVacias xss
                                 else xs : noVacias xss
```

----

```haskell
masQueCero [] = []
masQueCero (c:cs) = if (\x -> x > 0) c then c : masQueCero cs
                                       else masQueCero cs

noVacias [] = []
noVacias (xs:xss) =
    if (\xs -> not (null xs)) xs then xs : noVacias xss
                                 else noVacias xss
```

----

## Esquema del Filter

```haskell
filter :: ??
filter ? [] = []
filter ? (x:xs) = if (? x) then x : filter xs
                           else filter xs
```

----

Completamos la definición

```haskell
filter :: ??
filter p [] = []
filter p (x:xs) = if (p x) then x : filter xs
                           else filter xs
```

----

Como lo usamos?

```haskell
-- masQueCero' = filter (\x -> x > 0)
masQueCero' = filter (>0)

-- noVacias' = filter (\xs -> not (null xs))
noVacias' = filter (not . null)
```

----

```haskell
filter :: (a -> Bool) -> [a] -> [a]
filter p [] = []
filter p (x:xs) = if (p x) then x : filter xs
                           else filter xs
```
