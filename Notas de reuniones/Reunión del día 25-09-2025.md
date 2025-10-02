
---
---

- Al sistema no le gustan las imágenes. Hay problemas con las imágenes donde a veces no aparecen. Una revista de agronomía probó con diferentes tipos de imágenes, y no le funcionó ninguna.
  EN EL HTML LAS IMAGENES NO SALEN, HAY QUE CORREGIR ESTO TAMBIÉN... DEBEN SALIR LAS IMÁGENES EN EL HTML DE PREVISUALIZACIÓN.
  **ESTO ES LO MAS URGENTE**.
- Evaluar la estructura de la figura que contiene la imágen, a ver si cuando. 
  No es que la imágen no se encuentre, sino que hay un problema de servidor.  Si se visualiza el HTML, entonces 
  Encontrar en qué casos o no se hace el base64,, o se hace mal. Quizá alguna característica en el archivo haga que no se pase a base64 o se cargue mal.
  Evaluar si es una característica del archivo o de como está metido ese archivo en el XML para saber si es un problema de alguna característica del mismo o de la construcción del XML para ese archivo.
- LAS IMAGENES PUEDEN ESTAR CARGADAS EN DIFERENTES IDIOMAS DESDE LA SECCIÓN EDITAR DEL XML
  
  El PROBLEMA VIENE POR EL LADO DEL NOMBRE DEL ARCHIVO DE LA IMÁGEN... SI HAY UN ESPACIO SE AGREGA UN "+", ASÍ QUE NO HAY QUE PONER ESPACIOS EN LOS NOMBRES DE LAS IMÁGENES YA QUE OJS AGREGA UN + AUTOMÁTICAMENTE
  TAMBIÉN HAY UN TEMA DE TEXTURE QUE MUESTRA IMÁGENES DE ETAPAS ANTERIORES.
  
- Hay un artículo en el cual no aparece el cuerpo del artículo, solo las referencias.

- Tampoco salían los autores en las referencias del PDF en esta misma revista. Lu probó arreglar algunas referencias poniendo los autores pero estos tampoco salían... 
  Lo que pasó con los autores es que como esta revista los autores están cargados en inglés... el plugin solo debe estar recuperando en español. En esta revista los autores estaban cargados en inglés, cuando el idioma de la revista estaba en español.
  **El idioma que tengo que tener en cuenta a la hora de recuperar los datos del autor es el idioma del artículo, no el idioma del la REVISTA.**
  El plugin busca el idioma principal de la revista, no el idioma principal DEL ARTICULO, que es el que se tendría que utilizar y tener en cuenta, es por eso que no aparecía el autor.

- Cambiar la tipografía. Agarrar una de las que mandamos nosotros, la que mas pueda abarcar. Probar caracteres apóstrofe, ecuaciones matemáticas, mayor o igual, etc.

- Luego de generar el PDF, hay problemas con las referencias que quedan. 

- En las referencias hay campos que no se tienen en cuenta o no aparecen. Hay que lograr que todos los campos se recuperen desde texture y que aparezcan en el PDF. El rango de página no sale en el campo de metadato de referencias de OJS pero en el PDF si.
  Los datos que no salen en el PDF son mas relacionados con texture... pero el rango de página sí sale en el PDF... 
  **Quizá OJS detecte algo del html correspondiente a la referencia como código y lo elimine???**
  En el PDF los datos que no aparecen (traductor, editor, serie... etc) no son los mismos que no aparecen cuando se extraenlas referencias en el campo de referencias en los metadatos.

-  Al pasar de docx a xml jats, 

**LA PRIORIDAD SON LAS IMÁGENES.** Luego la tipografía.
Averiguar por qué al subir una imágen a mano en OJS para un XML, se agrega un + automáticamente si hay un espacio.

---

- Cambiar tipografía en el resumen y palabras clave (solo el contenido, no el título) -> **Solucionado**

- Cambiar tipografía en el pie de la carátula -> **Solucionado**

- Ajustar margen derecho, justificar aplicar estilos -> **¿Solucionado? HAY QUE TESTEARLO**

- Si no hay doi, que no salga el prefijo del doi -> **Solucionado**

- Reducir tamaño de fuente en el encabezado de las páginas -> **Solucionado** 

- Cambiar tipografía de correo y afiliación -> **Solucionado**

- Reducir un punto de tipografía en las notas -> **Solucionado**

- Aumentar el espacio entre el texto principal y el inicio de la cita a bando -> ****

- TEXTO DEL BODY JUSTIFICADO

- Buscar en el XML las citas obtenidas en la base de datos para filtrarlas en caso de que no existan. Una idea es agregar un botón para eliminar citas

- Priorizar idioma local del artículo a la hora de procesar autores, resumenes, palabras clave, titulos y subtítulos.