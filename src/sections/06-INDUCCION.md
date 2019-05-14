# Inducción

----
En los últimos encuentros estuvimos creando funciones recursivas, que como vimos nos pueden dar mucha potencia. Pero también vimos que puede haber problemas con ellas
----

fact 0 = 1
fact n = n * fact (n - 1)

¿Siempre termina? <!-- .element: class="fragment" -->
¿Podemos asegurarlo? <!-- .element: class="fragment" --> 

----

```haskell
sumatoria f 0 = 0
sumatoria f i = f 0 + (sumatoria f (i - 1)

sumatoria' f 0 = 0
sumatoria' f i = (sumatoria f (i - 1) + f 0
```

¿Hacen lo mismo? ¿Cómo podemos decirlo?

----

Usando Inducción, no sólo vamos a construir funciones recursivas sabiendo que terminan, si no que además vamos a poder decir un montón de propiedades más sobre ellas

----
### Repaso Matemático

En la teoía vieron un conjunto de axiomas, sobre los cuales basaron los fundamentos para hacer inducción. Uno de ellos decía lo siguiente:

----

Dado A, un subconjunto de N, si se cumple que:
a) 1 pertenece a N
b) cualquiera sea x, si x pertenece a A, entonces x + 1 pertence A

Entonces A = N

----

Con ésto podían decir que si un conjunto de Verdad satisfacía éstas reglas, entonces ese conjunto de verdad era N ¿Qué tienen de especiales éstas reglas para permitir decir algo tan potente?

----

### Conjuntos inductivos

Un conjunto se dice **inductivo**,o *definido* **inductivamente** si ésta definición es una colección de reglas que se separan en dos tipos

-> Reglas Base: Anuncian qué elementos están *incondicionalemente* en el conjunto

-> Reglas inductivas: Anuncian que un elemento está en el conjunto si otros lo están

----

### Ejemplo

Definamos el conjunto **A** que está compuesto por todas las cadenas que tienen **n** caracteres *S*, y al final una*Z*. Pediremos el menor conjunto que satisfaga las siguientes reglas:

- *Z* pertenece a **A** 
<!-- .element: class="fragment" -->
- si **e** pertenece a **A**, entonces *S***e** pertenece a **A**
 <!-- .element: class="fragment" -->
- **A** es el **menor** conjunto que satisface las reglas anteriores
 <!-- .element: class="fragment" -->

Note: hacer los dibujos de los posibles conjuntos **A**

----

Note: Hacer juntos la definición de Lista

----

Note: Dar la definición de función recursiva por inducción en la estructura
