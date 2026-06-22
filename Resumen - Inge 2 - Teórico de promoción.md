# CLASE 1: COMUNICACIÓN Y ESPECIFICACIÓN DE REQUISITOS (SRS)

1. Proceso de Desarrollo de Software y Elicitación

- **Definición Exacta:** Un proceso de software es un conjunto de actividades y resultados asociados que producen un producto de software. Dentro de este, la Elicitación es el proceso de adquirir ("sonsacar") todo el conocimiento relevante necesario para producir un modelo de los requerimientos de un dominio de problema. Sus objetivos incluyen conocer el dominio del problema, conocer el sistema actual, e identificar las necesidades explícitas e implícitas de clientes y usuarios.
- **En pocas palabras:** El proceso de software es todo lo que hacemos para fabricar el sistema. La elicitación es el primer paso crítico: "sacarle" al cliente la información para entender cómo trabaja, qué problema tiene y qué espera (incluso lo que da por sentado y no nos dice directamente).

2. Tipos de Requerimientos

- **Definición Exacta:**
    - _Requerimientos Funcionales:_ Definen el comportamiento y las tareas específicas del sistema.
    - _Requerimientos No Funcionales:_ Describen atributos deseables del sistema como el rendimiento, la seguridad y la usabilidad.
- **En pocas palabras:** Los funcionales son lo que el sistema _hace_ (ej. emitir un recibo). Los no funcionales son _cómo_ lo hace (ej. que la pantalla cargue en menos de un segundo o que sea seguro).

3. Técnicas de Elicitación (Recolección de datos)

- **Definición Exacta:** Según Whitten Bentley, son técnicas para investigar el dominio. Incluyen:
    - _Muestreo de documentación:_ Memos, minutas, registros contables.
    - _Observación del ambiente de trabajo:_ El analista observa sin interrumpir el trabajo de la persona.
    - _Cuestionarios:_ Con preguntas abiertas o cerradas.
    - _Entrevistas:_ Organizadas de forma Piramidal, Embudo o Diamante.
    - _JRP (Planificación Conjunta de Requisitos):_ Sesiones en equipo.
    - _Brainstorming:_ Generar ideas en corto tiempo sin análisis.
- **En pocas palabras:** Son las herramientas para investigar. Podés leer sus papeles, mirarlos trabajar en silencio, hacerles encuestas rápidas, sentarte a entrevistarlos, o juntar a todos en una sala para hacer una lluvia de ideas.

4. Especificación del Sistema (ConOps - IEEE Std. 1362-1998)

- **Definición Exacta:** Es un documento dirigido a los usuarios, que describe las características de un sistema propuesto, desde el punto de vista del usuario. Es el medio de comunicación que recoge la visión general, cualitativa y cuantitativa del sistema; compartido por la parte cliente y desarrolladora. (No confundir con el SRS).
- **En pocas palabras:** Es un documento a nivel general. Se escribe para que el cliente lo lea y entienda rápidamente cómo va a ser su sistema en la práctica, sin enredarlo con tecnicismos de programación.

5. Especificación de Requisitos de Software (SRS - IEEE Std. 830-1998)

- **Definición Exacta:** El SRS es una especificación detallada para un producto de software particular, escrito conjuntamente por la parte cliente y desarrolladora. Su estructura base incluye: 1. Introducción, 2. Descripción General, 3. Requisitos no funcionales, 4. Mantenimiento, 5. Apéndices. Debe cumplir obligatoriamente con 8 características para ser un buen SRS:
    1. _Correcto:_ Todo requisito debe estar en el software final.
    2. _No ambiguo:_ Cada requisito tiene una única interpretación.
    3. _Completo:_ Están todos los requisitos exigidos.
    4. _Consistente:_ Sin contradicciones.
    5. _Priorizado:_ Ordenado por importancia.
    6. _Comprobable (Verificable):_ Existe un proceso para verificar que el software cumple el requisito.
    7. _Modificable:_ Fácil de cambiar conservando su estructura.
    8. _Trazable:_ Se puede rastrear el origen y destino del requisito.
- **En pocas palabras:** Es el documento oficial y técnico del proyecto ("el contrato de los programadores"). Tiene que ser perfecto: sin contradicciones, detallando hasta la última función y exigencia (como la seguridad), y escrito de tal forma que no haya dobles interpretaciones. Todo lo que dice ahí, se tiene que poder probar después.

6. Elevator Pitch

- **Definición Exacta:** Es un mensaje corto de aproximadamente un minuto de duración para contar un proyecto de manera diferenciadora. Se recomienda comenzar con una afirmación o pregunta sorprendente para captar la atención. Posee 7 pasos: 1. Pregunta sorprendente, 2. Presentación, 3. Problemas que cubres, 4. Soluciones aportadas, 5. Beneficio principal, 6. Proyecto idóneo, 7. Llamada a la acción final.
- **En pocas palabras:** Es un discursito de un minuto preparado de antemano para "vender" tu idea si te cruzás a un inversor. Arrancás llamando la atención, decís qué problema resolvés, por qué tu equipo es el mejor para eso, y cerrás pidiéndole algo (como su tarjeta o una reunión).

---
---
---

# CLASE 2: GESTIÓN DE LA CONFIGURACIÓN Y PLANIFICACIÓN ORGANIZATIVA

1. Gestión de la Configuración del Software (GCS)

- **Definición Exacta:** Es el proceso de identificar y definir los elementos en el sistema, controlando el cambio de estos elementos a lo largo de su ciclo de vida, registrando y reportando el estado de los elementos y las solicitudes de cambio, y verificando que los elementos estén completos y que sean los correctos. Es una actividad de "autoprotección" que se aplica durante el proceso del software.
- **En pocas palabras:** A lo largo del proyecto, todo va a cambiar (el cliente pide cosas nuevas, surgen errores). La GCS es el "escudo" del proyecto: un conjunto de reglas para saber qué archivos tenemos, registrar cada vez que alguien los toca y asegurarnos de que ese cambio no rompa nada.

2. Elementos de la Configuración del Software (ECS)

- **Definición Exacta:** Son las partes del sistema sometidas a control y se dividen rígidamente en 3 categorías: 1) _Programas_ (aplicaciones de software utilizadas para tareas), 2) _Productos de Trabajo_ (resultados creados durante el proceso, como manuales, especificaciones y diseños), y 3) _Datos_ (información utilizada y generada por el software, como esquemas de bases de datos).
- **En pocas palabras:** No solo controlamos el código. Los ECS son el código, los documentos (manuales/diagramas) y las bases de datos. A todo ese paquete se le hace seguimiento.

3. Línea Base (Baseline)

- **Definición Exacta:** Según la IEEE, es una especificación o producto que se ha revisado formalmente y sobre el que se ha llegado a un acuerdo, y que de ahí en adelante sirve como base para un desarrollo posterior y que puede cambiarse _solamente_ a través de procedimientos formales de control de cambio. Queda marcado por el envío de uno o más ECS y su aprobación.
- **En pocas palabras:** Es un "punto de guardado" o _checkpoint_. Cuando el cliente y el equipo aprueban algo (ej. el documento de requisitos), queda "congelado" como Línea Base. A partir de ahí, nadie puede modificarlo a escondidas; si alguien quiere cambiarlo, tiene que pedir permiso mediante un trámite formal.

4. El Proceso de GCS (Los 5 Pasos)

- **Definición Exacta:** La GCS se aplica sistemáticamente mediante cinco pasos:
    1. **Identificación:** Se asigna un nombre sin ambigüedad y una descripción de atributos (tipo de ECS, identificador del proyecto y versión).
    2. **Control de versiones:** Combinación de procedimientos y herramientas para gestionar las distintas versiones o variantes del sistema (utiliza repositorios, _Master_, _Branch_, _Commit_ y _Merge_).
    3. **Control de cambios:** Una Autoridad de Control de Cambios (ACC) evalúa toda petición de cambio analizando cómo impactará en el hardware, el rendimiento, la calidad y la percepción del cliente para aprobarla o denegarla.
    4. **Auditoría de la configuración:** Mediante Revisiones Técnicas Formales (RTF), se verifica que el cambio especificado se hizo correctamente, sin añadir modificaciones extra y respetando los estándares.
    5. **Generación de informes de estado:** Documentación que responde a: ¿Qué pasó?, ¿Quién lo hizo?, ¿Cuándo pasó? y ¿Qué más se vio afectado?.
