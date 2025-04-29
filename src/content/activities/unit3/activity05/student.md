### experimento 3
#### Qué ocurre

Se imprimen primero 42 y 0.

global_inicializada estaba en el segmento .data con valor 42.

global_no_inicializada estaba en el segmento .bss y, por convención del loader, queda inicializada a 0.

Tras las asignaciones, imprime 69 y 666 sin problema alguno.

#### Por qué

Tanto la sección .data como .bss están mapeadas con permisos lectura+escritura.

Asignarles nuevos valores es perfectamente válido y el programa los reflejará inmediatamente.

### experimento 4
#### ¿Qué ocurre?
No compila

var_estatica tiene alcance de bloque dentro de funcionConStatic(), es decir, solo existe y se nombra ahí.

#### ¿Por qué?

Las static locales son variables de enlace interno y ámbito de bloque:

Viven en el mismo segmento RW que las globals (no se destruyen al salir de la función).

Pero solo pueden referenciarse por nombre desde dentro de esa función.

#### ¿Qué pasa con ellas cada vez que entras y sales de la función?

Se inicializan una sola vez (la primera vez que se ejecuta la función).

En llamadas posteriores, no vuelven a inicializarse y conservan el valor modificado en invocaciones previas.

#### Resumen sobre variables static locales

Tienen duración de almacenamiento estático (como globales) → existen todo el tiempo de ejecución.

Tienen alcance restringido al bloque donde se declaran → no puedes verlas ni modificarlas desde fuera.
