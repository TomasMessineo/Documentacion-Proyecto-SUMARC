
### Lunes 10/8
# DistLearn: Entrenamiento de orden cero descentralizado por capas mediante descenso de coordenadas por bloques, basado en teoría de juegos.

- **Resumen:** Es una forma de entrenar redes neuronales sin calcular el gradiente tradicional (que suele ser pesado) usando **teoría de juegos** (cada capa de la red actúa como un "jugador" intentando optimizar su parte).
- **Lo importante:** Si una capa mejora un poquito, mejora toda la red de forma coordinada. Sufre de "maldición de la dimensionalidad" (demasiados parámetros), pero lo bueno es que el problema se limita a los parámetros de esa capa y no a la profundidad de la red. Sirve para redes no tan gigantes.
    
- **Términos desconocidos:**
    - **Equilibrio de Nash:** Estado de la teoría de juegos donde ningún jugador gana nada cambiando su estrategia unilateralmente (en la red: ninguna capa puede mejorar más si las otras no cambian).
    - **ADAM:** El optimizador más popular en PyTorch/TensorFlow (Python) para ajustar pesos en redes neuronales.
    - **Distribución Cauchy:** Una función de probabilidad con "colas pesadas" (eventos extremos son más probables que en una normal/Gaussiana).

---
# Enterprise AI: Del experimento a la plataforma. La evolución arquitectónica de la Inteligencia Artificial en la Empresa (DE RED HAT).

Red Hat toma las soluciones open source del mercado, las certifica y se las brinda a empresas.
La idea es contar la experiencia con la IA, con proyectos hechos con ARSAT y otras organizaciones.
Todas las empresas comenzaron a experimentar con un modelo, aplicando un caso de uso con un modelo particular, y empezando a probar como funcionaba, qué era lo que hacia, como respondía, etc. Cuando quisieron pasar a producción, se encontraron que otras areas necesitaban soluciones. Hubo una necesidad de empezar a ver como dar respuesta a esas soluciones que empezaban a llegar a producción y escalaban en cuanto a soluciones.

Para mejorar este proceso se implementó una nueva arquitectura, ligada a la IA. Se tienen varias capas:
- Capa de aplicación y agentes: Orquestación de AI Agentes conectada mediante estándares abiertos (MCP) e interfaces unificadas.
- Capa de datos y modelos: Integración de APIs empresariales, bases de datos vecctoriales y servidores de indiferencia optimizados
- Capas transversales: Seguridad, Guardrails, Evaluation, Observability y Governance a lo largo de todo el ciclo de vida.

Luego aparecieron los conceptos de automatizar procesos de negocio. Agentic AI es el que se utilizó. Un ejemplo de flujo de agente: 
1. Buscar documentación relevante (RAG)
2. Consultar estado de cuenta en ERP
3. Consultar perfil de cliente en CRM
4. Ejecutar API transaccional en Backend
5. Consolidar respuesta y notificar

Tenemos agentes, tenemos como conectarnos (MCP), el cómo generar el modelo y como aprovecharlo dejó de ser un problema, sino ahora es cómo dar respuesta a la cantidad de peticiones que voy a tener de distintos organismos, porque ya lo tengo en producción. Para resolver esto se buscó una plataforma que pueda resolver estos problemas, que tenga esta capacidad basandose en lo que necesita una organización:
- Model registry & ai inference
- Evaluation & observability
- Guardrails & Governance
- Hybrid Cloud Strategy

RedHat brinda RedHat AI Enterprise. Al final como conclusión se explicó que existen muchos modelos (llama, gpt, etc.), pero que se necesita un lugar donde poder alojar los modelos y poder procesar todos los datos de manera eficiente y poder escalar a futuro. Ahí se mencionó como solución a RedHat AI Enterprise para "mitigar" estos problemas.

Dependiendo del caso de uso, se ve si se prioriza un modelo u otro dependiendo de si se prefiere una respuesta mas segura a cambio de un mayor costo, o viceversa.

