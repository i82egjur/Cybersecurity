
# Encriptación clásica

## Modelo de cifrado simétrico
1. A partir del texto plano
2. Y un algoritmo de encriptación
3. Se genera una clave secrera
4. Se cifra el texto -> C=Ek(M)
5. Se desencripta, mediante un algoritmo de desencriptacion M=Dk(C)

## Requisitos para una encriptación segura
- Algoritmo de encriptación fuerte
- La clave permanece segura

## Ventajas del algoritmo público
- Criptoanalistas pueden analizar, destapar errores, vulnerabilidades o debilidades. Probar científica y publicamente su eficacioa
- Fabricantes pueden hacer hardware específico reduciendo costes de cómputo y económicos

## Ataques
- Criptoanálisis
- Fuerza brita

## Ataque criptonalítico
- Cyphertext onli Attack
- Known plaintext attack
- Chosen plaintext attack
- Chosen ciphertext attack
- Existen variantes, modelos híbridos, y adaptativos

- Para que un algoritmo de cifrado sea seguro, no ha de tener suficiente información en el cipher text de manera que por mucha capacidad de computo no se pueda descifrar, a parte debe computacionalmente seguro, para que cueste más descifrar que la propia información.

## Elementos relevantes en el estudio de un sistema criptográfico
- Fundamento y tipo de operaciones
- Numero, tipo y longitud de claves, simetrico, o asimétrico
- Procesamiento, por bloques, stream
- Seguridad
- Caracteristicas particulares

## Historia de la encriptación
### Caesar
- Uno de los cifrados más antiguos conocidos, C = (p+k) mod (numero letras abecedario) <- Encriptación
                                              p = (c-k) mod (numero letras abecedarui) <- Desencriptado
                                
- Fuerza bruta posible, el algoritmo es conocido, clave de pocos valores, lenguaje conocido o facilmente identificable.
- Variante rot 13, es el mismo algoritmo para encriptar que para desencriptar, no es seguro, pero es útil.


### Cifrado monoalfabetico
- Cuando la sustitución viene dada por culaquier permutación de los caracteres del alfabeto, hay 26! posibles claves, puede parecer seguro, pero no lo es, ya que se pueden analizar regularidades del lenguaje, ataques estadísticos. Una soluciónes usar homophonos, y proporcionar multiples sustitutos a una misma letra. En número proporcional a su frecuencia. Sigue podiendo ser analizable, mejora multiple letter encription.

### Playfair cipher
- Se toma una tabla de 5x5, en cada celda de la tabla introducimos una letra, la i y la j se ponen juntas, ya que 5x5=25 y el abecedario ingles tiene 26 letras. Después se escoge una palabra de clave y se escribe, después se rellena siguiendo el abecedario en orden, si una letra ya ha sido escrita se salta a la siguiente. Después se separan las letras por pares, para evitar análisis estadisticos, si hay 2 letras repetidas, se introduce una x en medio de ambas. Posteriormente, se van cambian los valores de la siguiente forma, si los valores de un par aparecen en la misma fila en la tabla, se coge el inmediato a la derecha en el orden que aparecen en el par. Si están en la misma columna se coge el inmediato de abajo en el mismo orden que el anterior, y si están en distintas filas y columnas, se coge el que esté en la misma fila, en la columna del contrario.

- Muy usado en la ww1 y ww2.


### Hill cipher
- Creado en 1929, sustituye las m letras del plaintext por cipher text, para eso, se crea una matriz de nxn que se rellena con la posición
de los caracteres en el abecedario de la clave. Posteriormente, para cifrar, C = MxP mod 26. Para desencriptar, se multiplica por la matriz inversa. Si hay pares plain-cipher, known-plaintext attack, se pueden plantear ecuaciones lineares inversas.

- Todos los anteriores, son monolfabeticos, los mejora los polialfabeticos.

## Polialfabetico
- Cada letra usa una sustitución alfabetica diferente, el alfabeto que usamos cambia mientras avanza el procesamiento del plaintext.

### Vigenére
- Usa 26 cifrados cesars con un incremento de 0 a 25  denotando el incremento por una letra, la clave es tan larga como el mensaje. Cada letra tiene tantas substituciones como la longitud de la clave, las frecuencias de las letras están más ocultas. Aún sigue siendo posible el análisis de frecuencias. Con claves pequeñas, es fácil el criptoanálisis.

### One-time pad
- Creado en 1917, se usa una clave aleatoria tan larga como el mensaje, que solo se usa una vez. Para encriptar, key+plaintext mod 26
Para desencriptar, cipher-key mod 26. Es imposible de romper, pero generar claves verdaderamente aleatorias del tamaño del plaintext, 
y almacenar una clave de millones de caracteres complican mucho su uso.


### Técnicas de transposición
- Operaciones básicas en la encriptación, sustiución y permutación.
- Transponer, significa permutar las letras del mensaje, según un algoritmo. 
- Algoritmos, rail fence technique, transposición diagonal. Se concatenan los railes
    - Meet me
      - m e m
      -  e t e
  -  Row transposition
  -  Columnar transposition, Se escribe en una columna, se le pone un orden de aparicion en el cipher text a cada columna
  -  route cipher, se pone en una matriz, se pone el orden de aparicion en la clave. 

- Son facilmente criptoanalizables, se mantienen frecuencias del texto, son muy vulnerables. 


### Maquinas con rotor
- Primer esquema con varias etapas de encriptación, aplicación más importante de un esquema de varias etapas, antes de DES. Este funciona con varios rotores interconectados, en cada pulsación, se desplaza una posición el rotor, en la primera pulsación se mueve le primer rotor, en la segunda pulsación se mueve el 2 rotor, en la tercera se mueve el tercer rotor, según la cantidad de rotores que tenga la máquina será más o menos segura hay maquinas con más de 10 rotores. Usada por alemania en la SGM.

## Estenografía
- Tecnicas para ocultar mensajes en cartas, una de las más usadas es LSB en una imagen, least significant bit insertion, letras marcadas, tinta invisible.... 









