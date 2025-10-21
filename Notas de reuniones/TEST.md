
- PHPUnit

- Buscar artículos marcados en OJS, pasarlos a la version de testing de leo, generar el pdf con esos artículos

---

- En cuando al problema relacionado con los cambios realizados desde la pestaña "Tablas y Figuras" para las citas, no entendí muy bien a qué se refiere con "esos cambios no se reflejan luego con el Texture". En sí, la tabla de citas (donde aparecen las 2 opciones: Referencias y Tablas - Figuras) se utiliza para poder especificar el texto que queremos que aparezca para cada cita que marcamos desde texture. Los cambios que realicemos en la tabla de citaciones, sea para referencias o tablas y figuras, se verán reflejados SOLO al generar el PDF, no en texture. Texture solo sirve para indicar DÓNDE queremos que haya una cita (sea a una referencia, tabla o figura). 
  Además, en las sección de "Tablas y Figuras" dentro de la Tabla de Citas, solo aparecerán aquellas citas a figuras y tablas que se hayan indicado en Texture. Si desde Texture no se indicó ninguna cita a tablas o figuras, entonces estas mismas no van a aparecer en la Tabla de Citas.

- El error con las imágenes en la revista "Plurentes" está siendo encarado en estos momentos. Estamos trabajando para solucionar este problema lo antes posible.  

- Texture actualmente no soporta listados o viñetas dentro de tablas. A lo sumo puede copiarse un símbolo para el listado (como •) pero los items del listado saldrán uno tras otro sin salto de línea.

- La justificación para texto del artículo fue añadida en la última actualizacion de SUMARC.

- Con respecto a la edición de fechas de recepción, aceptación y publicación, el único valor que puede modificarse dentro de OJS es la fecha de PUBLICACIÓN. Las demás fechas no pueden modificarse de forma manual ya que OJS almacena estos metadatos internamente y los plugins recuperan estos mismos para mostrarlos 

---

- Validar XML mediante https://jats4r-validator.niso.org/
- Importar artículo de revista a un ojs local diferente. Hay varios errores, evaluar si esto se puede.
- Terminar de documentar, eliminar error_logs() y demás de integración con OpenAlex. Pushear los cambios.
- 