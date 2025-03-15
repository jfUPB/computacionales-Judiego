``` asm
// int a = 10;
@10
D=A
@a
M=D

// int b = 5;
@5
D=A
@b
M=D

// int *p;
// p = &a;
@a
D=A
@p
M=D

// b = *p;
@p
A=M    // A toma el valor almacenado en p (dirección de a)
D=M    // D = M[A] (valor de a)
@b
M=D    // b = valor de a (ahora b vale 10)
``` 
