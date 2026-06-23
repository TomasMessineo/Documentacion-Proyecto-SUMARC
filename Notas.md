
- Que scieloAdapter evalúe si existe el ext-link en el mixed-citation para tipos de referencia a Webpage, si no coincide, hacer lo mismo que source: Agregarlo al final de la referencia. Esto que se aplique si viene un mixed citation ya o hay que construir uno. Evaluar también si la validación de source para agregar en el mixed citation se hace siempre sin importar si existe o no mixed citation, o si solo se hace cuando el mixed NO existe.

- Cuando hay un link en las footnotes, hay que agregar el atributo: `_xlink:href_` en cada uno de los ext-link para que no haya errores de estructura.  AGREGAR XLINK.

- Si en una imágen marcada NO hay título, el validador de estructura tira error de que en <caption/> falta el título.

- **Solucionar este problema:** @article-type [[?]](https://scielo.readthedocs.io/projects/scielo-publishing-schema/pt_BR/latest//search.html?q=@article-type&check_keywords=yes&area=default)|[ERROR] [E1]|Asegúrese de que los elementos @article-type (research-article) y subject (Artículos) se identificaron correctamente. Maybe research-article is not a valid value for @article-type. Suggested values: artículo.|

- Poner s.f en la fecha hace que haya un fatal error