
- Terminar de documentar, eliminar error_logs() y demás de integración con OpenAlex. Pushear los cambios.
- Limpiar o buscar citas luego de importar los datos de la base de datos, para filtrar al renderizar la "tabla de citas" aquellas citas que hayan sido eliminadas desde texture para que no vuelvan a aparecer en la tabla de citas (no se rendericen)

--- 

Tareas para vacaciones:

- Probar si existe alguna IA o algo que se pueda hacer con las referencias que no se pueden procesar desde docxConverter... la idea sería evaluar qué se puede hacer con ellas para evitar errores registrados.
- Probar el docker de OJS donde se puede tener un entorno levantado directamente sin tener que hacer un contenedor docker separado
- Documentación técnica de Citation-parser y lo que hizo Leo
- Refactorizar la parte de la creación de la tabla de citaciones. Se me ocurrió que en vez de tener una especie de html que se va generando en base a un estilo de citación específico, se podría tener un html pelado donde se podría elegir el mismo en base a cada estilo de citación (cada estilo de citacion, sea apa, vancouver, AMA, etc. podría tener su propio html para las tablas) donde en base a cada estilo de citación, se va a buscar el html de la tabla, y si lo tiene, lo renderiza mediante el TPL correspondiente a la sección "jatsParser" en la ventana de publicacion
- Crear documentación completa de SUMARC, a lo mejor se puede hacer con gitbooks
- Mergear la branch de pps-leo en main o dev
- Mergear los cambios de Santi en docxConverter a main o dev
- Migrar nuevos plugins a OJS 3.3

- Resolver tarea de CSL -> Prioritario
- Meter mano en texture
- Documentar el plan de testing para la integración de OpenAlex en el submodulo citation-parser del plugin docxConverter. A lo mejor se pueden programar agentes de IA que reciban como input el XML antes de pasar por OpenAlex, el JSON retornado por OpenAlex y el XML después de ser pasado por OpenAlex (ya enriquecido). 

- Mixed citations en texture
- Coordinador en texture
- CiteProc en texture
- En Texture si hay referencias que no se detectan (por ejemplo vienen con un error desde el conversor), se genera de forma predeterminada como Journal, y no se puede modificar. Esto debería poder modificarse.

- Para el nuevo botón hay un problema con los permisos... en el servidor de producción NO aparece el botón "Descargar". Así que esto es un problema de permisos. Además, al apretar "Descargar" el servidor de producción lleva a una página con un error 404 not found, que también quizá sea un tema de permisos. En Sumarctest anda todo perfecto, en el servidor de producción NO.

- Mejorar el CSL