- **En pocas palabras:** Para que no haya caos, seguimos estos pasos: 1) Le ponemos nombre a todo, 2) Usamos herramientas (como Git) para guardar las versiones sin pisarnos, 3) Si hay un cambio grande, un grupo de expertos (la ACC) evalúa si es seguro hacerlo, 4) Una vez hecho el cambio, lo auditamos para ver que no hayan programado cualquier cosa, y 5) Le avisamos a todo el equipo qué fue lo que se modificó.

5. Gestión de Proyectos: Las 4 P

- **Definición Exacta:** La planificación especifica qué debe hacerse, con qué recursos y en qué orden. Para evitar el fracaso, se deben equilibrar las "4 P":
    - **Personal:** Es el activo más grande de la organización, el capital intelectual. Una mala administración del personal es la causa principal de fracaso.
    - **Producto:** El resultado intangible del esfuerzo de software.
    - **Proceso:** El marco de trabajo o metodología utilizada.
    - **Proyecto:** El esfuerzo temporal (con comienzo y fin) que necesita control y métricas para manejar su complejidad.
- **En pocas palabras:** Para que el proyecto no se hunda, tenés que mirar 4 cosas. **Personal** (la gente es lo más valioso, si los tratás mal, perdés), **Producto** (qué estamos haciendo), **Proceso** (qué reglas o método usamos, ej. Scrum) y **Proyecto** (el control del tiempo, la plata y los riesgos).

6. Paradigmas Organizacionales de Equipos de Software

- **Definición Exacta:** Son los modelos que definen la estructura y comunicación del equipo (idealmente no mayor a 10 miembros) para evitar la "toxicidad" y alcanzar la consolidación.
    1. **Paradigma Cerrado:** Jerarquía de autoridad tradicional (comunicación vertical). Eficiente para proyectos similares a otros del pasado, pero poco innovador.
    2. **Paradigma Abierto:** El trabajo es colaborativo, con gran comunicación total y decisiones consensuadas democráticamente. Ideal para resolver problemas muy complejos.
    3. **Paradigma Síncrono:** Se basa en la compartimentalización ("divide y vencerás"). Organiza subgrupos que trabajan en partes del problema con poca comunicación activa entre ellos. El riesgo es crear componentes que al final no encajen o no sirvan.
    4. **Paradigma Aleatorio:** Organización holgada que depende de la iniciativa individual, sin un líder definido. Excelente para lograr saltos tecnológicos, pero malo cuando se necesita un desempeño ordenado y cumplir fechas estrictas.
    5. **Equipos Ágiles:** Equipos pequeños, muy motivados y autoorganizados. Priorizan la competencia individual y la colaboración grupal. Se asemeja a un paradigma aleatorio (con pocos miembros) o a un paradigma abierto.
- **En pocas palabras:** Hay distintas formas de organizar a los programadores:
    - **Cerrado:** Estilo militar/jefe tradicional. Sirve si hacen siempre el mismo tipo de sistema. Cero innovación.
    - **Abierto:** Todos opinan y deciden juntos. Lento, pero genial para sistemas difíciles donde dos cabezas piensan mejor que una.
    - **Síncrono:** Partimos el sistema en pedazos y cada subgrupo hace lo suyo aislado. Sirve para sistemas inmensos, pero si no se hablan, cuando junten el código todo va a explotar.
    - **Aleatorio:** Creatividad al máximo sin jefes. Genial para inventar algo revolucionario, malísimo para cumplir con un horario o fecha límite.
    - **Ágil:** Expertos que se organizan solos, colaboran todo el tiempo y tienen un facilitador que les saca los problemas del camino.

---
---
---

# CLASE 3: GESTIÓN DE RIESGOS

1. Definición de Riesgo

- **Definición Exacta:** Un riesgo es un evento futuro no deseado que tiene consecuencias negativas (implica incertidumbre y pérdida). La gestión de riesgos busca proactivamente tanto evitar eventos no deseados como minimizar sus consecuencias.
- **En pocas palabras:** Es algo malo que todavía no pasó, pero que si llega a pasar, nos va a traer problemas (retrasos, pérdida de plata, fallas). Gestionarlo sirve para no vivir "apagando incendios", sino estar preparados desde antes.

2. Categorías de Riesgo (¡Ojo, tema clave de examen!)

- **Definición Exacta:** Los riesgos en el desarrollo de software se categorizan estrictamente en tres áreas:
    1. **Del Proyecto:** Afectan directamente el calendario, el presupuesto y los recursos. (Ejemplo: Rotación o falta de personal, problemas de integración).
    2. **Del Producto:** Afectan la calidad, los requerimientos o el rendimiento del software que se está construyendo. (Ejemplo: Falta de experiencia en tecnologías nuevas —el cual tiene un impacto _Catastrófico_—, problemas de escalabilidad o fallos de seguridad).
    3. **Del Negocio:** Amenazan la viabilidad de la empresa o del sistema en el mercado. (Ejemplo: Construir un sistema excelente pero que nadie quiere, pérdida de apoyo de la gerencia, cambios en las tendencias del mercado o cambios en la legislación fiscal).
- **En pocas palabras:**
    - _Proyecto:_ Problemas internos de plata, tiempos o tu equipo (ej. renuncia el programador estrella).
    - _Producto:_ Problemas técnicos del sistema (ej. elegimos una tecnología que no sabemos usar y el sistema no rinde).
    - _Negocio:_ Problemas del mercado o la empresa (ej. el gobierno saca una ley nueva que hace que nuestro sistema ya no sirva para nada).

3. Tipos de Riesgos

- **Definición Exacta:** Los riesgos se clasifican según su naturaleza en _Genéricos_ (comunes a todo desarrollo) y _Específicos_ (particulares del dominio del proyecto). Según su grado de previsibilidad, se dividen en: _Conocidos_, _Predecibles_ e _Impredecibles_.
- **En pocas palabras:** Un riesgo genérico es que se corte internet en la oficina; uno específico es que el hardware particular que el cliente pidió no sea compatible. A su vez, hay riesgos que ya sabés que tenés, otros que te los ves venir por la experiencia, y otros que te sorprenden totalmente de la nada.

4. El Proceso de Gestión de Riesgos (Los 4 pasos)

- **Definición Exacta:** Es un proceso iterativo que debe documentarse, compuesto por:
    1. **Identificación:** Creación de un listado de riesgos potenciales.
    2. **Análisis:** Evaluación de probabilidad e impacto para generar un listado de priorización.
    3. **Planeación:** Definición de estrategias (anulación o planes de contingencia).
    4. **Supervisión:** Valoración y seguimiento continuo de los riesgos a lo largo del tiempo.
- **En pocas palabras:** 1) Hacés una lluvia de ideas con todo lo malo que podría pasar. 2) Ordenás esa lista viendo qué es más grave o probable. 3) Pensás cómo vas a solucionar o esquivar esos problemas. 4) A lo largo del proyecto, seguís mirando la lista para ver si apareció algún peligro nuevo.

5. Análisis de Riesgos y la "Línea de Corte"

