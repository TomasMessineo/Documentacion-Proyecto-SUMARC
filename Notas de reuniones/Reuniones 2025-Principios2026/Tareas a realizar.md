
---
---

- Validar XMLs generados con algún validador de XML JATS. Fijarse si el xml luego de convertirlo desde docx es igual al guardar los cambios desde texture o se pierde información. Anotar errores que tenga el XML probando con varios validadores de JATS, tanto luego de pasar de docx -> xml jats, como luego de guardar los cambios desde texture. **Esta puede ser una tarea que sea realizada por Santi ya que no sería tan técnica**
  
- Generar salida HTML en base a lo que está realizando Leo (asi también como E-PUB, PDF-A, etc.)

- Datos eliminados por Texture -> como el traductor por ejemplo

- Añadir funcionalidad en SUMARC para gente con discapacidad visual (idea de Ari)

- Error en la revista plurentes con respecto a la carga de imágenes en artículos

- No sé en qué habrán quedado Lucía y Luisina con Veronika (de la revista Ecos) 

- Las imágenes pueden estar cargadas en diferentes idiomas desde la sección editar del XML

- Reconocer imágenes en texture por el nombre de la imágen. Esto supone algún tipo de error si las imágenes tienen nombres diferentes con respecto a como se suben y cómo aparecen en el XML JATS -> NO es un problema

-  Encarar LaTeX (no sé bien como funciona ni cómo habría que encararlo, pero lo tengo anotado en base a lo que se dijo en la última reunión sobre lo charlado en Alemania-Brasil)

- Integración con PrePrints. Ídem punto anterior.

- Mejorar las Regex para que la detección automática de referencias pueda ser mejor

- Cambiar a branch pp-leo-plugin y pp-leo-submodule en servidor SUMARC para que Leo pueda realizar pruebas con artículos reales

- Cambios de márgen dinámicos en la creación de un PDF -> a futuro, es imposible xd (nada es imposible, esta hecho pero se rompen headers y footers :)

- Tener claro que propone PKP con respecto al manejo del XML y demás.

- Soporte para nuevas referencias en docxConverter y mejorar el soporte para APA. Posibilidad: Meter referencias con errores al final del texto del body para mostrarlas en vez de que texture limite y las muestre SIEMPRE como referencias de tipo Journal a aquellas referencias que tengan errores. Además, soporte para otros tipos de estilos como AMA, IEEE, etc... pestaña de configuración para elegir el estilo de cita y aplicar Strategy para elegir como parsear.
  También se pueden soportar otras versiones de estpabdar de citación, como APA 6 por ejemplo, que supondría no muchos cambios...
  El docxConverter debería permitir elegir el 

- Texture pisa las citas, y en el caso de que se pasen de DOCX a XML JATS, la tabla de citas debería seguir estando ya que sino no hay manera de volverlas a modificar si texture las pisó. 

- Soporte para nuevas plantillas en base a la PPS de Leo

# Prioridades:

2-> En el HTML de previsualización las imágenes no salen, esto hay que corregirlo. Lo tengo marcado como urgente -> **Generarar salida HTML mediante base64 y de PDF con rutas** 

3-> Modificación de fechas de envío y aceptación de forma manual (si alguna revista usa QuickSubmit

-  Agregar soporte para convertir más elementos en docxConverter (como citas a bando y notas al final del documento, por ejemplo)

- Evaluar si Texture borra datos del < body > o el < front > del artículo al guardar los cambios. Se podría evaluar qué datos están en el XML JATS al generar el XML mediante un DOCX, y comparar ese mismo XML pero luego de guardar los cambios en Texture. De esta forma podríamos ver si se pierden datos entre etapas.

- ¿Documentar docxConverter? (citation-parser al menos) -> no para ya, pero testearlo

- Definir esquema de git con respecto a qué pushear, que mergear, etc.

5-> Ya que se va a trabajar bastante con el conversor de DOCX a XML JATS, quizá sea necesario añadir una forma genérica de testear lo que se viene haciendo. Una idea es integrar PHPUnit para realizar pruebas unitarias al implementar cada funcionalidad.

4-> Referencias incompletas al generar el PDF (como rangos de página, etc)... - ¿Posible archivo .csl de la UNLP? **Ticket:** https://trac.prebi.unlp.edu.ar/issues/12610 

- Identificar prioridades y pensar en Santiago para ordenarle el trabajo para que aprenda las tecnologías, todo, y empezar a hacer aportes pequeños para sentirse útil. Ver donde encaja Santi en todo esto. El martes tipo 10 hacemos una reunion para hablar mejor sobre el proyecto.

# A REVISAR:

-  Limpiar o buscar citas luego de importar los datos de la base de datos, para filtrar al renderizar la "tabla de citas" aquellas citas que hayan sido eliminadas desde texture para que no vuelvan a aparecer en la tabla de citas (no se rendericen). Lo que tengo que hacer es implementar un botón para eliminar citas específicas.

-  Había un tema con la tabla de citas si se tenían 2 archivos XML JATS en la etapa de publicación... si previamente se tenía información guardada sobre las citas de un XML JATS, al guardar una configuración específica para el otro XML JATS, se pierde la primer configuración guardada

- En vez de guardar la configuración de las citas en la base de datos, evaluar la posibilidad de hacerlo en un XML

# Tareas resueltas:

1) Terminar la integración de OpenAlex (eliminar error_logs, archivos de prueba, y migrarlo también a OJS 3.3). Testear la integración con OpenAlex 
   **Finalizado. Queda implementar integración con DOI**

**Pequeña aclaración en general:** Las imágenes que se asocien como archivos dependientes a un archivo XML en OJS deben tener como nombre designado EXACTAMENTE el mismo nombre que tienen en el XML. Si en el XML el nombre de la imágen es imagen1.jpg y como archivo dependiente su nombre es imagen1.png, la misma NO aparecerá. Tienen que tener el mismo nombre SÍ O SÍ.