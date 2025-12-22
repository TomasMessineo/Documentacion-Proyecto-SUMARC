Informe: Person-Group Types Faltantes por Tipo de Referencia en Texture
Resumen Ejecutivo
Este informe analiza los tipos de person-group (personas contribuyentes) que están implementados y faltan en cada uno de los 13 tipos de referencias de Texture, comparándolos con el estándar JATS Publishing 1.4.

Person-Group Types Reconocidos por JATS 1.4
Según el estándar JATS Publishing 1.4, los valores permitidos para person-group-type incluyen (pero no se limitan a):

person-group-type	Descripción	Uso común
author	Autores principales	Todas las referencias
editor	Editores	Libros, capítulos, journals
translator	Traductores	Traducciones de libros/artículos
compiler	Compiladores	Compilaciones, antologías
guest-editor	Editores invitados	Ediciones especiales de journals
inventor	Inventores	Patentes
assignee	Cesionarios	Patentes
sponsor	Patrocinadores	Reportes, datos
curator	Curadores	Datasets, exhibiciones
illustrator	Ilustradores	Libros ilustrados
director	Directores	Medios audiovisuales
producer	Productores	Medios audiovisuales
transed	Traductores-editores	Traducciones editadas
revisor	Revisores	Revisiones científicas
allauthors	Todos los autores	Alternativa cuando hay muchos autores
NOTE

JATS permite valores personalizados para person-group-type, por lo que esta lista no es exhaustiva.

