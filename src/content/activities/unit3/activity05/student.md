### experimento 3
#### Qué ocurre

Se imprimen primero 42 y 0.

global_inicializada estaba en el segmento .data con valor 42.

global_no_inicializada estaba en el segmento .bss y, por convención del loader, queda inicializada a 0.

Tras las asignaciones, imprime 69 y 666 sin problema alguno.

#### Por qué

Tanto la sección .data como .bss están mapeadas con permisos lectura+escritura.

Asignarles nuevos valores es perfectamente válido y el programa los reflejará inmediatamente.

