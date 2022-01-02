# Desarrollo seguro

## Introducción
- Para desarrollar algo de manera segura, debemos ser conscientes que construimos sistemas distribuidos, por eso hay que entenderlos bien,
además tener en cuenta que la protección es una prioridad siempre.

## Dificultades
- A la hora de implantar un nuevo software, podemos decidir entre comprarlo o implementarlo. Si decidimos implementarlo, hay que aplicar el 
desarrollo seguro del software.
- Sin embargo, este desarrollo seguro implica una serie de dificultades.
  - La aplicación de este, requiere un mayor tiempo de desarrollo y mantenimiento, a manos de alguien con una formación adecuada, lo cuál 
  incrementa los costes. Además, la seguridad, hace que al usuario se le complique ciertas acciones. Sin embargo, esto es imprescindible.
 
 ### Formación especializada
 - Los profesionales que apliquen el desarrollo seguro, necesitan tener una amplia formación sobre seguridad. 
 - En específico, sobre sistemas distribuidos, redes, sus amenazas. 
 - Sobre seguirdad informática, métodos, tecnologías, herramientas....
 - Una formación especifica del desarrollo seguro.
 -  Además de una continua actualización en la materia.

### Desarrollo seguro, formación específica
- El desarrollo seguro, implica, la integración de la seguridad en el ciclo de vida del software.
  - Captura de requisitos, análisis, diseño, implementación, pruebas,
- En cada fase, se requiere ejecutar controles de desarrollo seguro, que dependerán, del sistema, las tecnologías utilizadas. En cada fase
se activarán los controles de seguridad correspondientes, el desarrollador, deberá analizar riesgos y disponer contramedidas.

- Es importante, que se integre durante todo el ciclo de vida del software. No hacerlo todo al final, ni hacerlo todo al principio, ni hacerlo
todo en un momento dado. Hay que ir integrandolo poco a poco e ir viendo que es lo que realmente nos hace falta. Por eso, usar un grupo de aplicaciones
potentes, no siempre es la respuesta. 

### Tecnicas a incluir
- Casos de mal-uso
  - Los casos de uso, por su parte, reflejan acciones o actividades que realizará el sistema. Que serán lanzados por actores
  - Los casos de mal uso, describe escenarios con interacciones accidentales, maliciosas, imprevistas, con el objetivo de descubrir debilidades
  - y crear subsistemas de protección y contramedidas que las corrijan. Estos, aportan una nueva visión desde el punto de vista de el atacante.
   
  - Deben integrarse en los casos de uso habituales
  - Deben hacerse a un nivel de detalle que dirija decisiones de diseño
  - Si en un caso de uso el actor es un usuario o proceso que interatúa con el sistema. En los casos de mal uso, el actor es un usuario o proceso
  malintencionado que actúa de forma inesperado o indeseada
  - El objetivo de los casos de uso es describir el uso habitual de un buen sistema, El objetivo de los casos de mal uso es comprometer su seguridad
  - Si el caso de 'mal-uso' aporta una amenaza, se debe responder con un nuevo caso de uso que mitigue esa amenaza, lo cual demandará nuevos componentes
    y subsistemas que mitiguen.
  - Habrá casos de mal uso a todos los niveles. A alto nivel con actores siendo personas y a bajo nivel con otro tipo de riesgos
  - Se trata de considerar los requisitos funcionales, no funcionales: de seguridad y excepciones

## Comunidades
- Safecode.org, owasp.org, cwe...

## Principios del desarrollo seguro según owasp
- Keep security simple
- Minimizar la superficie de ataque
- Evitar la seguridad por ocultación
- Separación de roles
- Principio del menor privilegio
- Corregir adecuadamente riesgos
- Establecer ajustes por defecto seguros
- Fallar de forma segura
- Defensa en profundidad
- No confiar en seguros de terceros

Hemos hablado de que pasa al implementar nosotros el software, pero que hay de cuando lo compramos.
No solo nos interesa la funcionalidad. También como se ha desarrollado, (metodología de desarrollo, actualizacion de la metodología, papel de seguridad en ella)
quien la ha desarrollado (entrenamiento/actualización de los programadores), que política de privacidad.
 
