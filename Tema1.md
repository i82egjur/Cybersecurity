
# Una perspectiva sobre seguridad en sistemas de información
## Tema 1: Sistemas distribuidos. El modelo de seguridad

### Definición de sistema
- Grupo de entidades que interaccionan entre sí y forman un todo unificado
- Rodeado e influenciado por su entorno
- Descrito por su propósito, estructura y fronteras

### Sistema de información
#### Definición
- Sistema organizado para la coleccion, organización, almacenamiento, tratamiento y comunicación de información.
#### Peligros
- Con el uso universal de las redes, todo sistema es potencialmente distribuido
- Cualquier dispositivo depende de alguna forma de conectividad. Lo que trae muchos riesgos potenciales

### Sistema distribuido
#### Definición: 
Varios componentes que se ejecutan en diferentes ordenadores interconectados y coordinados por un objetivo común.
#### Componentes: 
Elementos que forman el sistema, comparten red, se comunican y coordinan mediante el paso de mensajes
#### Caracteristicas
- Concurrencia 
- Carencia de reloj global
- Heterogeneidad de componententes y entornos de ejecución
- Carácter abierto
- Escalabilidad
- Fallos independientes
#### Objetivos
Mejorar la eficiencia y compartir recursos


### Tipos de modelos
1. Modelo arquitectónico
2. Modelo de interacción
3. Modelo de fallos
4. Modelo de seguridad

#### Modelos arquitectónicos
- Cliente-servidor
- Cliente-multiples_servidores
- Servidores proxy y cachés
- Sistemas multicapa (MVC)
- P2p
- Grid computing
  - Menor acoplamiento
  - Más heterogéneo
  - Más dispersión geográfica.
##### Cloud computing
- Trabaja donde sea, como sea y con cualquier servicio
- Movil y sin cables cuando y donde sea
- Computación basada en la nube hace dificil distinduir entre red interna o externa
- Los servicios son IaaS, PaaS and SaaS
  - En un software cualquiera, tu lo gestionas todo, red, almacenamiento, ....
  - En un IaaS, solo gestionas el so y lo que corre encima de este
  - En un PaaS, solo gestionas la aplicacion y la información
  - En un SaaS, no gestionas nada
-  Problemas 
  - Los problemas de seguridad, aparecen porque la gente y los servicios, pueden estar fuera del perimetro de la red de la organización
  - Los problemas de seguridad aparecen porque la gente usa sus propios dispositivos dentro y fuera de la red de la organización
  - La allianza de seguridad de la nube, es la principal gobernanza para los estandars de la nube.
- Responsabilidades
  - IaaS -> el proveedor es responsable de la conectividad, hardware, facilities, cliente -> responsable de la info y el software
  - PaaS -> Proveedor asume la responsabilidad del middleware
  - SaaS -> El proveedor asume responsabilidad completa     
- Preocupaciones
  - Donde esta la información y de quien es
  - Infraestructura compartida con empresas -> control de aceso granular
  - Regulación diferente en cada pais
  - Alinear politicas de seguridad con el servicio de cloud
  - Que conocimiento se requiere al personal
  - Cuales son los atributos de recuperacion de desastre
  - Que controles CIA hya
  - La seguridad esta negociada en el acuerdo de nivel del servicio?
  - Procedimientos ante un incidente
  - Contigencias ante fallo del proveedor
##### Dispsitivos móviles
- Todo puede tener un pequeño computador conectado a la red.

#### Repercusiones de modelos arquitectónicos
- Cada modelo define una forma de distribución del trabajo entre componentes y tiene impacto sobre factores como la seguridad.

### Despliegue
- Diferentes modelos
  - Servidor propio
  - Centro de datos or computer center
  - Cloud computing 

#### Impacto despliegue
- Impacta sobre muchas cosas y por supuesto seguridad y privacidad



## Modelo de interacción
- Cuanto más compleja sea la comunicación, más vulnerabilidades puede tener, al haber entre otras cosas, más canales que controlar
- En una interacción, siempre hay un proceso a, que envía sincrona o asíncronamente, un mensaje o un stream, y que puede quedar o no bloqueado hasta que a otro proceso b le responda, a través de un canal con un ancho de banda, un latencia y unos retardos.

## Modelo de fallos
- Como gestiona el sistema los fallos. 
- Pero primero, que significa que falle el sistema. 
- Por ejemplo, si a quiere enviar un mensaje a b, puede ocurrir, que b no responda o que no llegue el mensaje, lo cuál sería un fallo por omisión de la respuesta. Que esta respuesta tarde demasiado, lo cual sería un fallo por temporización, timeout o cualquier otro fallo, que a priori no sabemos porque pasa, fallo arbitrario.
-  Estudiar esto, es importante, para crear servicios y contramedidas por si algo de esto pasa.

## Modelo de seguridad

- En un sistema distribuido, su seguridad depende mucho de la propia arquitectura de este, pero es imprescindible, la creación de un modelo de seguridad que describa las posibles amenazas y soluciones. Este depende mucho de la política de seguridad, de esta forma, dependiendo de esta será más o menos completo.
- Hemos dicho que el modelo de seguridad describe amenazas, pero cuales son estas amenazas:
- Pueden haber amenazas a los procesos, a los canales de comunicación o a los recursos que gestionan y comparten.
- Por tanto, el modelo de seguridad, se basa en emodelas al enemigo, desde las etapas iniciales del desarrollo, y modelar medidas de seguridad o contramedidas.
- Este es un componente de obligatorio uso más, sin embargo a veces no se tiene en cuenta.

## Modelo de red
- En su interacción, los modelos usan redes para comunicarse, que son susceptibles a ataques y hay muchos tipos de redes, protocolos, modelos, como el modelo osi.
- Ataques genéricos, como escuchas, suplantación, modificación, DoS
