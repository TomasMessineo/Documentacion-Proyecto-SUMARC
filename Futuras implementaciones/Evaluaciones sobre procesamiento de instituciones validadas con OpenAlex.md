
- Si tengo una referencia que tiene una institución inexistente como autor, debo imprimir un error en el mixed-citation de la referencia para que el usuario sepa que la institución que especificó NO existe en OpenAlex:
  ![[Captura desde 2025-10-09 11-31-44.png]]

- O simplemente basta con imprimir un error_log indicando este mensaje de error o advertencia?

En la imágen, si la institución no es válida entonces los demás datos de la referencia no se generan, solo se imprime el mixed-citation con la referencia y la indicación del error.

En el caso de que una referencia tenga en su contenido una institución como autora, por ejemplo: "Universidad Nacional de La Pla", esto no machea con "Universidad Nacional de La Plata", por ende entiendo que por mas de que una institución esté mal escrita, si esta no es exactamente igual al nombre de la institución, OpenAlex retornará **null**... esto quiere decir que entonces debería evaluar:

- Si la institución no existe en OpenAlex, entonces informar de un error que directamente no genere la referencia en XML (caso de la imágen anterior)
- Si la institución no existe en OpenAlex, entonces informar de un error en consola pero igualmente generar la referencia con todos sus elementos y tags correspondientes

La estrategia utilizada hasta el momento es: 
- ***Si OpenAlex retorna 0 resultados (null)***, entonces se imprime el error en el tag mixed-citation y NO se genera la referencia completa con todos sus tags correspondientes. **Este enfoque limita a que el nombre de la institución tenga que existir SI o SI en OpenAlex para generar la estructura XML completa de la referencia**
- ***Si OpenAlex retorna un solo resultado***, entonces ese resultado será válido. Por mas de que se ponga una letra menos en una institución, por ejemplo: **"Universidad Nacional de La Plat"**, OpenAlex retornará **NULL** y no la institución especificada (mas allá de que falte un solo caracter). 
- ***Si OpenAlex retorna mas de un resultado,*** entonces no se puede (hasta el momento) predecir con exactitud cuál será la institución que se especificó en la referencia. Lo que se decidió por el momento es generar la estructura XML completa para esa referencia manteniendo como autor a la institución especificada en la Referencia, sin imprimir ningún error en el mixed-citation o consola ni limitar la creación del XML correspondiente a la referencia. 

---

- Si se buscan instituciones por sus SIGLAS, también OpenAlex puede encontrarlas. Todo dependerá de si retorna un solo resultado o varios. Si retorna uno solo, esa institución será válida, pero si retorna varios, directamente se deja la institución tal y como está.
- 