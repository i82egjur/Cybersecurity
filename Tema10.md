


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
