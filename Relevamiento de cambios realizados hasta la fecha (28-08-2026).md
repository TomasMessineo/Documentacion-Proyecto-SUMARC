En este ticket se mencionaran todos los cambios realizados hasta el día de la fecha: 28 de agosto de 2026. 
Esto servirá para poder explicar detalladamente cada cambio realizado el día que lancemos una nueva release de SUMARC, además de que nos permitirá saber cuáles son las modificaciones que hasta el momento solo están agregadas como parche en el servidor de producción de revistas y que todavía no son parte de una release oficial de SUMARC.

h1. Cambios realizados y problemas revisados

*Corrección en el formato de fecha de publicación en vista de artículo:*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14769) ya fue solucionado.
Debido a que la solución a este problema aún no fue desplegada en producción (está implementado y subido en las ramas dev-3_4 y dev-3_3 del plugin JatsParser, pero no en las ramas stable-3-3 y stable-3.4), se aplicó un parche temporal directamente en la configuración del OJS de producción para normalizar la visualización de la fecha en los artículos. Esto está mejor explicado en el ticket  https://trac.prebi.unlp.edu.ar/issues/14504. 
La solución definitiva a este problema (sin necesidad de ningún parche) se verá reflejada cuando se lance la nueva release de SUMARC, ya que esta solución está subida a GitHub (commit: https://github.com/sedici/JATSParserPlugin/commit/c31431a9866f6ca8e14be7ec7d8d8e889e3a74b2), solo falta mergear todos los cambios a stable e instalar dicha versión en el servidor de producción. El ticket que detalla la solución definitiva a este problema es https://trac.prebi.unlp.edu.ar/issues/14504. 

*Traducción de "Palavras chave* a "Palavras-chave" en el PDF:
Este error no está explicado en ningún ticket, pero ya está solucionado y pusheado al repositorio de GitHub de JatsParser (commit https://github.com/sedici/JATSParser/commit/1fab9fe7b6ca646d066ac2721959cbaa3d9f061e), aunque no está en ninguna de las ramas estables. Lo que se hizo fue simplemente cambiar la traducción para el título de las palabras clave en portugués de "Palavras chave" a "Palavras-chave".
Esto ya está parcheado en el servidor de producción.

*Punto innecesario en la palabra "et al" en la Tabla de Citas:*
Este error no está explicado en ningún ticket, pero ya está solucionado y pusheado al repositorio de GitHub de JatsParser (commit https://github.com/sedici/JATSParserPlugin/commit/17523edc2dbbc0d2e6e18be2b88dfd0d2333024a), aunque no está en ninguna de las ramas estables. Lo que se hizo fue agregar un punto a la palabra "et al" que aparece en la tabla de citaciones cuando se está citando a una referencia con 3 o más autores. En vez de "et al", aparece "et al.".
Esto ya está parcheado en el servidor de producción.

*Impresión de palabra "Article" hardcodeada en referencias de tipo "Webpage":*
Este error no está explicado en ningún ticket, pero ya se solucionó y se pusheó al repositorio de GitHub de JatsParser (commit https://github.com/sedici/JATSParser/commit/4b483eaa2972a784a62e69e7e59306d836ea9d05), aunque todavía no está subido a las ramas estables.. Lo que se hizo fue hacer un pequeño cambio en el archivo csl de APA que utilizamos en SUMARC, para eliminar la aparición de esta palabra hardcodeada antes del e-location ID (aparecía algo como por ejemplo: "Article e123" y solo debe ser "e123").
Esto ya está parcheado en el servidor de producción, donde se modificó a mano una línea de código.

*Impresión de &amp; literal en vez de & en las referencias:*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14496) se solucionó y se pusheó al repositorio de Github de JatsParser (Commit [https://github.com/sedici/JATSParser/commit/cea5855fda2b4d9f892952a6588868f1149f0930](https://github.com/sedici/JATSParser/commit/d0a810e404e293a4ba07df33691ab23cb096c1c2)). Esta solución aún no está en las ramas estables, pero aún así fue parcheado en el servidor de producción. 

*Error al generar las referencias por caracter especial "&amp;"*:
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14552 y su solución: https://trac.prebi.unlp.edu.ar/issues/14556) ya fue arreglado, se debía a autores institucionales que tenían un ampersand en su nombre, los cuales ocasionaban que las referencias no sean renderizadas por la librería CiteProc. Este arreglo ya está subida a GitHub (commit https://github.com/sedici/JATSParser/commit/d9f4c4d30a969cfb7f9e2799c0c38bc9c3eab983) pero aún no está desplegada en producción, por ende se optó por realizar el cambio a mano en el servidor de producción. La solución a este problema está detallada en el ticket https://trac.prebi.unlp.edu.ar/issues/14556.

*Corrección de cursivas en referencias de tipo Sitio Web (webpage)*:
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14534) ya fue solucionado y está subido a GitHub (commit https://github.com/sedici/JATSParser/commit/3fa718f49dcde1106d1697072aac1d46be3c9bdd), pero aún no está desplegada en producción, por ende se optó por realizar el cambio a mano en el servidor de producción. 

*Corrección de Navegación Bidireccional en Referencias y Notas al pie (HTML y PDF):*
Se corrigieron dos errores relacionados con la navegación bidireccional citas->referencias y viceversa (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14495), los cuales tienen que ver con la ausencia de flechas de retorno en las notas al pie del HTML para publicar y las flechas duplicadas en la sección de referencias y notas al pie del PDF. El cambio para solucionar este problema está pusheados en una rama del repositorio JatsParser en GitHub (commit https://github.com/sedici/JATSParser/commit/c71058c15e860a4c7ffd517fdf64ab15930482d5) pero aún NO está en ninguna rama estable ni tampoco parcheado en el servidor.

*Error en preg_match para la generacion del HTML de previsualizacion en jatsParser:*
Se corrigió un error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14334) para utilizar la función stripos a la hora de procesar el HTML de publicación recuperado de la base de datos en vez de utilzar preg_match(), ya que resulta ineficiente utilizar las regex en este caso (debido a las imágenes que estan en base64, lo cual hace que se exceda el pcre.backtrack_limit definido en la configuración de PHP).
Este error fue solucionado y pusheado en una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParserPlugin/commit/67c0656f16e92c321f9c39fe5dc755c2aa941fb5), pero aún no está en ninguna rama estable. 
En el servidor de producción se modificó el archivo php.ini para parchear este problema.

*Falta el metadato "prefijo" en el PDF generado:*
Se corrigió un error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14173) que tenía que ver con la no aparición del prefijo (metadato que se carga en OJS) en el PDF.
Esto ocurría porque en el frontpage.tpl de la plantilla PDF no se especificaba su recuperación en la estructura definida.
La solución a este problema está pusheada en el repositorio de GitHub de JatsParser (commit https://github.com/sedici/JATSParserPlugin/commit/17523edc2dbbc0d2e6e18be2b88dfd0d2333024a ---> se me mezcló con el commit del et al de la tabla de citas jeje srry), pero aún no está en las ramas estables. Está parcheado en el servidor de producción (se hizo el cambio en el archivo frontpage.tpl de la plantilla).

*Reubicación del directorio de plantillas compiladas de Smarty (templates_c):*
Este error (explicado en https://trac.prebi.unlp.edu.ar/issues/14149) fue solucionado y pusheado a una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParser/commit/c22177186a6f14747f27cb799fc4d0dee13cf3ea), pero todavía no está en ninguna rama estable. 
Esto está parcheado a mano en el servidor de producción.

*Error por dejar campo "otro" vacío al seleccionar el estilo de cita en la configuración de JatsParser":*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14147) ya fue solucionado y pusheado a una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParser/commit/be199bfa0a091a7aeddd6a6a9ee2fa3b6b0dc9e0), pero todavía no está en ninguna rama estable.
Esto no está parcheado ni subido al servidor de producción.

*Warning de PHP al procesar artículos sin endnotes:*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14142) ya fue solucionado y pusheado a una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParser/commit/6af400419ff531d1bb311eceb5f2ba0df9bfbf64), pero todavía no está en ninguna rama estable.
Esto no está parcheado ni subido al servidor de producción.

*PHP Warning: "Undefined array key 1 / 2" al formatear la fecha de publicación en JatsParserPlugin.inc.php:*
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14139) ya fue solucionado y pusheado a una rama del repositorio de JatsParser en Github (commit https://github.com/sedici/JATSParserPlugin/commit/92f69a1849f27dd4d411f83c4d2ab36e4117f202), pero todavía no está en ninguna rama estable.
Este cambio NO recuerdo si estaba parcheado y subido en el servidor de producción (creo que no).

*PHP Warning: "Trying to access array offset on null" al renderizar subtítulo en frontpage.tpl*:
Este error (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14140) ya fue solucionado y pusheado a una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParserPlugin/commit/fbc2345ac72861a35bda59b892bd12bcea012fe0), pero todavía no está en ninguna rama estable.
Este cambio tampoco recuerdo si estaba parcheado y subido en el servidor de producción.

*Añadido de botones "Volver" y "Restablecer Todo" en la configuración de plantillas PDF:*
Este problema (explicado en el ticket https://trac.prebi.unlp.edu.ar/issues/14057) ya fue solucionado y pusheado a una rama del repositorio de JatsParser en GitHub (commit https://github.com/sedici/JATSParserPlugin/commit/797cbf62a5b8dd51601d027f77c782268953eb3a, y se le suma un pequeño cambio en las traducciones PO: https://github.com/sedici/JATSParserPlugin/commit/8dcd45f9ffd28b1a167e8366f4c15a01996909c6). 
Este cambio no está parcheado ni subido al servidor de producción.

---

h1. Errores o problemas/trabas pendientes para solucionar

*En discord:*

1. https://discord.com/channels/707986471834877994/1280517594960629792/1498286569780416584
2. https://discord.com/channels/707986471834877994/1280517594960629792/1497303022328484113
3. https://discord.com/channels/707986471834877994/1280517594960629792/1497297342058205205
4. https://discord.com/channels/707986471834877994/1280517594960629792/1496994058264908027
5. https://discord.com/channels/707986471834877994/1280517594960629792/1496952531304054926
6. https://discord.com/channels/707986471834877994/1280517594960629792/1496900357685510175
7. https://discord.com/channels/707986471834877994/1280517594960629792/1496849346132578445 -> Error del directorio caché de smarty que ya fue solucionado (creo)
8. https://discord.com/channels/707986471834877994/1280517594960629792/1503441651492982914 -> Ya parcheado en producción, pero no está en rama stable
9. https://discord.com/channels/707986471834877994/1280517594960629792/1503403134268080199 -> solución: https://discord.com/channels/707986471834877994/1280517594960629792/1503448298248470638
10. https://discord.com/channels/707986471834877994/1280517594960629792/1503753515183640637 -> Esto lo hicimos, sería el sandbox para el taller (y faltaría hacer el que solo tiene SUMARC instalado sin ningún usuario creado)
11. https://discord.com/channels/707986471834877994/1280517594960629792/1524488990831677610
12. https://discord.com/channels/707986471834877994/1280517594960629792/1535308597502943414
13. **Idea para OpenAlex:** https://discord.com/channels/707986471834877994/1280517594960629792/1534582585198645269
14.  Había un mensaje donde Lola mencionaba lo de sacar el punto cuando se menciona el número de la edición o algo así, osea en vez de ser "1°. ed." que sea 1° ed o algo así era. Le podemos consultar a Lola esto.
15. https://discord.com/channels/707986471834877994/1280517594960629792/1542595782572507228
16. https://discord.com/channels/707986471834877994/1280517594960629792/1542533950612971611 -> Solo el punto 3, el de los links que no son clickables.
17. Documentar y tener en cuenta el peso del plugin JatsParser, ya que pesa +100 MB

*En Trac:*
- https://trac.prebi.unlp.edu.ar/issues/14622
- https://trac.prebi.unlp.edu.ar/issues/14492