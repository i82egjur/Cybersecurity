


# Protocolos de seguridad

- Internet no fue diseñada con la seguridad en mente, los protocolos tcp/ip como tal no poseen ningún tipo de seguridad inherente. Para 
tratar con esto, tenemos ciertos protocolos que refuerzan la seguridad, estos son SSL/TLS Secure Sockets Layer, Transport Layer Security
IPsec, Internet Protocol Security, SSH, secure shell, sftp, Secure File Transfer Protocol

## SSL/TLS
- El objetivo de tls, es proporcionar privacidad e integridad entre 2 aplicaciones que se comunican, esto se consigue mediante la encriptación
end-to-end, la autenticación de cliente y servidor y la comprobación de integridad. Es un protocolo de nivel de aplicación y generalmente
se usa en web, pero se puede usar en cualquier aplicación que lo requiera. Durante su historia ha ido actualizarse, y cambiandose de nombre,
acualmente, la versión más actualizada de ssl, es tls, The transport layer security, aunque se suelen poner juntos. El objetivo, ha cambiado
poco, siendo este proveer un canal seguro para la comunicación de pares, de manera que se cumpla con la triada cia.

- La conexión entre cliente y servidor se establece termporalmente a partir de la sesión que es una asociación entre el cliente y el servidor.
para establecer esta, cliente y servidor tienen que negociar hasta que se termine el trato y estén de acuerdo, handshake (apreton de manos).
Este handshake se establece de la siguiente forma, el cliente manda un mensaje al servidor, y estos acuerdan la version del protocolo a usar, 
una vez tienen un acuerdo en este, acuerdan el algoritmo de encriptación a usar. Una vez hecho esto, mediante la emisión de sus certificados
se comprueban que o bien solo el servidor o bien el cliente y el servidor son quienes dicen ser. Una vez haya una cierta confianza entre ambos,
Mediante la encriptación asíncrona, acuerdan una clave sincrona, por ejemplo con diffie-helman + rsa. Con esta clave que solo ellos conocen
proceden a cifrar/descifrar los mensajes del otro de manera sincrona, que es mucho más rápida que la asíncrona.

- Generalmente se usa para web, y se mezcla con http creando https, pero también se puede usar en cualquier aplicación que lo necesite.


## IP sec
- Ip security protocol
- Está definido por un estandard abierto de IETF, Provee, autenticación, integridad y privacidad entre 2 entidades ip
- Se implementa a nivel de kernel sobre la capa IP, usa encriptación simétrica, que usa IKE, Internet Key Exchange para intercambiarse las claves de forma segura.
- Es similar a ssl/tls, e excepción de que ssl se implementa en la capa de aplicación y es algo más fácil de usar, pero ip sec es más seguro.
- El objetivo es securizar cualquier aplicación, de manera que se de Autenticación, control de acceso, integridad, confidencialidad, protección, y flexibilidad.
- Esta compuesto de 2 protocolos, un Authentication header (AH), garantiza integridad y autenticación. y un ESP, Encapsulating Security Payload, garantiza confidencializad, aunque también integridad y confidencialidad, al ser cifrado de forma simétrica. Así como 1 método de intercambio
seguro de claves, ISAKMP, Internet Security Association Key Management Protocol. 
- Ipsec tiene 2 modos de operación
  - Transporte y tunel. Las diferencias son el nivel de protección que aportan, en transporte, se securizan los datos, en tunel se securiza todo el paquete ip original, encapsulandolo en otro paquete ip.


## SSH
- Su nombre refleja muchas cosas, comando, empresa un protocolo.
- Conversación completa encriptada, incluida las autenticaciones de usuario, ssh, tras establecer una conexión, se usa como túnel para cualquier otra conexión TCP. Su seguridad radica en que cliente y servidor negocian, algoritmos de encriptación, metodo de intercambio de claves, mecanismos de comprobación de integridad. Es similar a ssl/tls, tanto que la v2 de ssh lo implementaba. El servidor controla los tiempos cambiando los parámetros cada cierto tiempo.    
