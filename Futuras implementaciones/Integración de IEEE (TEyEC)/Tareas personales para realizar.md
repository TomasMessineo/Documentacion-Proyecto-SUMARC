
**Preguntar a Gonza bien por este tema, mas que nada para saber si ya de a poco voy encarando esto y documentando y escupiendo todo lo que voy haciendo en un documento de google docs** 
- Armar un prototipo de plan por etapas sobre mi PPS, explicando y documentando las cosas que voy a hacer en distintos niveles. Entre ellas: 
	- Compatibilizar IEEE con SUMARC (aprovechando el taller que se dará en informática) en cada uno de los plugins
	- Evaluar la integración de la conversión de Latex a XML JATS (si es que en TEyEC lo usan) 
	- Conversión automática de referencias en docxConverter utilizando Regex con reglas para IEEE
	- Desarrollo de una nueva plantilla a doble columna (la utilizada por TEyEC) utilizando el módulo de plantillas personalizadas implementado por Leo 
	- Compatibilidad con ecuaciones matemáticas y otros elementos (a evaluar)
	- Para trabajar con ellos sugerirles un nuevo documento de WORD estructurado como nosotros lo pensamos, mas que nada porque eso le quita mucha carga al autor. De la manera en la que nosotros pensamos la estructuración del DOCX, el autor no tendría que estructurar un docx complejo (con titulo, resumen, a doble columna, etc), sino que simplemente debería especificar en el mismo el cuerpo del artículo completo, y todo lo demás será cargado como metadato, hasta llegar al PDF final que contenga todo lo mencionado. En este caso existen 2 vías: eliminar lo innecesario en texture y mantener la estructuración de docx que ellos proponen, o estructurar el DOCX como proponemos nosotros para que luego el trabajo en Texture sea menor.

- Terminar la conversión de JATSParser con OpenAlex y documentar todo el proceso. Hacer ticket de implementación con OpenAlex.
- Leer https://docs.google.com/document/d/17z_SG4w4_7M8KlZTnZ3NnkcbhDX-ItZKIC1_D9qwPhA/edit?tab=t.0
- **Prioridad por contrato:** Desarrollar la generación de ePUB con JATSParser.

**Fuentes relevantes investigadas:**
- Estructuración de citas y referencias en formato IEEE: https://docs.google.com/document/d/e/2PACX-1vSBoV_hTIURPZKtQkxI6bAONJtjyDLxQIUvCHi-XPzD8NKLcxRfZrpvQLFrjWZ3M6FFR_Obau3R-t63/pub -> Sacado de https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-the-text-of-your-article/ieee-editorial-style-manual/

**Preguntar a Gonza:**

- Sale un punto después del número de edición en las referencias. Ese punto NO tiene que ir.
  
- Del 17 al 28 es la presentación en el BIREDIAL . Para la semana del 9 al 13 de noviembre hacer una presentación de SUMARC mas global y federal, un taller mas acotado, para 12 o 15 revistas.