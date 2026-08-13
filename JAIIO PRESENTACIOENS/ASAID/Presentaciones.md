
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
    -  _Gen 1:_ Prompts simples a GPT-4. Los modelos no razonaban bien.    
    - _Gen 2 (Agentes 1.0):_ Agentes en loop para traducir, validar y corregir. Sufrían de **sobreespecificación** (darle instrucciones ultra detalladas al modelo empeoraba el resultado).        
    - _Gen 3 (Actual):_ **Sistemas Compuestos de IA**. Usan modelos con capacidad de razonamiento, **MCP** para que el agente examine bases de datos y repositorios en vivo, y **Skills/Progressive Disclosure** (el modelo decide qué herramientas usar a medida que las necesita).

**Definiciones:**

¿Migración o reingeniería? Nunca es una sola cosa.
- **Lift and Shift:** Lo que tenía en el sistema viejo me lo llevo al sistema nuevo. En datos nunca es 100% lift and shift. Cambiar el motor de ejecución fuerza reingeniería quieras o no.
- **Modernización/Reingeniería:** Rebuild completo, modelo de datos, ETL, ML y consumidores downstream.
- **Persist:** Se queda en el legado por ahora, impacto del negocio demasiado crítico. Lo que no se usa lo matamos y no perdemos tiempo en cosas que no tiene sentido atacar.
- **Deprecate:** No se migra. Ya no se usa, o fue reemplazado por algo mas nuevo.

No hay nada mas definitivo que lo temporal.
El refactor del futuro no va a llegar. 

Migrar no es traducir código.

--------------------

2. Cuatro generaciones - Y los aprendizaques que nos fueron dejando

Generación 0: A mano.
Tengo que ver por dónde arranco o cuál es el principio. Arrancamos con una ingeniería inversa. Esto lleva mucho tiempo hacerlo manual. Si podemos sobrevivir a eso, sigue la varianza entre las personas. La implementación del código original y entender cómo es, es una varianza, que genera deuda técnica ya que se está migrando sin definir estándares. Una obviedad también es que hacer esto a mano genera agotamiento. Esto tiene una sobrecarga operativa grande. Es un trabajo repetitivo de alta precisión.

Generación 1 - Prompt engineering, traducir con parseo:
Se usaba GPT 4, eran modelos que no razonaban y no existían herramientas maduras. Se intentó reducir la carga laboral de los empleados al realizar la migración.
Luego se empezó a pensar en la utilización de RAG's en vez de Prompt Engineering, para llegar por último a los Sistemas Inteligentes, que pueden decidir, ejecutar acciones y comunicarse entre sí.
Acá se empezó a hablar de agentes. El agente toma feedback basandose en el entorno para generar una respuesta.

Generación 2 - Agentes 1.0:

Empezaron a utilizarse agentes para los siguientes puntos:

1. Conversión: Traduce de (casi) cualquier cosa a Databricks
2. Validación: Ejecuta el código traducido en un entorno de test
3. Corrección
4. Optimización

En ese momento los modelos no razonaban, no existía MCP, los agentes eran torpes en el loop y existía la sobreespecificación. En cuanto a la sobreespecificación. 

Se empezó a pensar cómo solucionar la sobreespecificación, donde cuanto mas se especifica, peor es el resultado. Hay que enfocarse mas en el objetivo y el "cómo" dejarselo al modelo, que ya tendrá esa capacidad.

Generación 3 - Hoy: Qué cambió, en tres cosas:
1. Modelos que razonan: Frente a un mapping ambiguo, exploran, leen las dependencias, corren query, revisan el test, deciden.
2. MCP: El agente ya no razona sobre un archivo, se conecta al repositorio, al catálogo, a la base, al orquestador. Puede descubrir.
3. Skills, no orquestación: Carpetas con isntrucciones, scripts y recursos cargadas por progressive disclosure. Determinismo donde funciona, modelo donde hace falta juicio.

Al principio se hablaba de construir un wrapper al rededor del LLM (no llegué a anotar lo siguiente, pero era algo de que seguía una arquitectura donde se enviaba un mensaje por medio del cliente y se retornaba una respuesta procesada por el LLM)

