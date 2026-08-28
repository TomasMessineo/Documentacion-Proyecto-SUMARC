En este ticket se mencionaran todos los cambios realizados hasta el día de la fecha: 28 de agosto de 2026. 
Esto servirá para poder explicar detalladamente cada cambio realizado el día que lancemos una nueva release de SUMARC, además de que nos permitirá saber cuáles son las modificaciones que hasta el momento solo están agregadas como parche en el servidor de producción de revistas y que todavía no son parte de una release oficial de SUMARC.

*Error solucionado: Corrección en el formato de fecha de publicación en vista de artículo*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14769) ya fue solucionado.
Debido a que la solución a este problema aún no fue desplegada en producción (está implementado y subido en las ramas dev-3_4 y dev-3_3 del plugin JatsParser, pero no en las ramas stable-3-3 y stable-3.4), se aplicó un parche temporal directamente en la configuración del OJS de producción para normalizar la visualización de la fecha en los artículos. Esto está mejor explicado en el ticket  https://trac.prebi.unlp.edu.ar/issues/14504. 
La solución definitiva a este problema (sin necesidad de ningún parche) se verá reflejada cuando se lance la nueva release de SUMARC, ya que esta solución está subida a GitHub (commit: ). El ticket que detalla la solución definitiva a este problema es https://trac.prebi.unlp.edu.ar/issues/14504. 

*Error solucionado: Error al generar las referencias por caracter especial "&amp;"*:
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14552) ya fue arreglado, se debía a autores institucionales que tenían un ampersand en su nombre, los cuales ocasionaban que las referencias no. Este arreglo ya está subida a GitHub pero aún no está desplegada en producción, por ende se optó por realizar el cambio a mano en el servidor de producción. La solución a este problema está detallada en el ticket https://trac.prebi.unlp.edu.ar/issues/14556.

*Corrección de cursivas en referencias de tipo Sitio Web (webpage)*:
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14534) ya fue solucionado y está subido a GitHub, pero aún no está desplegada en producción, por ende se optó por realizar el cambio a mano en el servidor de producción. 