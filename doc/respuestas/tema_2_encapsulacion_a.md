<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.

### Respuesta:

<span style="font-size: 1.3em;">

La **encapsulación** busca agrupar los datos (atributos) y el código (métodos) que actúan sobre ellos en una unidad única llamada clase. La **ocultación de información** complementa esto haciendo que ciertos detalles internos no sean accesibles directamente desde fuera de la clase. 🔒

**Ventajas principales de la ocultación de información:**
- 🛡️ **Protección de invariantes:** Los atributos se modifican únicamente a través de métodos que validan los cambios
- 🔧 **Flexibilidad en cambios internos:** Se puede modificar la implementación interna sin afectar al código externo
- 📋 **Control de acceso:** Se decide explícitamente qué se expone y qué se oculta
- 🎯 **Interfaz clara:** Los usuarios de la clase solo ven lo necesario, simplificando su uso

</span>


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Respuesta:

<span style="font-size: 1.3em;">

La **interfaz pública** es el conjunto de métodos y atributos que se han marcado como `public` en una clase, es decir, lo que el mundo exterior puede ver y utilizar. Es el "contrato" que la clase ofrece a otros desarrolladores. 📢

La interfaz pública está intimamente ligada a la ocultación de información: mientras que la interfaz pública expone **qué** hace la clase, los detalles privados ocultan **cómo** lo hace. Los atributos privados y los métodos privados forman la **interfaz privada**, que es interna y no debe ser accedida desde fuera. De esta forma, la clase mantiene el control sobre su estado mientras proporciona una forma segura de interacción. 🔐

</span>


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Respuesta:

<span style="font-size: 1.3em;">

La interfaz pública de una clase es como un "contrato" con quien la usa. 📝 Una vez publicada, cualquier código externo puede depender de ella, por lo que cambiarla posterior­mente puede **romper el código que la utiliza**. Si se modifica un método público o se elimina un atributo público, todos los clientes de esa clase pueden verse afectados.

**No es fácil cambiarla.** ❌ Una vez que se expone públicamente, se asume estabilidad. Por eso es fundamental diseñar cuidadosamente qué se expone en la interfaz pública desde el principio, considerando solo lo esencial. Cambios en la interfaz requieren sincronizar cambios en todo el código que dependa de ella, lo que puede ser una pesadilla en proyectos grandes. 😰

</span>


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Respuesta:

<span style="font-size: 1.3em;">

Las **invariantes de clase** son condiciones que deben mantenerse siempre como verdaderas durante toda la vida del objeto. 📌 Por ejemplo, en una clase `Cuenta`, la invariante podría ser que el saldo nunca sea negativo, o en un `Círculo`, que el radio siempre sea mayor que cero. Son las "reglas" que garantizan que el objeto siempre este en un estado válido y coherente.

La ocultación de información protege estas invariantes de forma crucial. 🛡️ Si los atributos fueran públicos, el código externo podría modificarlos directamente, violando las invariantes (por ejemplo, asignando un radio negativo). Al mantener los atributos como privados, la clase controla **todas** las modificaciones a través de métodos que pueden validar y asegurar que las invariantes se cumplan siempre. Esto es un superpoder de la encapsulación: garantizar la integridad del objeto. ✅

</span>


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### Respuesta:

<span style="font-size: 1.3em;">

```java
public class Punto {
    // Atributos privados (ocultos) 🔒
    private double x;
    private double y;
    
    // Constructor público (interfaz pública)
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    
    // Método público (interfaz pública)
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}
```

**`public`** 📢 significa que el método o atributo es accesible desde cualquier otra clase. En este ejemplo, el constructor y `calcularDistanciaAOrigen()` son públicos, por lo que cualquiera puede crear un `Punto` y llamar al método.

**`private`** 🔒 significa que el atributo o método solo es accesible dentro de la propia clase. Los atributos `x` e `y` son privados, por lo que solo métodos dentro de `Punto` pueden acceder o modificarlos directamente.

**Interfaz pública de `Punto`:** El constructor `Punto(double, double)` y el método `double calcularDistanciaAOrigen()`. Solo estos son visibles y utilizables desde fuera de la clase.

</span>


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### Respuesta:

<span style="font-size: 1.3em;">

Los modificadores `public` y `private` en Java se pueden aplicar a:

- 🔹 **Atributos de instancia:** `private double x;` o `public int contador;`
- 🔹 **Métodos:** `public void saludar()` o `private void validar()`  
- 🔹 **Constructores:** `public Punto(...)` o `private Punto(...)`
- 🔹 **Clases internas (inner classes):** Una clase anidada dentro de otra

**No se pueden aplicar directamente a variables locales** (variables dentro de métodos), ya que estas tienen un alcance limitado al método en el que se declaran.

Es importante notar que los modificadores solo controlan la **visibilidad** desde fuera de la clase, pero dentro de la misma clase, todos los miembros (públicos y privados) son siempre accesibles. 🎯

</span>


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Respuesta:

<span style="font-size: 1.3em;">

Aunque pública y privada son los extremos más comunes, existen **niveles intermedios de visibilidad** en la mayoría de lenguajes orientados a objetos. 📊

En **Java** existen **4 niveles de visibilidad:**
- 🌍 **`public`:** Accesible desde cualquier clase en cualquier paquete
- 🏢 **`protected`:** Accesible solo dentro del mismo paquete y por subclases (herencia)
- ⚪ **Sin modificador (package-private):** Accesible solo dentro del mismo paquete
- 🔒 **`private`:** Accesible solo dentro de la misma clase

En **otros lenguajes:** Varían según el diseño. Por ejemplo, C++ tiene `public`, `private` y `protected`, mientras que Python confía más en convenciones de nombres (como prefijo `_` para indicar "privado") que en restricciones del lenguaje. 🐍 Algunos lenguajes como C# ofrecen incluso más opciones como `internal` o `protected internal`.

</span>


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Respuesta:

<span style="font-size: 1.3em;">

**Respuesta: (a) Otras clases.** 🎯 Los miembros privados están ocultos para otras clases, pero **no** para otras instancias de la misma clase. Una instancia de `Punto` puede acceder a los atributos privados de otra instancia de `Punto`.

```java
public class Punto {
    private double x;
    private double y;
    
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    
    // Este método puede acceder a los atributos privados de otro Punto ✅
    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x;  // Acceso a x privada de otra instancia
        double dy = this.y - otro.y;  // Acceso a y privada de otra instancia
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```

La visibilidad `private` se define a nivel de **clase**, no a nivel de **instancia**. Por lo tanto, dentro de la clase, cualquier instancia puede acceder a los miembros privados de cualquier otra instancia de la misma clase. 🔓 Esto tiene sentido porque son todas "del mismo tipo" y se presume confianza entre ellas. Solo las clases externas son las que no pueden acceder.

</span>


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Respuesta


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### Respuesta


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Respuesta


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Respuesta


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Respuesta


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### Respuesta


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### Respuesta


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Respuesta


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Respuesta


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### Respuesta


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### Respuesta


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### Respuesta


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### Respuesta


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Respuesta


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

### Respuesta


## 24. Añade a la clase `Mes` del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta
