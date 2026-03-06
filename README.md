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

b: Comando para “caminar” el árbol MIB del router

Se puede usar el comando:

snmpwalk -v2c -c public 192.168.1.1

Este comando utiliza SNMPv2c, la comunidad public y permite recorrer (walk) el árbol MIB del router para obtener todos los valores de sus interfaces.

2. Evento que provoca el trap authenticationFailure

Este trap ocurre cuando un dispositivo intenta acceder al router con una comunidad SNMP incorrecta o no autorizada.

3. Ventaja de recibir un Trap en lugar de usar polling

La ventaja es que el router envía la alerta automáticamente cuando ocurre el evento, lo que:

Reduce tráfico de red

Permite detectar problemas inmediatamente

Evita consultas constantes del gestor SNMP.


<img width="641" height="505" alt="image" src="https://github.com/user-attachments/assets/be28327d-7f9a-478f-892f-7e95a1985aad" />
<img width="621" height="294" alt="image" src="https://github.com/user-attachments/assets/aa42edc1-1d92-41a2-a9d1-4d019f66fc99" />
Paso 1: Verificación de conectividad básica y resolución de nombres
1. Comando para verificar conectividad con GitHub
Comando:
ping github.com
Qué verifica:
Este comando comprueba si el equipo tiene conectividad IP con el servidor de GitHub.
Protocolo utilizado:
Utiliza ICMP (Internet Control Message Protocol).
Capa del modelo OSI:
Capa 3 – Red
Qué ocurre:
Se envían paquetes ICMP Echo Request al servidor y este responde con Echo Reply si hay conectividad.

2. Cómo obtiene el equipo la dirección IP de github.com
Cuando escribes github.com, el sistema realiza una resolución DNS para convertir el nombre de dominio en una dirección IP.
Proceso:
El equipo consulta al servidor DNS configurado.
El DNS busca la IP asociada al dominio.
El servidor responde con la dirección IP de GitHub.
El equipo ya puede comunicarse con ese servidor.
Protocolo utilizado:
DNS (Domain Name System)
Capa OSI:
Capa 7 – Aplicación
Estructuras de datos que viajan:
Paquetes IP
Segmentos UDP (generalmente puerto 53)
Comando para verificar DNS:
nslookup github.com
Si falla la resolución DNS se puede usar:
nslookup github.com
o revisar el DNS configurado con:
ipconfig /all


3. Latencia alta pero ping exitoso
Si el ping responde pero con latencia alta y variable, la métrica afectada es:
Latencia y Jitter
Impacto en git push:
El envío de datos será más lento
Puede haber retransmisiones de paquetes
El throughput (velocidad efectiva) disminuye
El git push puede tardar más tiempo o incluso fallar si la red es muy inestable

<img width="964" height="507" alt="image" src="https://github.com/user-attachments/assets/9ea7a446-aac2-4c60-b908-b47844395e55" />
Paso 2: Establecimiento de la conexión para el push
1. Protocolo de transporte y establecimiento de conexión
El protocolo de transporte que se utiliza es TCP (Transmission Control Protocol).
TCP establece una conexión confiable mediante el proceso llamado Three-Way Handshake:
SYN:
El cliente (tu computador) envía un segmento SYN al servidor de GitHub para iniciar la conexión.
SYN-ACK:
El servidor responde con SYN-ACK, aceptando la solicitud.
ACK:
El cliente responde con ACK, confirmando la conexión.
Después de este proceso, la conexión queda establecida y Git puede comenzar a enviar los datos del git push usando HTTPS.
Capa OSI:
Capa 4 – Transporte
Estructura de datos:
Segmentos TCP

2. Herramienta para observar los segmentos TCP
La herramienta que se puede usar es Wireshark.
Filtro para ver solo tráfico hacia GitHub:
ip.addr == IP_DE_GITHUB
Ejemplo si la IP fuera 140.82.114.4:
ip.addr == 140.82.114.4
También se podría usar un filtro más específico para HTTPS:
tcp.port == 443
Esto permite observar los segmentos TCP intercambiados durante la conexión.

3. Puertos origen y destino en la cabecera TCP
Puerto destino típico:
443 (HTTPS)
Puerto origen:
Puerto efímero generado por el sistema operativo
(generalmente entre 49152 – 65535).
Ejemplo:
Campo	Valor
Puerto origen	52344
Puerto destino	443
Capa del modelo OSI que gestiona los puertos:
Capa 4 – Transporte.

<img width="943" height="487" alt="image" src="https://github.com/user-attachments/assets/a2803546-d460-4c8a-9c34-b734572eff76" />
Paso 3: Encapsulamiento y enrutamiento de los datos
1. Proceso de encapsulamiento desde Git hasta la trama Ethernet
Cuando haces un git push, los datos (archivos, commits, mensajes, etc.) pasan por las capas del modelo de red (modelo TCP/IP / OSI). En cada capa se encapsulan agregando cabeceras.
1. Capa de Aplicación
Aquí trabaja Git, normalmente usando HTTP/HTTPS o SSH.
Los datos aún son simplemente datos de aplicación.
PDU: Datos o mensaje.

2. Capa de Transporte
Se utiliza TCP porque Git necesita transmisión confiable.
TCP divide los datos en partes más pequeñas.
Agrega puertos origen y destino, número de secuencia, control de errores, etc.
PDU: Segmento TCP.

3. Capa de Red
El segmento TCP se encapsula dentro de un paquete IP.
Se agregan:
Dirección IP origen
Dirección IP destino
Aquí es donde los routers pueden encaminar los paquetes.
PDU: Paquete IP.

4. Capa de Enlace de Datos
El paquete IP se encapsula en una trama Ethernet.
Se agregan:
Dirección MAC origen
Dirección MAC destino
FCS (control de errores).
PDU: Trama Ethernet.
Resumen de PDU por capa
Capa	PDU
Aplicación	Datos / Mensaje
Transporte	Segmento (TCP)
Red	Paquete (IP)
Enlace	Trama (Ethernet)

2. Router congestionado y pérdida de paquetes
Si un router se congestiona y empieza a descartar paquetes, el git push se verá afectado porque algunos segmentos TCP no llegarán al destino.
Mecanismo TCP que se activa
El mecanismo es retransmisión de TCP, que ocurre cuando:
El receptor no envía ACK.
O llegan ACK duplicados.
TCP activa mecanismos como:
Retransmisión
Control de congestión
Fast Retransmit
Congestion Window Reduction
Esto reduce la velocidad de envío para evitar más congestión.
Efecto visible:
El git push se vuelve más lento.
Puede parecer que se queda congelado temporalmente.
Comando para identificar en qué salto se pierden paquetes
El comando es:
traceroute github.com
o en Windows:
tracert github.com
Este comando muestra cada router (salto) por el que pasan los paquetes y permite detectar:
alta latencia
pérdida de paquetes
dónde se interrumpe la comunicación

3. Campo que evita que un paquete dé vueltas infinitas
El campo es TTL (Time To Live) en la cabecera IP.
Funcionamiento
TTL es un contador numérico (por ejemplo 64 o 128).
Cada router que procesa el paquete resta 1 al TTL.
Cuando el TTL llega a 0, el router:
descarta el paquete
envía un ICMP Time Exceeded al origen.
Objetivo
Evitar que los paquetes circulen indefinidamente en caso de:
bucles de enrutamiento
errores en tablas de routing
Git genera datos de aplicación.
TCP los encapsula en segmentos.
IP los encapsula en paquetes.
Ethernet los encapsula en tramas.
Si hay congestión:
TCP activa retransmisión y control de congestión.
Para detectar pérdidas:
usar traceroute / tracert.
Para evitar bucles:
se usa el campo TTL en la cabecera IP.
<img width="906" height="476" alt="image" src="https://github.com/user-attachments/assets/c6927c47-c071-4c16-a8f3-7306c938dc00" />
Paso 4: Confirmación y fin de la comunicación
1. Mensaje TCP que confirma la recepción de datos
GitHub confirma la recepción correcta de los datos mediante mensajes TCP ACK (Acknowledgment).
Cada vez que el receptor (GitHub) recibe correctamente un segmento TCP, envía un ACK indicando el siguiente número de secuencia esperado.
Esto le dice al emisor que los datos llegaron correctamente.
Relación con pérdida de paquetes y fiabilidad
TCP es un protocolo confiable porque utiliza:
ACK (Acknowledgments)
Confirman que los datos llegaron correctamente.
Números de secuencia
Permiten reordenar datos si llegan fuera de orden.
Retransmisión
Si el emisor no recibe un ACK dentro de un tiempo, asume pérdida de paquete y retransmite el segmento.
Gracias a estos mecanismos, TCP garantiza fiabilidad en la transmisión, incluso si algunos paquetes se pierden en la red.

2. Cierre ordenado de la conexión TCP
Cuando el git push termina, TCP realiza un cierre de conexión en cuatro pasos (four-way handshake):
1️⃣ FIN
El cliente envía un segmento FIN indicando que terminó de enviar datos.
2️⃣ ACK
El servidor responde con ACK confirmando el FIN.
3️⃣ FIN
El servidor también envía su propio FIN cuando termina de enviar datos.
4️⃣ ACK
El cliente responde con ACK final.
Flujo simplificado:
Cliente → FIN → Servidor
Cliente ← ACK ← Servidor
Cliente ← FIN ← Servidor
Cliente → ACK → Servidor
Esto asegura que ambos lados terminaron de transmitir datos correctamente.

3. Métricas SNMP para monitorear el tráfico del push
Si fueras administrador de red, en el agente SNMP del router de salida podrías observar métricas como:
Tráfico de red
Bytes transmitidos (ifOutOctets)
Bytes recibidos (ifInOctets)
Paquetes
Paquetes transmitidos (ifOutUcastPkts)
Paquetes recibidos (ifInUcastPkts)
Errores y congestión
Paquetes descartados (ifOutDiscards / ifInDiscards)
Errores de transmisión (ifOutErrors / ifInErrors)
Estas métricas permiten identificar:
saturación del enlace
pérdida de paquetes
errores de interfaz

4. Versión de SNMP para consultas cifradas
La versión adecuada es SNMPv3.
SNMPv3 agrega:
Autenticación
Cifrado (encryption)
Control de acceso
Esto protege la información de monitoreo contra interceptación o manipulación.
