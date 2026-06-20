# CLASE 1: COMUNICACIÓN Y ESPECIFICACIÓN DE REQUISITOS

### ### Concepto 1: Proceso de Desarrollo de Software y Elicitación de Requisitos

1. **DEFINICIÓN TÉCNICA FORMAL**: Un proceso de software es un conjunto de actividades y resultados asociados que producen un producto de software. Para representar abstractamente este proceso, se utilizan modelos que abarcan cuatro actividades fundamentales: Especificación, Desarrollo, Validación y Evolución. Dentro de la Especificación, reside la Elicitación de Requisitos, que es el proceso crítico de adquirir (o "sonsacar") todo el conocimiento relevante necesario para producir un modelo de los requerimientos de un dominio de problema determinado.
2. **ATRIBUTOS Y COMPONENTES CLAVE**:
    - **Objetivos de la Elicitación**:
        - Conocer en profundidad el dominio del problema para establecer un canal de comunicación efectivo con clientes y usuarios.
        - Conocer y analizar el sistema actual (ya sea manual o informatizado).
        - Identificar las necesidades explícitas e implícitas de los clientes y sus expectativas reales sobre el sistema.
    - **Tipos de Requerimientos**: Se dividen dicotómicamente en Funcionales (definen el comportamiento y las tareas del sistema) y No Funcionales (describen atributos deseables como el rendimiento, la usabilidad, seguridad, etc.).
3. **REGLAS DE NEGOCIO Y MODELADO**: La elicitación correcta obliga a que las necesidades implícitas (aquellas que el cliente da por sentado) sean transformadas en reglas de negocio explícitas para el modelado de datos. El fracaso en esta extracción de conocimiento genera un abismo entre la solicitud inicial del usuario y el soporte operativo real (el clásico problema del "columpio en el árbol").
4. **CASOS DE USO O ESCENARIOS TÍPICOS**: Un equipo comienza a relevar un sistema hospitalario. La elicitación exige no solo anotar que "el médico debe cargar la historia clínica" (necesidad explícita funcional), sino investigar el dominio médico para entender cómo fluye físicamente el paciente (necesidad implícita), impactando en cómo se diseñan las interfaces del sistema.
5. **DISYUNTIVAS DE DISEÑO (TRADE-OFFS)**:
    - _Ventaja_: Descubrir las necesidades implícitas evita la reestructuración tardía de la base de datos o arquitectura.
    - _Desventaja_: Es un proceso altamente dependiente de la calidad de la interacción humana; los problemas de comunicación (verbal y no verbal) y malentendidos suelen extender crónicamente esta fase inicial.

---

### ### Concepto 2: Técnicas de Recolección de Hechos (Whitten Bentley)

1. **DEFINICIÓN TÉCNICA FORMAL**: Son métodos heurísticos estandarizados para investigar y extraer la información pertinente de una organización. Según el enfoque de Whitten Bentley, van desde la revisión pasiva de documentos hasta la interacción dinámica extrema como el JRP (Planificación Conjunta de Requisitos).
2. **ATRIBUTOS Y COMPONENTES CLAVE**:
    - **Muestreo de Documentación**: Recolección de hechos a partir de organigramas, memos, minutas, registros contables y solicitudes de proyectos anteriores.
    - **Observación del Ambiente de Trabajo**: El analista se convierte en un observador directo. Lineamientos estrictos: determinar quién/cuándo observar, obtener permiso, mantener bajo perfil, no interrumpir, tomar notas y revisarlas con el personal.
    - **Cuestionarios**: Pueden ser de formato _Abierto_ (lentos para analizar, pero con alta amplitud/profundidad) o _Cerrado_ (rápidos, fáciles de analizar, pero sin naturaleza exploratoria).
    - **Entrevistas**: Requieren preparación (leer antecedentes, objetivos, lenguaje, selección de entrevistados, guion). Las estructuras pueden ser: _Piramidal_ (inductivo), _Embudo_ (deductivo) o _Diamante_ (combinación).
    - **JRP (Planificación Conjunta de Requisitos)**: Sesiones altamente estructuradas que reúnen a profesionales de TI, gerentes, usuarios y un facilitador en un entorno especialmente equipado.
    - **Brainstorming (Tormenta de ideas)**: Generación de ideas de forma intensiva en un tiempo corto, sin someterlas a análisis crítico inmediato.
