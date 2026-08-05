
***

# [TICKET REDMINE] Refactorización de la tabla de asignación de citas en JatsParser para soporte dinámico basado en CSL

* **Proyecto:** OJS 3.4 / Plugins / JatsParser
* **Categoría:** Mejora / Refactorización (Feature / Refactoring)
* **Asunto:** Dinamizar la tabla de asignación de citas en el panel de publicación según la categoría del estilo CSL activo (Autor-Fecha, Numérico, Notas)

---

## 1. Descripción del Problema / Contexto Actual

Actualmente, el plugin `jatsParser` incluye una interfaz gráfica (tabla en modal) dentro de la pestaña de publicación (`PublicationJATSUploadForm`) que permite al editor revisar y ajustar la forma en que se renderizará cada cita (`<xref ref-type="bibr">`) dentro del documento XML.

Sin embargo, el formateo de las opciones disponibles en el desplegable de esa tabla está **hardcodeado para el estilo APA 7** en la clase `ApaReferencesRenderer.php` y `ApaFormatter.php` (formateando manualmente `(Apellido, Año)`, `(Año)` y `Personalizado`).

Esto genera serias inconsistencias cuando la revista configura un estilo de citación distinto a APA (por ejemplo, estilos numéricos como **Vancouver** o **IEEE**, o estilos internacionales como **ABNT** en Brasil):
* Si una revista usa **IEEE** o **Vancouver**, le aparecen opciones de "(Autor, Año)", lo cual invalida la coherencia de las citas numéricas `[1]`.
* Si usa **ABNT** o **Chicago**, no se respetan las reglas CSL específicas de puntuación, mayúsculas o separadores.

---

## 2. Objetivo

Refactorizar la arquitectura de la tabla de asignación de citas para **desacoplarla de APA 7** y utilizar el motor de CSL (`Seboettg\CiteProc`, ya integrado en el plugin) y la categoría del estilo CSL activo (`citation-format`), adaptando dinámicamente la cantidad y el tipo de opciones ofrecidas en el formulario.

---

## 3. Especificación Técnica de la Solución

### 3.1. Detección de la Categoría CSL (`citation-format`)
Cada estilo `.csl` (almacenado en `JATSParser/src/JATSParser/Back/CSL/` o cargado desde la configuración) contiene en su cabecera la etiqueta `<category citation-format="..."/>`.

Se debe implementar un lector/parser ligero de metadatos CSL (o consultar la estructura del estilo cargado por `StyleSheet::loadStyleSheet()`) para clasificar el estilo activo en una de las siguientes familias:
1. **`author-date`** (APA, ABNT, Harvard, Chicago Author-Date, MLA)
2. **`numeric`** (Vancouver, IEEE, ACM, ACS)
3. **`note`** (Turabian, Chicago Notes)

---

### 3.2. Lógica de Opciones Dinámicas por Familia de Estilo

La tabla construida en el backend deberá generar las opciones del desplegable `<select name="citationStyle[xrefId]">` según la familia del estilo activo:

#### A) Familia `author-date` (3 opciones)
1. **Cita Parentética Completa (CSL Estándar):** Generada mediante `$citeProc->render($data, "citation", [$citeObject])`.
   * *Ejemplo APA:* `(García & Pérez, 2020)`
   * *Ejemplo ABNT:* `(GARCÍA; PÉREZ, 2020)`
2. **Cita Narrativa / Solo Año:** Generada mediante `CiteProc` aplicando la opción/flag de renderizado `suppress-author => true`.
   * *Ejemplo:* `(2020)`
3. **Personalizado (`custom`):** Permite entrada libre de texto en un `<input type="text">`.

#### B) Familia `numeric` (2 opciones)
1. **Cita Numérica Estándar (CSL Estándar):** Generada mediante `$citeProc->render(...)`.
   * *Ejemplo IEEE/ACM:* `[1]`
   * *Ejemplo Vancouver:* `(1)` o `1`
2. **Personalizado (`custom`):** Permite entrada libre de texto para casos especiales (ej: rangos `[1-3]` o notas numéricas).

#### C) Familia `note` (2 opciones)
1. **Llamada de Nota Estándar (CSL Estándar):** Generada mediante `$citeProc->render(...)`.
   * *Ejemplo:* `¹`
2. **Personalizado (`custom`)**

---

### 3.3. Archivos a Refactorizar / Crear

1. **[`classes/components/forms/CitationStyles/Core/Renderers/CslReferencesRenderer.php`](file:///home/santi/SEDICI/ojs3-4-docker/data/ojs/plugins/generic/jatsParser/classes/components/forms/CitationStyles/Core/Renderers/)** *(Nuevo / Reemplazo de `ApaReferencesRenderer.php`)*:
   * Recibe el objeto `CiteProc` inicializado con el `.csl` del contexto.
   * Renderiza la fila de la tabla construyendo las opciones del `<select>` de forma dinámica evaluando la familia CSL.

2. **[`classes/components/forms/TableHTML.php`](file:///home/santi/SEDICI/ojs3-4-docker/data/ojs/plugins/generic/jatsParser/classes/components/forms/TableHTML.php)**:
   * Reemplazar la instanciación estática `$className = ... . 'ApaCitationTable'` por un invocador genérico `CslCitationTable` o directamente hacer uso del renderer CSL genérico.

3. **[`app/citationTable.js`](file:///home/santi/SEDICI/ojs3-4-docker/data/ojs/plugins/generic/jatsParser/app/citationTable.js)**:
   * Garantizar que el manejador de eventos `change` detecte dinámicamente si el `<select>` seleccionó `custom` para alternar la visibilidad del `<input class="custom-input">` sin asumir valores duros del backend.

4. **Persistencia (`CustomPublicationSettingsDAO.inc.php`)**:
   * Mantener el esquema de almacenamiento existente en `jatsParser::citationTableData` para garantizar 100% de retrocompatibilidad con las citas personalizadas previamente guardadas.

---

## 4. Criterios de Aceptación (Definition of Done)

- [ ] **Soporte APA / ABNT (`author-date`):** Si la revista usa APA o ABNT, la tabla muestra 3 opciones *(Parentética completa, Solo año, Personalizado)* y respeta las mayúsculas/puntuación de CSL (ej: ABNT usa `(SILVA; SOUZA, 2021)`).
- [ ] **Soporte Vancouver / IEEE (`numeric`):** Si la revista usa Vancouver o IEEE, la tabla muestra únicamente 2 opciones *(Número CSL estándar ej `[1]`, y Personalizado)*.
- [ ] **Persistencia:** Al guardar el formulario de publicación, la opción seleccionada o el texto personalizado introducido se guardan correctamente en la BD y se aplican en la generación del HTML/PDF.
- [ ] **Retrocompatibilidad:** Artículos que ya tengan datos guardados en `jatsParser::citationTableData` siguen manteniendo sus selecciones personalizadas sin romper la interfaz.
- [ ] **Estabilidad:** No se presentan errores en el log de PHP si un estilo CSL no contiene alguna definición opcional.