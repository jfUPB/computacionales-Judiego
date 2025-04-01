## PREGUNTA 1
A instruction: deja cargar un valor en el registro A que se puede usar en operaciones o calculos.

C instruction: realiza operaciones y controla el flujo del programa con operaciones aritmeticas y darle un destino al resultado o hacer un salto.

## PREGUNTA 2
A Comienza con un bit 0, luego de 15 bits que representan el valor o la dirección.
C comienza con 111, luego 7 bits de comp que especifican que operacion es, 3 bits de dest que indican donde se guardara el resultado o 3 bits de jump que especifica el tipo de salto.

## PREGUNTA 3
### A INSTRUCTION
@2: carga el valor 1 en resgistro A.
@LOOP: carga la dirección de la etiqueta LOOP en el registro A. por ejemplo si LOOP esta en la posicion 10 A tomara este valor.
@R0: carga la direccion del registro R0 en el registro A.

### C INSTRUCTION
D=M: Almacena el valor contenido en la dirección de memoria apuntada por A en el registro D.
D=D+A: Suma el valor de D con el de A y almacena el resultado en D.
0;JMP: Realiza un salto incondicional a la dirección especificada en el registro A
