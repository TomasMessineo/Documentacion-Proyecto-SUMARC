
- Uso epubcheck para validar la integridad y la versión de los epubs generados (con PHPePUB se generan epubs version 2 y version 3)
- Cambios en el fork creado https://github.com/lumielis/PHPePub/tree/main para que se algunas funciones de php 8.2 funcionen.

**En cuanto a su integración con SUMARC (JatsParser):**
- En vez de separar cada página en "capítulos" (como he visto en varios ePUB), se podrían separar en base a las secciones, teniendo en cuenta por ejemplo los encabezados h1, donde cada vez que se detecte un h1, se cree otra página u otro capítulo (la librería PHPePUB permite ir creando capítulos pasandole distintos fragmentos de HTML en vez de uno solo)