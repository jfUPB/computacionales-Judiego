### condicionales
int x = 7;
int y;
if (x > 0) {
    y = 1;
} else {
    y = 0;
}

#### ensamblador
@7
D=A
@x       // x en R16
M=D

@x
D=M       // D = x
@IF_TRUE
D;JGT    // Si x > 0, salta a IF_TRUE
@ELSE
0;JMP

(IF_TRUE)
@1
D=A
@y       // y en R17
M=D
@END_IF
0;JMP

(ELSE)
@0
D=A
@y
M=D

(END_IF)

### ciclo while
int x = 2;
while (x < 5) {
    x = x + 1;
}

#### ensamblador
@2
D=A
@x
M=D          // x = 2

(WHILE_START)
@x
D=M          // D = x
@5
D=D-A       // D = x - 5
@WHILE_END
D;JGE       // Si x >= 5, termina el ciclo

@x
M=M+1      // x = x + 1
@WHILE_START
0;JMP

(WHILE_END)

### ciclo for
int sum = 0;
for (int i = 0; i < 10; i++) {
    sum = sum + i;
}

#### ensablador
@0
D=A
@i
M=D          // i = 0

@0
D=A
@sum
M=D          // sum = 0

(FOR_START)
@i
D=M
@10
D=D-A       // D = i - 10
@FOR_END
D;JGE      // Si i >= 10, termina el ciclo

@i
D=M        // D = i
@sum
M=M+D      // sum = sum + i

@i
M=M+1      // i = i + 1
@FOR_START
0;JMP

(FOR_END)

### punteros
// Asigna 42 a la variable a a través de un puntero.
int a = 5;
int *p;
p = &a;
*p = 42;

#### ensamblador
@5
D=A
@a
M=D         // a = 5

@a
D=A
@p
M=D         // p = dirección de a

@p
A=M         // A apunta a la dirección almacenada en p (la dirección de a)
@42
D=A
M=D         // *p = 42  --> a = 42

### lectura de variables por punteros
int a = 77;
int *p;
int b;
p = &a;
b = *p;

#### ensablador
@77
D=A
@a
M=D         // a = 77

@a
D=A
@p
M=D         // p = dirección de a

@p
A=M         // A apunta a a
D=M         // D = *p (valor de a)
@b
M=D         // b = *p

### manipulacion de arreglo por punteros
// Incrementa el primer elemento del arreglo arr en 1 a través de un puntero.
int arr[3] = {10, 20, 30};
int *p;
p = arr;       // p apunta a arr[0]
*p = *p + 1;   // arr[0] = arr[0] + 1

#### ensamblador
@10
D=A
@arr0
M=D        // arr[0] = 10

@20
D=A
@arr1
M=D        // arr[1] = 20

@30
D=A
@arr2
M=D        // arr[2] = 30

@arr0
D=A
@p
M=D        // p = dirección de arr[0]

@p
A=M        // A apunta a arr[0]
D=M        // D = arr[0]
@1
D=D+A      // D = arr[0] + 1
@p
A=M
M=D        // arr[0] = arr[0] + 1

### llamado de funciones con parametros
int add(int a, int b) {
    return a + b;
}
int x = add(3, 4);

#### ensamblador
// Preparar parámetros:
@3
D=A
@param0
M=D       // param0 = 3

@4
D=A
@param1
M=D       // param1 = 4

// Llamar a la función add:
@add
0;JMP

(return_add)
@x
M=D       // x = resultado (en R22, por ejemplo)
@END
0;JMP

(add)
    @param0
    D=M     // D = param0
    @param1
    D=D+M   // D = param0 + param1
    @return_add
    0;JMP

### llama funcion con retorno de parametro
// Función que multiplica dos enteros (usando suma repetida)
int multiply(int a, int b) {
    int result = 0;
    while(b > 0) {
        result = result + a;
        b = b - 1;
    }
    return result;
}
int y = multiply(2, 5);

#### ensablador
// Preparar parámetros:
@2
D=A
@param0
M=D      // param0 = 2

@5
D=A
@param1
M=D      // param1 = 5

// Inicializar result = 0:
@0
D=A
@result
M=D     // result en R23 = 0

// Llamar a la función multiply:
@mult
0;JMP

(return_mult)
@y
M=D     // y en R24 = resultado (valor en D)
@END
0;JMP

(mult)
    // Verificar si param1 == 0:
    @param1
    D=M
    @END_MULT
    D;JEQ      // Si b == 0, termina

    // result = result + param0:
    @result
    D=M
    @param0
    D=D+M
    @result
    M=D

    // param1 = param1 - 1:
    @param1
    M=M-1

    @mult
    0;JMP

(END_MULT)
    // Dejar el resultado en D:
    @result
    D=M
    @return_mult
    0;JMP
