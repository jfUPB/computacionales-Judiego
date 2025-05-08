## pregunta 1
En el simulador las variables no tienen direcciones fijas y se almacenan en la RAM a partir de la dirección 16 porque las direcciones de 0 a 15 están reservadas para otros usos.
entonces i y sum estarán en alguna posición de memoria RAM a partir de la dirección 16.

## pregunta 2
La dirección de una variable es el lugar en la memoria donde se almacena su valor.
El contenido de una variable es el valor guardado en esa dirección de memoria, si i está en RAM[16] y su valor es 1, significa que en la dirección 16 de la RAM hay un 1 almacenado.

## pregunta 3
@i
D=M      // D = i
@100
D=D-A    // D = i - 100
@END
D;JGT    // Si (i - 100) > 0, saltar a END
