

# Public key encryption

- Encriptación asimétrica, es un aporte muy importante, totlamente diferente, se basa en propiedades matematicas, es más lenta. Pioneros, diffie-hellman en 1976.
- Es falso, que la pke sea mejor, resuelva mejor el problema de distribución de claves o que haya dejado obsoleta la encriptación simetrica.

## Bases de pke.

- La encriptación de clave pública funciona gracias a un par de claves, si se encripta con una se desencripta con la otra. Son diferentes, 
pero está relacionadas la una con la otra. Es sencillo generar la pareja de claves, pero imposible obtener la clave privada a partir de una pública.


## Componentes.
- Texto plano
- Algoritmo encriptación
- Claves, publicas y privada
- Texto cifrado
- Algoritmo de descifrado

## Esquema

Si bob quiere encriptar y enviar un mensaje a alice, necesita la clave publica de esta, lo encripta usando esa clave y solo se podrá desencriptar 
usando la clave privada que solo tendrá alica.

De esta forma, se proporciona autenticación y confidencialidad.

## Aplicaciones
- Encriptación, RSA, ECC, EG, distribución de claves, RSA, Eliptic curve cryptograpy, elgamal, diffie-hellman
- Protocolo: TLS, SSL

## Algoritmos
- Se han desarrollados pocos algoritmos debido su complejidad, se basan en problemas que tienen muy dificil solución o que son muy costosos de resolver.
- Se basan en los llamados problemas intratables, factorización de enteros, logaritmo discreto..

## RSA
- Algoritmo de encriptación de clave publica, basado en el trabajo de diffie-hellman, creado por Rivest-Shamir-adleman. Es un cifrado
de bloque donde tanto el texto plano como el cifrado estan entre 0 y n-1 para un determinado n.

- Funciona de la siguiente manera.
- RSA, se basa en el problema de la factorización de enteros, por ello, partimos de un numero n, producto del cociente de dos numero p y q
de grandes dimensiones, cuanto más grandes sean, más dificil será de descrifrar, despues necesitamos una función phi, resultante del siguiente
producto phi(n) = (p-1)x(q-1)
Después necesitamos elegir un e tal que mcd(phi(n), e)=1, generalmente se elige 0x10001, 65537, después necesitaremos un d=e⁻1 mod phi(n)

Así creamos las claves publica, e, n
privada, d, n
n = p*q

e = un entero tal que mcd(phi(n), e) = 1
phi(n) = (p-1)(q-1)
d = e^-1 mod phi(n)


Una vez los tenemos, ciframos realizando la siguiente operación C=M^e mod n

Desciframos, M=C^d mod n

El problema que tiene es que es muy lento, 1000 veces más lento que des por ejemplo.


## ECC
- Más rápido que rsa, necesita claves más pequeñas 128, 256b, en auge, no tan testeado como rsa, introducida por koblitz, miller, 1985,

## ElGAmal
- Basadp en el intercambio de clave de diffie-hellman. Desarrollado por taher elgamal en 1984, usado en gnu privacy guard, seguro con una
clave a partir de 1024 bits.

# Distribución de claves.
Conviene utilizar un esquema de distribución de claves para afrontar esta problemática. Seegún el tipo de clave, podemos diferenciar, entre
esquema de distribución de claves publicas o de claves privadas.

## Claves públicas.
- Public announcement, la distribuye publicamente, inseguro, nos podrian mentir
- Publicly available directory, Puede tener entradas falsas
- Public-key authority, lento pero seguro necesita contacto con autoridad certificadora
- Public-key certificates, segurop y rapido, no necesita contacto con ca, certidicado clave publica + id propietario firmado todo por una ca


## claves secretas
- Hacerlos públicos es muy inseguro, por ello, necesitamos un plan para estos, hay algortimos específicos que se usan para el intercambio de claves
secretas, un ejemplo de esto es el algoritmo de diffie-hellman. Se basa en la dificulta de cálculo de lofaritmos complejos.

- bob y alice, ambos generan su par de claves pulica/privada y  distribuye la clave publica. Despues de obtener un copia autentica de las claves publicas
del otro, Alice and bob puede computar una clave secreta compartida a partir de las claves de ambos.


# Firma digital
- Equivalente a la firma real, debe ser rápido, fácil distribución de claves, puede conseguirse con pke + hash functions.

# Firma digital
- Verificar autor, fecha y hora
- Verificar contenido
- Implica no repudio, solo el emisor puede haber firmado el documento.


# Aplicaciones httpos, 







