# primer-parcial-
<img width="943" height="446" alt="image" src="https://github.com/user-attachments/assets/da0caf8f-b373-428b-89ca-f3b65cddde91" />
<img width="881" height="452" alt="image" src="https://github.com/user-attachments/assets/82bc5c4e-3ed4-4774-be43-fa9d13b9b44d" />

A: La latencia es el tiempo que tarda un paquete en ir desde el origen hasta el destino, es decir, el retraso total en la comunicación.
El jitter es la variación en el tiempo de llegada de los paquetes, o sea, cuando los paquetes no llegan de forma constante sino con diferencias irregulares entre uno y otro.
En una llamada VoIP, el jitter tiene un impacto más negativo, porque la voz necesita un flujo continuo y uniforme. Si los paquetes llegan con variaciones, el audio se escucha cortado, distorsionado o entrecortado. La latencia alta solo genera retraso en la conversación, pero el jitter afecta directamente la calidad del sonido.


B:En la transmisión de video, UDP es más eficiente en términos de throughput, porque tiene una cabecera más pequeña y no necesita establecer conexión ni enviar confirmaciones (ACK). Al no retransmitir paquetes perdidos ni aplicar control de congestión tan estricto, envía datos más rápido y con menor sobrecarga.
Por otro lado, TCP ofrece mayor control de la pérdida de paquetes, ya que establece conexión, utiliza números de secuencia, confirma la recepción de datos (ACK) y retransmite los paquetes que se pierden. Además, implementa mecanismos de control de flujo y congestión.


C:El protocolo que llena la tabla mostrada con el comando arp -a es ARP, cuya función principal en una red local es asociar direcciones IP con direcciones MAC. Esta relación es necesaria porque la comunicación dentro de una LAN se realiza mediante tramas Ethernet que utilizan direcciones físicas (MAC), mientras que las aplicaciones y el protocolo IP trabajan con direcciones lógicas (IP).
ARP permite que un equipo obtenga la dirección MAC correspondiente a una IP destino antes de enviar los datos. De esta manera, el paquete IP puede encapsularse correctamente dentro de una trama Ethernet, completando los campos de dirección MAC origen y destino.
En términos técnicos, ARP facilita la interacción entre la Capa 3 (Red) y la Capa 2 (Enlace de datos), garantizando que los datos puedan transmitirse correctamente dentro de la red local


d: Seguridad
•	SNMPv2c utiliza un mecanismo básico de autenticación mediante community strings (texto plano), sin cifrado ni protección contra interceptación.
•	SNMPv3 incorpora autenticación fuerte (usuario y contraseña), cifrado de datos (encriptación) y control de integridad, ofreciendo mayor seguridad.
2️⃣ Tipo de mensajes y control
•	SNMPv2c maneja operaciones como Get, Set, GetNext, GetBulk y Trap, pero sin mecanismos de seguridad integrados en los mensajes.
•	SNMPv3 maneja los mismos tipos de operaciones, pero añade encabezados y parámetros de seguridad (autenticación, privacidad y control de acceso basado en usuarios), permitiendo modos como noAuthNoPriv, authNoPriv y authPriv.


e: Un OID (Object Identifier) es un identificador único numérico que representa una variable específica gestionada por SNMP. Los OID están organizados jerárquicamente y forman parte de la MIB (Management Information Base), que es la base de datos estructurada donde se definen y describen todos los objetos administrables de un dispositivo de red.
Si un administrador quiere conocer la cantidad de bytes recibidos por una interfaz de red, debe utilizar la operación Get, porque esta permite consultar el valor actual de una variable específica (OID) en el dispositivo.
No sería adecuado usar un Trap porque un Trap es un mensaje enviado de manera automática por el dispositivo hacia el administrador cuando ocurre un evento específico. No sirve para solicitar información bajo demanda, sino para notificar eventos.

<img width="947" height="504" alt="image" src="https://github.com/user-attachments/assets/efbec7f6-65fb-4fe6-9ef0-e51ff9ebaf3d" />
<img width="879" height="176" alt="image" src="https://github.com/user-attachments/assets/b12b38e1-2dc9-4d1a-93c7-583aa298be93" />

a: La cabecera Ethernet II está compuesta por tres campos principales:
1.	Dirección MAC destino: identifica el dispositivo receptor dentro de la red local.
2.	Dirección MAC origen: identifica el dispositivo que envía la trama.
3.	Campo Tipo (EtherType): indica qué protocolo de capa superior está encapsulado en la trama.
El valor 0x0800 en el campo Tipo significa que la trama transporta un paquete del protocolo IPv4.


b:Análisis de la cabecera IPv4
•	Campo Protocolo (Protocol): Indica el protocolo de nivel superior (Capa de Transporte) al que deben entregarse los datos del paquete una vez procesada la cabecera IP.
o	En este caso: El valor es 6, lo cual identifica que el protocolo encapsulado es TCP.
•	Campo TTL (Time To Live): Es un contador que limita la vida útil del paquete en la red para evitar que circule indefinidamente. Cada router que procesa el paquete resta, como mínimo, una unidad a este valor.
o	En este caso: El valor inicial es 128.
________________________________________
Importancia del TTL en la red
El TTL es fundamental por dos razones principales:
1.	Prevención de bucles infinitos: Si un paquete entra en un bucle de enrutamiento (debido a tablas de rutas mal configuradas), el TTL llegará eventualmente a 0. En ese momento, el router descarta el paquete, evitando que congestione la red para siempre.
2.	Diagnóstico de red: Es la base de herramientas como traceroute, que manipulan este valor para identificar cada salto (router) en el camino hacia un destino.


c:Análisis de la cabecera TCP
En la cabecera del segmento TCP, los campos mencionados cumplen las siguientes funciones:
•	Flag ACK (Acknowledgment): Indica que el campo "Acknowledgment Number" es válido. Su función principal es confirmar la recepción de paquetes de datos previos enviados por el otro extremo de la conexión.
•	Flag PSH (Push): Solicita al receptor que pase los datos directamente a la aplicación de destino de forma inmediata, sin esperar a que el búfer de recepción se llene. Es común en tráfico interactivo como HTTP para agilizar la carga de la página.
•	Puerto Destino 80: Este valor identifica el servicio al que se intenta acceder en el servidor. El puerto 80 es el puerto estándar y reservado para el protocolo HTTP (HyperText Transfer Protocol), indicando que se trata de una solicitud de navegación web no cifrada.


d:Cabecera Transición a IPv6
•	de reemplazo: La cabecera IPv4 de longitud variable (mínimo 20 bytes) sería reemplazada por la Cabecera Fija de IPv6, que tiene un tamaño constante de 40 bytes.
•	Mejora notable en el procesamiento: La eliminación del campo Checksum (suma de comprobación) en la cabecera IPv6.
 En IPv4, cada router debe recalcular el Checksum cada vez que decrementa el TTL, lo que consume ciclos de CPU. En IPv6, se asume que las capas superiores (como TCP/UDP) y la capa de enlace ya realizan sus propias comprobaciones de error, permitiendo que los routers conmuten los paquetes de forma mucho más rápida y eficiente.

<img width="936" height="325" alt="image" src="https://github.com/user-attachments/assets/250d32cb-3776-44c7-a028-fc4a4dc3e219" />
<img width="882" height="288" alt="image" src="https://github.com/user-attachments/assets/7ba685c6-0da5-4808-a15d-9db290fd5bca" />


a: Análisis de la Cabecera TCP
•	Flag ACK (Acknowledgment): Indica que el número de acuse de recibo es válido. Su función es confirmar al emisor la recepción exitosa de datos previos.
•	Flag PSH (Push): Solicita al sistema receptor que entregue los datos a la aplicación de forma inmediata sin esperar a llenar el búfer de entrada.
•	Puerto Destino 80: Identifica que el paquete está dirigido a un servidor HTTP (tráfico web estándar sin cifrar).
________________________________________
 Transición a IPv6
•	Cabecera de reemplazo: La cabecera IPv4 sería sustituida por la Cabecera Fija de IPv6, la cual tiene un tamaño constante de 40 bytes.
•	Mejora en el procesamiento: La eliminación del campo Checksum (suma de comprobación) en la cabecera de red.
•	Razón técnica: En IPv4, cada router debe recalcular el Checksum tras modificar el campo TTL (o Hop Limit). Al eliminarlo en IPv6, se reduce la carga computacional en los routers intermedios, agilizando el reenvío de paquetes.
________________________________________
 Comando pathping 8.8.8.8 en Windows
Este comando es una herramienta de diagnóstico que opera en tres niveles:
1.	Información proporcionada:
o	Muestra la ruta completa (saltos) hacia el destino, similar a tracert.
o	Proporciona estadísticas de latencia y, crucialmente, la pérdida de paquetes por cada nodo individual.
2.	Proceso de ejecución:
o	Fase de Descubrimiento: Identifica todos los routers en la ruta usando paquetes con TTL incrementales.
o	Fase de Análisis: Una vez detectada la ruta, envía ráfagas de pings a cada salto durante un periodo determinado (normalmente 250 segundos).
o	Fase de Informe: Calcula el porcentaje de pérdida en cada router para determinar con precisión en qué punto de la red existe una falla o saturación