Análisis por Tipo de Referencia
1. Journal Article (journal-article-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
editors → person-group-type="editor"
compilers → person-group-type="compiler" (recién agregado)
❌ Person-Groups Faltantes:

translators - para artículos traducidos
guest-editor - para ediciones especiales de journals
curator - para colecciones curadas de artículos
Prioridad: 🟡 Media

translators es el más importante (común en journals multiling üístiques)
guest-editor sería útil para números especiales
2. Book (book-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
editors → person-group-type="editor"
translators → person-group-type="translator"
❌ Person-Groups Faltantes:

compiler - para antologías y compilaciones
illustrator - para libros ilustrados
transed - para traducciones editadas
Prioridad: 🟡 Media

compiler sería útil para antologías
illustrator para libros ilustrados o infantiles
3. Chapter (chapter-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author" (del capítulo)
editors → person-group-type="editor" (del libro)
translators → person-group-type="translator"
❌ Person-Groups Faltantes:

compiler - para capítulos en compilaciones
illustrator - para capítulos con ilustraciones específicas
Prioridad: 🟢 Baja

Chapter-ref tiene buena cobertura
4. Conference Paper (conference-paper-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
❌ Person-Groups Faltantes:

editor - editores de los proceedings ⚠️ CRÍTICO
translator - para proceedings traducidos
compiler - para compilaciones de conferencias
Prioridad: 🔴 Alta

editor es crítico - los proceedings casi siempre tienen editores
Sin editores, las citas de conferencias están incompletas
5. Data Publication (data-publication-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author" (creadores del dataset)
❌ Person-Groups Faltantes:

curator - curadores del dataset ⚠️ IMPORTANTE
compiler - quien compiló/agregó los datos
sponsor - patrocinadores del proyecto de datos
Prioridad: 🔴 Alta

curator es muy importante en datasets (ej: repositorios biológicos)
sponsor es común en datasets de investigación financiada
6. Patent (patent-ref)
✅ Person-Groups Implementados:

inventors → person-group-type="inventor"
assignee → stored as STRING (debería ser person-group)
❌ Person-Groups Faltantes:

N/A - Patent tiene los person-groups específicos necesarios
⚠️ Nota Importante: assignee actualmente está almacenado como STRING, pero según JATS debería ser:

<person-group person-group-type="assignee">
  <collab>Company Name</collab>
</person-group>
Prioridad: 🟡 Media

Refactorizar assignee de STRING a CHILDREN('ref-contrib')
7. Article (article-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
editors → person-group-type="editor"
❌ Person-Groups Faltantes:

translator - para artículos traducidos
compiler - para compilaciones de artículos
Prioridad: 🟡 Media

translator sería útil para preprints traducidos
8. Newspaper Article (newspaper-article-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
❌ Person-Groups Faltantes:

editor - editores de la sección/columna
translator - para artículos traducidos
Prioridad: 🟢 Baja

Newspaper articles raramente necesitan más que authors
9. Magazine Article (magazine-article-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
❌ Person-Groups Faltantes:

editor - editores de la revista
translator - para artículos traducidos
illustrator - para artículos con ilustraciones específicas
Prioridad: 🟢 Baja

Magazine articles generalmente solo necesitan authors
10. Report (report-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
sponsors → person-group-type="sponsor"
❌ Person-Groups Faltantes:

editor - editores del reporte
compiler - para reportes compilados
translator - para reportes traducidos
Prioridad: 🟡 Media

editor sería útil para reportes técnicos multi-autor
11. Software (software-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author" (desarrolladores)
❌ Person-Groups Faltantes:

compiler - quien compiló/empaquetó el software
editor - mantenedores principales
contributor - contribuyentes (aunque esto se maneja diferente)
Prioridad: 🟢 Baja

Software generalmente solo necesita authors
GitHub/GitLab manejan contribuyentes de forma separada
12. Thesis (thesis-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author" (estudiante)
❌ Person-Groups Faltantes:

editor - directores de tesis ⚠️ MUY IMPORTANTE
translator - para tesis traducidas
Prioridad: 🔴 Alta

editor (o mejor advisor/director) es crítico para tesis
Las tesis siempre tienen directores/advisors
Actualmente no hay forma de registrar esta información crucial
Recomendación Especial: Considerar agregar un person-group-type específico para tesis:

advisor o director para directores de tesis
committee-member para miembros del comité
13. Webpage (webpage-ref)
✅ Person-Groups Implementados:

authors → person-group-type="author"
❌ Person-Groups Faltantes:

editor - editores del sitio web
translator - para contenido traducido
curator - curadores de contenido web
Prioridad: 🟢 Baja

Webpages generalmente solo necesitan authors
Matriz de Person-Groups por Tipo de Referencia
Tipo de Referencia	authors	editors	translators	compilers	curators	sponsors	inventors	advisors	illustrators
Journal Article	✅	✅	❌	✅	❌	❌	-	-	-
Book	✅	✅	✅	❌	-	-	-	-	❌
Chapter	✅	✅	✅	❌	-	-	-	-	❌
Conference Paper	✅	❌	❌	❌	-	-	-	-	-
Data Publication	✅	-	-	❌	❌	❌	-	-	-
Patent	-	-	-	-	-	-	✅	-	-
Article	✅	✅	❌	❌	-	-	-	-	-
Newspaper	✅	❌	❌	-	-	-	-	-	-
Magazine	✅	❌	❌	-	-	-	-	-	❌
Report	✅	❌	❌	❌	-	✅	-	-	-
Software	✅	❌	-	❌	-	-	-	-	-
Thesis	✅	❌	❌	-	-	-	-	❌	-
Webpage	✅	❌	❌	❌	❌	-	-	-	-
Leyenda:

✅ = Implementado
❌ = Faltante y recomendado
- = No aplicable o poco común
Recomendaciones Prioritarias
🔴 Prioridad Crítica
Thesis → advisors/director

NUEVO person-group-type: Las tesis necesitan directores
Implementar como advisors o director
Esencial para citación correcta de tesis
Conference Paper → editors

Los proceedings casi siempre tienen editores
Sin esto, las citas están incompletas
Data Publication → curator

Crítico para datasets en repositorios
Común en bioinformática y ciencias de datos
🟡 Prioridad Alta
Journal Article → translators

Importante para journals multilingües
Común en publicaciones internacionales
Book/Chapter → compiler

Necesario para antologías y compilaciones
Diferente de editor
Book/Chapter → illustrator

Importante para libros ilustrados
Reconocimiento de contribución artística
🟢 Prioridad Media
Report → editor

Útil para reportes técnicos multi-autor
Refactorizar Patent → assignee

Cambiar de STRING a person-group
Patrón de Implementación
Para agregar un nuevo person-group-type a cualquier referencia:

// 1. Schema (ejemplo para thesis-ref)
ThesisRef.schema = {
  type: 'thesis-ref',
  authors: substance.CHILDREN('ref-contrib'),
  advisors: substance.CHILDREN('ref-contrib'), // NUEVO
  // ... otros campos
};
// 2. Import XML
node.authors = _importPersonGroup(el, doc, 'author');
node.advisors = _importPersonGroup(el, doc, 'advisor'); // NUEVO
// 3. Export XML
el.append(_exportPersonGroup($$, doc, node.authors, 'author'));
el.append(_exportPersonGroup($$, doc, node.advisors, 'advisor')); // NUEVO
// 4. UI Labels
config.addLabel('advisors', 'Thesis Advisors');
config.addLabel('edit-advisors', 'Edit Advisors');
// 5. Preview Rendering
if (entity.advisors && entity.advisors.length > 0) {
  fragments = fragments.concat(
    ' Directed by: ',
    _renderAuthors($$, entity.advisors, entityDb),
    '.'
  );
}
Notas Finales
IMPORTANT

Person-Group Types Personalizados en JATS

JATS permite valores personalizados para person-group-type. Algunos útiles podrían ser:

advisor o director - para tesis (más específico que editor)
contributor - para contribuyentes generales
maintainer - para software
reviewer - para revisiones científicas
TIP

Diferencia entre Editor y Compiler

Editor: Revisa, corrige, y supervisa el contenido
Compiler: Recopila y organiza trabajos existentes sin modificarlos sustancialmente
Una antología puede tener ambos: un compiler que seleccionó los textos y un editor que preparó la edición.

WARNING

Caso Especial: Patent assignee

Actualmente assignee en patent-ref es un STRING. Según JATS, debería ser:

<person-group person-group-type="assignee">
  <collab>Company Name</collab>
</person-group>
Esto permite múltiples assignees y mejor estructuración de datos.