3. **REGLAS DE NEGOCIO Y MODELADO**: La revisión de "formularios existentes" y "registros contables" predefine directamente la cardinalidad, los atributos y tipos de datos del modelo relacional o de objetos.
4. **CASOS DE USO O ESCENARIOS TÍPICOS**: En un sistema contable, en lugar de preguntar al empleado (que puede omitir pasos automáticos), el analista utiliza la técnica de _Observación_ para ver exactamente en qué orden ingresa los remitos y a qué bases de datos consulta en paralelo.
5. **DISYUNTIVAS DE DISEÑO (TRADE-OFFS)**:
    - _Entrevistas vs Cuestionarios_: Los cuestionarios cerrados ahorran una enorme cantidad de tiempo de análisis pero son inflexibles. Las entrevistas permiten repreguntar y captar lenguaje no verbal, pero consumen gran cantidad de horas del recurso humano clave (el cliente y el analista).

---

### ### Concepto 3: Especificación del Sistema y el Estándar IEEE Std. 1362-1998 (ConOps)

1. **DEFINICIÓN TÉCNICA FORMAL**: Regulado por el estándar IEEE Std. 1362-1998, es un documento dirigido principalmente a los _usuarios_, que describe el "Concepto de Operaciones" (ConOps) y las características del sistema propuesto desde un punto de vista puramente operativo y del usuario final. **¡Atención! Este documento NO debe confundirse con el SRS (IEEE 830)**.
2. **ATRIBUTOS Y COMPONENTES CLAVE**:
    - Es el medio de comunicación que recoge la visión general cualitativa y cuantitativa del sistema.
    - Compartido amigablemente por la parte cliente y desarrolladora.
    - Funciona como una guía de referencia y líneas generales, no especificando técnicas de desarrollo exactas.
    - Permite incorporar elementos personalizados (cláusulas y sub-cláusulas adicionales) según el contexto del proyecto.
3. **REGLAS DE NEGOCIO Y MODELADO**: No define modelados de bases de datos o diagramas UML de alto nivel técnico; se centra en reglas de proceso del negocio orientadas a la operativa diaria (ej. "El empleado debe poder acceder desde su móvil en el depósito").
4. **CASOS DE USO O ESCENARIOS TÍPICOS**: Entregar este documento a la Gerencia Comercial de la empresa cliente para que valide que la propuesta operativa del software (pantallas, accesos, funcionalidades macros) es exactamente lo que esperan usar a nivel de negocio.
5. **DISYUNTIVAS DE DISEÑO (TRADE-OFFS)**:
    - _Ventaja_: Es comprensible por personas sin formación técnica (directivos, inversores), asegurando que todos estén en la misma sintonía conceptual.
    - _Desventaja_: Al no ser técnico, no sirve como guía de construcción para los programadores, requiriendo obligatoriamente un esfuerzo adicional de traducción hacia un documento SRS técnico (IEEE 830).

---

### ### Concepto 4: Especificación de Requisitos de Software (SRS) - Estándar IEEE Std. 830-1998

1. **DEFINICIÓN TÉCNICA FORMAL**: El SRS (Software Requirements Specification) está normalizado por el IEEE Std. 830-1998. Es una especificación rigurosa de las funciones que realizará el software en un determinado entorno. Se asume como el contrato técnico base, escrito conjuntamente por representantes del desarrollo y del cliente.
    
2. **ATRIBUTOS Y COMPONENTES CLAVE**: Debe cumplir con 8 características ineludibles:
    
    - **Correcto**: Cada requisito declarado se encuentra fehacientemente en el software final.
    - **No ambiguo**: Cada requisito tiene una y _solo una_ interpretación posible.
    - **Completo**: Contempla todos los requisitos impuestos por la especificación superior.
    - **Consistente**: No existen contradicciones lógicas internas ni conflictos con documentos de nivel superior.
    - **Priorizado**: Organizado según la criticidad o importancia del requerimiento.
    - **Comprobable (Verificable)**: Existe un proceso (humano o por máquina) para verificar empíricamente que el software cumple el requisito.
    - **Modificable**: Estructura que permite incorporar cambios fácilmente conservando el estilo.
    - **Trazable**: Es posible identificar el origen de un requisito y rastrear su impacto hacia el código y las pruebas futuras.
    
    _Estructura obligatoria del Documento_:
    
    - **1. Introducción**: Propósito, Alcance (qué hará y qué NO hará), Referencias.
    - **2. Descripción General**: Perspectiva, Funcionalidad resumida, Características de los usuarios, Evolución previsible.
    - **3. Requisitos no funcionales**: Rendimiento (carga esperada, mensurable ej. "95% de transacciones en < 1 seg"), Seguridad (criptografía, roles, logs de auditoría), Portabilidad (% de dependencia del hardware o S.O.).
    - **4. Mantenimiento**: Definición de soporte post-entrega.
    - **5. Apéndices**: Casos de Uso, prototipos, etc.
