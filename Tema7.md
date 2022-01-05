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
  - Se basa en clave secreta  

## No repudio
- protege contra usuarios que niegan falsamente que enviaran o recibieran un mensaje. Permite demostrar que un evento o acción ha tenido lugar.
- Es necesario la integridad del mensaje.

