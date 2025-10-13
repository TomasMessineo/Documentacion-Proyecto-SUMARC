
# Clase "AuthorValidator":

Para validar si una institución autora o un nombre completo de un autor son válidos según lo obtenido mediante la API de OpenAlex, se implementó una clase denominada "AuthorValidator", la cual se encargará de realizar estas tareas de validación. El método `validateInstitutionAsAuthor()` verifica que el nombre de la institución exista en OpenAlex, y el método `validateFullNameAsAuthor()` se encarga de verificar si el nombre completo del autor indicado en la referencia es válido con respecto al autor obtenido mediante la API de OpenAlex (esto servirá para poder evaluar si el/los nombres de los autores en la referencia fueron escritos de forma correcta o no).

A continuación se detallarán todos los 

# Validación de Instituciones como Autores:

 Si tengo una referencia que tiene una institución inexistente como autor, ***por ejemplo: "Universidad Inexistente del No Se Nada (2025). Título de la referencia.***, se imprime un error en el mixed-citation de la referencia para que el usuario sepa que la institución que especificó NO existe en OpenAlex:
  ![[Captura desde 2025-10-09 11-31-44.png]]

Si la institución no es válida entonces los demás datos de la referencia no se generarán, solo se imprime el mixed-citation con la referencia en cuestión y su error.

En el caso de que una referencia tenga en su contenido una institución como autora, por ejemplo: "Universidad Nacional de La Pla", esto no machea con "Universidad Nacional de La Plata", por ende entiendo que por mas de que una institución esté mal escrita, si esta no es exactamente igual al nombre de la institución, OpenAlex retornará **null**... ante esto hay dos posibilidades:

- Si la institución no existe en OpenAlex, entonces informar de un error que directamente no genere la referencia en XML (caso utilizado, se puede observar en la imágen anterior)
- Si la institución no existe en OpenAlex, entonces informar de un error en consola pero igualmente generar la referencia con todos sus elementos y tags correspondientes

La estrategia utilizada hasta el momento es: 
- ***Si OpenAlex retorna 0 resultados (null)***, entonces se imprime el error en el tag mixed-citation y NO se genera la referencia completa con todos sus tags correspondientes. **Este enfoque limita a que el nombre de la institución tenga que existir SI o SI en OpenAlex para generar la estructura XML completa de la referencia**
- ***Si OpenAlex retorna un solo resultado***, entonces ese resultado será válido. Por mas de que se ponga una letra menos en una institución, por ejemplo: **"Universidad Nacional de La Plat"**, OpenAlex retornará **NULL** y no la institución especificada (mas allá de que falte un solo caracter). 
- ***Si OpenAlex retorna mas de un resultado,*** entonces no se puede (hasta el momento) predecir con exactitud cuál será la institución que se especificó en la referencia. Lo que se decidió por el momento es generar la estructura XML completa para esa referencia manteniendo como autor a la institución especificada en la misma, sin imprimir ningún error en el mixed-citation o consola ni limitar la creación del XML correspondiente a la referencia, tal y como se hace si se retornan 0 resultados.

- Si se buscan instituciones por sus SIGLAS, también OpenAlex puede encontrarlas.

---
# Validación de autores con nombre completo

### Contexto del problema

Este problema surge debido a que en una referencia bibliográfica se pueden indicar autores que **no están registrados en OpenAlex para el DOI especificado**.  
- Si no se valida correctamente, podría ocurrir que se pisen los datos existentes del XML JATS: los datos de un artículo podrían sobrescribir la referencia manual con información incorrecta de otro DOI.  
- Por eso es fundamental verificar que todos los autores indicados en la referencia coincidan con los autores reportados por OpenAlex para el DOI correspondiente.

### Estrategia de validación implementada

Para validar los autores de una referencia frente a los datos obtenidos desde OpenAlex, se implementó el método `validateFullNameAsAuthor()` en la clase `AuthorValidator`. La lógica principal es:

1. **Coincidencia de apellido:**  
	- Se toma el apellido de cada autor en la referencia y se busca su ocurrencia en el `display_name` del autor obtenido desde OpenAlex.  
	- Actualmente se utiliza `strpos` (PHP) para esta búsqueda, lo que permite manejar casos donde los nombres estén abreviados o en distinto orden.  
    - Si el apellido no se encuentra, se registra un error indicando que ese autor no existe para el DOI proporcionado.
   
2. **Validación de nombres o iniciales:**  
	- Una vez identificado el apellido, se elimina del `display_name` de OpenAlex para no necesitarlo más.  
	  **Esto se hace "restándole" o quitándole al nombre completo de un autor (el de OpenAlex) el apellido identificado en la referencia, lo cual termina dejando como resultado solo el/los nombres, los cuales posteriormente serán validados.**
	- Cada inicial o nombre del autor en la referencia se compara con las partes restantes del nombre completo de OpenAlex:
		1. Si todas las iniciales/nombres del autor coinciden, se considera que el autor es válido.
		2. Si alguna inicial/nombre no coincide, se registra un error indicando qué autor no pudo ser validado.
	- **Además, el método contempla el caso en que la referencia contiene solo las iniciales de los nombres, mientras que OpenAlex posee los nombres completos.** Esto significa que, por ejemplo, un autor con nombre “J. A.” en la referencia coincidirá correctamente con “John Alexander” en OpenAlex, siempre que las iniciales correspondan a las primeras letras de los nombres. Así también si tuviera otro nombre extra en OpenAlex que en la referencia no existe, en este caso el autor será **valido**

3. **Resultado final:**  
   - El método retorna `true` solo si **todos los autores de la referencia** fueron validados correctamente.  
   - Retorna `false` si al menos un autor no coincide, registrando un error específico para cada caso.

> Nota: La implementación actual con `strpos` permite aceptar abreviaciones en la referencia mientras el apellido coincida, pero no detecta errores tipográficos. En el futuro, se podrían usar funciones como `levenshtein` o `similar_text` para mejorar la detección de coincidencias aproximadas.
