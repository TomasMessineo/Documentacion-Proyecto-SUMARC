
---
---

- Evaluar quitar IDs del catálogo ya que no es necesario. Se pueden recorrer las partes del catalogo con un foreach (como ya se hace) de forma secuencial sin necesidad de agregar IDs

- Analizar el tema de seguridad al querer acceder a los metadatos mediante el TPL, existe el riesgo de que suban un .tpl y a partir de esto creen un nuevo usuario o accedan a información sensible utilizando un servicio de OJS. Es una herramienta flexible pero al poder subir archivos, 
  En el templating existen "jaulas" donde se pueden definir comandos específicos que se pueden utilizar, ignorando los que no estén definidos 
  **Probar con un "call" en un .tpl acceder a información específica de OJS que puede ser sensible e imprimirla, probar hacer diferentes cosas con esto.**
  Quizá se puede restringir el acceso a ejecución remota de código y disponibilizar variables (hay que ver bien cómo se haría)

- Se genera un PDF A/2b, el cual es aceptable pero mejorable. Sirve para la preservación pero no para la accesibilidad

- Evaluar si en el PDF de salida se puede poner una marca de agua. Esto debería evaluarse, para ver si la versión de CSS que soporta mPDF puede integrar esto

- Tener una plantilla de versión previa y una plantilla de versión final. 