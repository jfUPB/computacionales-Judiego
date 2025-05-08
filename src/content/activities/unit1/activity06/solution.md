## pregunta 1
el direccionamiento directo es una forma de acceder a la memoria en la que se especifica una direccion de memoria, osea que el programa usa un valor especifico para dirigirse a una direccion de la memoria.
el lenguaje ensamblador se usa la @n para cargarlo en el registro A y despues acceder a este en M

#### ejemplo
@2 //almacena el valor de 5 en A
D=M //carga el valor de D en la direccion de memoria 2 en este caso

## pregunta 2
D=M guarda el valor almacenado en D en la direccion de memoria del valor que tenga A
M=D carga el valor de la direccion de memoria que tenga el valor de A en D

## pregunta 3
un puntero es una direccion de memoria almacenada en una varibale, osea es una direccion de memoria que su valor representa otra direccion de memoria 

@100  // Carga la dirección 100 en A
D=M   // D tiene el valor almacenado en la dirección 100 que es 200
@D    // Carga la dirección almacenada en D (200) en A
M=10  // Guarda el valor 10 en la dirección 200