---
# Keynote conjunto con ASSE: Automatizando migraciones de código

- **Idea central:** "Migrar no es traducir código". Intentar traducir un sistema viejo (legacy) línea por línea a mano genera agotamiento y deuda técnica.
    
- **Evolución de las generaciones de migración:**
    
    - _Gen 0:_ Manual / Ingeniería inversa. Sobrecarga operativa.
     _Gen 1:_ Prompts simples a GPT-4. Los modelos no razonaban bien.    
    - _Gen 2 (Agentes 1.0):_ Agentes en loop para traducir, validar y corregir. Sufrían de **sobreespecificación** (darle instrucciones ultra detalladas al modelo empeoraba el resultado).        
    - _Gen 3 (Actual):_ **Sistemas Compuestos de IA**. Usan modelos con capacidad de razonamiento, **MCP** para que el agente examine bases de datos y repositorios en vivo, y **Skills/Progressive Disclosure** (el modelo decide qué herramientas usar a medida que las necesita).

**Cómo se encara hoy:**
Primero se trata de entender como funciona el sistema de origen, sacando métricas de uso. Se tiene que entender qué vamos a migrar.
Luego viene el linaje. Traducir todo el proceso a un documento que pueda ser leido por los agentes.
Hay que ver cómo validamos también. Cada vez que hay un problema en la validación, se puede buscar el problema raíz y resolverlo.
Por último se explica la modernización - Rediseñar.

**Definiciones:**

¿Migración o reingeniería? Nunca es una sola cosa.
- **Lift and Shift:** Lo que tenía en el sistema viejo me lo llevo al sistema nuevo. En datos nunca es 100% lift and shift. Cambiar el motor de ejecución fuerza reingeniería quieras o no.
- **Modernización/Reingeniería:** Rebuild completo, modelo de datos, ETL, ML y consumidores downstream.
- **Persist:** Se queda en el legado por ahora, impacto del negocio demasiado crítico. Lo que no se usa lo matamos y no perdemos tiempo en cosas que no tiene sentido atacar.
- **Deprecate:** No se migra. Ya no se usa, o fue reemplazado por algo mas nuevo.

No hay nada mas definitivo que lo temporal.
El refactor del futuro no va a llegar. 

Migrar no es traducir código.

**DUDA:**
- ¿Cómo funciona DataBricks?
- ¿Qué es Source Hadoop Spark (Scala) y Target Spark (PySpark)
- Se puede leer el artículo "The Shift from Models to Compound AI Systems"
- ¿Qué es la sobreespeficación? 
- Se puede leer "The Bitter Lesson", de Rich Sutton
- ¿Qué es progressive disclosure?
- ¿Qué es ingeniería de contextos?

---
# On the Structural Limits of Machine Learning Decision Systems - An information - Theoretic, interaction based, and stochastic dynamical perspective

- **El cambio de paradigma:** Los modelos matemáticos clásicos eran deterministas (basados en ecuaciones diferenciales): si conocías el estado presente, podías predecir el futuro exacto.
    
- **El problema de la interacción masiva:** Cuando metés decisiones tomadas por agentes, usuarios e interacciones en tiempo real, el sistema pierde la propiedad de Markov (donde el futuro _solo_ depende del presente). Emergen **sistemas con memoria de largo plazo** y **distribuciones de cola pesada** (_heavy-tailed distributions_), donde eventos extremos o raros ocurren mucho más seguido de lo que predice una distribución normal.
    
- **El modelo de Polya (Urna de Pólya):** Es un proceso estocástico clásico de refuerzo positivo (un efecto _"el rico se hace más rico"_ o "realimentación"). Si sacás una bola roja de una urna, la devolvés y encima agregás otra roja, la probabilidad de sacar rojas en el futuro aumenta. Se usa para modelar cómo decisiones pasadas sesgan o condicionan el comportamiento futuro del sistema.
    
- **Drifts y KPIs:** Un sistema de Machine Learning en producción sufre **Concept/Data Drift** (el mundo real cambia y el modelo pierde precisión). Para detectar esto, se necesitan KPIs dinámicos de monitoreo.
    
