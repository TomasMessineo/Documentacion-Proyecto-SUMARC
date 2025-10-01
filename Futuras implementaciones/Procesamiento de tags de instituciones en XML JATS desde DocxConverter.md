
Dentro de JournalPrinter testeé lo siguiente:

// Manejar institución si existe

if (isset($this->reference['institution'])) {

// Si no existe un person-group de tipo "author", se crea

if ($authorElement === null) {

$authorElement = $this->dom->createElement('person-group');

$authorElement->setAttribute('person-group-type', 'author');

$elements[] = $authorElement;

}

// Crear la estructura collab para la institución

$collabElement = $this->dom->createElement('collab');

$institutionNameTag = $this->dom->createElement('named-content');

$institutionNameTag->setAttribute('content-type', 'name');

$institutionSurnameTag = $this->dom->createElement('named-content');

$institutionSurnameTag->setAttribute('content-type', 'surname');

$institutionSurnameTag->textContent = "&#160";

  

$institutionNameTag->textContent = $this->reference['institution'];

// Ensamblar la estructura

$collabElement->appendChild($institutionNameTag);

$collabElement->appendChild($institutionSurnameTag);

$authorElement->appendChild($collabElement);

}

**ALGO QUE PUDE IDENTIFICAR:** Si desde texture se agrega solo "surname" de un autor en alguna referencia, el tag de base que se guardará es  "collab", que dentro tendrá un named-content que contendrá la institución.
Si se agrega surname y given-names el tag cambia y está contenido en "name", que dentro tiene surname y given-names.

---

- Cambiar tipografía en el resumen y palabras clave (solo el contenido, no el título) -> **Solucionado**

- Cambiar tipografía en el pie de la carátula -> **Solucionado**

- Ajustar margen derecho, justificar aplicar estilos -> **¿Solucionado? HAY QUE TESTEARLO**

- Si no hay doi, que no salga el prefijo del doi -> **Solucionado**

- Reducir tamaño de fuente en el encabezado de las páginas -> **Solucionado** 

- Cambiar tipografía de correo y afiliación -> **Solucionado**

- Reducir un punto de tipografía en las notas

- Aumentar el espacio entre el texto principal y el inicio de la cita a bando (imágen siguiente)

- Recuperar idioma primario del artículo para los autores

- Buscar en el XML las citas obtenidas en la base de datos para filtrarlas en caso de que no existan

- Priorizar idioma local del artículo a la hora de procesar autores, resumenes, palabras clave, titulos y subtítulos. Una idea es agregar un botón para eliminar citas

