
# QoCode: Evaluación automática de calidad de código en tareas de programación

**Tontexto y neceesidades detectadas:** Los tests automáticos verifican si el código funciona, aunque estos no dicen nada sobre calidad o diseño del código.
Antecedentes relevantes: Messer et. al, Edulint

Se definieron caracteristicas en cuanto a la legibilidad:
- Claridad semántica de nombres
- Etilismo de nombres:
- Formato del código
- Claridad semántica de valores

Para la mantenibilidad:
- Código repetido
- Diseño pobre
- Simplificable
- Construcción inadecuada

De esto surge QoCode.

Es una web para que sea ligero, y tenemos un servidor HTTP, luego la lógica de la aplicación y el motor de analisis que mezcla Pylint, FlakeS y otras cosas, y algunas validaciiones propias sobre el AST.
Capa de traducción: Unifica todos los hallazgos en un formato común, incluyendo línea, mensaje, descripción y consejo. 
Los docentes tienen que usar este feedback devuelto por la app, no los alumnos.

En la Demo mostrada en video se puede subir un archivo solo o un zip, donde se ven las medidas particulares de qué es lo que se va a buscar en el código, el docente elegirá esto. En la parte de hallazgos se da el feedback, algo como: La función es muy larga, la variable cambia de Integer a String. Esto se puede exportar a TXT, md o PDF.

En cuanto la evaluación de la herramienta, había dos escenarios marcados:
Escenario A: de 9 grupos, 7 de 9 presentaba números mágicos, entre otros problemas, 6  de 9 hacían métodos largos. En 4 trabajos, el docente dijo "esta función es difícil de leer" -> Feedback docente rico y detallado

Escenario B: 20 grupos, el feedback docente está centrado en lo funcional.

Escenario C: Se refinó para que se tuviera mas en cuenta otros aspectoss de semátntica. Como catálogo de medidas ampliado, parsing tolerante a errores de sintáxis, categoría "otros" para errores críticos, mas formatos de descarga.

Discusiones y conclusiones:
- QoCode cubre bien defectos estructuraes basados en reglas y en el AST.
- Se le escapa lo relativo al contexto semántico profundo.

Conclusión:
- No reemplaza, sino que complementa, que los alumnos puedan llevarse un poco mas de info a bajo costo.

Próximamente se quiere aplicar como pate de los cursos. Además, se quiere generalizar mas allá de Python, no solo para python. Se quiere ampliar aún más la semántica.
**Para probarlo hay que escribirle a los autores: didactica@dc.uba.ar**

---


# Codexi: An AI-Based Adaptive Tutor for Guided Learning of Algorithms

 Diseñado para guiar a los alumnos en la resolucion de problemas algorítmicos.

El desafío pedagógico de los docentes es el cambio en el proceso de aprendizaje de los alumnos, donde los mismos tienen un problema, van a alguna plataforma de IA y obtienen un resultado. Están saltando el proceso de aprendizaje y análisis. La pregunta es si estos modelos pueden brindarnos un acompañamiento además de resolver, eso es lo que se plantea.

La propuesta a la solución es Codexi, que es un tutor con IA integrada con un objetivo especial que es guiar al alumno en la solución a un alumno, sin darle una respuesta inmediata. La idea es guiarlo paso a paso, brindando retroalimentación en cada uno de los mismos. Esto también va a detectar inconsistencias e ir brindando pistas para ir solucionando el problema.

La metodología pedagógica planteada es un 

La idea es que el alumno no ingrese un problema de programación y que tenga que ir a codificar, sino que vaya analizando un problema entendiendo lo que debe hacer previo a la programación. La plataforma tiene niveles progresivos para entender los temas básicos, sugiere ejercicios o permite plantearlos mediante imágenes, audios, etc. Durante todas las etapas está integrada la IA mediante un grafo de reglas. Se puede desarrollar un pseudo código y hacer una compilación de ese programa también mediante. Si estas por superar el nivel hace preguntas para saber si los conocimientos están acentados. Brinda feedback sobre los fundamentos en los que se está sólido y en los que no tanto.

La IA está orquestada, no utilizada directamente
Estudiante -> Reglas pedagócias -> Tutor de IA -> Retroalimentación.

Está implementado en GTP 4o mini.
Está integrado Whisper-1 para entrada de mensajes de voz para reducir de fricción en la escritura.

El modelo de datos del alumno, los ejercicios por nivel creados (si se agotan se aregan ejercicios online con la IA, para consumir menos tokens) hecho en postreSQL. Esto está integrado con google analytics para tener en cuenta métricas. Hay un modo entrevista que es un exámen, donde el tutor se comporta distinto y no te responde mucho.

Se generaron reglas para usar pseudocódigo que luego será directamente transformado para compilarse en C 

Se utilizó en 2 comisiones, con 51 alumnos con una tasa de 65% de ejerciciso terminados, con un aproximado de 17 minutos para terminarse los ejercicios.
Esto se plantea para que un alumno pueda tener feedback sin estar cara a cara con el profesor.

Aportes:
- IA como tutor 
- Metodología estructurada
- IA + entorno de programación
- Validacion inmediata: C y pseudocódigo pueden ejecutarse dentro del entorno

Proximos pasos:
- Avanzar sobre metricas y estudios longitudinales de la adopción y del aprendizaje, para ver si realmente esto mejora el aprendizaje
- Métricas de aprendizaje específicas
- Evaluación de percepción estuidantil
- Amplición de la experiencia a nuevos grupos

codexiapp.com

---

# Desarrollo de habilidades en programación para estudiantes de ciencias agropecuarias de la Universidad Nacional de Córdoba

