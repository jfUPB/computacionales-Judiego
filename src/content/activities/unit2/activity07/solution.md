``` asm
// Inicialización manual del arreglo en direcciones 16 a 25.
// arr[0] = 1:
@16
M=1      

// arr[1] = 2:
@2
D=A
@17
M=D      

// arr[2] = 3:
@3
D=A
@18
M=D      

// arr[3] = 4:
@4
D=A
@19
M=D      

// arr[4] = 5:
@5
D=A
@20
M=D      

// arr[5] = 6:
@6
D=A
@21
M=D      

// arr[6] = 7:
@7
D=A
@22
M=D      

// arr[7] = 8:
@8
D=A
@23
M=D      

// arr[8] = 9:
@9
D=A
@24
M=D      

// arr[9] = 10:
@10
D=A
@25
M=D      

// Inicialización de las variables sum y j.
// Usaremos las direcciones 26 y 27 para sum y j respectivamente.
@0
D=A
@26
M=D    // sum = 0

@0
D=A
@27
M=D    // j = 0

(LOOP)
// Verificar la condición: j < 10.
// Calcula D = j - 10.
@27
D=M      // D = j
@10
D=D-A    // D = j - 10
@END
D;JGE   // Si j >= 10, salta a END

// Calcular la dirección de arr[j]: base (16) + j.
@16
D=A      // D = 16 (base del arreglo)
@27
D=D+M   // D = 16 + j
A=D      // A apunta a arr[j]
D=M      // D = arr[j]

// Sumar arr[j] a sum: sum = sum + arr[j].
@26
M=D+M   // Usamos D+M en lugar de M+D

// Incrementar j: j = j + 1.
@27
M=M+1

@LOOP
0;JMP   // Regresa al inicio del ciclo

(END)
// Fin del programa (loop infinito para detener la ejecución)
@END
0;JMP
``` 
