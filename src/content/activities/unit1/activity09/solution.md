// contador y acumulador
@1
D=A
@1
M=D

@0
D=A
@2
M=D

// Ciclo para sumar números del 1 al 5
(LOOP)
    // Si R1 es igual a 6, salimos del ciclo
    @1
    D=M
    @6
    D=D-A
    @END
    D;JEQ

    // Suma: R2 = R2 + R1
    @1
    D=M
    @2
    M=D+M

    // Incrementa R1 (contador)
    @1
    M=M+1

    // Regresa al inicio del ciclo
    @LOOP
    0;JMP

// Guarda la suma en RAM[12] y entra en bucle infinito
(END)
    @2
    D=M
    @12
    M=D

    @END
    0;JMP

![image](https://github.com/user-attachments/assets/13be56fa-1269-4fa5-b121-ae9ef78c73e7)
