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

----

**Ejemplo**

```haskell
sumatoria f 0 = 0
sumatoria f i = f 0 + (sumatoria f (i - 1)

sumatoria' f 0 = 0
sumatoria' f i = (sumatoria f (i - 1) + f 0
```

-  ¿Hacen lo mismo? <!-- .element: class="fragment" -->
-  ¿Cómo podemos decirlo? <!-- .element: class="fragment" -->

----

Usando **Inducción** no sólo vamos a construir funciones recursivas _**sabiendo**_ que terminan, si no que además vamos a poder decir un montón de propiedades más sobre ellas.

----

### Definición Matemática
## Repaso

----

En la teoía vieron un conjunto de axiomas, sobre los cuales se basan los fundamentos para hacer inducción.

----

<!-- .slide: style="text-align: left" -->

### Axioma

Sea $A \subseteq \mathcal{N}$, si se cumple que:

-  $1 \in \mathcal{N}$
-  Cualquiera sea $x$, si $x \in A$, entonces $x + 1 \in A$

Entonces $A = \mathcal{N}$

----

Con ésto se puede decir que si un conjunto de _Verdad_ satisface éstas reglas, entonces ese conjunto de verdad es $\mathcal{N}$. Pero, _¿Qué tienen de especiales éstas reglas para permitir decir algo tan fuerte?_

----

<!-- .slide: style="text-align: left" -->

### Conjuntos Inductivos

Un conjunto se dice **Inductivo**, o *definido* **inductivamente**, si se define en base a una colección de reglas que se separan en dos tipos:

- **Reglas Base** Anuncian qué elementos están *incondicionalemente* en el conjunto.

- **Reglas Inductivas** Anuncian que un elemento está en el conjunto si otros lo están.

----

### Ejemplo

Definamos el conjunto $\mathcal{A}$ que está compuesto por todas las cadenas que tienen **n** caracteres *S*, y al final una *Z*. Pediremos el menor conjunto que satisfaga las siguientes reglas:

- *Z* pertenece a $\mathcal{A}$

- Si **e** pertenece a $\mathcal{A}$, entonces *S* **e** pertenece a $\mathcal{A}$.
 <!-- .element: class="fragment" -->

- $\mathcal{A}$ es el **menor** conjunto que satisface las reglas anteriores.
 <!-- .element: class="fragment" -->

Note: hacer los dibujos de los posibles conjuntos $\mathcal{A}$

----

Note: Hacer juntos la definición de Lista.

----

Note: Dar la definición de función recursiva por inducción en la estructura.
