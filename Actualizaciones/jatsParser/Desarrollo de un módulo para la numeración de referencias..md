### **Implementación del módulo**  
Para llevar a cabo la implementación de este módulo se procesaron todas las referencias provenientes del XML JATS, las cuales se almacenan en un arreglo asociativo con la forma **clave => valor**, donde:
- **clave**: identificador único de la referencia.
- **valor**: texto completo correspondiente a la referencia.

### Técnica utilizada en la implementación
Este arreglo se envía a una nueva clase denominada **ReferenceProcessor**, que expone el método `getNumberedReferences()`.

**Dentro de este método, las referencias se procesan siguiendo los siguientes pasos:**

1. Se toma el texto previo al primer cierre de paréntesis y se guarda como **clave** en un nuevo arreglo, mientras que la **referencia completa** se almacena como valor.
    
2. Si otra referencia contiene el mismo fragmento de texto antes del primer cierre de paréntesis, se asocia bajo la misma clave ya existente.
    
3. Una vez procesadas todas las referencias y agrupadas, se procede a enumerarlas secuencialmente con letras (a, b, c, …). Para ello, se añade la letra correspondiente justo antes del primer cierre de paréntesis.

**De este modo, el resultado queda con un formato similar a:**

- `Messineo, T. (2025a) Primer Título`
- `Messineo, T. (2025b) Segundo Título`

Cabe mencionar que esta enumeración se aplica únicamente cuando, en la configuración del plugin dentro de la sección "Módulos", el estilo de citación seleccionado es **APA**.

Además, se añadió la funcionalidad de que al hacer clic en cada cita, se dirija directamente a la referencia específica, y no solamente a la página en general.