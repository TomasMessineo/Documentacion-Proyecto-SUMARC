
# QoCode: Evaluación automática de calidad de código en tareas de programación

**Contexto y necesidades detectadas:** Los tests automáticos verifican si el código funciona, aunque estos no dicen nada sobre calidad o diseño del código.
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

# Estilos de aprendizaje y preferencias de los estudiantes

**Modelo de felder y silverman:**
Clasifica al estudiante según cuatro dimensiones dicotómicas que describen cómo recibe y procesa la información: 
- Percepción 
- Entrada 
- Procesamiento 
- Comprensión

---
# Project-Based Learning with Arduino for Addressing Sustainable Development Goals in Higher Education

- Aprendizaje basado en proyectos
- ODS
- Educación STEAM

Proyectos desarrollados:
- Respira+: Herramienta desarrollada para prevenir intoxicación doméstica
- Ecomusic: Teclado musical educativo

---


# Formación docente innovadora en programación desenchufada: impacto y resultados de una intervención en Nivel Inicial

**Pilas bloques:**
- Es una herramienta diseñada por el equipo de la fundación Sadoski (?. Es pensar la ciencia de conceptos de programación utilizando un lenguaje de programación basado en bloques, donde hay desafíos.

**Pilas bloques desenchufado (juego de mesa):** 
- Sirve para enseñar a programar en diferentes contextos educativos, enfocado en chicos de un nivel educativo inicial.
- Se creó teniendo en cuenta los pilares del nivel inicial: El juego, descubrimiento, creación y socialización. 

**Estrategia de formación docente:**

- **Propuesta compuesta de 3 componentes articulados:**
  - Taller presencial intensivo
  - Cuaderno para docentes
  - Acompañamiento especializado

- **Objetivo:**
  - Transformar la formación en prácticas pedagógicas concretas

**El rol del responsable de la formación:**
- No transmite soluciones
- Pregunta: Orienta la exploración, recupera estrategias y errores
- Conceptualiza: Relaciona la experiencia con los conceptos

226 estudiantes estuvieron involucrados en la experiencia, junto con 11 profesores.

---

# Análisis Comparativo de la Generalización Algebraica y la Programación en la Cuadrícula como Estrategias que Favorecen el Desarrollo del Pensamiento Computacional

- Abordar tipos de problemas que se puedan trabajar para favorecer la construccón del pensamiento computacional desde la escuela (en especial primaria).

Interesa que los estudiantes reflexionen sobre cuestiones como:
Qué estrategia aplicó al resolver in problema?
Eixisten otras soluciones?
Qué es mejor? 
Etc.

**La máquina de dibujar en la Cuadrícula:**
- Para ejecutar un programa, usaremos hojas de papel cuadriculado. Para crear un programa, escribiremos cada sencuencia de instrucciones de izquierda a derecha. Un programa es una secuencia de pintar y moverse por la cuadrícula. Los primeros ejercicios son cosas como dibujar un cuadrado. La idea es buscar estrategias distintas, como empezar a dibujar el cuadrado desde arriba hacia abajo, de izquierda a derecha, etc.
- La herramienta es sencilla, permite repeticiones. Como moverse a la derecha 3 veces. Se pueden parametrizar las funciones. Permite definir funciones/procedimientos.
- Los conceptos fundamentales que se trabajan son las instrucciones, la estrategia, los procedimientos, los parámetros, el programa y las dos visiones de un programa: ejecución y descripción de la solución que describe la estrategia que hay que llevar a cabo.
- La idea es que los alumnos puedan escribir secuencias de instrucciones y también ejecutarlas, y luego validar/verificar dichas secuencias para corregir aquellas que sean incorrectas. Estos son niveles de actividades.

**Generalización algebráica:**
- Como introducción al algebra, los profesores plantean "Contar sin Contar: El borde del cuadrado", un ejercicio como dibujar una escalera para subir, donde cada escalon sea de 4 cuadraditos, y la altura de 2 cuadraditos (por ejemplo).
- Problema 1: Dado un cuadrado, calcular la cantidad de cuadraditos sombreados. Luego, en grupos, redactar o explicar en lenguaje natural cuál es la estrategia que usaron para contar. Luego, que se pueda generalizar la estrategia a una fórmula que sea su equivalente.

---

# Estrategias Pedagógicas para la Alfabetización en Datos: Un Enfoque Integrador entre la Universidad y la Escuela Secundaria

La idea es incluir contenidos de ciencia de datos en escuelas secundarias. Una escuela puede tener ciertos recursos y otra otros, por ende, la idea sería pensar en una estrategia dependiendo de los recursos de las mismas.
La idea es que los estudiantes generen el conocimiento de lo que estamos tratando de implementar en el aula con respecto a analisis de datos, con respecto a las actividades, haciendo que ellos analicen y piensen sobre un modelo o conjunto de datos, sin estudiar de memoria.
Cuando quiero contar un resultado, se explica cómo mostrar lo que quiero mostrar, mediante gráficos, mapas, artículos, informes, etc.
La taxonomía utilizada es la de Bloom. 
