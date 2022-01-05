# Message authentication and hash functions

## Authentication
- Autenticar es confirmar la veracidad de los datos a todos los niveles, engloba 3 dimensiones, autenticación, integridad y no repudio.
- Este confirma la veracidad de cualquier objeto, y que viene de una entidad verdadera.

## Integridad
- Asegura que un objeto no fue modificado sin autorización.
- Tecnologías usadas
  - Encriptación simétrica
  - MAC
  - HASH
  - HMAC 

### Integridad con encriptación simétrica
- Receptor garantiza orgien ya que es con quien se comparte la clave.
- Si añadimos un error-detection code, se asegura la integridad
- Numero de secuencia, orden
- Con timestamp, se asegura fecha y hora
- Problemas
  - Es complicado gestionar las claves cuando hay más de un destino
  - Puede traer una carga computacional grande
  - Puede querer distribuir un documento y garantizar su integridad
  - Separar confidencialidad e integridad, permite más flexibilidad

### Sin encriptación
- Se basa en añadir un tag de control, no hay confidencialidad ya que el mensaje no se encripta.
  - MAC
  - HASH
  - HMAC
- MAC
  - Se basa en que tanto el emisor como el receptor tengan una clave secreta, el emisor, encripta el mensaje y añade el encriptado al mensaje a enviar, lo envía y cuando el receptor lo recive, encripta el mensaje y compara su encriptado con el recivido. Incluso, se puede comprobar si hay algun timestamp, codigos de error o números de secuencia, si se añaden. Los problemas de esto, vienen al usar ambos la misma clave, ya que es lento, además al usar la misma clave no hay no repudio.

- One way hash
  - Este solo verifica que el mensaje no ha sido alterado. Es bastante rápido, pero algo incompleto, ya que entre otras cosas, no verifica al emisor, cosa que mac si hace al tener ambos emisor y receptor la misma clave.
  - La familia más usada es sha, tanto sha-0 y sha-1, ya están comprometidos, al haberse vulnerado su seguridad. Actualmente la versión más usada es sha-256, usos bitcoin, pero esta basado en sha-1 que es vulnerable, así que ya se están buscando alternativas, sha-3. 
  - Este metodo de encriptación tiene varias particularidades, cualquier cosa que se cifre, siempre va a tener el mismo tamaño de salida, no es necesaria una clave, puesto que no se puede descrifrar, no pueden haber 2 cifrados iguales de 2 plain text distintos, y aunque se cambie un solo bit del plaintext, el cifrado va a cambiar enormemente, enorme efecto avalancha.

- HMAC
  - Los hashes solo no proporcionan autenticación, alguien podría alterar el mensaje, y el hash.
  - Podríamos usar una clave, añadirla al mensaje y calcular el hash, pero esto no es muy distinto de mac. Para hacerlo más seguro, nos
  basaremos en esta idea, pero calculando 2 hashes, para esto, necesitaremos la clave, y 2 paddings, i-pad y o-pad por ejemplo usando sha-128, tendremos que o-pad será de 64 bytes, e i-pad será <= 64 bytes. Ahora, añadiremos los i-pad primeros bytes al mensaje y calcularemos el hash, después, añadiremos a los o-pad ultimos bytes, el hash sum anterior, y volveremos a cifrar, de esta forma, tendremos una manera de permitir la autenticación, por el uso de claves, e integridad, de una manera muy eficiente, al usar los one way hash. 

## No repudio
- protege contra usuarios que niegan falsamente que enviaran o recibieran un mensaje. Permite demostrar que un evento o acción ha tenido lugar.
- Es necesario la integridad del mensaje.

