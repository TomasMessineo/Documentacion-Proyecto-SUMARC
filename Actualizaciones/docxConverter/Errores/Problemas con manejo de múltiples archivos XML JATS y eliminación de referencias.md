## Problemas con manejo de múltiples archivos XML JATS en etapa de publicación y el renderizado de la Tabla de Citaciones luego de la eliminación de referencias

#### Descripción
Se identificaron dos inconvenientes en la etapa de publicación relacionados con el manejo de múltiples archivos **XML JATS** y el renderizado de la **Tabla de Citaciones**.

### Problema 1: Reemplazo de información al usar múltiples XML JATS

- Actualmente, la base de datos almacena las citas, tablas y figuras sin diferenciar a qué archivo XML JATS corresponden.
    
- Si se guarda información de un XML y luego se selecciona un segundo XML diferente, la información previamente almacenada es **reemplazada**.
    
- Esto ocurre porque la BD no maneja un esquema diferenciado por XML JATS.
 **Se requiere**:  
Implementar una estructura de almacenamiento en la base de datos que asocie las citas, tablas y figuras **a cada archivo XML JATS de forma independiente**.

### Problema 2: Persistencia de citas eliminadas en Texture

- Si se almacenan citas para un XML y luego se eliminan referencias bibliográficas desde Texture, al volver a abrir la tabla de citaciones las referencias eliminadas **siguen apareciendo**.
    
- Esto se debe a que al procesar la configuración precargada (no-default) desde la BD no se valida contra el XML si la referencia aún existe.

 **Se requiere**:  
Agregar un proceso de validación/filtrado que compare las citas almacenadas en la base de datos con las referencias reales presentes en el XML, de modo que no se muestren aquellas eliminadas.

### Propuesta de solución

1. Ajustar el esquema y la lógica de la base de datos para manejar múltiples XML JATS con datos de citas, tablas y figuras diferenciados por archivo (file id).
    
2. Implementar un mecanismo de verificación que, al renderizar la tabla de citaciones, filtre y muestre únicamente las referencias que aún existan en el XML activo.