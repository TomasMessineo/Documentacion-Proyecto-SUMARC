
---
---

- Texture es limitado

- Tésis no te deja elegir qué tipo de tesis es

- Campo de serie NO sale

- Evaluar si texture te deja usar el XML normal y el XML completo generado por el nuevo plugin que habrá que implementar

- A SCieLO si se debe enviar todo el articulo completo (tanto body, front y back), no debe faltar ninguna sección por mas de que el validador lo tome como opcional

- Para cargar en crossref los metadatos de un artículo, solo se necesita un XML con el Front (ya existe un plugin de OJS que hace esto), pero para SCiELo si se necesita el XML completo con las 3 secciones

- Para el martes 25 tener listas las pruebas para leo, para mandarle a Lucía y Adela

----------------------------------------------------------

Idenfiticar qué es un error de CSS y cuál sería el arreglo que hay que hacer (como tamaño de fuente), y cuáles son errores de lógica de programación (como footer faltante).

---

Como posible solución a la no inclusión del tipo de tesis, se me ocurrió que desde Texture se puede indicar en el campo "Publisher Location" tanto el tipo de tesis como la institución que brinda el título y además en el campo "Publisher Name" no se debe indicar nada (debe quedar vacío). Esto claramente generará un problema en la estructura del XML JATS correspondiente a la referencia de tesis, ya que el tag "publisher-loc" contendrá un dato compuesto: "Tesis de Doctorado, Universidad Nacional de La Plata" por ejemplo... cuando en realidad "Tesis de Doctorado" debería ir en otro tag, ya sea "thesis" o "comment". 
Esto puede ser una solución (no muy buena claramente), pero sirve para que CiteProc genere la referencia a tesis incluyendo todo "Publisher Location" entre corchetes. 
Algo que se puede pensar, es que ya que el XML que se está trabajando en el flujo de trabajo NO es el original