- **Definición Exacta:** Cada riesgo identificado requiere estimar su _Probabilidad_ (de Insignificante a Muy Alta) y su _Impacto_ (Insignificante, Tolerable, Serio, Catastrófico). Con estos datos se construye una tabla ordenada y se traza una **Línea de Corte**. Boehm recomienda identificar y supervisar activamente los 10 riesgos más altos. Los riesgos que quedan por encima de la línea reciben toda la atención de la administración; los que quedan por debajo se reevalúan con prioridad de segundo orden.
- **En pocas palabras:** A cada problema de tu lista le ponés dos puntajes: "¿Qué chance hay de que pase?" y "¿Qué tan fuerte nos destruye si pasa?". Los ordenás del peor al más inofensivo y pasás una raya en el medio (la línea de corte). A los que quedaron arriba (los más críticos), los atacás con todo tu esfuerzo. A los de abajo, por ahora, solo los mirás de reojo para no perder tiempo.

6. Estrategias de Planeación de Riesgos

- **Definición Exacta:** Para cada riesgo por encima de la línea de corte, se determina estrictamente una de estas estrategias:
    1. **Evitar el riesgo:** El sistema se rediseña o se cambia el enfoque de modo que el evento negativo no pueda ocurrir físicamente.
    2. **Minimizar el riesgo:** Se toman acciones preventivas para que la probabilidad de que el riesgo se presente se reduzca significativamente.
    3. **Plan de contingencia:** Se asume que el riesgo va a suceder (se acepta su aparición). Se está preparado para lo peor mediante un plan de acción destinado exclusivamente a minimizar las consecuencias una vez que el problema estalló.
- **En pocas palabras:** Frente a un problema inminente tenés tres opciones:
    1. _Esquivarlo (Evitar):_ Cambiás la ruta para no cruzarte con el problema.
    2. _Achicarlo (Minimizar):_ Hacés cosas para que sea muy difícil que el problema te alcance.
    3. _Tener un Plan B (Contingencia):_ Aceptás que el problema te va a chocar sí o sí, pero ya tenés lista la ambulancia y los curitas para que el daño sea mínimo.

---
---
---

# CLASE 4: PLANIFICACIÓN TEMPORAL Y DISEÑO DE SOFTWARE

1. Planificación Temporal y Calendarización

- **Definición Exacta:** La calendarización del proyecto de software es una acción que distribuye el esfuerzo estimado a través de la duración planificada del proyecto, asignando el esfuerzo a tareas específicas. Está compuesta por:
    - **Tarea:** Secuencia de acciones a realizar en un plazo determinado.
    - **Tarea Crítica:** Es aquella cuyo retraso genera un retraso en todo el proyecto.
    - **Hito (Milestone):** Es "algo" que se espera que esté hecho para alguna fecha. Un logro fácil de evaluar y notable (ej. un módulo terminado).
- **En pocas palabras:** Es armar el cronograma del proyecto. Definís qué tareas hay que hacer, cuáles son intocables porque si se atrasan arruinan toda la fecha de entrega (tareas críticas), y ponés "banderitas" en el calendario (hitos) para celebrar que terminaste una parte importante.

2. Herramientas: PERT, CPM, Margen Total y Camino Crítico

- **Definición Exacta:**
    - **PERT:** Técnica para analizar las estimaciones cuando las duraciones de las tareas son inciertas o probabilísticas.
    - **CPM (Método del Camino Crítico):** Identifica la secuencia de actividades que determinan el tiempo mínimo de finalización, centrándose en tareas con duraciones conocidas y determinísticas.
    - **Margen Total:** Representa el tiempo total que se puede retrasar una tarea sin afectar el proyecto. Si el Margen Total es 0, la tarea es crítica.
    - **Camino Crítico:** Es el camino formado por la sucesión de tareas críticas (tareas con margen cero).
- **En pocas palabras:** PERT y CPM son mapas de red para organizar tareas. Te sirven para calcular el "Margen Total", que es tu colchón de tiempo. Si una tarea tiene margen de 6 días, podés relajarte un poco. Si su margen es 0, es una "Tarea Crítica"; un solo día de atraso ahí y se atrasa todo el sistema. El hilo que une a todas estas tareas sin margen se llama "Camino Crítico".

3. Criterios Técnicos para un Buen Diseño

- **Definición Exacta:** Un buen diseño debe cumplir con ciertas pautas:
    1. Debe presentar una estructura arquitectónica creada mediante patrones reconocibles y componentes con buen diseño.
    2. Deberá ser modular.
    3. Deberá contener distintas representaciones de datos, arquitectura, interfaces y componentes.
    4. Deberá conducir a estructuras de datos adecuadas.
    5. Deberá conducir a componentes que presenten independencia funcional.
    6. Deberá conducir a interfaces que reduzcan la complejidad de las conexiones.
- **En pocas palabras:** Un sistema bien diseñado está partido en pedazos (módulos) que son fáciles de entender, que no están enredados de forma caótica entre sí, que ocultan sus datos y que siguen modelos ya probados (patrones) para no reinventar la rueda.

4. Los 8 Conceptos Clave del Diseño

- **Definición Exacta:** Sin importar el tipo de diseño, es necesario aplicar este conjunto de conceptos básicos:
    1. **Abstracción:** Permite concentrarse en un problema a un nivel de generalización sin tener en cuenta los detalles de bajo nivel.
    2. **Arquitectura:** Es la estructura general del software y las formas en que proporciona integridad conceptual.
    3. **Patrones:** Describen una estructura de diseño que resuelve un problema particular dentro de un contexto específico.
    4. **Modularidad:** El software se divide en componentes nombrados y abordados por separado (módulos).
    5. **Ocultamiento de Información:** La información que está dentro de un módulo es inaccesible a otros que no la necesiten.
    6. **Independencia Funcional:** Se logra mediante módulos con "alta cohesión" y "bajo acoplamiento" (resultado de unir Modularidad + Abstracción + Ocultamiento).
    7. **Refinamiento:** Ayuda a revelar los detalles de grado menor de manera sucesiva (es el complemento de la abstracción).
    8. **Refabricación (Refactoring):** Técnica de reorganización que simplifica el diseño de un componente sin cambiar su función o comportamiento externo.
- **En pocas palabras:** Cuando diseñás, primero mirás el problema desde lejos sin enredarte en el código (Abstracción). Vas bajando al detalle de a poco (Refinamiento). Partís el sistema en partes (Modularidad) y le ponés un candado a los datos de cada parte para que no cualquiera los toque (Ocultamiento). Si a futuro el código queda feo pero funciona, lo limpiás por dentro sin que el cliente se dé cuenta (Refactoring).

5. Cohesión y Acoplamiento (TEMA CLAVE)

- **Definición Exacta:**
    - **Cohesión:** Medida de fuerza o relación funcional existente entre las sentencias o grupos de sentencias de un mismo módulo. Va de lo peor a lo mejor: _Coincidental, Lógica, Temporal, Procedimental, Comunicacional, Funcional_ (la mejor, donde todo el módulo hace una única función específica).
    - **Acoplamiento:** Medida de interconexión (dependencia) entre los módulos. Va de lo peor a lo mejor: _De contenido, Común, Control, Marca, Datos_ (el mejor, donde solo se pasan parámetros).
    - **Regla de Oro:** Se debe buscar siempre **ALTA COHESIÓN** y **BAJO ACOPLAMIENTO**.
- **En pocas palabras:**
    - **Cohesión (lo de adentro):** Es qué tan enfocadas están las líneas de código de un módulo. Si un módulo hace 20 cosas distintas que no tienen nada que ver, tiene cohesión coincidental (basura). Si hace 1 sola cosa perfecta, tiene cohesión funcional (excelente).
    - **Acoplamiento (lo de afuera):** Es qué tan pegoteado está un módulo con otro. Si un módulo necesita leer las variables internas de otro para funcionar, tienen un acoplamiento alto (malísimo, si tocás uno, rompés el otro). Tienen que ser lo más independientes posibles.

---
---
---

# CLASE 5: DISEÑO DE INTERFAZ DE USUARIO (UI / UX)

1. Diferencia entre UI y UX (y la metáfora del Iceberg)

