
# Seguridad perimetral

- Perimetro -> frontera fortificada de una red
- Routers, firewalls, antivirus, balanceadores de carga, vpn, nat, pat, .....

- Importante defensa en profuncidad
- Perímetro, red interna, host y factor humano, importancia de la política de seguridad

## Firewalls
- Dentro de la seguridad en profundidad, trabaja en la defensa del perímetro, es núcleo de la infraestructura de la seguridad de red, controla el acceso a la red, de esta forma elimina riesgos imprevistos, permitiendo lo que queremos y denegando lo demás.

- Para hacer esto, implementa las siguientes tecnologías, filtrado de paquetes, filtrado de paquetes con control de estado, proxy, DMZ,
VPN, NAT, otros elementos, como identificar/controlar aplicaciones, usuarios y tráfico. Nuevos conceptos como UTM y nuevas tecnologías firewall aparecen cada día.

## Tecnologías firewall
- Filtro de paquetes, screening router, control de tráfico de paquetes basado en reglas.
  - Estas reglas se establecen sobre, direcciones ips, protocolo, tipo de puerto origen/destino TCP, UDP, tipo de mensaje, ICMP, Flags y otros camplos, tamaño del paquete, interfaz donde llega/sale el paquete.

## Standard router vs screening
### Standard router
- Encamina paquete en base solo a su destino

### Screening router
- Toma de decisiones, acceptar, tirar, registrar o incluso notificar, modificar, etc.

## Filtro de paquetes
- Básico: filtrado simple, controles rutinarios
- Filtro de paquetes con estado:
  - Filtrado de 2º generación mantiene el estado de la conexión, es más potente y versatil. Analiza aspectos del interior de los paquetes y reconoce signatures, patrones, series. 
  
  - Ventajas: 1 dispositivo para toda la red, eficientes, gran diversidad/disponibilidad
  - Inconvenientes: Dificil de configurar y testear, aumenta la carga de la red, no implementa muchos aspectos de la política de seguridad, falsa sensación de seguridad. 

## DMZ
- Su nombre viene de zona desmilitarizada, los hosts dmz, son hosts más expuestos al exterior, por tanto su acceso está restringido a la red interna, y al tratarse de manera distinta que al resto de la red interna, necesita una politica de seguridad distinta de la red internza.

- A veces se diferencia entre las zonas DMZ, que se situan entre el router y el firewall, y screened subnet que simplemente son zonas que el firewall trata de manera distinta que al resto de la red, pero las trata.  

## Proxys
- La traducción de proxy es apoderado, es decir hacer alguien en nombre de alguien. Cuando usamos un proxy, este gestiona la conexión. Necesita una gateway a nivel de aplicación, a esta es a la que nos conectamos para que funcione la aplicación. La actuación del proxy puede ser o no transparente, y algunos necesitan clientes proxy, estos ejercen funciones de seguridad, y eficiencia.

- Pueden controlar todo a nivel de aplicación. También hay port-forwards o generic proxies, que no aportan seguridad, solo un control rutinario

- Ventajas:
  - Seguridad, logging, caching, intelligent-filterint, user-level authentication
- Inconvenientes
  - Cada nuevo servicio necesita un proxy
  - Cada vez hay servicio más complejos para los que no hay proxy
  - Requiere modificación de clientes, procedimientos....   

### Proxy inverso
- Protege al servidor
- Servidor expuestos a ataques
- Balanceadores de carga suelen disponer de esta funcionalidad

## NAT/PAT
- Netword Addres Translate, cambia la dirección de origen al salir y la de destino al entrar
- Port Adder Translate, modifica el puerto de entrada/salida

- Ventajas, fuerza el uso de un firewall, ocultación de estructura interna
- Desventajas, aumenta la carga, conflictos con software, y con encriptación/autenticación 


## VPN
- Virtual Private Network, tunel encriptado por donde circulan los datos de forma segura por una red insegura que es internet
- El firewall es un buen sitio para ubicar vpn
- Alta interacción con el firewall
- Proporciona seguridad donde el firewall no puede
- Ventajas, cifrado, autenticación, integridad, asegura protocolos dificiles de asegurar de otra forma
- Desventajas, Relaja la seguridad habitual de la red interna, extiende la red que se debe proteger

## Arquitecturas firewall
- Diseño y configuración de los elementos de la seguridad perimetral, influye, tamaño, servicios, funciones, componentes....

### Solo un screening router
- Está formado por un router con un firewall o se le añade uno con estas capacidades, tienen unas reglas para permitir o prohibir el tráfico. Primera y última línea de defensa perimetral

### Single-box
- So/ho
- Estos forman la arquitectura firewall más simple, están compuestos por un objeto que sirve de firewall. Es barato, fácil de configurar, no es demasiado y con el solo no hay defensa en profundidad. 

