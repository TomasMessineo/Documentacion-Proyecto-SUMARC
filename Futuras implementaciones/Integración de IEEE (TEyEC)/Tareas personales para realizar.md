
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

- Tener anotado en un documento, en el directorio de SUMARC hacer una carpeta que sea PPS TOMI y anotar un documento que tenga objetivos (no formal, para nosotros), los cuales son: adaptar SUMARC para revistas de informática, como el caso TEyET, pero se piensa mas ampliamente y general para otras revistas. Este es el objetivo general. Luego hay cosas concretas a cumplir con dicho objetivo general, tareas como: trabajar en procesamiento de normas en IEEE para generar el XML (mejorando el plugin docxConverter), verificar que la exportación al PDF y HTML salga con formato IEEE, construir una plantilla que siga los lineamientos de diseño de la revista TEyET (proponer una plantilla PDF para que la gente de TEyET cambie en su flujo actual para que a los autores no les pidan mas las plantillas formateadas, sino que ahora lo voy a hacer yo). Estos son los objetivos de base, los que son prioridad digamos. Opcionalmente, como tareas extra está la posibilidad de mejorar la visualización y procesamiento de formulas en PDF y HTML. Además, dejar en claro que todo esto será un cambio real sobre la revista, donde todas las implementaciones y desarrollo que yo haga será puesto en producción, y posteriormente habrá una instancia de capacitación que yo voy a dar mostrandoles todos estos cambios y nuevas funcionalidades, donde además les voy a dejar el power point y documentación que elabore para que a ellos les quede de respaldo y no tengan que volver a consultarme. La idea es dejar en claro como objetivo o como aclaración, que no solo haré un trabajo de desarrollo de código y análisis de implementación, o todo lo que tenga que ver con cosas técnicas, sino que también voy a hacer un trabajo de ingeniería de software donde programaré y organizaré reuniones con los editores de TEyET (específicamente Natalia, que es la persona con la que nos estamos comunicando hasta el día de hoy), les mostraré avances y los capacitaré para que puedan utilizar correctamente estas herramientas con las implementaciones realizadas, mediante la realización de PPTs  y documentación de usuario. 
  Otro punto u objetivo a atacar, si se llega con el tiempo, es el enlace automático entre citas y referencias cuando se hace la conversión de docx a XML JATS, cuando el DOCX está estructurado con formato IEEE, para que el XML JATS ya se genere con las citas enlazadas automáticamente, lo cual puede ser posible ya que las citas aparecen como [1] y las referencias están ordenadas y ennumeradas también. Esta opción hay que evaluarla.
  
  Dar la opción a elegir a los editores para usar el HTML de visualización generado por sumarc, es decir, se tiene que poder decidir si usar el HTML generado por sumarc o no, y además, dar la opción para eliminarlo.

  Lo siguiente es un plan de tareas o plan de trabajo, que tenga el orden de las tareas, donde especificaré lo primero que voy a encarar en la PPS, ya sea el CSL para jatsparser, o el parser de docxconverter a IEEE, la plantilla personalizada para TEyET, etc. 