
### Lunes 10/8
# DistLearn: Entrenamiento de orden cero descentralizado por capas mediante descenso de coordenadas por bloques, basado en teoría de juegos.

Filtrado de partículas y teoría de juegos -> fundamento para el algoritmo.
Cada capa es una función o un jugador. Asociado al mismo está el espacio donde viven sus coeficientes. 
Si tengo 2 partículas o dos configuraciones para una capa y miro la diferencia encontrada de verosimilitud, la diferencia que veo en la red completa es la misma que veo en las capas. Una mejora que produce una capa, es una mejora que se va a reflejar completamente en toda la red. Esto me permite ir por turnos mejorando cada capa. 
Se adotpa una distribución Cauchy como función de verosimilitud. DistLearn no estima el gradiente, pero se puede planear.

DistLearn sufre de la explosión de la dimensionalidad, pero esta explosión es independiente de la profundidad de la red. Está limitada a la cantidad de parámetros de cada etapa.
La cantidad de partículas ayuda a la convergencia.

La idea del algoritmo es su utilización para redes neuronales no tan grandes (o eso entendí yo al menos).

**Términos desconocidos:**
- Equilibrio de Nash.
- ADAM (en python)
- Distribución Cauchy

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

Lovelytics es una empresa consultora de datos e inteligencia artificial. Ayuda a empresas a definir sus estrategias de datos.
