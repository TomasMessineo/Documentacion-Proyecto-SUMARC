
- Uso epubcheck (mantenida po w3c) para validar la integridad y la versión de los epubs generados (con PHPePUB se generan epubs version 2 y version 3)
- Cambios en el fork creado https://github.com/lumielis/PHPePub/tree/main para que se algunas funciones de php 8.2 funcionen.
- Para leer los ePUB uso https://epub-reader.online/

**Ideas para la integración con SUMARC (en el plugin JatsParser):**
- En vez de separar cada página en "capítulos" (como he visto en varios ePUB),  separar en base a las secciones, teniendo en cuenta por ejemplo los encabezados h1, donde cada vez que se detecte un h1 se cree otra página u otro capítulo (la librería PHPePUB permite ir creando capítulos pasándole distintos fragmentos de HTML a una misma instancia de la clase Epub() en vez de mandar un único HTML).

- Evaluar si en una primera versión, se va a mostrar la caratula (que incluye todos los metadatos, aprovechando la misma configuración y estilos que se usa para las plantillas PDF) o sino simplemente dejar el cuerpo del artículo, sin carátula, 
  
- Evaluar si se inyecta algún CSS al HTML que se manda a la librería. Podrían ser los mismos que se usan para el PDF o un CSS independiente para evitar este acoplamiento de estilos, ya que el PDF e ePUB son salidas diferentes).
 
- Procesar el HTML para obtener sus imágenes. Luego usar la función addFile() que brinda la librería PHPePUB para agregar dichas imágenes a la instancia de la clase Epub.