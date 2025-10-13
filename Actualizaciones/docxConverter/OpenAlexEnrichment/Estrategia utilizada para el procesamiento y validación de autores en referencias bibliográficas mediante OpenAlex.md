
# Clase "AuthorValidator":

Para validar si una institución autora o un nombre completo de un autor son válidos según lo obtenido mediante la API de OpenAlex, se implementó una clase denominada "AuthorValidator", la cual se encargará de realizar estas tareas de validación. El método `validateInstitutionAsAuthor()` verifica que el nombre de la institución exista en OpenAlex, y el método `validateFullNameAsAuthor()` se encarga de verificar si el nombre completo del autor indicado en la referencia es válido con respecto al autor obtenido mediante la API de OpenAlex (esto servirá para poder evaluar si el/los nombres de los autores en la referencia fueron escritos de forma correcta o no).

A continuación se detallarán todos los 

# Instituciones como Autores:

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

---

- Si se buscan instituciones por sus SIGLAS, también OpenAlex puede encontrarlas. 

# Autores con nombre completo:

