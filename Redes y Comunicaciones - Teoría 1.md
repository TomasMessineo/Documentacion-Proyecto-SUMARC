
### ¿Qué es una red?

### ¿Qué es internet?
Internet es una red de redes, una red interconectada. Cuando digo "me conecto a internet", en realidad internet es un conjunto de redes que están interconectadas. Antes se conectaba a un equipo que permitía conectarse a internet, pero internet no es una empresa ni nada de eso, internet es la red de redes y hay distintos organismos que la "gobiernan" de alguna manera para generar este internet. Hay empresas que la controlan. 

### ¿Qué es la web?
La web es una parte de internet, no es todo internet. La web es una aplicación o capa dentro del internet

### ¿Qué pasa cuando navego por internet? ¿Qué pasa cuando accedo a Facebook o miro un video de Youtube?

---

### Red de computadoras:
Conjunto de computadoras (o dispositivos, mas en general) interconectados. Ahora en una red están interconectados dispositivos móviles, relojes, etc.
El objetivo es compartir recursos: dispositivos, información, servicios. El conjunto de computadoras, software de red, medios y dispositivos de interconexión forman un sistema de comunicación (tengo computadoras interconectadas ya sea por fibra, o o que sea interconectadas, formando un sistema de comunicación, generando un camino por el cual se puedan comunicar los equipos intercoenctados).
Ejemplos: Red de la sala de PCs, red universitaria, internet.


### Componentes de un sistema de comunicación:
- Fuente (software)
- Emisor/Transmisor (Hardware)
- Medio de transmisión y dispositivos intermedios (Hardware)
- Proceso intermedios que tratan la información (Software y Hardware)
- Receptor (Hardware)
- Destino (Hardware)
- Otros: Protocolos (Software), Información, mensaje transmitido (Software)
- Señal de información, materialización del mensaje sobre el medio (Hardware?)

Si una computadora "habla un idioma", pero la computadora receptora no entiende ese mensaje, no lo va a poder responder. Además, tengo que ver como se manda ese mensaje. Para que el sistema funcione, hay una serie de protocolos que se van a tener que cumplir para que la comunicación se realice correctamente.
**Emisor (Fuente) -> Medio + dispositivos intermedios (Fibra, via satélite, cobre, entre muchos otros) -> Receptor (Destino)**

### Componentes de una Red

Fuera del punto de vista sistémico, podemos ver un gran número de componentes:
- Computadoras, en el modelo de internet: Hosts (PCs, laptops, servidores)
- Routers/switches, Gateways, AP (Access Point)
- NIC (Placas de red). Modems.
- Vónculos/Enlaces: Conformados por:
	- Medios: Cables, fibras ópticas, señales electromagnéticas, antenas, interfaces, etc
- Programas: Browsers, Servidores Web, Clientes de Mail, Servidores de Streaming
- Etc...
Las componentes de la red deben interactuar y combinarse a través de reglas. Estas reglas, se traducen en protocolos.

**Protocolo:** El conjunto de conductas y normas a conocer, respetar y cumplir no sólo en el medio oficial ya establecido, sino también en el medio social, laboral, etc.
**En la vida real:** 
Tenes hora? -> Son las 19:45 -> Gracias
**Del lado de las redes:**
TCP connect -> Acepta TCP connect. TCP connect -> Acepta y Request: URL -> Response: Contenido -> TCP close.

Cuando un servidor recibe un mensaje que dice "TCP connect", debe saber qué responder. Esto ya está establecido, estas formas están estandarizadas. Un protocolo define el formato, el orden de los mensajes intercambiaddos y las acciones que se llevan a cabo en la transmisión y/o recepción de un mensaje u otro evento.

**Protocolo de red:** Conjunto de reglas que especifican el intercambio de datos u órdenes durante la comunicación entre las entidades que forman parte de una red. 

### Protocolos de Redes Propietarios

A principios de los 80', las empresas o compañías comenzaron a implementar redes propias (privadas y cerradas) empezó la necesidad de interconectar redes que eran propietarios. Esto surgió en el ámbito académico de EEUU. Una universidad implementaba su propia red, donde los dispositivos de su propia red podían comunicarse. Luego esto se amplió y debía comunicarse con otras universidades, dando origen al protocolo de mail. Los problemas surgieron porque cada red tenía sus propios protocolos (especificaciones propias). Ej: La universidad X implementó el protocolo de motorola, pero cuando alguien que no usaba motorola quería usar la red, esta funcionaba mal. Los resultados fueron incompatibilidad. LA comunicación entre redes era muy difícil, evolución más lenta, carencia de estándares. 

### Combinación de protocolos

Una red va a tener muchísimos protocolos, por ende se complejizó el diseño de las redes, y se empezaron a organizar las redes como un componente de modelo en capas. 
Modelo en Capas: Layering, divide la complejidad en componentes reusables. Esas capas en las que se divide el modelo, ocultan la forma de la cual está implementado, como si fueran una especie de API. En este modelo de capas, las capas superiores van a usar servicios de capas inferiores, sabiendo qué servicios brinda pero sin saber cómo los implementa. En lugar de tener un solo protocolo grande y dificil de mantener, tengo un sistema de comunicación compuesto por varios componentes, y estos van a poder evolucionar más rápido y de forma independiente. Estos cambios que hayan en cada una de las capas no deberían afectar a las capas superiores. El modelo de capas también simplifica la implementación de protocolos en sistemas.

### Modelo OSI (Open System Interconnection)

Modelo abierto y estándar, dividido en 7 capas. Es un Modelo de Referencia.
Este modelo permite entender cómo funcionan las redes y cómo se implementan los protocolos. Permite su estudio de una manera mas ordenada.
En la materia se usara el modelo TCPIP, pero es un modelo parecido a OSI.
Las capas inferiores permiten interconectar los dispositivos donde en general se brinda el contenido de la red. Para poder hacer esto, necesitamos de la implementación de protocolos de las capas inferiores.
En este modelo de capas, cada capa inferior le brinda servicios a la capa superior. Ej: La capa de sesión va a usar servicios de la capa de transporte. La comunicación va a ser peer to peer. C

Las capas de Host (Host Layers) proveen envío de datos de forma confiable.
Las capas de Medio o inferiores (Media Layers) controlan el envío físico de los mensajes sobre la red. 

Si tengo dos computadoras conectadas a una misma red, resolver el envío del mensaje de una computadora a la otra va a ser más facil que resolver la comunicación con otra computadora que está en otra red, donde en el medio el mensaje pasará por la capa de red para llegar al destino.

**Capa de aplicación (7):** Servicios de red a los usuarios y a procesos, aplicaciones
**Capa de representación/presentación (6)**: Formato de los datos
**Capa Sesión (5):** Mantener track de sesiones de la aplicación.
**Capa de Transporte (4):** Establecer y mantener canal "seguro" end-to-end (applic-to-applic)
**Capa de Red (3):** Se ocupará de hacer que el mensaje que sale de un equipo vaya a otro. Direcciona y rutea los mensajes host-to-host. Sirve para comunicar varias redes. Esto a través de la famosa dirección IP.
**Capa de Enlace de datos (2)**: Comunicación entre entes directamente conectados. Comunicar una misma red. Acceso al Medio. 
**Capa Física (1):** Transportar la información como señal por el medio físico. Características físicas. Información binaria, digital.

### Modelo TCP/IP

Modelo que se convirtió en estándar. Todo dispositivo conectado a la red tiene este modelo TCP/IP. 

¿Qué protocolos se encuentran en internet?
- Modelo abierto con varios protocolos de nivel de enlace: Ethernet, 802.3, PPP, HDLC, Frame-Relay, entre otras cosas...
- PRotocolos propios de internet y transporte (núcleo): ARP, IP, ICMP; entre otras cosas.

