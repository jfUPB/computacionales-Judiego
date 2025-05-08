### 2. Explicación de la diferencia entre objetos en stack y en heap
Stack

Se asigna automáticamente cuando entras en el bloque donde declaras la variable.

Su memoria se libera automáticamente al salir de ese bloque (scope).

Las direcciones suelen ser “altas” (0x00FFBxxx en nuestro ejemplo) y decrecen a medida que se anidan más funciones.

Heap

Se asigna manualmente con new y permanece hasta que llamas a delete.

Su tamaño es dinámico y no está limitado al lifetime de un scope concreto.

Las direcciones suelen ser distintas de las del stack (0x0123C4D0 en nuestro ejemplo) y crecen según cómo el allocator gestione la memoria.

### 3. ¿Qué es pStack? ¿Objeto o referencia?
pStack es el propio objeto de tipo Punto, almacenado directamente en el stack.

Cuando escribes &pStack obtienes la dirección donde sus miembros x e y están contiguos en memoria.

### 4. ¿Qué es pHeap? ¿Objeto o referencia? ¿A qué hace referencia?
pHeap es una referencia (un puntero) que vive en el stack, cuyo valor es la dirección del objeto real en el heap.

Ese objeto real se creó con new Punto(50,60) y ocupa memoria a partir de la dirección pHeap (ej. 0x0123C4D0).

### 5. Observaciones en Memory 1
Al escribir &pHeap en Memory 1 vemos los bytes almacenados en la variable pHeap (por ejemplo D0 C4 23 01 …).

Esos bytes, interpretados como little-endian de 4 bytes, coinciden exactamente con la dirección que el depurador muestra en Locals para pHeap.

Significado: el puntero pHeap ocupa 4 u 8 bytes (según la plataforma) en el stack y contiene la dirección del objeto en el heap. En memoria se ve el valor bruto de ese puntero.
