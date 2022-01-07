
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
