
Este documento resume los cambios aplicados en el plugin para resolver la previsualización de HTML con imágenes y otros detalles relevantes.
## Objetivo
Corregir el error de visualización de imágenes al previsualizar y/o publicar el HTML correspondiente al artículo. 

## Cambios principales
Sustitución de imágenes en la previsualización HTML (case `view`) mediante data URI (base64).
  
- Archivo modificado: `JatsParserPlugin.inc.php`
- Método modificado: `_setSupplImgPath(SubmissionFile $submissionFile, string $htmlString): string`

- Cambio: En el `case 'view'`, en lugar de generar una URL al handler (`/article/downloadFullTextAssoc/<submissionId>/<assocId>/<fileId>`), se lee el archivo desde el almacenamiento privado y se incrusta como `data:<mime>;base64,<contenido>`.

## ¿Por qué resuelve el problema?
La previsualización (`view`) ya no requiere llamadas HTTP a una ruta del backend para cargar imágenes.
Ahora, al estar integradas en el HTML como data URI, desaparecen los 403 causados por políticas de acceso en OJS 3.4.

## Implicancias
El HTML de previsualización será más pesado (las imágenes están embebidas). Esto es aceptable para la vista previa.

**Si en el futuro se desea optimizar cache/peso, se puede re-habilitar el uso del handler y ajustar su autorización para OJS 3.4.**

## Handler (opcional a futuro)
Para volver a incorporar imágenes por URL mediante el HANDLER en lugar de data URI, se recomienda que el handler:
- Permita acceso público cuando el envío esté publicado.
- Permita acceso a roles editoriales autenticados durante el workflow.
- Verifique que el adjunto pertenezca al archivo JATS indicado (match estricto de `assocId` + `fileId`).

## Sobre `JatsParserSettingsForm`
- Con el nuevo enfoque (imágenes en base64) la previsualización HTML ya no depende de configurar rutas/permisos para servir adjuntos.

- Por lo tanto, `JatsParserSettingsForm` queda obsoleto para el manejo de imágenes en la vista previa.

- Si el formulario se utiliza para otras configuraciones del plugin (p. ej., estilos de citación, flags de conversión a PDF), puede seguir presente para esos fines.

  

## 🧪 Cómo verificar

  

1. Abrir la previsualización HTML del artículo (view) y confirmar que las imágenes se muestran.

2. Inspeccionar el HTML y verificar que los `src` comienzan con `data:image/*;base64,`.

3. Generar el PDF y confirmar que las imágenes siguen apareciendo correctamente (flujo sin cambios en `editPublication`).

  

## 🗂 Archivos tocados

  

- `plugins/generic/jatsParser/JatsParserPlugin.inc.php`

- `_setSupplImgPath(...)`: case `view` -> incrustación como data URI; fallback a handler.

- (Opcional) `plugins/generic/jatsParser/FullTextArticleHandler.inc.php`

- Puede mantenerse para compatibilidad/fallback, pero ya no es necesario para la previsualización HTML.

  

## ⚠️ Notas

  

- Si actualmente hay personalizaciones locales del handler, no se ven afectadas por este cambio en la previsualización.

- Si se elige reactivar el handler para servir imágenes en preview, se deben ajustar las políticas de autorización a OJS 3.4.