
**Lunes 10/8**
# Revisión de código automatizada utilizando Large Language Models.

Actualmete la revisión manual se convierte en un cuello de botella en la integración de desarrollos utilizando LLMs.
Los tres problemas que se identifican son:
- El costo.
- Repetitividad.
- Presión operativa.

Automatización parcial del feedback look:
1. Analizar diffs
2. Evaluar reglas
3. Generar comentarios

Integración en el flujo de CI/CD
1. Desarrolo
2. Commit
3. Pull request
4. Revisión automática -> Agrega comentarios con las evaluaciones
5. Validación humana

PR -> Github Action -> entrypoint.py -> GithubInterface (GitHub API) -> Reviewer (se junta con prompts.yml, define las reglas para que el revisor pueda hacer una evaluación del código que se está subiendo) -> LLM

**Reviewer: clase abstracta extensible**
1. Como entrada se tienen los diff, metadatos del PR y reglas del repositorio. 
2. Hooks: Funciones de pre y postprocesamiento registrables

Se deben tener 3 prompts: 
- Prompt base
- Prompts de regla
- Formato de salida

Tres dimensiones complementarias:
- Rendimiento
- Aceptación: Se encuestó a 8 desarrolladores. 6/8 dijeron que sí usarían la herramienta, los demás no.
- Factibilidad

La propuesta utiliza un modelo vía API y trabaja sobre contexto y reglas del proyecto. La implementación evaluada consume la API de Azure OpenAI preview 4.2. Este modelo se usó durante todo el desarrollo del proyecto.
El agente solo tiene acceso al diff, no tiene un acceso mas profundo sobre el código. 

---

