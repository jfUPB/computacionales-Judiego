### experimento 1
#### Qué ocurre:
Al intentar escribir en la dirección donde está almacenada la función main el proceso viola el permiso de escritura de esa página de memoria.
→ Segfault (SIGSEGV) en tiempo de ejecución.

#### Por qué:
El text segment (código) se mapea como lectura + ejecución (RX) pero no escritura.

Cualquier intento de modificar esas instrucciones rompe la protección de página y el hardware genera una falta de segmento.
en caso de que consiguir forzar la escritura (por ejemplo, estaria corrompiendo el flujo de ejecución.

### experimento 2
#### Qué ocurre:
Este código también genera un segfault al intentar escribir en la dirección donde esta mensaje_ro porque esas páginas están marcadas como solo lectura.

#### Por qué:
El literal de cadena ("Hola, …") se ubica en el segmento .rodata o en una sección const del binario, con permisos RX o únicamente R.

La variable mensaje_ro es un puntero const, y el compilador normalmente lo coloca también en una sección de solo lectura.

Al hacer un cast y escribir ahí, se viola la política de la tabla de páginas y el OS aborta el programa con SIGSEGV.
