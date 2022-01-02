# Tema 4

## ¿Qué deseamos proteger?
- Nuestros datos, información, nuestros recursos, nuestra posición

## ¿Qué significa proteger?
- Según nist, proteger, es garantizar la integridad, disponibilidad y confidencialidad de los recursos de un sistema de información. Triada CIA
- Que es Disponibilidad, la propiedad de ser accesible y usable
- Confidencialidad, No dejar acceder a la información a personas no autorizadas
- Integridad. La información no debe manipularse sin consentimiento
- A estas generalmente se le añade, la trazabilidad. Poder saber quien ha hecho cualquier cosa (no repudio)

## Tipos de amenzas, ataques
- Una amenaza es un factor externo, ataque en potencia
- Una vulnerabilidad, es un factor interno, grado de exposición de un componente del sistema.
- Un ataque es el asalto real deribado sobre una amenza.

## ¿De qué queremos proteger?
- De ataques, todos atienden a una de estas categorías.
1. Destrucción de información y/o recursos
2. Corrupción/modificación de información
3. Robo, supresión o perdida de información y/o recursos
4. Revelación de información
5. Interrupción de servicios

- Dependiendo de la posición del atacante, estos pueden ser bien ataques activos o pasivos

## Tipos de atacantes.
- Ladrones, vándalos
- Joyriders, teenagers, scorekeepers
- Espías, servicios de inteligencia
- Gente aburrida
- Estupidez voluntaria, involuntaria
- No confundir con hackers.

## Defensa ante ataques
- Seguridad por ocultación, este se basa en ocultar las cosas en vez de en protegerlas, ofreciendo una falsa sensación de seguridad. No es un modelo válido
- El objetivo, es un sistema seguro
  - No solo eficiente, sino también seguro 
- Para ello, es conveniente aplicar una organización segura: ISMS (SGSI)

## Servicios de seguridad.
- Son los que demandamos para un sistema cuando necesitamos seguridad.
- Servicios básicos:
  - Autenticación
  - Control de acceso
  - Confidencialidad de datos
  - Seguridad de la comunicación
  - Disponibilidad
  - Integridad
  - No repudio
  - Privacidad 
- Cuando hablamos de servicios de seguridad, es habitual usar las siguientes referencias, CCITT REC X.800/ISO 7498-2 de 1991, descripción general
  de servicios de seguridad. ITU-T TEC X.805/ISO 18028-2 de 2003, arquitectura de seguridad para sistemas de comunicación.

- Las 8 anteriores, son dimensiones de seguridad, que son medidas a tomar según un aspecto de la seguridad considerado
- Después hay 3 capas que proporcionan la perspectiva de dónde hay que intervenir
  - Infraestructura(Dispositivios), servicios(DNS, DHCP), aplicaciones(Web, FTP de usuario..)
  
### Autenticación
- Verifica la identidad de las entidades que se van a conectar. Este servicio se extiende al lote AAA de servicios, Autenticación, autorización.
y Accounting (Seguimiento del uso y consumo de los recursos de red por los usuarios)

### Control de acceso
- Una vez hemos autenticado al usuario en AAA y determinado el nivel de acceso, debemos de garantizar que este solo va a acceder a lo que le 
está permitido

### Confidencialidad
- Protege la revelación no autorizadad deliberada o accidental de cualquier objeto

### Disponibilidad
- Los recursos están siempre accesibles bajo demanda de los usuarios autorizados

### Integridad
- El objeto no fue modificado sin autorización

### No repudio
- Protege contra usuarios que niegan falsamente que enviaran o recibieran el mensaje

### Seguridad de la comunicación
- Garantiza que la información sólo circula entre los puntos extremo autorizados

### Privacidad
- Propicia el derecho a controlar que información revelar y a quién


### Mecanismos de seguridad
- Técnicas con los que se construyen los servicios de seguridad
  - Cifrado
  - Otros elementos criptográficos
  - Firma digital
  - Control de acceso
  - Integridad de datos
  - Intercambio de autenticación
  - Traffic Padding (Insercción de birs en huecos, para que sea difícil la monitorización de transacciones)
  - Routing control (Permitir especificar rutas seguras para cierto tipo de tráfico)
  - Notarization (Uso de terceras personas o entidades que aseguren la veracidad/seguridad de las transacciones)
  - Trused functionality
  - Secutiyy label
  - Event detection
  - Security audit trail
  - Security recovery































