
---
---

#### Ultima actualización: 19/09/2025

Se está implementando una nueva funcionalidad que permite enriquecer las referencias bibliográficas del XML JATS generado por este plugin utilizando la API de OpenAlex:[https://docs.openalex.org/how-to-use-the-api/api-overview]()

De esta manera, la generación automática de referencias no depende únicamente de las expresiones regulares desarrolladas, sino que puede complementarse y enriquecerse con la información obtenida a través de dicha API.  
La respuesta de OpenAlex se recibe en formato **JSON**, el cual es procesado para realizar el enriquecimiento de los datos previamente extraídos.

A continuación, se detallan los elementos del JSON recuperado mediante la API de OpenAlex y su correspondiente adaptación al XML JATS generado por este plugin.
- El **primer valor** (entre etiquetas) corresponde a la etiqueta del XML JATS.
- El **segundo valor** indica el dato del JSON retornado por OpenAlex que debe reemplazarse en la etiqueta correspondiente.
### Para referencias bibliográficas de tipo Journal:

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

---------------------------------------------------------------------------------------------------------------------------------------------------

Al modificar el JournalPrinter, se crea un método nuevo llamado enrichment() el cual se encarga de procesar la información recibida desde OpenAlex en formato JSON.
Se define un array de elementos simples y un procesamiento específico llamando a nuevos métodos implementados en GenericPrinter para reemplazar o crear correctamente los datos correspondientes recibidos desde OpenAlex, enriqueciendo así el xml final.
Este enfoque podría permitir en algún futuro, si se quieren utilizar otras APIs para recibir mas información y seguir enriqueciento el XML, poder agregar nuevos datos a este arreglo de datos simple o crear nuevos métodos para la realización de tareas específicas que requieran recorrer elementos del XML los cuales tienen subelementos dentro.

El método enrichment de JournalPrinter recibe todo el element citation para modificarlo completamente si es necesario y luego reemplazarlo (se asigna de nuevo a element-citation el nuevo element-citation modificado). Básicamente se le da prioridad a los datos de OpenAlex, reemplazando todo a su paso. 
No sigo el enfoque de crear un elemento y meterlo en un array elements[] como se hace en los printers ya que en este caso no estoy creando elementos, sino que los estoy reemplazando... entonces yo entiendo que va a ser mejor recorrer el element citation de forma completa reemplazando lo necesario antes que crear los elementos, guardarlos en un arreglo elements[] y luego hacer un appendChild sobre element-citation. 

Puedo ver si aplicando la misma lógica de createElement en enrichment(), luego de volver del método retornar un arreglo elements[], iterarlo y en vez de ejecutar un appendChild, hacer un replaceChild

En base al nombre y el apellido de los autores en una referencia, crear el tag person-group de forma correcta con given-names y surname. Además, esto me servirá para poder detectar si me llega información de openalex sobre una referencia que no tiene nada que ver con la procesada, en base al nombre puedo detectar si el doi utilizado es correcto o NO.