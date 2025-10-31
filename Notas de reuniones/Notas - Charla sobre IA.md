
# Charla sobre IA -> Vibecoding, generadores de mockups, v0 y APIs libres


## Cursor AI
- $20 por cursor y $20 por Claude
- Antes de comenzar, pedirle a la  que analice el contexto de un proyecto y que arme una propuesta de diseño en un archivo .md
- Al seleccionar la opción "cloud" en Cursor IDE se copia codigo en la nube, se genera una rama y luego genera el PR.
- Opción de configuración "Tools y MCP": Permite conectar servidores MCP como Playwright, Figma, atlassian, etc. 
- Opción de configuración "Rules, memories, commands": Se definen ciertas reglas para seguir buenas prácticas a seguir a la hora de desarrollar. Además, se pueden agregar documentaciones .md de reglas a seguir sobre buenas prácticas que la IA seguirá a la hora de generar código.
-  @ -> Permite elegir archivos

## N8N
-  Sirve para generar un flujo donde hay entradas y salidas de datos y van conectandose nodos que pueden ser MCP

## NotebookLM
- Necesita mucho contexto. Mientras mas contexto se le de, mejor.
- Se le pueden hacer preguntas y en base a lo que se le compartió y responde especificando el lugar de dónde lo sacó en base a las fuentes/archivos compartidas. Si hay que armar un proyecto de financiamiento, armar especificaciones de software, armar artículos, escribir tésis, resúmenes, etc. Se puede arrancar en base a esta herramienta y adjuntar toda la información (fuentes, archivos, etc).
- En la opción de **"insertar nota"**, se le puede forzar cierto razonamiento. Se indican premisas o cosas que tienen que ser así.

**Se podría intentar armar documentación del plugin citation-parser indicando a NotebookLM las fuentes, papers o presentaciones que haya relacionadas a SUMARC.**

## v0
| Concepto           | Qué es                                                                                                                              | Nivel de Interactividad    | Ejemplo                                                       |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- | ------------------------------------------------------------- |
| **Mockup**         | Una **representación visual estática** del diseño (boceto o maqueta). Muestra colores, tipografías, distribución de elementos, etc. | ❌ Sin interacción          | Imagen o diseño plano hecho en Photoshop, Figma o Illustrator |
| **Prototipo**      | Una **versión funcional o simulada** del producto. Permite **interactuar** (botones, navegación, transiciones).                     | ✅ Interactivo              | Prototipo navegable hecho en Figma, Adobe XD o código         |
| **Producto final** | El software real, implementado con código.                                                                                          | 💻 Completamente funcional | App web, móvil o sistema real                                 |


**Resúmen:**

| Etapa             | Qué hacés               | Herramientas                     |
| ----------------- | ----------------------- | -------------------------------- |
| **Mockup**        | Boceto visual           | Figma, Photoshop, Canva          |
| **Prototipo**     | Interacciones simuladas | Figma (modo prototype), Adobe XD |
| **Producto real** | Desarrollo funcional    | React, Flutter, HTML/CSS, etc.   |


## Gamma: IA para PPT's
- Sirve para armar presentaciones en base a un prompt
- 