- **Definición Exacta:**
    - **UI (User Interface / Interfaz de Usuario):** Es la categoría de diseño que crea un medio de comunicación físico o lógico entre el hombre y la máquina. Se centra en la apariencia visual, la estética y la interacción inmediata con los elementos en pantalla.
    - **UX (User Experience / Experiencia de Usuario):** Es un proceso multidisciplinar mucho más amplio. Se enfoca en la satisfacción total del usuario al interactuar con el producto. Incluye la investigación del usuario, la arquitectura de la información y el flujo de navegación. En la metáfora del "Iceberg", la UI es solo la punta visible (la web final), mientras que la UX es toda la enorme masa sumergida (necesidades, estructuras, contexto cultural).
- **En pocas palabras:** La UI es "la chapa y pintura" (qué colores usamos, dónde está el botón, la tipografía). La UX es "cómo se siente manejar el auto" (si fue fácil llegar a donde querías, si te frustraste en el camino o si el sistema resolvió tu problema de forma intuitiva). La UI es lo visual, la UX es todo el cerebro que hay por detrás.

2. Las 3 Reglas Doradas (o básicas) de Theo Mandel

- **Definición Exacta:** El diseño de interfaz debe regirse por tres principios fundamentales para adaptarse a los humanos:
    1. **Dar el control al usuario:** Proporcionar una interacción flexible, incluir opciones de interrumpir y "deshacer" acciones, y permitir interacción directa.
    2. **Reducir la carga de memoria del usuario:** Minimizar el esfuerzo de recordar, definiendo valores por defecto con sentido, creando accesos directos intuitivos y desglosando la información progresivamente.
    3. **Hacer la interfaz consistente:** Mantener una estructura y comportamiento uniforme en toda la familia de aplicaciones. El usuario debe saber de dónde viene y hacia dónde puede ir.
- **En pocas palabras:** 1) _Que el usuario mande_ (si toca algo sin querer, tiene que poder darle a "deshacer" (Ctrl+Z) y cancelar procesos). 2) _No lo hagas pensar demasiado_ (dáselo servido, ponele valores por defecto para que escriba menos). 3) _Mantené la coherencia_ (si el botón de "Guardar" siempre fue verde y estuvo abajo a la derecha, no se lo cambies de color y lugar en la siguiente pantalla).

3. Principios de Usabilidad de Nielsen

- **Definición Exacta:** Reglas heurísticas de Jakob Nielsen para evaluar la usabilidad del sistema:
    - **Diálogo simple y natural / Lenguaje del usuario:** Evitar jerga técnica, hablar en el idioma del usuario.
    - **Consistencia:** Mantener uniformidad visual y terminológica.
    - **Feedback (Retroalimentación):** El sistema debe mantener al usuario informado de lo que está sucediendo y el estado de sus procesos en tiempo real.
    - **Salidas evidentes (Exit):** El usuario debe tener siempre a su alcance, de forma identificable, una opción de salida, cancelación o "deshacer".
    - **Ayudas:** Brindar asistencia contextual, manuales y soporte en línea.
- **En pocas palabras:** Háblale fácil al usuario, no le tires códigos que solo un programador entiende. Si el sistema está cargando algo pesado, ponele una barrita de porcentaje o un cartel de "Cargando..." (Feedback) para que no piense que se tildó todo. Y siempre, pero siempre, ponele un botón de "Cancelar" o "Salir" a la vista.

4. Prevención de Errores y Mensajes de Error (¡Tema Fijo!)

- **Definición Exacta:**
    - **Prevención de Errores:** Es el principio fundamental que busca evitar que el usuario llegue a una instancia de error. Se logra brindando rangos de entradas posibles mediante selectores (para que no tenga que tipear), mostrando ejemplos o valores por defecto, y aplicando mecanismos de corrección automática.
    - **Mensajes de Error:** Cuando el error es inevitable, el mensaje debe brindar información clara de lo ocurrido, explicar el error y dar alternativas para solucionarlo. **Nunca** deben utilizarse mensajes de error intimidatorios (ej. mostrar una traza de la base de datos).
- **En pocas palabras:** La mejor manera de atajar un error es _no dejar que el usuario lo cometa_. En vez de darle un campo vacío para que escriba "Buenos Aires" (y capaz lo escribe con V corta o sin mayúsculas), dale una lista desplegable con las provincias. Y si se manda una macana, no le tires un cartel rojo gigante que diga "FATAL ERROR SQL 0x009"; ponele un cartel amable que diga: "Ups, parece que faltan datos. Por favor revisá el campo del DNI".

5. Estilos de Interfaces

- **Definición Exacta:** Son las diferentes formas en las que un humano puede interactuar con el sistema:
    1. **Interfaz de Comandos:** Basada solo en texto (línea de comandos). Es muy poderosa y rápida para expertos, pero con una curva de aprendizaje alta (difícil de aprender).
    2. **Selección de Menú:** Se elige entre opciones presentadas. Evita errores, pero es lenta para usuarios avanzados.
    3. **Relleno de Formularios:** Introducción de datos sencilla en campos. Es fácil de aprender pero ocupa mucho espacio de pantalla.
    4. **GUI (Interfaz Gráfica de Usuario):** Utiliza elementos gráficos y ventanas. Es intuitiva y muy fácil de usar.
    5. **Manipulación Directa:** Interacción táctil directa con los objetos en pantalla (ej. celulares modernos).
    6. **Reconocimiento de Voz:** Interfaz controlada por comandos hablados (ej. Siri, Alexa).
- **En pocas palabras:** Es cómo interactuás. La consola negra con letras blancas de Windows (Comandos) es potente pero tenés que saber los códigos de memoria. Los Formularios o Menús son fáciles para tu tía, pero aburren a un experto. La gráfica (con ratón y ventanas) es la clásica de la PC, la de Manipulación Directa es la del celular táctil (tocás lo que querés mover), y la de Voz es cuando le hablás a la máquina.

---
---
---

# CLASE 6: DISEÑO ARQUITECTÓNICO

1. Diseño Arquitectónico (Concepto General)

- **Definición Exacta:** Es el proceso de identificar los subsistemas dentro del sistema y establecer el marco de control y comunicación entre ellos. Define la relación entre los elementos estructurales para lograr los requisitos del sistema. La arquitectura afecta directamente a los requerimientos no funcionales más críticos, como el rendimiento, la protección, la seguridad, la disponibilidad y la mantenibilidad.
- **En pocas palabras:** Es armar el plano del edificio antes de poner los ladrillos. Acá decidís cuáles van a ser los bloques principales del sistema y cómo van a hablar entre ellos. Es clave porque si le pifiás acá, tu sistema va a ser lento, inseguro o imposible de actualizar en el futuro.

2. Organización del Sistema (Los Patrones Arquitectónicos)

Es la estrategia básica usada para estructurar el sistema. Existen varios estilos o patrones:

A. Patrón de Repositorio

- **Definición Exacta:** Todos los datos compartidos se almacenan en una base de datos central (repositorio). Los datos son generados por un subsistema y utilizados por otros.
    - _Ventajas:_ Forma eficiente de compartir grandes cantidades de datos sin tener que transmitirlos de un subsistema a otro. Las actividades de backup y seguridad están centralizadas.
    - _Desventajas:_ Los subsistemas deben estar acordes y acoplados al modelo de datos del repositorio. Es difícil distribuir el repositorio en varias máquinas (problemas de redundancia).
- **En pocas palabras:** Es como una biblioteca central gigante. Todos los programas (módulos) van y sacan los libros (datos) del mismo lugar. Es genial porque hacés una sola copia de seguridad de todo, pero es peligroso porque si se cae la base de datos central, se cae todo el sistema.

B. Patrón Cliente-Servidor

