
# Detección Automatizada de Interferencias en Espectro Radioeléctrico bajo Escasez de Datos: Un Análisis Comparativo de Enfoques de Machine Learning y Reglas Determinísticas

Problema: Detección de interferencias
Las interferencias son producto de una mala operación de un equipo (en ocasiones). 
Las interferencias se detectan manualmente hoy en día. Pero, existe la posibilidad de que se haga de forma automática las 24 horas, teniendo al operario evaluando si eso es una interferencia o no?
La idea es crear un sistema que pueda monitorear el espectro de forma continua.
La idea es poblar al area geográfica con sensores, y con eso generar datos. Por el momento se tenían pocos datos, y además se quería implementar en una operación real.
El problema central fue no tener suficientes datos. Se tenían muy pocas muestras para entrenar a la IA, para lo que requería deep learning (entre 10 a la 5 o 10 a la 6 muestras). Por ende se enfocó mas en la utilización de modelos estadísticos y de machine learning tradicionales. Las reglas del dominio fueron identificar formas de onda (gaussian), pico espurio, ripple y asimetría. 
Se eligió FM porque es ubícua, y por cuestiones de tiempo también. La idea es hacerlos sobre los servicios mas críticos.

Ante la ausencia de datos se utilizó un híbrido de algoritmos.

P1, P2 y P3 se empezó con algoritmos de ML tradicional. Se esperaba una sensibilidad por encima del 90%, pero se logró aprox un 80%.
En cuanto a P6, se añadieron reglas y se mejoró la sensibilidad. Y en P7 se agregaron otras reaglas, lo cual mejoró la exactitud y la precisión.
La sensibilidad mide cuántas interferencias realmente detecté. -> Este es el que aplica mejor
La exactitud mide cuales no dejé pasar.

Los próximos pasos:
- Salir de FM e ir a SMA. Este importa por el tema de seguridad de las personas. Además, la forma de onda no tiene ni siquiera simetría, es otro tipo de ondas, por lo que habrá que cambiar el dominio espectral.
- Luego, si varios sensores detectan interferencias, se podría generar una triangulación para saber de dónde viene la interferencia y poder llamar la atención a esa persona o entidad para que baje la frecuencia.
- Si hay muchos sensores se podría reevaluar si usar un modelo de deep learning mediante redes neuronales, teniendo muchas muestras mas.

La inteligencia no está solamente en el modelo, sino también en los datos + conocimiento del dominio + ingeniería + expertos

Hubo generación de datos sintéticos, generandolos con una función o herramientas. Las interferencias reales utilizadas fueron reales, pero generadas por ellos de forma voluntaria y manual. En sí no es un dato sintético, las interferencias fueron generadas por ellos. 

**Algoritmos o reglas usadas:**
- Isolation Forest
- XGBoost
- PCA
- Distancia de Mahalanobis

**Dudas:**
- **Protocolo MQTT - HiveMQ**

---