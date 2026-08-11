
# Enhancing Cybersecurity Resilience in SMEs: A Governance Model for Third-Party Risk and AI-Enabled Services


# Security Analysis of SSL/TLS Configuration Gap in Django-Based Industrial Embedded Systems: A Code-Level Assessment

TLS versión 1.3 se usa actualmente, anteriormente era solo SSL

Bandit 1.7 -> Herramienta para analizar archivos Python -> NO analiza los archivos .conf

OWASP ZAP 2.14 -> Herramienta que sirve como proxy para confirmar si las configuraciones son correctas o no.
CVSS v3.1 sirve para analizar qué tan potente  o maligno es un ataque

La evaluación de seguridad arrojó que el ataque tiene un puntaje de 6.5 -> Medio

# THE SEGURANDO: "Técnicas de Hacking Ético" y "Seguridad en Android"

El contexto inicial de la charla explica que los celulares contienen credenciales bancarias, tokens 2DA, y datos personales, lo cual hace que se conviertan en el objetivo principal de los atacantes.

**Factor humano:** La ingeniería social aprovecha la confianza del usuario mediante mensajes de phishing para eludir los filtros iniciales de seguridad del sistema.
**Confianza en Hardware:** El sistema operativo confía por defecto en todos los periféricos de entrada conectados por USB, abriendo una ventana de ataque físico no autenticado

Se generó un entorno controlado para simular los distintos vectores de ataque hacia los dispositivos móviles.

**Escenario 1: Phishing y APK Maliciosa** Creación de una página web falsa (Spoofing).
**Ingeniería Social (Phishing):** Redirección de la víctima a una página web falsa.

Para hacer estas páginas se usaron varias herramientas: Una fue FACA (o algo así). 

**Meta exploit**

**Escenario 2: Inyección HID con Raspberry** 

1. Preparación de entorno: Configuración de una raspberry pi pico w para emular un teclado USB legítimo.
2. Ingeniería social (Juice Jacking)
3. Ataque silencioso y automatizado
4. Posible impacto

**Atom Ducky**

**Android** permite descargar apps inseguras desde google play. A lo suma avisa de esta inseguridad, pero permite su descarga y no la bloquea.

---
# Adquisición forense móvil de baja intrusión en campo: un enfoque operativo para la recolección selectiva de evidencia digital.

Las herramientas diseñadas para extracción completa son muy costosas y por lo general, extranjeras.
CAPTA: 
- Herramienta de triaje: Se enfoca en la obtención en campo de información de alto valor en forma rápida trazable desde celulares Android.
- Ventajas: La inmediatez en la obtención de la información permite que la misma sea utilizada en la toma de decisiones investigativas.
- Método de documentación:  Permite que los PEP extraídos cueten con respaldo documental verificable (reporte PDF, hashes y actas) listo para el expediente. Para la justicia, si no hay documentación entonces no hay pruebas.
- Complemento al laboratorio: Funciona como etapa previa de selección de dispositivos y extracción de baja intrución, para descongestión del laboratorio.

**Principios del modelo:**
- Mínima intervención y preservación
- Selectividad e integridad verificable
- Trazabilidad completa
- Detectabilidad como garantía explícita

**Arquitectura de CAPTA:**
- Interfaz y coordinación
- Núcleo forense
- Parsers y documentación

---

# Integración de modelos de IA para la identificación de Información de Identificación Personal (PII) en el marco de las Regulaciones vigentes de la República Argentina

PII: Es cualquier dato que se puede usar para identificar, localizar o contactar a una persona, ya sea solo o junto con otros datos. Las empresas deben protegerla para evitar robos de identidad. [[1](https://www.malwarebytes.com/es/cybersecurity/basics/pii), [2](https://caseguard.com/es/articles/proteccion-de-la-intimidad-en-el-sanitario-pii-phi-y-pci/), [3](https://www.youtube.com/watch?v=h1Q5Ze37njk), [4](https://www.youtube.com/watch?v=N1qdvQVke0s)]

Una vez que se detecta la PII, se usa el Anonymizer para aplicar la operación más adecuada según el tipo de entidad y el contexto de uso.

**Modelo SpaCy: Modelo entrenado en idioma español**

---

# Criptografía programable para la preservación de privacidad en protocolos blockchain

Privacidad en protocolos de verificación blockchain: Toda la inforamción solicitada (por lo general, excede lo que realmente se necesita o se piden datos de mas) queda guardada en una base de datos. Muchas empresas empiezan a aprovechar esto para tener otro accionar sobre la información de sus clientes. Toda esta información está centralizada en una empresa, lo cual es un atractivo principal para un ciberdelincuente, teniendo acceso a información sensible. 
En una blockchain todo es publico e inmutable, y por ende hay cosas sensibles. 

### **Objetivo: Blockchain con privacidad.**

¿Existe alguna herramienta para resolver este problema? Sí, la criptografía programable. 

ZK Proofs permiten demostrar algo sin revelarlo. Por ejemplo, si quiero sacar un préstamo, el banco pedirá muchísimas cosas, entre otras cosas, el sueldo que cobro. Yo no quiero que otra persona sepa cuanto cobro, entonces yo puedo mostrar legibilidad para ese préstamo pero sin decir cuanto cobro, donde vivo, etc.
En este tipo de protocolos suele existir un probador, una prueba (succinct) y un verificador (responde con si/no sobre esa prueba).

Las pruebas que se utilizaron fueron ZK - S N AR K.
Zk: Cero conocimiento
S: Sucinto
N: No interactivo
Ar: Argumento
K: Conocimiento

Estas pruebas tienen una ventaja: Son chicas y no interactivas. 

**Se menciona la propiedad de la simulabilidad**

Se plantea usar la criptografía programable para solucionar la privacidad en protocolos de verificación Blockchain.
3 elementos clave:
- EligibleIMT: Smart contract que representa un arbol incremental. 
- Circuito Noir: Lenguaje de programación.
- LocalVerifier: Otro smart contract que ve todo lo que se hace y es por local.

Poseidon2 es un algoritmo que funciona muy bien con este tipo de protocolos.
Con las pruebas se va a querer demostrar que estoy en el arbol, pero no vas a saber quién soy, por sí o por no.

Existen 3 actores:
- Operador: Encargado de administrar el contrarto ElligibleIT
- Beneficiario: Persona elegible para un beneficio
- Verificador: Contrato independiente por cada punto de verificación.

Hay un problema, el doble gasto controlado: se usa nullifier, que hace un mapeo interno para verificar que un dato ya fue consultado, o algo así, sin necesidad de conocer a la persona.

**Beneficios:**
- El beneficiario tiene control sobre su historial
- Para el operador, se elimina la responsabilid de custodiar datos personales sensibles
- Para el verificador, simplifica el cumplimiento normativo (RGPD): No acumula lo que no necesita.