Es un modelo de 5 capas:
- Capa de aplicación (Process/Application): FTP, HTTP. SMTP, DNS conectados a TCP, DNS, TFTP conectados a UPD
- Capa de transporte o Host-to-host: TCP, UPD conectados a IP
- Capa de internet o internetworking: IP
- Capa de enlace (Link Layer)
- Capa Física

Por simplicidad algunos autores hablan de 4 capas, agrupando a la capa de enlace y capa física en una sola capa que llaman capa de acceso a la red.

### Encapsulamiento

Cada capa define su PDU: Protocol Data Unit. Cuando un equipo quiere comunicarse con otro, se comunica con un componente de la misma capa, pero tiene que pasar por el modelo de capas para que el mensaje llegue del otro lado, y volver a correr el modelo de capas para llegar a la misma capa a la cual le estaba hablando el emisor.
Cada capa tendrá el PDU, el componente o mensaje que va a manejar cada una de las capas. En el protocolo HTTP se habla de mensaje HTTP, cuando la app le manda un mensaje a otra app, a nivel HTTP se entenderán, pero para que el mismo llegue del otro lado, la capa de aplicación le mandará el mensaje a la capa de transporte solicitandole los servicios. Entonces, ese mensaje se va a enviar a la capa inferior y la capa inferior lo meterá en un paquete, agregandole información adicional. Cada capa le agregará información para que se sepa qué hacer ocn ese mensaje. Por ejemplo, en la capa de aplicación se envía Get, luego la capa de transporte le agregará información adicional, como el puerto de la web por ejemplo. La capa de transporte, lo que agrega lo entenderá tanto la del emisor como la del receptor. Luego, la capa de red recibirá la información y lo agrupará todo añadiendole la dirección IP. Cuando el mensaje llega al destino, se empieza a desempaquetar para saber a qué aplicación entregarselo. Llega al destino por la dirección ip, que ayuda a la red para atravesar los routers y llegar al dispositivo que corresponde. La capa de transporte me permite a qué aplicación entregarselo. 

En el libro: Encaminadores = Routers

### Clasificación de Redes:

Diferentes clasificaciones de acuerdo a diferentes aspectos
Se pueden clasificar por:
- Cobertuda, distancia, alcance
- no llegué.

- **LAN (Local Area Network):** Red de cobertura local. Ethernet, Wi-FI
- **MAN (Metropolitan Area Network):** Red de cobertura metropolitana, dentro de una ciudad. MetroEthernet, MPLS, Wi-Max
- **WAN (Wide Area Network):** Red de cobertura de área amplia. Geográficamente distribuida. PPP, Frame-Relay, MPLS, HDLC, SONET/SDH
- **SAN (Storage Area Network):** Red de almacenamiento, son como servidores pero de disco, donde hay que implementar una red para conectar los equipos de cómputo con los que no son de cómputo, ISCSI, Fibre Channel, ESCON
- **PAN:** Red de cobertura personal. Red con alcance de escasos metros para conectar dispositivos cercanos a un individuo. Bluetooth, IrDA, USB
- **Otros términos:** CAN (Controller Area Network o CAmpus Area Network), NAN (Near-me AN, NFC)



### Clasificación Públicas y Privadas

- **Internet:** Red pública global, tecnología TCP/IP
- **Intranet:** REd privada que utiliza la tecnología de internet.
- **Extranet:** Red privada virtualizada sobre enlaces WAN: Internet. Intratnet con acceso de usuarios remotos. VPN (Virtual Private Network), IPSEC, PPTP, SSL

### ¿Qué es internet?

Es una red de redes de computadoras, descentralizada, pública, que ejecutan el conjunto abierto de protocolos (suite) TCP/IP. Integra diferentes protocolos deu n nivel mas bajo: **INTERNETWORKING**. 

Internet se originó principalmente por diferentes motivos en la guerra fría. 
Internet funciona porque hay estándares. Estos estándares los hace el IETF.
RFC (Request fot Comments)

Los proveedores intercambian información (tráfico de red) con otros proveedores mediante "alianzas". Si yo me conecto a internet, la nube de internet se podría decir que está dividida en diferentes proveedores que me permiten comunicarme con la red de destino. 