**Cómo se encara hoy:**
Primero se trata de entender como funciona el sistema de origen, sacando métricas de uso. Se tiene que entender qué vamos a migrar.
Luego viene el linaje. Traducir todo el proceso a un documento que pueda ser leido por los agentes.
Hay que ver cómo validamos también. Cada vez que hay un problema en la validación, se puede buscar el problema raíz y resolverlo.
Por último se explica la modernización - Rediseñar.

No hay que validar una vez que se migró todo.

**DUDA:**
- ¿Cómo funciona DataBricks?
- ¿Qué es Source Hadoop Spark (Scala) y Target Spark (PySpark)
- Se puede leer el artículo "The Shift from Models to Compound AI Systems"
- ¿Qué es la sobreespeficación? 
- Se puede leer "The Bitter Lesson", de Rich Sutton
- ¿Qué es progressive disclosure?
- ¿Qué es ingeniería de contextos?

3. Migration Factory - Cómo lo encaramos hoy

---
# On the Structural Limits of Machine Learning Decision Systems - An information - Theoretic, interaction based, and stochastic dynamical perspective

- Drifts y KPIs nec

Los modelos clásicos estaban basados en ecuaciones diferenciales, donde conociendo el presente se puede conocer el futuro (como los modelos de difusión)
Al haber mas interacciones, la cosa se complica un poco y no alcanza con que el modelo sea de Markov, sino que aparecen modelos de memoria (de largo plazo) o distribuciones de cola pesada.
Se plantea que se estuvo trabajando en un modelo que surge a partir de un modelo de ¿Polya?

No hay que perder de vista el modelo que está atras del algoritmo, ya que nos puede brindar una visión mas amplia de como funciona ese algoritmo.

---

# CHARLA FINAL

La evolución de los productos no es continua. 
Aproximadamente hay un aumento en la demanda de proyectos a medida. Un 22,5% de crecimiento.
Hay mucho miedo con respecto a "la informática o computación no sirve mas", pero según el gráfico planteado, siempre habrá proyectos, y para el 2028 se prevee una explosión de los mismos, y habrá que saber hacerles frente adaptándonos a las tecnologías de ese entonces.

**¿Cómo evolucionan los productos?** 


Duda:
- ¿Qué es Greenfield? Producto que se comienza a desarrollar desde cero. También existen los productos Brownfield (sistemas heredados) y Bluefield (mezcla entre brownfield y greenfield para migrar solo lo que sea útil).

---

**Miércoles 12 de agosto**

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

# Destilación de Modelos Multilingües para la Detección de Sesgo de Género con Pocos Ejemplos en Textos Judiciales en Español: Una Revisión Sistemática de la Literatura




---

# Evaluación de modelos de lenguaje locales en un sistema RAG para asistencia educativa



---

# Evaluación Experimental de Estrategias de Retrieval en Arquitecturas RAG Aplicadas al Dominio Judicial



---

# Not All Instructions Are Forgotten Equal

Es normal que cuando un agente tiene la ventana de contexto disponible, sea mas lúcido. Si le digo cosas como "no me des la razón siempre", etc, lo hace. Estas cosas las mantiene.
Luego de su utilización durante un tiempo, la ventana se satura y empieza a ser mas lenta.

1. El problema
2. Metodología
3. Resultados
4. Por qué importa?

A Closer look at System Prompt Robustness, Mu et al. 2025. 
**Bambi, ArviZ y PyMC**
Statistical Rethinking, 12.3.3. Richard McElreath (2020)

BKT (Bayesian Knowledge Tracing) -> Medir cuando un alumno está por caer en su rendimiento
Hay instrucciones a las que un modelo les da mucha mas prioridad, y a otra las retiene, es decir, no les da la misma atención que a otras. Medir por instrucción habilita monitoreo selectivo.
Los modelos se dan cuenta cuando los estan evaluando o testeando y cambian su comportamiento. Para evitar esto, se implementaron diferentes técnicas.