3. **REGLAS DE NEGOCIO Y MODELADO**: La sección "3. Requisitos no funcionales" y "Seguridad" impacta arquitectónicamente obligando a modelar esquemas de bases de datos que soporten cifrado (_encryption_), tablas de registros de actividad (_logs_ de auditoría) y un diseño en capas que separe la persistencia de la presentación. Las reglas de "Rendimiento" condicionan la elección del gestor de base de datos y la concurrencia.
    
4. **CASOS DE USO O ESCENARIOS TÍPICOS**: Un requerimiento de seguridad exige que "Todo acceso al módulo de Facturación debe registrar el ID del operador, Fecha, Hora e IP". Esto se documenta bajo la cláusula 3.2 (Seguridad) del IEEE 830, impidiendo ambigüedades en la programación de los perfiles de acceso.
    
5. **DISYUNTIVAS DE DISEÑO (TRADE-OFFS)**:
    
    - _Ventaja_: Su nivel de formalidad reduce drásticamente el "deslizamiento del alcance" (_scope creep_) y previene disputas contractuales.
    - _Desventaja_: Es un documento estático por naturaleza que choca con los principios ágiles; mantener su "trazabilidad y modificabilidad" en proyectos con altísima volatilidad de requerimientos exige una burocracia que ralentiza el desarrollo.

---

### ### Concepto 5: Presentación de la Idea - Elevator Pitch

1. **DEFINICIÓN TÉCNICA FORMAL**: Un "Elevator Pitch" es una técnica de comunicación ejecutiva consistente en un mensaje extremadamente corto (aproximadamente un minuto o 20 segundos según la urgencia) estructurado para contar el proyecto de una manera diferenciadora, persuasiva e impactante, con el fin de obtener apoyo, financiamiento o atención inmediata.
2. **ATRIBUTOS Y COMPONENTES CLAVE**:
    - **Los 7 pasos estructurados**:
        1. Afirmación o pregunta sorprendente (rompehielo).
        2. Presentación (quién eres).
        3. Problema o necesidad que se cubre.
        4. Soluciones aportadas (qué hace único al proyecto).
        5. Beneficio principal para el usuario.
        6. Idoneidad (por qué este equipo/proyecto es el correcto).
        7. Llamada a la acción final (invitación a otra reunión o inversión).
    - **Tips de comunicación**:
        - _Escrito/Guion_: Investigación de la audiencia, estructura lógica, claridad (evitar tecnicismos), ejemplos prácticos y control del tiempo.
        - _Oral/Presencial_: Lenguaje corporal (manos), entonación, contacto visual y adaptabilidad.
        - _Video_: Sonreír, usar los dedos para enmarcar ideas y modular el énfasis vocal.
3. **REGLAS DE NEGOCIO Y MODELADO**: A nivel de gestión de proyecto, obliga a realizar una "abstracción" radical del alcance del software. Se debe despojar toda complejidad arquitectónica para exponer únicamente las reglas de negocio críticas que generan "Valor de Mercado" o ROI (Retorno de Inversión) para el _stakeholder_.
4. **CASOS DE USO O ESCENARIOS TÍPICOS**: El líder de proyecto de una Startup de software se encuentra casualmente con un inversor (Angel Investor). En lugar de explicar la arquitectura de microservicios o el diagrama de base de datos, en 60 segundos lanza una pregunta retórica sobre una falla del mercado actual, propone su aplicación como la única solución integrada y pide una reunión formal al final.
5. **DISYUNTIVAS DE DISEÑO (TRADE-OFFS)**:
    - _Ventaja_: Maximiza las posibilidades de conseguir los recursos financieros o el apoyo gerencial (Sponsor) en organizaciones con directivos sin tiempo disponible.
    - _Desventaja_: Su brevedad extrema puede llevar a la sobre-simplificación técnica de un software complejo, creando expectativas funcionales poco realistas en el oyente comercial.

---
---
---