- **Definición Exacta:** Modelo donde el sistema se organiza como un conjunto de servicios y servidores asociados, más unos clientes que utilizan los servicios a través de una red. Los clientes conocen el nombre del servidor y el servicio que brinda, pero el servidor no necesita conocer al cliente.
- **En pocas palabras:** Como ir a un restaurante. Vos sos el cliente, pedís un plato (petición), y el mozo/cocinero (servidor) te lo trae. El servidor atiende a un montón de clientes pero no necesita saber quiénes son íntimamente.

C. Patrón de Arquitectura en Capas

- **Definición Exacta:** El sistema se organiza en capas, donde cada una de ellas presenta un conjunto de servicios _solo_ a sus capas adyacentes.
    - _Ventajas:_ Soporta el desarrollo incremental y es muy portable. Una capa puede ser reemplazada siempre que se mantenga su interfaz.
    - _Desventajas:_ Es difícil de estructurar. Los servicios requeridos por el usuario pueden tener que atravesar varias capas adyacentes, lo que implica que la solicitud debe ser interpretada varias veces, penalizando el rendimiento.
- **En pocas palabras:** Es el modelo "cebolla". Tenés la capa visual (lo que ve el usuario), la capa lógica (las reglas del negocio) y la capa de datos. Para que la pantalla guarde un dato, tiene que pasar sí o sí por las capas del medio. Si el día de mañana cambiás la base de datos (capa más profunda), a la pantalla no le importa porque ni se entera, lo que lo hace súper fácil de mantener.

3. Descomposición Modular

Una vez organizado el sistema en subsistemas, a estos se los divide en componentes más pequeños (módulos).

- **Definición Exacta:**
    - **Descomposición orientada a flujo de funciones:** Los datos fluyen de una función a otra y se transforman a medida que pasan por una secuencia de funciones hasta llegar a la salida (como una tubería).
    - **Descomposición orientada a objetos:** Estructura al sistema en un conjunto de objetos débilmente acoplados y con interfaces bien definidas.
- **En pocas palabras:** ¿Cómo partimos el problema chico? O lo hacemos como una línea de ensamblaje de fábrica donde el dato entra, cada máquina le hace algo y sale (Flujo), o creamos "entidades" independientes que charlan entre sí pasándose mensajes (Objetos).

4. Modelos de Control (Centralizado vs Eventos)

Define cómo se coordinan y ejecutan los subsistemas para que los servicios se entreguen en el momento preciso.

A. Control Centralizado

- **Definición Exacta:** Un subsistema se diseña como "controlador" y asume la responsabilidad de gestionar la ejecución de los otros subsistemas.
    - _Modelo de Llamada y Retorno:_ Subrutinas descendentes, aplicable a modelos secuenciales.
    - _Modelo de Gestor:_ Un gestor controla el inicio y parada coordinado con el resto de los procesos. Aplicable a modelos concurrentes.
- **En pocas palabras:** Hay un "jefe" claro. En _Llamada y Retorno_, el programa principal llama a una función, espera a que termine, recibe el resultado y sigue. En el _Modelo Gestor_, el jefe coordina a varios empleados (procesos) que están trabajando todos al mismo tiempo.

B. Control Basado en Eventos

- **Definición Exacta:** Se rigen por eventos generados externamente al proceso (una señal, un clic, un comando).
    - _Modelos de Transmisión (Broadcast):_ Un evento se transmite a todos los subsistemas; cualquier subsistema programado para manejar ese evento lo atenderá.
    - _Modelo dirigido por interrupciones:_ Usado en sistemas de tiempo real. Las interrupciones externas son detectadas por un manejador y derivadas a un componente para su procesamiento.
- **En pocas palabras:** No hay una secuencia fija. El sistema está "escuchando". Si es _Broadcast_, alguien grita "¡Hicieron clic en Guardar!" y el módulo encargado de guardar salta y dice "¡Yo me ocupo!". Si es por _Interrupciones_ (ej. los frenos ABS de un auto), es algo recontra urgente que frena todo el sistema para ser atendido al instante.

5. Arquitectura de Sistemas Distribuidos

- **Definición Exacta:** Es un sistema en el que el procesamiento de información se distribuye sobre varias computadoras. Tienen la particularidad de la impredecibilidad, ya que el tiempo de respuesta varía según la carga de la red.
    - _Multinivel / Dos Niveles:_ Cliente ligero (el servidor hace todo el procesamiento) o Cliente pesado (el cliente procesa la lógica y el servidor solo guarda datos).
    - _Objetos Distribuidos (Middleware):_ No hay distinción tajante entre cliente y servidor. Los componentes se distribuyen en varias máquinas y usan un software intermedio (Middleware, como DCOM de Microsoft) para poder comunicarse entre sí sin importar la infraestructura.
    - _Peer-to-Peer (P2P):_ Sistemas descentralizados donde el cálculo puede llevarse a cabo en cualquier nodo de la red.
    - _Orientada a Servicios (SOA):_ Un proveedor publica un servicio en un registro, y un solicitante lo busca y lo enlaza a su aplicación.
- **En pocas palabras:** El sistema no corre en una sola PC, está desparramado. Puede ser _Cliente pesado_ (tu compu hace todo el cálculo y solo pide datos), _P2P_ (como descargar por Torrent, todos somos clientes y servidores al mismo tiempo), o por _Servicios/SOA_ (como cuando una app de delivery usa el mapa de Google; la app "consume" un servicio que Google ofrece en la nube).

---
---
---

# CLASE 7: GESTIÓN DE PROYECTOS (MÉTRICAS Y ESTIMACIONES)

1. Métricas de Software (Concepto y Tipos)

- **Definición Exacta:** Las métricas son fundamentales para gestionar y mejorar procesos o sistemas de software. Se apoyan en cuatro objetivos principales: _Entender, Controlar, Mejorar y Evaluar_. Se dividen en tres grandes grupos:
    - **Métricas del Proyecto:** Cumplen propósitos tácticos (ej. ajustar el calendario, evitar demoras, rastrear riesgos).
    - **Métricas del Proceso:** Cumplen propósitos estratégicos a largo plazo a través de múltiples proyectos para mejorar el proceso global. (Regla: no se deben usar para evaluar a las personas, sino al proceso).
    - **Métricas del Producto:** Evalúan el software en sí. Pueden ser _Dinámicas_ (programa en ejecución, miden eficiencia y fiabilidad) o _Estáticas_ (representaciones del sistema o código, miden complejidad y mantenibilidad, ej. Líneas de Código -LDC- o Puntos de Función -PF-).
- **En pocas palabras:** Medir es saber dónde estamos parados. Podés medir cómo va el proyecto hoy para no atrasarte (Proyecto), cómo trabaja la empresa en general a lo largo de los años para mejorar (Proceso), o medir el código puro y duro para ver si está bien escrito o si tiene muchos errores (Producto).

2. Método GQM (Goal, Question, Metric) - _¡Tema Fijo!_

- **Definición Exacta:** Desarrollado por Victor Basili, es un marco estructurado orientado a lograr una métrica que “mida” un objetivo específico para mejorar la calidad del proyecto. Su estructura es estrictamente descendente:
    1. **Objetivo (Goal):** Define el objetivo central o propósito organizacional a mejorar (ej. evaluar la asignación de roles).
    2. **Preguntas (Question):** Interrogantes formulados para verificar el cumplimiento del objetivo (ej. ¿Hay un responsable asignado?).
    3. **Métricas (Metric):** Medidas cuantitativas diseñadas exclusivamente para responder a esas preguntas (ej. un valor binario: Verdadero/Falso, o cantidad de horas).
- **En pocas palabras:** No hay que inventar fórmulas matemáticas por inventar. El GQM te dice: primero pensá **qué querés lograr** (Objetivo). Después, pensá **qué preguntas te harías** para saber si lo lograste. Y por último, inventá un **número o cálculo** (Métrica) que te responda esa pregunta. Todo tiene que tener un sentido.

3. Estimaciones de Software