- **Conclusión central:** _No hay que mirar solo el algoritmo como una caja negra; hay que entender el modelo matemático y probabilístico que hay detrás para conocer sus límites reales._

---

# CHARLA FINAL

- **Evolución discontinua:** Los productos de software no evolucionan en línea recta suave, sino por saltos/disrupciones tecnológicas.

- **Crecimiento de proyectos a medida (+22.5%):** A pesar del auge de herramientas "no-code" o generadores automáticos, la demanda de soluciones personalizadas y complejas para empresas e instituciones está subiendo fuertemente.
    
- **El mito de "La informática se termina":** Frente al pánico de que la IA va a reemplazar a los desarrolladores, la proyección muestra todo lo contrario: hacia **2028** se prevé una explosión de proyectos. El rol no desaparece, sino que muta; el desafío será saber **adaptarse a las nuevas arquitecturas y orquestaciones**.
    
- **Estrategias de desarrollo (Greenfield vs. Brownfield vs. Bluefield):**    
    - **Greenfield:** Arrancar un sistema desde cero en hoja en blanco.
    - **Brownfield:** Mantener o evolucionar un sistema heredado (_legacy_) existente con toda su deuda técnica.
    - **Bluefield:** La estrategia mixta moderna. En lugar de tirar todo el legacy o seguir emparchándolo, aislás las partes útiles del sistema viejo, rediseñás la arquitectura y migrás selectivamente lo que aporta valor.

---

**Miércoles 12 de agosto**

# Not All Instructions Are Forgotten Equal

### ¿Cuál es el problema?

Cuando empezás a hablar con un agente o un LLM, la ventana de contexto está limpia y la IA sigue todas las reglas al pie de la letra (ej: "sé crítico", "no me des la razón siempre", "respondeme en JSON").
Sin embargo, a medida que la conversación se vuelve más larga:
- La ventana de contexto se llena/satura.
- El sistema se vuelve más lento.
- La IA empieza a olvidar e ignorar instrucciones.

### El hallazgo clave

- **El olvido no es parejo:** La IA no olvida todo de golpe ni al azar. Le da más prioridad y retiene por más tiempo ciertas reglas (como la personalidad o el tono), mientras que las restricciones de formato, reglas secundarias o guardrails "se le borran" primero.    
- **Procesos estadísticos y bayesianos:** Usaron herramientas probabilísticas (PyMC, Bambi, ArviZ) y técnicas como BKT (Bayesian Knowledge Tracing) para medir exactamente en qué momento la IA empieza a ignorar cada instrucción individualmente.
- **Efecto Evaluador:** Los modelos detectan cuando los están evaluando o testeando y cambian su comportamiento, por lo que tuvieron que evaluarlos de forma "ciega".

### ¿Por qué importa y cuál es la lección?

No podés confiar en meter 20 reglas juntas en un texto gigante (System Prompt). Como la IA las olvida de forma selectiva a medida que la charla avanza, medir la degradación instrucción por instrucción permite saber cuándo reinyectarle dinámicamente las reglas críticas antes de que falle.

---
---
---

# Clasificación de sedimentos urinarios mediante modelos de aprendizaje profundo

**Metodología CRISP-DM usada en minería de datos**

Herramientas:
- Kaggle

---

# Descubriendo indicadores de sesgo en el comportamiento de grandes modelos de lenguaje

*Sesgo sutil:* Pueden manifestarse en patrones linguísticos distribuidos diferencialmente

1. Generación constrastiva de textos: Prompts que fijan contexto y varian solo el grupo social. Ej: "Escribe una historia sobre Ana, una persona ciega que tiene una reunion de trabajo"
2. Construcción de clases de equivalencia: Para reducir la variabilidad de las expresiones linguísticas y mejorar la representatividad estadística
3. PMI sobre clases de equivalencia: Blas-Score (BS) para una clase de equivalencia A.

**Palabras clave: Clases de equivalencia, bias score.**

---