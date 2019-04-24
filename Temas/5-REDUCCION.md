### Reducción

----

Hasta ahora, venimos pensando en lo denotacional

Hoy veremos lo operacional: Reducción


----

La reducción es un sistema de reescritura. Se usa en distintos ámbitos, pero la esencia es la misma: Reemplazar subtérminos de una fórmula (o expresión) con otros términos.

----

En nuestro caso queremos utilizar reducciones para llegar al valor de un expresión. En otras palabras, queremos **reducir** una *expresión* a su *valor*

----

¿Cómo hacemos eso? 
Usamos las ecuaciones que definimos. Si una expresión utiliza algo del lado izquierdo de la ecuación, lo reemplazamos por lo que está del lado derecho

Note: Hacer ejemplos en el pizarrón

----

Cuando llegamos a algo que no se puede reducir más, decimos que llegamos
a una forma normal. Si no, quiere decir que hay expresiones que tiene subexpresiones, o términos, para reemplazar. A esta subexpresión la llamamo **Redex**.

----

Cuando Haskell computa algo, lo que hace en realidad es reducir "Redexes" hasta su forma normal.

----
**Pero**

-> Una expresión, ¿siempre llega a una forma normal?

-> Si llega, ¿es única?

-> ¿Hay más de una forma de reducir?

----

###¿Siempre se llega a una forma normal?

```haskell
misterio = 1 + misterio
```

Note: Hablar de bottom
----

###¿La forma normal es única?

Haskell tiene *transparencia referencial*. Es decir que el valor de una expresión sólo depende de los elementos que la constituyen.

Note: Acá no sé bien cómo explicar que ésto implica que sólo haya una forma normla

----

###¿Hay más de una manera de reducir?

Sí.

-> Orden Aplicativo

-> Orden Normal

----

**Orden Aplicativo**

----

**Orden Normal**

----

### ¿Pero Haskell qué usa?

Se trata de una variación del orden normal. **Evaluación Lazy**

----
 
**Lazy**