- **Definición Exacta:** La estimación de software es el proceso de predecir la cantidad más realista de esfuerzo (expresado comúnmente en horas-persona), tiempo y costo monetario requeridos para desarrollar o mantener un software. Mientras las métricas miden el pasado/presente, las estimaciones miran hacia el futuro.
- **En pocas palabras:** Es tratar de adivinar (usando la ciencia y la experiencia) cuánta plata, cuántas personas y cuántos meses nos va a llevar hacer el sistema antes de escribir la primera línea de código.

4. Técnicas de Estimación - _¡Tema Fijo!_

- **Definición Exacta:** Son los métodos utilizados para predecir el esfuerzo. Las principales son:
    - **Juicio Experto:** Consulta a individuos o grupos con gran experiencia en el dominio del negocio o tecnología. Estiman, comparan y discuten. Se usa en las primeras etapas cuando la información es limitada o el alcance es vago.
    - **Técnica Delphi:** Método de consenso grupal (panel de expertos). Se caracteriza por ser iterativo (múltiples rondas) y **anónimo**. El anonimato reduce la influencia de personalidades dominantes (jefes) y permite retroalimentación controlada hasta llegar a un acuerdo.
    - **División de Trabajo (Top-Down):** Consiste en descomponer jerárquicamente un proyecto grande en componentes o actividades progresivamente más pequeñas y fáciles de estimar.
    - **Planning Poker:** Técnica colaborativa y basada en consenso muy usada en _desarrollo ágil_ (Scrum). Participan todos los involucrados iterativamente usando cartas con la secuencia de Fibonacci para puntuar historias de usuario.
    - **Modelos Empíricos (COCOMO II):** Fórmulas matemáticas basadas en métricas de proyectos anteriores. Incluye modelos como "Composición de aplicación" (basado en puntos de aplicación/pantallas), "Diseño temprano", "Reutilización" y "Post-arquitectura".
- **En pocas palabras:** Hay varias formas de estimar:
    - _Juicio experto:_ Le preguntás a los que más saben (los gurús de la empresa) para que tiren un número en base a su experiencia.
    - _Delphi:_ Le preguntás a los gurús, pero en _secreto_ (por escrito y anónimo). Así evitás que el que grita más fuerte imponga su idea. Lo hacen varias veces hasta que todos coinciden.
    - _Top-Down:_ Agarrás el problema gigante, lo partís en pedacitos chiquitos, estimás cuánto tarda cada pedacito y después sumás todo.
    - _Planning Poker:_ Es el juego de cartas de las metodologías ágiles. Todo el equipo debate una tarea y tiran cartas con números (Fibonacci) al mismo tiempo. Si no coinciden, discuten por qué y vuelven a tirar hasta ponerse de acuerdo.
    - _COCOMO:_ Usar matemáticas y estadísticas de sistemas viejos para calcular el costo del nuevo.

---
---
---

# CLASE 8: PRUEBAS DEL SOFTWARE (CAJA NEGRA Y CAJA BLANCA)

1. El Objetivo de las Pruebas y los Tipos de Defectos

- **Definición Exacta:** El primer objetivo de la prueba es diseñar casos que saquen a la luz diferentes clases de errores, haciéndolo en la menor cantidad de tiempo y esfuerzo. Una prueba **solo tiene éxito si descubre errores**. Los defectos principales se dividen en:
    - _Defecto por omisión:_ Falta algún aspecto clave del código (ej. no inicializar una variable).
    - _Defecto de cometido:_ Algún aspecto es incorrecto (ej. variable inicializada con un valor erróneo).
    - _Principio de Pareto aplicado:_ El 80% de los errores de un software es generado por un 20% del código de dicho software.
- **En pocas palabras:** Probar un sistema NO es tratar de demostrar que funciona bien, ¡es tratar de destruirlo! Si haces una prueba y todo sale perfecto, la prueba fracasó porque no encontró el error. Además, acordate de Pareto: casi todos los dolores de cabeza (80%) siempre están escondidos en un pedacito muy chico (20%) del código.

2. Pruebas de Caja Negra (Prueba de Comportamiento)

- **Definición Exacta:** También denominadas pruebas de comportamiento. Se centran exclusivamente en los requisitos funcionales del software. Se evalúa la interfaz del programa inyectando entradas y analizando las salidas, ignorando por completo la estructura lógica interna (el código fuente). Buscan errores como: funciones incorrectas, errores de interfaz, problemas de rendimiento y errores de inicialización.
- **En pocas palabras:** Imaginate el sistema como una caja cerrada y oscura. No tenés idea de cómo está programado por dentro (no mirás el código Java o Python). Simplemente te sentás como un usuario normal, metés datos (entradas) y te fijás si el resultado que te tira la pantalla (salidas) es el correcto.

3. Técnicas de Caja Negra: Partición Equivalente y Valores Límite

- **Definición Exacta:**
    - **Partición Equivalente:** Divide el dominio de entrada del programa en "clases de equivalencia" (agrupaciones de datos) de donde se derivan los casos de prueba. Por cada condición, se define una _clase válida_ y clases _inválidas_.
    - **Análisis de Valores Límite (AVL):** Complementa la partición equivalente. Como los errores tienden a darse más en los límites del campo de entrada que en el «centro», el AVL selecciona los casos de prueba apuntando exactamente a los "extremos" o bordes de las clases (ej. para un rango de A a B, se prueba A, B, menores a A y  mayores a B).
- **En pocas palabras:**
    - _Partición Equivalente:_ Si un campo acepta edades de 1 a 100, no vas a probar los 100 números porque no terminás más. Creás un grupo de datos "válidos" (ej. probar con el 25) y grupos "inválidos" (probar con letras, o números negativos).
    - _Valores Límite (AVL):_ Los programadores siempre le pifian en el signo menor o en el menor igual. Por eso, los errores están en las "fronteras". Si la edad es de 1 a 100, la técnica AVL te dice que pruebes exactamente con 0, 1, 100 y 101.

4. Pruebas de Caja Blanca (Prueba de Cristal/Estructural)

- **Definición Exacta:** Deriva casos de prueba a partir de un escrutinio profundo de la estructura de control interna y los detalles procedimentales del código. Garantiza que se ejercite por lo menos una vez cada camino independiente del módulo, obligando a ejecutar todas las decisiones lógicas y todos los bucles (while/for) en sus límites.
- **En pocas palabras:** Al revés de la caja negra, acá la caja es de cristal: ves todo el código. Diseñás pruebas para asegurarte de que el flujo de ejecución pase por absolutamente cada renglón de código, cada "IF" (por el lado del verdadero y del falso) y cada bucle que el programador haya escrito.

5. Prueba del Camino Básico y Complejidad Ciclomática (TEMA FIJO)

- **Definición Exacta:** Es una técnica propuesta por Tom McCabe que utiliza un "grafo de flujo" (con Nodos, Aristas y Regiones) para obtener una medida cuantitativa de la complejidad lógica del código. Esta métrica se llama **Complejidad Ciclomática (V(g))** y define el número máximo de caminos independientes de un programa. Existen tres fórmulas para calcularla:
    1. V(g) = Cantidad de regiones del grafo (incluyendo el exterior).
    2. V(g) = Aristas - Nodos + 2.
    3. V(g) = Nodos Predicado + 1 _(Un nodo predicado es aquel del que salen dos o más flechas, como un IF)_.
- **En pocas palabras:** Es agarrar el código y dibujarlo como un mapa de flechas y circulitos (grafo). La _Complejidad Ciclomática_ es una cuentita matemática muy simple que hacés mirando ese dibujo. El resultado de esa cuenta te dice exactamente: _"Tu código tiene X caminos distintos"_. Entonces, el equipo de pruebas ya sabe que tiene que inventar exactamente X casos de prueba para cubrir todo el código sin dejar nada afuera.

---
---
---

# CLASE 9: ESTRATEGIAS DE PRUEBA Y DEPURACIÓN

1. Enfoque Estratégico, Verificación y Validación

