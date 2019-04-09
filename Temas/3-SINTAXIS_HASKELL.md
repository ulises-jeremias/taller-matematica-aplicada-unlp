#Sintaxis

----

#GHCI

GHC un compilador para código escrito en Haskell. Ghci es un ambiente interactivo donde pueden _*evaluarse expresiones*_ e _**Interpretarse programas**_

----


#Usando scripts

En cualquier editor de texto escribiremos nuestro código. Lo guardamos con una extensión .hs. Por ejemplo, *el_mejor_programa.hs*
Una vez que guardamos nuestro código, en la misma ubicación dónde está el archivo iniciamos _ghci_ y con el comando _:l_ cargamos el código. Con el script anterior sería:
:l el_mejor_programa.hs
----


#Usando nuestras funciones

Una vez que cargamos nuestro módulo podemos usar las funciones que creamos

Note: Hacerlos que carguen algunas de las funciones que definieron
----


#Jugo para funciones

----

#Pattern Matching

A veces puede ser útil especificar bien los casos "particulares" para nuestras funciones. Es decir, qué cosas específicas cuando nos llega un valor de un cierto tipo. 

```haskell
buscadorDeSietes :: Int -> String
buscadorDeSietes 7 = "Uyy, un sieteeee ¡Genial!"
buscadorDeSietes x = "Meh, no me interesa"
```

Cuando nuestra entrada "matchea" con el 7 podemos decirle que devuelve ese string, si no, otra cosa

----

También podemos indicar cosas que no me interesan. Para eso uso el caracter '_'

```haskell
ceroFobico :: (Int,String) -> String
ceroFobico (0,_) = "Diu, tenes un cero al lado"
ceroFobico (_,str) = str
```
----

Después veremos otros usos del pattern matching

----

#Guardas

Otra forma de analizar un valor entrada, es pidiendo que cumpla cierta proposición. Para ello usamos **guardas**. Una guarda está compuesta por una función proposicional con la variable de entrada y un valor que retorna la función en caso de cumplirse. Al tener varias guardas, se analiza la primera, y si esta falla se continúa analizando la siguiente. Así hasta que alguna de verdadero	

----

```haskell
succPositivos x
     | x>0 = x+1
     | x <= 0 = x
```
Se pone el nombre de la función junto con sus parámetros y luego, **identando** se ubican las guardas (indicadas con |) y luego se define el valor a devolver para cada una