### Dual-hommed host
- pymes, casas
- Tambien es single-box
- Es un host con dos interfaces de red, le entra una del router, y la otra sale a la subred. Tiene instalado un firewall que filtra los paquetes, puede alojar servidores proxy. No es adecuado para mucho tráfico, puede necesitar balanceo de carga y redundancia. Si cae el host, el atacante ya ha entrado en la red.

## Screnned host
- Screening router + host especialmente securizado(bastion host)
- casas y pymes
- El screening router controla las conexiones de la red interna, y el bastion host puede hacer de proxy, para redes pequeñas / con poco tráfico
- Si cae el bastion estamos expuestos.

## Screened subnet
- Compuesto de un router exterior, y un router interior, de forma que se crea una red perimetral, con un bastion host dentro, de forma que aunque esté más expuesto y pueda caer, está aislado de la red interna.

- Medianas y grandes infraestructuras de red


## Multiple bastion hosts
- Igual que el anterior, pero con varios hosts en la red perimetral. Al haber 2, se aumenta el balanceo de carga, y por ende el rendimiento, además que permite añadir redundancia.

## Mezcla router interior/exterior
- Emula a la screened subnet, pero con solo un router que hace las veces de router exterior e interior y el bastion host en la red perimetral que se sigue creando. Solo se puede dar, si el router es capaz. Sencillez sin perder seguridad.

## Bastion con router exterior
- En cuanto a seguridad es equivalente a la screened subnet con 2 routers, ya que hay un router exterior que esta mezclado con router exterior. Buena seguridad, pero no admite mucho tráfico

## Bastion con ruter interior
- No recomendable
- No es equivalente a 2 routers
- Tráfico interno no protegido

## Multiples routers internos.
- NO recomendable, dificultad de doble configuración
- Puede haber trafido interno-red perimetral-interno y ser esnifado
- Dos sitios por donde salir, routers internos son muy importantes

## Multiples redes internas 1 router
- Organización por sectores
- No mezcla el tráfico
- Añade capa de seguridad

## Multiples redes 2
- 1 router interno no es suficiente, cada departamento su propia red perimetral con su router

## Multiples routers externos
- 1 router externo no es suficiente

## Multiples routers externos 2
- Varias redes perimetrales. 1 para internet, 1 para clientes, 1 para hospedaje, otra para red interna, etc.

## Firewalls internos
- Laboratorios
- Hay unas redes internas más seguras que otraws
- Redes internas de alta seguridad.


## Previo a la implantación de un firewall conviene analizar diversos aspectos
- Definir las necesidades, servicios, nivel de seguridad, ancho de bamda, autitabilidad, disponibilidad, presupuesto, personal...

## Evaluando los productos del mercado
- Precio
- Hardware
- Software
- Tipo de licencias
- Instalación/Configuración/Mantenimiento
- Actualizaciones
- Asistencia y soporte técnico

## Variedad de hardware
- Pequeño dispositivo router/firewall
- Host/servidor
- Appliances/network appliances
- Racks
- Cloud security

## Características/funcionalidad mínima
- Fácil configuración, permitir reglas, aplicarlas. Registrar y diferenciar el tráfico. Capacidad para probar y validar, soporte, actualizaciones, documentación.

## Proxy vs filtrado
- Operacionez que requienen conocimiento detallado del protocolo y segimiento prolongado de eventos es mejor en sistemas proxy
- Operaciones simples y rápidas sobre paquetes individuales, mejor filtro de paquetes. Aunque hay cosas que solo pueden hacer los filtros de paquetes, aplicar reglas generales sobre paquetes mal formado ,bloquear ciertos paquetes, son más fáciles de asegurar.

### Filtrado básico
- No hace nada en base a los datos, solo en base a la cabecera. 

### Filtrado dinámico
- Seguimiento del estado de una conexión
- Detectar patrones
- Hay diferentes niveles de seguimiento
- Aumentan bastante la carga

### Aspectos prácticos del filtrado de paquetes
- Por defecto permitir o denegar
- Strategia del menor privilegio
- Acciones del router
  - Accept, pass, permit
  - Drop, deny
- Loggin actions
- Error codes

### Convenciones en las reglas
- El filtro va regla a regla hasta hacer match
- Si no hace match, hace política por defecto.

## UTM
- Unified Threat Management
- Siguiente generación de FW
- Se trata de integrar todo en un dispositivo
- FW, Anti-virus, spam, balanceo de carga, filtro de contenidos, detección de intrusos, perdida de datos
- Son las tecnologías fw en un único dispositivo

- Ventajas, reducir la complejidad
- Desventajas, único punto de error, compromiso si hay vulnerabilidades, impacto en la latencia, poca escalabilidad.

## Netfilter/iptables
- Packet filtering framework

## Otros elementos
- Bastion hosts
- Intrusion Detection Systems, Deteción de intrusos, con sensores, analizadores, Network based, o host based, es complejo usarlos, usan honeypots.

- Intrusion Prevention Systems, reactivos, muchos más ventajosos que ids, actuan antes de producirse el mal

- SNORT

