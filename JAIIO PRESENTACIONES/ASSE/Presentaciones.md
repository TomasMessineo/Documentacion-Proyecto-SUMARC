
**Lunes 10/8**
# Revisión de código automatizada utilizando Large Language Models.

Actualmete la revisión manual se convierte en un cuello de botella en la integración de desarrollos utilizando LLMs.
Los tres problemas que se identifican son:
- El costo.
- Repetitividad.
- Presión operativa.

Automatización parcial del feedback look:
1. Analizar diffs
2. Evaluar reglas
3. Generar comentarios

Integración en el flujo de CI/CD
1. Desarrolo
2. Commit
3. Pull request
4. Revisión automática -> Agrega comentarios con las evaluaciones
5. Validación humana

PR -> Github Action -> entrypoint.py -> GithubInterface (GitHub API) -> Reviewer (se junta con prompts.yml, define las reglas para que el revisor pueda hacer una evaluación del código que se está subiendo) -> LLM

**Reviewer: clase abstracta extensible**
1. Como entrada se tienen los diff, metadatos del PR y reglas del repositorio. 
2. Hooks: Funciones de pre y postprocesamiento registrables

Se deben tener 3 prompts: 
- Prompt base
- Prompts de regla
- Formato de salida

Tres dimensiones complementarias:
- Rendimiento
- Aceptación: Se encuestó a 8 desarrolladores. 6/8 dijeron que sí usarían la herramienta, los demás no.
- Factibilidad

La propuesta utiliza un modelo vía API y trabaja sobre contexto y reglas del proyecto. La implementación evaluada consume la API de Azure OpenAI preview 4.2. Este modelo se usó durante todo el desarrollo del proyecto.
El agente solo tiene acceso al diff, no tiene un acceso mas profundo sobre el código. 

---

# Adaptación de Scrum para Jornada Laboral de 4 días

Se pensó en cómo se lleva Scrum y como se piensa para esta jornada laboral reducida. Se buscó coordinar y buscar trazabilidad en el equipo.
Se buscaron trabajos relacionados, donde se buscaban distintos objetivos.

**¿Cómo adaptamos scrum para operar en JLR-4D preservando cordinación y productividad percibida?**
Se parte con Scrum. El sprint dura 2 semanas, 10 días habiles fijos, los mismos roles. Artifactos como el Spring backlog, etc.
Se arranca con un cronograma y capacidad, para planificar con 6 días efectivos y 4 parciales con superposición real. 
El handoff estructurado habilita al compañero a poder seguir una tarea si yo no puedo asistir.
Se hicieron adaptaciones en el Spring, la capacidad, la daily, la review/retro, entre otras cosas.

Para el handoff tiene que haber información asincrónica y conectividad entre los integrantes del equipo.
El scrum master coordina hand-offs.

Se validó con una opinión experta + SUS, pero no con una implementación industrial.
Lo que se busca es adaptar scrum reconfiurando lo básico de scrum adaptandolo a este entorno planteado. Quieren que el equipo esté predispuesto y también se busca que el equipo se sienta cómodo trabajando de esta manera. Para esto es necesaria una implementación en un entorno de trabajo real.

Tres ideas para llevarse: 
1. JLR-4D exise rediseño metodológico
2. Scrum puede adaptarse sin dejar de ser Scrum
3. La evidencia inicial es favorable, pero preliminar

Cualquier adaptación Scrum puede ser viable, es una estrategia surgida de la práctica, no es algo formal. El scrum es flexible, por ende cualquier variación o adaptación debería ser viable siempre y cuando esté bien adaptada.
El Scrum surgió de la práctica, de las prácticas de la guerra, que fue adaptado como metodología agil.

Para garantizar que el mecanismo de hand-off funcione y al volver el trabajo que se estaba haciendo se haya avanzado al menos un poco. -> Si el kanban está bien, las prioridades van a estar bien definidas, y al final del día de trabajo, me tomo una media horita para poner al día a la persona y que entienda qué es lo que tiene que hacer. Luego, la otra persona decide si hay que bajar un cambio, si entiende, si no. Tiene que haber un paso de información muy claro para saber hasta donde se llegó, sino cuando la persona que delegó la tarea, vuelve, va a estar perdido y no va a entender muy bien qué hacer. También depende mucho de la maduración del equipo y hace cuánto trabajan juntos. Hay que tener en cuenta el equilibrio de Seniority bien definido. Es importante también que el equipo esté dispuesto al cambio.