- **Definición Exacta:** Una estrategia de pruebas proporciona una guía que describe los pasos a seguir, cuándo se planean, y cuánto esfuerzo, tiempo y recursos se requerirán. En esta etapa se diferencian dos conceptos clave:
    - **Verificación:** Responde a _¿Estamos construyendo el producto correctamente?_ (se enfoca en que los componentes funcionen bien desde lo técnico).
    - **Validación:** Responde a _¿Estamos construyendo el producto correcto?_ (asegura que el software satisface las expectativas y necesidades reales del cliente).
- **En pocas palabras:** La estrategia es tu mapa de ruta para no probar a ciegas. La **verificación** es chequear que el código no tenga _bugs_ (hacerlo bien). La **validación** es chequear que no construiste algo que el cliente nunca te pidió (hacer lo correcto).

2. Pruebas de Unidad y su Entorno (Conductores y Resguardos)

- **Definición Exacta:** Es el primer nivel de prueba, donde el foco es un componente individual (el módulo o clase). Se prueban su interfaz, estructuras de datos locales, condiciones límite y caminos independientes. Para probar un módulo de forma aislada, se necesita crear un entorno de prueba compuesto por:
    - **Controlador (Driver / Conductor):** Un programa principal temporal que acepta los datos de prueba y "llama" al módulo a probar.
    - **Resguardo (Stub):** Un subprograma "ficticio" que reemplaza a los módulos subordinados que el módulo principal necesita llamar, pero que aún no han sido desarrollados.
- **En pocas palabras:** Es agarrar un solo engranaje del sistema y probarlo suelto. Como el engranaje no funciona solo, le armamos un programa falso que lo ponga en marcha (_Driver_) y pedacitos de código de mentira que devuelvan resultados básicos (_Stubs_) para fingir que el sistema está completo.

3. Pruebas de Integración (Descendente vs. Ascendente)

- **Definición Exacta:** Se toman los componentes que pasaron las pruebas de unidad y se los combina según la arquitectura para verificar que trabajen juntos correctamente. Existen dos enfoques principales:
    - **Integración Descendente (Top-Down):** Inicia por el programa principal y va bajando por la jerarquía. Su principal desventaja es que requiere programar muchos **resguardos** (stubs) para simular los módulos inferiores faltantes.
    - **Integración Ascendente (Bottom-Up):** Empieza por las "hojas" (los módulos de más bajo nivel). En este caso, se eliminan los resguardos, pero se requiere programar **conductores** (drivers) para coordinar las pruebas. La desventaja es que el programa como entidad global "no existe" hasta que se agrega el último módulo superior.
- **En pocas palabras:** Ya probaste las piezas sueltas, ahora hay que armar el rompecabezas.
    - _Top-Down_ es armar la casa desde el techo hacia el piso (tenés que poner "columnas de cartón" o _stubs_ para simular el piso que todavía no hiciste).
    - _Bottom-Up_ es armarla desde el piso hacia el techo (no usás cartón, pero no vas a ver la casa completa hasta el mismísimo final).

4. Pruebas de Regresión

- **Definición Exacta:** Consiste en volver a ejecutar un subconjunto de todas las pruebas anteriores cuando se agrega un nuevo módulo o se corrige un error. Su objetivo es asegurar que los cambios en el software no hayan introducido efectos colaterales no deseados ni roto funciones que antes andaban bien.
- **En pocas palabras:** Si tenías una aplicación andando perfecto y hoy le agregaste el "Botón de Pagar", tenés que hacer _pruebas de regresión_ para asegurarte de que al agregar ese botón no rompiste sin querer el "Botón de Iniciar Sesión". Es probar lo viejo para protegerlo de lo nuevo.

5. Pruebas de Validación: Alfa y Beta (¡TEMA FIJO!)

- **Definición Exacta:** Demuestran la conformidad del software con los requisitos del cliente (pruebas de aceptación).
    - **Pruebas ALFA:** Las llevan a cabo los clientes en un entorno estrictamente controlado, **en el lugar de desarrollo**, con el desarrollador presente como observador anotando los errores.
    - **Pruebas BETA:** Las realiza un grupo selecto de usuarios finales en su propio entorno de trabajo real (el mercado). **Los desarrolladores NO se encuentran presentes**.
- **En pocas palabras:**
    - _ALFA:_ Invitás al cliente a tu oficina, le das un café, lo sentás en la compu y lo mirás fijamente mientras usa el sistema para ver dónde se traba.
    - _BETA:_ Le tirás el sistema por internet a miles de usuarios reales (como el programa Beta Tester de Google) y que lo usen en sus casas. Vos no podés ayudarlos; si explota, te mandan un reporte automático.

6. Depuración (Debugging)

- **Definición Exacta:** Es el proceso de identificar la causa de un error y corregirlo. **La depuración no es una prueba**, sino la consecuencia directa de una prueba que tuvo éxito (encontró un error). Si no se encuentra la causa fácilmente, el depurador debe plantear hipótesis y diseñar pruebas adicionales para arrinconar el fallo de forma iterativa.
- **En pocas palabras:** La prueba es el policía que encuentra el problema. El _debugging_ (depuración) es el cirujano que se mete a revisar el código línea por línea para entender por qué falló y operarlo hasta arreglarlo. ¡No son lo mismo!

---
---
---

# CLASE 10: MANTENIMIENTO Y REJUVENECIMIENTO DEL SOFTWARE

1. El Mantenimiento de Software y los Sistemas Heredados

- **Definición Exacta:** El mantenimiento de software es el proceso de modificar, actualizar y cambiar el software para satisfacer las necesidades del cliente (fase llamada "Evolución del Sistema"). Comienza casi de inmediato tras liberar el software a los usuarios,. Involucra entre un 40% a 70% del costo total de desarrollo. Es frecuente lidiar con _sistemas heredados_, los cuales son viejos, carecen de metodología, documentación o modularidad.
- **En pocas palabras:** El trabajo no termina cuando entregás el sistema; de hecho, ahí empieza el gasto más grande. El mantenimiento es todo lo que le hacés al sistema una vez que ya está usándose. Suele ser un trabajo poco atractivo porque te toca leer código viejo, desordenado y sin manuales que hizo otra persona hace años.

2. Dinámica de Evolución y las "Leyes de Lehman"

- **Definición Exacta:** Manny Lehman desarrolló teorías sobre la evolución de los programas. Las más destacadas son:
    - _Cambio continuado:_ Un programa en un entorno real necesariamente debe cambiar o se volverá menos útil,.
    - _Complejidad creciente:_ A medida que cambia, su estructura tiende a ser cada vez más compleja,.
    - **Barrera de mantenimiento:** Llega un punto donde cada modificación aumenta tanto la complejidad que mantener el sistema resulta lento, costoso y difícil. En ese momento, es necesario rediseñar o reemplazar el software.
- **En pocas palabras:** Lehman dijo algo muy simple: un software vivo tiene que actualizarse sí o sí. Pero cada vez que le metés un "parche", el código se enreda más. Llega un punto crítico (la barrera) donde el código es un plato de espagueti tan inmanejable que te sale más barato tirarlo a la basura y hacerlo de nuevo que intentar arreglarlo.

3. Tipos de Mantenimiento (¡TEMA FIJO A DESARROLLAR!)

- **Definición Exacta:** El mantenimiento se divide estrictamente en 4 categorías:
    1. **Correctivo:** Acción reactiva para diagnosticar y corregir errores o fallos detectados en producción,,.
    2. **Adaptativo:** Modificación del software para interaccionar correctamente con un entorno cambiante (ej. cambios en el sistema operativo, hardware, nube o políticas fiscales),,.
    3. **Perfectivo:** Mejoras al sistema en respuesta a peticiones de los usuarios para mejorar la eficiencia, el rendimiento o agregar nuevas funcionalidades,,.
    4. **Preventivo:** Se efectúa antes de que haya una petición o fallo, para facilitar el futuro mantenimiento y prevenir problemas (ej. refactorizaciones, instalar antimalware, backups),.
