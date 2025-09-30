
---
---

# Corrección de imágenes dependientes en Texture (OJS 3.4)

Estas correciones solucionan dos cosas:
- Al cambiar de etapa, ya no aparecen imágenes que pertenecen a etapas anteriores.
- Si se suben de nuevo las imágenes como archivos dependientes en la nel ueva etapa, ahora sí aparecen en el editor texture (siempre y cuando en la etapa anterior hayan existido).

## Qué pasaba antes

- Al abrir el editor en una etapa nueva, se veían imágenes “viejas” de otra etapa.
- Aunque volvieras a subir las imágenes de una etapa anterior como archivos dependientes en la etapa actual, el editor texture no las mostraba.
  
## Qué se hace ahora

- El editor solo muestra las imágenes que se suben para el XML que se está editando en una etapa específica, no busca en todas las etapas anteriores.
- Cuando se sube una imagen (desde el editor o al importar un ZIP/DAR), queda vinculada a ese XML y se ve al instante.

## Cómo probarlo rápido

1) Agregar imágenes en un XML JATS desde Texture
2) Pasar a la etapa siguiente enviando el XML JATS que contiene las imágenes subidas en el paso 1) y abrir el XML en el editor texture.
3) Subir las imágenes en la nueva etapa como archivos dependientes (desde el botón del editor o importando un DAR/ZIP). Lo que se puede hacer es ir al XML de la etapa anterior y descargar las imágenes que aparezcan como archivos dependientes.
   
   En la etapa anterior, si vemos los archivos dependientes tendremos un listado con las imágenes subidas en el XML. Estos archivos son los que se pueden descargar para subirlos en la nueva etapa:
   ![[Captura desde 2025-09-29 13-12-50.png]]
   
   En la nueva etapa, podemos subir los archivos de imágenes que se descargaron en la etapa anterior como archivos dependientes, y de esta forma se podrán visualizar las imágenes en Texture exactamente en el mismo lugar y posición donde se cargaron en la etapa anterior:
    ![[Captura desde 2025-09-29 13-20-11.png]]
   ![[Captura desde 2025-09-29 13-19-19.png]] ![[Captura desde 2025-09-29 13-21-38.png]]
   La imágen cargada "image1.jpeg" corresponde a una imágen cargada como archivo dependiente existente en la etapa anterior. 
   Luego, si abrimos el XML con el editor texture las imágen cargada aparecerá correctamente:
   ![[Captura desde 2025-09-29 13-23-45.png]]
   
   4) Actualizá la página del editor.

Deberías ver solo las imágenes de esta etapa. Si una imagen no aparece:
- Revisá que el nombre del archivo coincida con el que el XML espera (por ejemplo, si el XML usa `figures/Fig1.png`, subí un archivo llamado `Fig1.png`).
- Probá volver a subirla con ese nombre.

  

## Consejito con los nombres

***El editor busca las imágenes por el nombre del archivo que figura en el XML. Si se mantienen esos nombres cuando se suben las imágenes, se vinculan solas y aparecen sin problemas.***
## Preguntas rápidas

¿Por qué ya no veo imágenes viejas?
- Porque ahora el editor solo toma las imágenes asociadas al XML de la etapa actual.

Subí una imagen y no se ve, ¿qué hago?
- Asegurarse de que el nombre del archivo sea el mismo que aparece en el XML. Si no coincide, cambiarlo y volver a subirlo.

---

Con esto, cada etapa muestra solo sus propias imágenes y no se mezclan con las de las etapas anteriores.

## Detalles técnicos de la solución

Esta sección explica exactamente qué cambia en el código y por qué resuelve el problema.

### Alcance correcto de archivos dependientes (scoping por assocId)

En OJS, los archivos dependientes deben estar vinculados al archivo base (el XML) mediante dos campos:

- `assocType = ASSOC_TYPE_SUBMISSION_FILE`
- `assocId = <ID lógico del SubmissionFile (XML) actual>`

Al aplicar este criterio en todas las rutas relevantes:
- El editor no ve dependientes ajenos a ese XML (evita fugas entre etapas).
- Cuando se suben dependientes nuevos en la etapa actual, el editor los reconoce al instante.

### Mantener media (imágenes) solo del XML abierto

Archivo: `plugins/generic/texture/TextureHandler.php`
Función: `media($args, $request)`

**Pasos clave:**

1. Se obtiene el `assocId` (ID del SubmissionFile del XML abierto) desde la request.

2. Se listan los archivos con `fileStage = SUBMISSION_FILE_DEPENDENT` para la misma submission.

3. Se filtra por `assocType = ASSOC_TYPE_SUBMISSION_FILE` y `assocId = <XML actual>`.

4. Se selecciona el archivo cuyo `fileId` coincide con el que pide el editor.

**Efecto:** aunque existan otros dependientes en la submission, solo se mantienen los asociados a ese XML.

### Construcción de resources (mapping por path del manuscrito)

Archivo: `plugins/generic/texture/classes/DAR.php`
Función: `createMediaInfo($request, $assets)`

Pasos clave:

1. `assets` proviene del manifest y contiene las rutas referenciadas en el XML (por ejemplo, `figures/Fig1.png`).

2. Se recogen todos los dependientes en `SUBMISSION_FILE_DEPENDENT` y se filtran SOLO los que tienen `assocType = ASSOC_TYPE_SUBMISSION_FILE` y `assocId = <XML actual>`.

3. Se indexan por `basename` en minúsculas (se usa `originalFileName` o, si no está, el `name` localizado del dependiente).

4. Por cada `asset.path` del manifest, se calcula su `basename` y se busca en el índice.

5. Si hay match, se arma la URL a `texture/media` con los parámetros: `submissionId`, `stageId`, `assocId` y `fileId` del dependiente encontrado.

6. El mapa final de `resources` usa como clave el `path` EXACTO del manifest (el que espera Texture), y como valor la URL de `media`.

**Efecto:** cuando se re-sube una imagen en la etapa actual, el editor la resuelve automáticamente si su nombre coincide con el que aparece en el XML.

### Asociación correcta durante extracción (DAR/ZIP)

Archivo: `plugins/generic/texture/TextureHandler.php`
Función: `extract($args, $request)`

Al crear dependientes a partir de un DAR/ZIP, ahora el `assocId` se fija con el **ID lógico** del nuevo `SubmissionFile` (XML) creado (`$insertedSubmissionFile->getId()`), no con el `fileId` físico. Esto asegura que todos los dependientes quedan ligados al XML de la etapa actual.

### Notas de compatibilidad

- Este comportamiento intenta replicar la lógica de texture en OJS 3.3 (donde `media()` ya aplicaba el scoping por archivo base) y la adapta a OJS 3.4.