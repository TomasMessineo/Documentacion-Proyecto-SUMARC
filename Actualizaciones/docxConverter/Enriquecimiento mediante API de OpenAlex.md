#### Ultima actualización: 22/09/2025

Se está implementando una nueva funcionalidad que permite enriquecer las referencias bibliográficas del XML JATS generado por este plugin utilizando la API de OpenAlex:[https://docs.openalex.org/how-to-use-the-api/api-overview]()

De esta manera, la generación automática de referencias no depende únicamente de las expresiones regulares desarrolladas, sino que puede complementarse y enriquecerse con la información obtenida a través de dicha API.  
La respuesta de OpenAlex se recibe en formato **JSON**, el cual es procesado para realizar el enriquecimiento de los datos previamente extraídos.

A continuación, se detallan los elementos del JSON recuperado mediante la API de OpenAlex y su correspondiente adaptación al XML JATS generado por este plugin.
- El **primer valor** (entre etiquetas) corresponde a la etiqueta del XML JATS.
- El **segundo valor** indica el dato del JSON retornado por OpenAlex que debe reemplazarse en la etiqueta correspondiente.
### Para referencias bibliográficas de tipo Journal:

```xml jats

<doi> ------>  "doi"

<source> ----> "primary_location":{source{display_name:}}" = nombre de la revista

<issn-l/> ---> "primary_location":{"source"{"issn_l":} = Identifica a la revista como conjunto, independientemente del formato

<issn> ------> "primary_location":{"source"{"issn":} = Identifica un formato específico (impreso o electrónico). En el JSON, dentro de este elemento se encuentran los dos ISSN, tanto el ISSN como el ISSN normal

<article-title> -----> "title" = título del artículo

<date> --------> "publication_date" = fecha de publicación COMPLETA. El tag <date> contiene 3 subelementos: day, month y year
		 "publication_year" = solo año de publicación

<person-group person-group-type="author"> ---------> "authorships": [{"author"}] = el "author" del elemento del json definiría que el autor es "autor" y no "editor", por ejemplo.
   <name>	
     <surname> -------------->Nombre/s 
     <given-names> --> Apellido/s --> en el JSON se guarda el nombre y apellido completos en "authorships": [{"author": "display_name"}], no hay distinción entre nombre y apellido
   </name>
</person-group>

<volume/> ------> "biblio: {"volume"}" = Volúmen de la revista

<issue/> -------> "biblio: {"issue"}" = Número de la revista

<fpage/> -------> "biblio: {"first_page"}" = Primera página

<lpage> --------> "biblio: {"last_page"}" = Número de la revista

<ext-link ext-link-type="uri"> --------> "primary_location":{"landing_page_url":}

De forma genérica para cualquier tipo de referencia, en el JSON aparece un elemento "type_crossref", el cual define el tipo de referencia que se va a procesar

```

--- 

## Información sobre las modificaciones técnicas y estrategias realizadas

Al modificar el JournalPrinter, se crea un método nuevo llamado enrichment() el cual se encarga de procesar la información recibida desde OpenAlex en formato JSON.
Se crean elementos de tipo DOMElement, los cuales se agregan a un array llamado $elements.
Cada uno de los elementos almacenados en este array es procesado de manera tal que se creen si y solo si no existen en el XML JATS correspondiente a la referencia bibliográfica específica, o se reemplacen si es que ya existen en la misma. Se le da prioridad a los datos de OpenAlex, reemplazando todo a su paso (esto debido a que los datos recibidos mediante su API son mas fiables que los recuperados mediante las expresiones regulares, es decir, los ingresados por un usuario).

Se realizaron cambios en la manera por la cual se detectan los errores en las distintas secciones de la referencia (si los autores, fecha o título de la referencia estan mal escritos).
Lo que se hacía anteriormente era ir concatenando un string el cual contenía todos los errores que se iban detectando de la referencia. Por ejemplo: Si tengo una referencia donde los autores están definidos correctamente según el estándar APA (por el momento este conversor solo convierte referencias que sigan el estándar APA) pero la fecha y el título están mal escritos, lo que se hace es detectar estos errores y concatenarlos en una variable. Luego, al imprimir el XML JATS de salida, el mixed-citation correspondiente a esta referencia incorporará este texto para que los usuarios puedan saber dónde están los errores.
**Ahora lo que se añadió** es la indicación de error si un DOI específico NO existe en la base de datos de OpenAlex (si no existe el DOI se retorna un json sin resultados). Lo que se hace es verificar si el arreglo de datos retornado por OpenAlex para cada referencia está vacío

### A realizar:

- En base al nombre y el apellido de los autores en una referencia, crear el tag person-group de forma correcta con given-names y surname. Además, esto me servirá para poder detectar si me llega información de OpenAlex sobre una referencia que no tiene nada que ver con la procesada, en base al nombre puedo detectar si el doi utilizado es correcto o NO.
  Si intento buscar el nombre y apellido indicado en el JSON dentro del XML JATS correspondiente a dicha referencia, podría identificar si coinciden o no. Si coinciden, eso quiere decir que la información del JSON es correcta con respecto a los datos ingresados manualmente por el usuario. Si no coinciden estos datos, entonces puedo suponer.
