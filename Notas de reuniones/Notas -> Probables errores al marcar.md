
---
---

- En Texture, en la sección correspondiente a las referencias hay campos en los cuales hay "," extras. Por ejemplo, en la referencia: 
  **"Carrillo AM. ,Ley Brazos Vacíos: cuidado de la salud mental de la mujer y familia en duelo perinatal en Colombia [Archivo de video]. [https://www.youtube.com/watch?v=s8sk1oX_1Hc&t=2s](https://www.youtube.com/watch?v=s8sk1oX_1Hc&t=2s). Accessed 2024 abril 24."** 
  En el campo "Title" hay una coma al principio del texto. Esto NO debe ir, ya que la referencia se armará automáticamente

- Las referencias extraídas desde el metadato de "Referencias" en la pestaña de Publicación son las que aparecerán luego en el HTML o la página principal del artículo, y por otro lado, las que se generan para el PDF solo permanecerán allí (en el PDF). 
  Básicamente, si uno modifica de manera manual las referencias que están en el metadato "Referencias" en la pestaña de Publicación, lo que estaría modificando es el cómo se van a ver las Referencias en la página principal (el HTML) del artículo... estos cambios realizados de forma manual en las referencias NO se van a ver reflejados en el PDF.

- Para cargar los rangos de página en una referencia desde texture, existe el campo "Page Range", que se puede rellenar "24-26" por ejemplo, y también los campos "First Page" y "Last Page", que pueden cargarse con los datos "24" y "26" por ejemplo (lo cual dejaría como salida en la referencia 24-26 para el rango de página).
  ***DATO IMPORTANTE*:** El rango de página **únicamente funciona con referencias de tipo "JOURNAL"**. 
  Si se quiere especificar un rango de página en referencias de **tipo "CHAPTER" (capítulo de libro) este rango NO aparecerá** al extraer el metadato "Referencias" en publicación ni tampoco al generar el PDF. **Esto se debe a un error en la herramienta que se encarga de armar las referencias automáticamente, no es un error que se arrastre desde texture. ES un PROBLEMA INTERNO DE LA HERRAMIENTA.** 

- Las imágenes no están cargadas en el artículo (tener en cuenta por si surge algún problema con esto)


---

Soy **Tomás**, uno de los desarrolladores de **SUMARC**. Estuve revisando el caso que mencionó Lola y te detallo algunos puntos que sería importante que revises para asegurarnos de que todo esté funcionando correctamente:

- En **Texture**, dentro de la sección de **referencias**, notamos que algunos campos incluyen **puntos o comas adicionales**. 
  Es importante tener en cuenta que **las comas entre autores, los puntos entre el título del artículo y el nombre de la revista (por ejemplo), o la puntuación final se generan automáticamente** al momento de construir la referencia (al generar el PDF o extraer las referencias desde el metadato "Referencias" de la pestaña de Publicación en OJS).  
  Por ese motivo, **no debe agregarse manualmente una coma o un punto al final de cada campo**, ya que esto puede generar errores o duplicaciones al exportar las referencias.
  
  Por ejemplo, en la referencia:  
  _Carrillo AM. ,Ley Brazos Vacíos: cuidado de la salud mental de la mujer y familia en duelo perinatal en Colombia [Archivo de video]. [https://www.youtube.com/watch?v=s8sk1oX_1Hc&t=2s] (https://www.youtube.com/watch?v=s8sk1oX_1Hc&t=2s)_
  En el campo **Title** hay una coma al inicio que **no debe estar**, ya que la herramienta que genera las referencias bibliográficas se encarga de colocar las puntuaciones y comas automáticamente.
    
  - Las **referencias extraídas desde el metadato “Referencias”** en la pestaña _Publicación_ son las que se muestran en el **HTML del artículo (la página principal)** y las del **PDF** salen del XML. Esto significa que, si se editan manualmente las referencias en el metadato _Referencias_, los cambios **solo se verán reflejados en la versión web**, **no en el PDF**.  
    
- Para los **rangos de página** en _Texture_, podés usar el campo _Page Range_ (por ejemplo, “24-26”), o bien los campos _First Page_ y _Last Page_ (“24” y “26”).  
  Tené en cuenta que este rango **solo funciona con referencias del tipo “JOURNAL”**.  
  En las de tipo _CHAPTER_ (capítulo de libro), el rango **no se mostrará** ni en el HTML ni en el PDF.  
  Esto se debe a una **limitación interna de la herramienta que arma las referencias automáticamente**, no a un problema en _Texture_.  
      
    
- Finalmente, observamos que **las imágenes aún no están cargadas** en el artículo, por lo que sería bueno tenerlo presente en caso de que surja algún inconveniente con la visualización o exportación.
    

Si luego de revisar estos puntos seguís con dudas o se te complica resolver alguno, podemos coordinar una **reunión junto a Santi (también desarrollador de SUMARC)** y **Luisina** para repasar todo con más detalle y aclarar tus consultas.

Quedo atento a tu respuesta para coordinar.

Saludos,  
**Tomás**  
Desarrollador – SUMARC  
Portal de Revistas UNLP