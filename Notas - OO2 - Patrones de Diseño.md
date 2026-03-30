
---
---

El refactoring no afecta funcionalidad de código, sino que la deja mas legible y extensible.

- No siempre que vamos a solucionar un problema vamos a encontrar la solución real y nunca mas tener que modificar algo. 
- Diseñar es algo difícil. Inclusive muchas veces no lo podemos hacer la primera vez, sino que hay que intentar varias veces. En cada intento hay que saber qué salio bien y qué salió mal para saber por donde llevar el problema.
- Para diseñar necesitamos encontrar las abstracciones correctas (para un problema no hay una abstracción única), la asignación correcta de responsabilidades, las jerarquías adecuadas y hacer que nuestros diseños sean modulares, exrtensibles, comperensibles y reusables.

Un patron es la relacion entre un problema recurrente y la solución a dicho problema. Los patrones no son inventados, sino que se descubren. 
Un patrón es un par problema-solución. Los mismos tratan con problemas recurrentes y buenas soluciones (probadas) a esos problemas.

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

**Consecuencias (no son todas positivas):**