
# Encriptación Simétrica Moderna

La criptografía moderna depende de una clave K para encriptar y descencriptar. Si la clave para desencriptar es la misma que para encriptar, 
esto se llama encriptación simétrica. Si no, se llama asimétrica. 

La fortaleza del cifrado, depende del número de claves posibles para ese cifrado.
Así, si un algoritmo es viable con un numero reducido de claves. Será más fácil de romper por fuerza bruta. El conjunto de todas las posibles
claves se llama keyspace y depende del algoritmo.

En realidad, que conzcamos el algoritmo de cifrado no disminuye su seguridad. Un buen algoritmo es aquel que aunque se conozca el mismo, si no
se conoce la llave, la encriptación sigue siendo segura. Además que el algoritmo sea abierto, es bueno así la comunidad puede analizarlo, y
se pueden implementar software y hardware optimos para ese algoritmo.

## Qué posibles ataques tiene la encriptación.
- Que alguien descrifre un mensaje -> El sistema esta roto
- Que se obtenga la clave a partir del mensaje -> Completamente roto
- QUe se obtenga por fuerza bruta
- Mediante cripto-análisis. Ciphertext-only, known-plaintext, chosen-chiphertext, chosen-plaintext

## Qué necesita un algoritmo para ser seguro
- Que no haya suficiente información en él para descrifrarlo
- Que sea computacionalmente inviable desencriptarlo por fuerza bruta por ejemplo


# Algoritmos simétricos
- Son los algoritmos convencionales, que encriptan/desencriptan con la misma llave

## Categorías
- Cifrado de stream, cifrado de bloque.

### Cifrado tipo stream
- Se recorre y cifra bit a bit. No es necesaro padding

### Cifrado bloque
- Se cifra un grupo/bloque de bits cada vez, es necesario un padding para ir cambiando de bloque

## Cifrado Ideal de bloque

- Poniendonos en un bloque de 4 bits, lo ideal, sería que entrara el bloque y lo redirigiera a otro valor de manera que 
se construyese una tabla con las equivalencias entre (1)texto-plano -> (2)texto-cifrado y (3)texto-cifrado -> (4)texto-plano. Donde nuestra
clave serían estas tablas. En 4 bits, tenemos 16 posibles combinaciones y como necesitamos almacenar las anteriores equivalencias
la clave sería de 16x4. Por norma general, las claves van a ser de nx2^n. 4x2⁴ = 4x16=64. Teniendo en cuenta que el tamaño normal de n es
64, el tamaño de nuestra clave sería 64x2^(64) = 2⁶ x 2^64 = 2^70. Lo cual son millones de terabytes, algo impracticable en el mundo real.
- Las que finalmente se almacenan son nx2^n. Sin embargo hay 2^n! combinaciones posibles.

- Para solventar esto, Feistel propone aproximar el ideal block cipher con una clave de k bits, para un bloque de k bytes, permitiendo 
2^k posibles combinaciones en vez de 2^n!. Para hacer esto de manera segura de combina con las ideas shanon quien demostró que combinar
de forma iterativa transformaciones diferentes del plaintext, mezcladas con una clave obtiene resultados muy dificiles de criptoanalizar.
De esta forma surgió el product cipher El cual itera operaciones simples sobre los bloques y la clave.
De esta forma se crean redes como las S-P networks.


## Shanon confusion and diffusion
- Para shanon, para hacer un cifrado más resistente, es necesario que cumplan con la confusión y la difusión.
- La difusión significa que cuando se cambia un bit en el texto sin cifrar, se cambien muchos en el texto cifrado
- La confusión significa que la relación entre el texto cifrado y la clave sea lo más compleja posible.

## Feistel Network.
- Una aplicación de esto son las clásicas redes de feistel.
- El texto plano se divide en 2: L0 y R0
- Se aplica una función Feistel sobre R0 con k1 
- Se aplica una or-exclusiva sobre l0 
- li y ri son permutadas al final de cada etapa
- En cada etapa se utiliza una k diferente derivadas de la primera k

Parámteros:
- Tamaño bloque
- Tamaño clave
- Algoritmo de generación de subclave
- Función feistel
- Numero de rondas

# DES
- IBM inicia un proyecto liderado por Horst Feistel, que dio lugar a LUCIFER, un algoritmo de cifrado de bloques de tamaño de 64-bits, que 
posteriormente se modifica para poder implementarse un un solo chip, se reduce la clave a 56 bits.
- Después cuando NIST, pide un aloritmo standard,  se selecciona LUCIFER y se modifica resultando en DES.
- Se descubrió que des no era seguro y salió 3DES, el cual es bastante seguro, aunque tiene un posible ataque teórico que requiere de muchos
recursos. Sin embargo, NIST lanzó una llamada a propuesta, lo cual desencadenó en AES.

 ## SDES
 - Simplified DES
 - Algoritmo con fin educacional, más fácil de explicar
 - Consta de 5 pasos, con 3 funciones diferentes
 1. Permutacion inicial (IP)
 2. Funciones complejas llamadas fk
 3. Una función de intercambio simple SW
 4. Otra vez funciones complejas fk
 5. Inversa de la permutación inicial

- La entrada son 8 bits.
- La clave es de 10 bits, que mediante un shift se combierten a 8 bit para que sirvan como entrada a fk


















