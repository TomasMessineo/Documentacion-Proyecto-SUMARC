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

