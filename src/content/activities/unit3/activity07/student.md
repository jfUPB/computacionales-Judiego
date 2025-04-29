### 1. Almacenamiento de bytes y endianness
Little-endian (x86/x86-64): el byte de menor peso se almacena en la dirección más baja.

Para Punto p(10,20), en memoria (hex):

python
0x…: 0a 00 00 00   14 00 00 00
       ↑ 4 bytes ↓   ↑ 4 bytes ↓
         x = 10         y = 20
Big-endian: el byte de mayor peso va primero, así que serían:

00 00 00 0a   00 00 00 14
### 2. Diferencia entre constructor y destructor en C++
Constructor

Es un método especial que se ejecuta en el momento de crear (construir) un objeto.

Inicializa los datos miembros del objeto (y puede reservar recursos).

Destructor

Es un método especial que se ejecuta cuando el objeto deja de existir (por salir de scope o delete).

Se encarga de liberar recursos adquiridos por el objeto (memoria, handles, etc.).

### 3. Diferencia entre clase y objeto en C++
Clase: el tipo o plano (blueprint) que define qué datos (miembros) y comportamientos (métodos) tendrán sus instancias.

Objeto: una instancia concreta de esa clase, con su propia área de memoria donde viven sus datos miembros.

### diferencias entre el objeto punto

en C++:

cpp
Punto p(10,20);
p es el bloque de memoria donde están x e y, y se destruye al salir de main.

En C#:

csharp
Punto p = new Punto(10,20);
p es un puntero/handle en el stack que apunta a un Punto asignado en el heap, y el GC destruye el objeto cuando lo recolecta.

### 5. capura depurador
![image](https://github.com/user-attachments/assets/3f4d0e03-ca70-46cb-8fe2-f21e5b2d29b1)

### 6. ¿Qué observaste acerca de p? ¿Qué es un objeto en C++?
Al inspeccionar &p y luego la ventana de memoria, vi que:

p ocupa dos enteros contiguos (x y y).

Cada entero ocupa 4 bytes (en tu plataforma).

Los valores se almacenan en little-endian.
