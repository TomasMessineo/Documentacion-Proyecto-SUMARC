
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

