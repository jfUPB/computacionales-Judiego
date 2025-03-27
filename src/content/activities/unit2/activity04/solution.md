``` asm
// a = 10
@10
D=A
@a
M=D

// p = a   se guarda la dirección de a en p
@a
D=A
@p
M=D

// p = 20   se accede a la dirección almacenada en p y se escribe 20
@p
A=M      // A = contenido de p, que es la dirección de a
@20
D=A      // D = 20
M=D      // Se escribe 20 en la dirección apuntada por p (a)
``` 
