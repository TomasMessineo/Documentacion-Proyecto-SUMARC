# Documentación para la instalación de plugins de SUMARC para OJS 3.4
#### 📅 Última actualización: 11/07/2025

---
👉 1) Descomprima el archivo "SUMARC-ojs_3_4.zip", el cual generará una carpeta llamada "SUMARC-PARA-OJS_3_4"

👉 2) Dentro de la carpeta descomprimida, se encontrarán
los 3 plugins para SUMARC: docxToJats, jatsParser, texture.
Estas carpetas deberán copiarse en el directorio donde se encuentran los plugins genéricos de OJS, dentro del servidor. Por lo general, este directorio está en: `plugins/generic`. Dentro de la carpeta `generic` es donde debemos copiar los 3 plugins.

👉 3) Una vez copiados los plugins:
    - Ingrese al panel de administración de OJS
    - Diríjase a "Sitio web" > "Módulos instalados"
    - Habilite los módulos de conversión de DOCX a XML JATS (plugin DocxConverter), el módulo editor Texture (plugin Texture) y el módulo jatsParser (plugin JatsParser) 

**DATO IMPORTANTE:** Asegurese de que los plugins esten habilitados correctamente. Además, para habilitar de forma correcta el plugin para la generación de PDF (jatsParserPlugin) deberá buscar este plugin en la sección de módulos (aparece como JATSParser). Luego, haga clic en el ícono de triángulo a la izquierda del nombre para expandir el apartado.
Seguidamente, deberá hacer click en "Ajustes".
Esto abrirá la configuración del plugin jatsParser, donde deberá seleccionar el formato de citación que desee y habilitar la conversión a PDF (si esto último no se habilita, el plugin no podrá generar los PDF).

✅ ¡Listo! Ya puede disfrutar de los plugins de SUMARC...

--------------------------

**Cargar logos de revistas e instituciónes (opcional):**
Para que el logo de una institución y el logo de una revista se visualicen en el PDF generado es necesario copiar manualmente estos logos dentro de la carpeta correspondiente al ID de la revista en el directorio privado de OJS, donde se encuentran las revistas (`{directorio privado de ojs}/journals/{id de la revista}`) del servidor.
Dentro de la carpeta correspondiente al id de la revista se deben copiar los logos.

IMPORTANTE:
- El logo de la revista debe llamarse logo.jpg.
- El logo de la institución debe llamarse institution.jpg.

👉  Este proceso puede repetirse para cada revista. De esta forma cada una de estas tendrá su propio logo de revista e institución. 
