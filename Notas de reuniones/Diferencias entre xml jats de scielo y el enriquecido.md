
- En el XML enriquecido, en el front, el tag journal-title y el abbrev-journal-title están dentro de otro tag "journal-title-group", y en el XML de scielo-uruguay dichos tags están sueltos está suelto
- El XML de scielo tiene dos article-id (dentro de article-meta), en el enriquecido solo hay uno
- En el XML enriquecido hay un tag que no está en el de scielo: "article-categories".
- En el XML de Scielo los article-title salen en distintos idiomas, con el prefijo indicado (por ejemplo "es" en español o "en" si está en inglés), en el enriquecido esto no sucede.
- En el XML JATS enriquecido, dentro de cada tag "contrib" aparece el contrib-id, en el de scielo no. Lo mismo sucede con el tag "email"
- En el XML enriquecido, los tags "aff" están dentro del contrib-group, en el de scielo no, están luego del contrib-group
- En lo que sería el tag pub-date, hay un atributo en el de scielo que se llama pub-type, mientras que en el enriquecido parece llamarse date-type. Pub type está obsoleto según JATS
- En el XML de scielo hay dos tags: copyright-statement y copyright-year que están sueltos luego del tag "número". En el enriquecido, estos tags aparecen luego de "history" dentro de un tag llamado "permissions". Además, en el mismo se añade otro tag "copyright-holder" y "license"
- En el XML enriquecido, aparece el tag "history", en el de Scielo.
- El tag "count" lo preservamos si ya viene de antemano en el XML. Es opcional según el estándar y creemos que el error NO está acá.


- Tener dos verisones de XML: Una con lo mínimo que se necesite SOLO con los datos que pide Scielo, y otro mas completo (agregando emails, etc).