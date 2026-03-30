
---
---

El refactoring no afecta funcionalidad de código, sino que la deja mas legible y extensible.

- No siempre que vamos a solucionar un problema vamos a encontrar la solución real y nunca mas tener que modificar algo. 
- Diseñar es algo difícil. Inclusive muchas veces no lo podemos hacer la primera vez, sino que hay que intentar varias veces. En cada intento hay que saber qué salio bien y qué salió mal para saber por donde llevar el problema.
- Para diseñar necesitamos encontrar las abstracciones correctas (para un problema no hay una abstracción única), la asignación correcta de responsabilidades, las jerarquías adecuadas y hacer que nuestros diseños sean modulares, exrtensibles, comperensibles y reusables.

Un patron es la relacion entre un problema recurrente y la solución a dicho problema. Los patrones no son inventados, sino que se descubren. 
Un patrón es un par problema-solución. Los mismos tratan con problemas recurrentes y buenas soluciones (probadas) a esos problemas.

## Patron de diseño 1: ADAPTER

En los exámenes es importante utilizar el máximo posible de detalles en los diagramas UML. 
Adapter: Intermediario que adapta el protocolo de actuador hacia el protocolo de telegramNotifier (en el ejemplo visto en la materia). La idea es agregar una clase intermedia que contenga dentro el objeto, y en dicho adapter se llama al método del objeto, retornando el resultado. Haciendo una subclase de actuador solucionamos el problema de tipos. El adapter es un pasamanos que recibe un sensor, con ese sensor arma un mensaje y le manda un mensaje "notify" al objeto TelegramNotifier. Se soluciona el problema de tipos y la adaptación de protocolos sin modificar telegramNotifier y sin modificar el comportamiento ya establecido en Actuador. Telegram adapter no podría existir o sería malo que no tenga asociado un telegramNotifier, por ende necesita tener una composición. Al mismo tiempo, hay herencia para hacer que telegramAdapter sea un Actuador (subclase).

**Intención:**
La intención de este patrón es convertir la interfaz de una clase en otra que el cliente espera. Cuando uno empieza a usar patrones, el nombre empieza a tener un significado muy concreto. Cada patrón tiene un nombre específico. Tener soluciones complejas asociadas a un nombre es loq ue se empezó a hacer cuando surgieron los patrones, para ya saber inmediatamente cuál es la solución que hay que implementar. Si dicen "Es adapter", ya debemos venir a este patrón de diseño.
Adapter permite que ciertas clases con interfaces incompatibles puedan trabajar en conjunto.

**Aplicabilidad:** Use adapter cuando usted quiere usar una clase existente y su interfaz no es compatible con lo que precisa.

**Participantes:**
- Target: Define la interfaz específica que usa el cliente.
- Client: Colabora con objetos que satisfacen la interfaz de Target.
- Adaptee: Define la interfaz que precisa ser adaptada.
- Adapter: Adapta la interfaz del Adaptee a la interfaz de Target.

**Colaboraciones (cómo se relacionan o colaboran los distintos roles):**
- Los objetos Client llaman a las operaciones en la instancia del Adapter.
- A su vez, el Adapter llama a las operaciones definidas en el Adaptee.

**Consecuencias (no son todas positivas):**
- Positiva: Una misma clase de Adapter puede usarse para muchos Adaptees (el Adaptee y todas sus subclases).
- Positiva: El adapter puede agregar funcionalidad a los adaptados.
- No tan positiva: Se generan más objetos intermediarios. Si hay muchos Adapters, el código puede volverse medio engorroso.

## Patron de diseño 2:

**Problema:** Debemos realizar una serie de pasos para dos formatos de salida: CSV y PDF por ejemplo. Y en el futuro se agregarán mas...
Si tenemos código repetido, hay que repetir la serie de pasos en cada clase, teniendo así repetición de código y a medida que se agreguen "exporters" se hará un lío.

El patrón que soluciona este problema es Template Method. Tendremos un esqueleto definiendo una serie de pasos. Lo importante en estos problemas es detectar los pasos en común. Dichos pasos podrán ser extendidos atómicamente por las subclases.

**Intención:** Definir el esqueleto de un algoritmo en un método, dirigiendo algunos pasos a las subclases. Template Method permite que las subclases redefinan ciertos pasos de un algoritmo sin cambiar la estructura del algoritmo. Este patrón es estático, lo que hacemos se resuelve en tiempo de compilación, no de ejecución.

**Aplicabilidad:** 
- Para implementar las partes invariantes de un algoritmo una vez y dejar que las subcalses implementen los aspectos que varían.
- Para evitar duplicación de código entre subclases
- Para controlar las extensiones que pueden hacer las subclases.

**Participantes:**
- AbstractClass: Implementa un método que tiene el esqueleto de un algoritmo (el template method). Este método llama a operaciones primtivas así como operaciones efinidas en AbstractClass.
**Completar**

**Colaboraciones:** 
- ConcreteClass confía en que la superclase implemete las partes invariantes del algoritmo.

**Consecuencias:**
- Técnica fundamenteal de reuso de código
- Lleva a tener inversión de control (la superclase llama a las operaciones de las subclases)
**Completar**

---

**Cada patrón tiene:** 
- Nombre
- Intención (prestar atención a esto al estudiar)
- Motivación (prestar atención a esto al estudiar)
- Aplicabilidad
- Estructura
- Participantes
- Colaboraciones
- Consecuencias (prestar atención a esto al estudiar. En un final se puede preguntar cuáles son las consecuencias de haber aplicado un patrón específico)
- Implementación
- Código (C++)
- Usos conocidos
- Patrones relacionados

---
---
---

## Explicación práctica 30/3

- En refactoring se ataca un problema a la vez
- Refactorizar no es tirar el código y escribrlo de nuevo
- Se debe preservar el comportamiento
- Refactorizar es seguir un método para mejorarlo:
	1. Identificar code smells
	2. Determinar cómo mejorarlo
	3. Aplicar la mejora

Ejercicio 1.1: 

La clase cliente tiene un protocolo. Para mejorarlo aplicamos Rename Method.
Por fuera, a los métodos los van a llamar otras clases. Por ende, al renombrar los métodos hay que tener en cuenta otras cosas, no solo cambiarlo y ya.

**Ejercicio 1.3:**

El código muestra un método largo que hace mucho y también la utilización de un for (podría usarse un stream)