- **En pocas palabras:**
    - _Correctivo:_ Saltó un bug y el cliente no puede facturar. Hay que arreglarlo ¡ya!
    - _Adaptativo:_ Salió Windows 11 o cambió una ley de la AFIP. El sistema andaba bien, pero tenés que tocarlo para que se adapte al nuevo entorno.
    - _Perfectivo:_ El sistema anda perfecto, pero el cliente quiere que le agregues un botón nuevo para sacar reportes en Excel.
    - _Preventivo:_ Actualizás el antivirus y limpiás el código hoy para que no explote mañana.

4. Rejuvenecimiento del Software (¡TEMA FIJO A DESARROLLAR!)

- **Definición Exacta:** Es el proceso que intenta aumentar la calidad global de un sistema "heredado" existente, contemplando sus partes retrospectivamente,. Se divide en 4 tipos:
    1. **Re-estructuración:** Simplifica la estructura del código y elimina código muerto para hacerlo más fácil de entender y cambiar, _sin alterar la funcionalidad_ del sistema,.
    2. **Re-documentación:** Realiza un análisis estático del código vivo para generar la documentación faltante del sistema (ej. obtener diccionarios de datos, jerarquías de clases o diagramas),,.
    3. **Ingeniería Inversa:** Proceso de analizar el código binario o fuente de un sistema para extraer y recuperar su diseño y especificación original perdida (se pueden usar herramientas como _Ghidra_),.
    4. **Re-ingeniería:** Produce un _nuevo_ código fuente. Involucra hacer ingeniería inversa para entender el sistema viejo, modificar y actualizar el diseño, y luego hacer ingeniería progresiva regenerando un sistema completamente nuevo,,.
- **En pocas palabras:** Cuando el sistema heredado está al borde del colapso, le hacemos un tratamiento de belleza:
    - _Re-estructurar:_ Ordenar y limpiar el código por dentro para que se lea mejor (el usuario ni se entera).
    - _Re-documentar:_ Como no hay manuales, usamos programas que lean el código y nos dibujen los planos automáticamente.
    - _Ingeniería Inversa:_ Es agarrar el auto, desarmarlo pieza por pieza para entender cómo lo fabricaron en su momento porque nadie se acuerda.
    - _Re-ingeniería:_ Es el "borrón y cuenta nueva". Analizás el sistema viejo para entender qué hacía, y lo volvés a programar entero desde cero con lenguajes y arquitecturas modernas.

---
---
---

# CLASE 11: AUDITORÍA INFORMÁTICA

1. ¿Qué es la Auditoría Informática?

- **Definición Exacta:** Es un examen crítico que se realiza con el objeto de evaluar la eficiencia y la eficacia de una sección o de un organismo, y determinar cursos alternativos de acción para mejorar la organización y lograr los objetivos propuestos. Es una función desarrollada para asegurar la salvaguarda de los activos de los sistemas, mantener la integridad de los datos y lograr eficacia y eficiencia (según Ron Weber). Es una actividad **preventiva** (permite prevenir delitos y problemas legales) y no es una actividad meramente mecánica. El auditor sugiere estrategias.
- **En pocas palabras:** Es como hacerle un chequeo médico completo a los sistemas de una empresa. No vas a arreglar el código, vas a revisar si la empresa está protegiendo bien sus datos, si no es vulnerable a hackeos o si están perdiendo plata por tener malos sistemas. Mirás, anotás los problemas y decís: "Acá tienen que mejorar esto para que no ocurra un desastre".

2. Tipos de Auditoría y Roles (Consultor vs. Auditor)

- **Definición Exacta:**
    - _Auditoría Interna / Externa:_ La interna usa los propios recursos de la organización y puede disolverse por decisión de la misma. La externa es realizada por terceros independientes.
    - _Consultor Informático:_ Tiene un enfoque estratégico, organizativo y amplio.
    - _Auditor Informático:_ Tiene un enfoque más técnico y específico; se centra en identificar riesgos, vulnerabilidades y evaluar controles perimetrales.
- **En pocas palabras:**
    - _Interna/Externa:_ O contratás a tus propios empleados para que te auditen (interna), o le pagás a una consultora de afuera para que sea más imparcial (externa).
    - _Consultor vs Auditor:_ El consultor te ayuda a pensar en grande ("Deberíamos migrar a la nube para vender más"). El auditor va al detalle técnico y te marca los errores ("Tenés un agujero de seguridad en el puerto 80 del servidor").

3. Las Etapas de la Auditoría Informática

- **Definición Exacta:** El proceso de auditoría no es improvisado; consta de 4 etapas formales:
    1. **Planeación:** Definir qué se va a auditar y cómo.
    2. **Ejecución:** Llevar a cabo el análisis y recopilar información.
    3. **Análisis de los datos recabados:** Evaluar las condiciones observadas frente a las ideales.
    4. **Elaboración de un informe escrito:** Emisión de la opinión formal del auditor.
- **En pocas palabras:** 1) Planificás qué vas a revisar. 2) Vas y te metés en los sistemas (ejecutás). 3) Pensás en todo lo que encontraste. 4) Escribís el informe final para dárselo a la gerencia.

4. Los Principios del Auditor (¡Temas fijos de Choice!)

- **Definición Exacta:** El auditor debe regirse por un código ético muy estricto. Los más evaluados son:
    - **Principio de Independencia:** Obliga al auditor a mantener autonomía absoluta en su trabajo y juicio, incluso si tiene una relación laboral de dependencia con la empresa auditada.
    - **Principio de Discreción (Secreto Profesional):** Exige al auditor evitar divulgar cualquier dato obtenido durante la auditoría, incluso si este parece inofensivo.
    - _Otros principios:_ Beneficio del auditado, economía, precisión, información suficiente, comportamiento profesional.
- **En pocas palabras:** Si sos auditor, tenés que ser un juez imparcial (**Independencia**): si tu jefe hizo un desastre en la base de datos, lo tenés que reportar igual, sin dejarte influenciar. Y además, tenés que tener la boca cerrada (**Discreción**); no podés andar contándole a nadie lo que viste en los servidores de la empresa.

5. Metodologías de Auditoría: OCTAVE y MAGERIT

- **Definición Exacta:**
    - **OCTAVE:** (_Operationally Critical Threat, Asset, and Vulnerability Evaluation_). Es un enfoque estructurado para evaluar riesgos de seguridad. Sus pasos ineludibles son: 1) Identificar activos, 2) Analizar amenazas, 3) Determinar vulnerabilidades.
    - **MAGERIT:** Es otra metodología formal de análisis de riesgos. Su orden de etapas comienza estrictamente con la _Planificación_, seguida por el _Análisis_, luego la _Evaluación_ (de controles) y finaliza con las _Recomendaciones_.
- **En pocas palabras:** Son las "recetas" que usa el auditor para no hacer las cosas a lo loco. _OCTAVE_ te dice: primero buscá qué cosas de valor tiene la empresa (activos), fijate quién los quiere atacar (amenazas) y por dónde podrían entrar (vulnerabilidades). _MAGERIT_ te marca un paso a paso ordenado: primero planificás, después analizás, luego evaluás qué tan bien se defienden, y por último les das recomendaciones.

6. El Reporte de Hallazgos

- **Definición Exacta:** Es el componente clave y final de la auditoría informática. En esta etapa se documentan de manera clara y concisa los problemas, debilidades o riesgos identificados. Clasifican los problemas asignándoles un **Nivel de Riesgo** (ej. Alto, Medio, Bajo) y proponen recomendaciones específicas para solucionarlos.
- **En pocas palabras:** Es el boletín de calificaciones que le entregás al cliente al final. Es una tabla donde le decís directamente: _"Hallazgo: Los usuarios comparten la misma contraseña. Nivel de riesgo: ALTO."_ Y abajo le explicás cómo solucionarlo.

---