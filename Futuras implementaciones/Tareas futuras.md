
- Validar XML mediante https://jats4r-validator.niso.org/
- Importar artículo de revista a un ojs local diferente. Hay varios errores, evaluar si esto se puede.
- Terminar de documentar, eliminar error_logs() y demás de integración con OpenAlex. Pushear los cambios.
- Limpiar o buscar citas luego de importar los datos de la base de datos, para filtrar al renderizar la "tabla de citas" aquellas citas que hayan sido eliminadas desde texture para que no vuelvan a aparecer en la tabla de citas (no se rendericen)

--- 

Tareas para vacaciones:

- Probar si existe alguna IA o algo que se pueda hacer con las referencias que no se pueden procesar desde docxConverter... la idea sería evaluar qué se puede hacer con ellas para evitar errores registrados.
- Probar el docker de OJS donde se puede tener un entorno levantado directamente sin tener que hacer un contenedor docker separado
- Documentación técnica de Citation-parser y lo que hizo Leo