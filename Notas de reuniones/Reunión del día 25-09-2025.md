
---
---

- Al sistema no le gustan las imágenes. Hay problemas con las imágenes donde a veces no aparecen. Una revista de agronomía probó con diferentes tipos de imágenes, y no le funcionó ninguna.
  EN EL HTML LAS IMAGENES NO SALEN, HAY QUE CORREGIR ESTO TAMBIÉN... DEBEN SALIR LAS IMÁGENES EN EL HTML DE PREVISUALIZACIÓN.
  **ESTO ES LO MAS URGENTE**.

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

- 