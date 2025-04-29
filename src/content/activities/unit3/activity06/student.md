### experimento 5
#### Qué ocurre:

En cada iteración, funcionSinStatic() imprime siempre 100, porque su variable local var_no_estatica se recrea e inicializa a 100 en cada llamada. El var_no_estatica++ solo afecta a la copia temporal que se destruye al salir de la función.

En cambio, funcionConStatic() imprime 100, 101, 102, 103, 104 a lo largo de las cinco llamadas, porque su var_estatica se inicializa una sola vez y conserva el valor incrementado entre llamadas.

#### Diferencias clave:

#### Variable no estática (stack):

Duración de almacenamiento automático: existe solo durante la llamada; al volver, se destruye.

Alcance: bloque de la función.

Inicialización en cada llamada.

#### Variable estática local (data segment):

Duración de almacenamiento estático: vive durante toda la ejecución, igual que una global.

#### Alcance: únicamente visible dentro de la función.

Inicialización una única vez, la primera vez que se ejecuta la función, y luego mantiene su último valor.

#### Qué pasa al entrar y salir de la función:

No estática: cada entrada crea y inicializa de nuevo; cada salida destruye la variable.

Estática: no se crea ni destruye en cada llamada; permanece en memoria (en la sección RW del binario) y preserva su estado.

### experimento 6
``` cpp
int* arrayHeap = new int[tam];
// … inicializamos y mostramos …
delete[] arrayHeap;

cout << arrayHeap[0] << endl;    // <<--- UB: acceso tras free
```

#### Qué ocurre
Comportamiento indefinido (undefined behavior).

Imprimir un valor “basura” (datos residuales).

Provocar un segfault si el SO/allocator marca la página como inaccesible.

Parecer funcionar “bien” en un momento e “ir mal” en otro.

#### Heap y Stack:

Stack:

Asignación y liberación automática al entrar/salir de bloques o funciones.

Tamaño limitado, LIFO, sin fragmentación compleja.

Heap:

Asignación y liberación manual mediante new/delete.

Permite tamaños variables y persistencia más allá del scope de la función.

Puede fragmentarse y requiere bookkeeping por parte del allocator.

#### Consecuencias de no liberar la memoria:

Memory leak: memoria reservada que nunca se devuelve al sistema.

Si ocurre repetidamente o en bucles, agota la memoria RAM disponible y puede causar que el programa o el sistema operativo se queden sin recursos y fallen.

#### Importancia de usar delete[] para arreglos:

Debe coincidir exactamente con new[].

Llama al destructor de cada elemento del arreglo (relevante si fueran objetos complejos).

Permite al allocator saber cuánto espacio liberar; usar delete (sin []) en vez de delete[] es también UB y puede corromper el heap.

