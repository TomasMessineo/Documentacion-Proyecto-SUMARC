En este ticket se mencionaran todos los cambios realizados hasta el día de la fecha: 28 de agosto de 2026. 
Esto servirá para poder explicar detalladamente cada cambio realizado el día que lancemos una nueva release de SUMARC, además de que nos permitirá saber cuáles son las modificaciones que hasta el momento solo están agregadas como parche en el servidor de producción de revistas y que todavía no son parte de una release oficial de SUMARC.

h3. **Error solucionado: Corrección en el formato de fecha de publicación en vista de artículo**
Este error ya fue solucionado. Se puede leer con más detalle en el ticket https://trac.prebi.unlp.edu.ar/issues/14769.
Actualmente, este error está solucionado luego de que lo hayamos parcheado solo en el servidor de producción. Cuando se lance la nueva versión de SUMARC, esto se solucionará gracias a la implementacion de una nueva configuración en el plugin JatsParser que permite cargar la estructura para las fechas de las referencias. Esto está explicado en el ticket  https://trac.prebi.unlp.edu.ar/issues/14504 (mas adelante en este ticket también se menciona).

h3. 