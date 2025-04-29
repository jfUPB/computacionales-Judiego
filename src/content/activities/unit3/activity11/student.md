Conclusiones sobre miembros estáticos vs de instancia en C++

Miembro de instancia (valor)

Cada objeto tiene su propia copia de valor, ubicada en la memoria del objeto (stack o heap según dónde se cree).

Se ocupa espacio proporcional al número de instancias.

Útil cuando cada objeto necesita mantener su propio estado independiente.

Miembro estático (total)

Hay una sola variable total compartida por todas las instancias de la clase.

Se almacena en el segmento de datos estáticos (.data), no dentro de ningún objeto en el stack ni en el heap.

Permite llevar contadores globales o compartir información común sin replicarla por objeto.

Gestión en memoria

Instancias (c1, c2) se ubican en el stack si se crean como variables locales, y sus miembros de instancia cruzan el stack contiguamente.

El puntero c3 vive en el stack, pero el objeto apuntado por c3 se aloja en el heap. Sus datos miembros (incluido valor) residen dentro de ese bloque de heap.

Contador::total vive en la sección de datos estáticos del ejecutable, con permisos lectura/escritura, y existe durante todo el ciclo de vida del programa.

Ventajas y desventajas

Estáticos:

Compartición fácil de información común.

No aumenta el tamaño por instancia.

– Rompen la encapsulación si se abusa, pueden introducir dependencias globales.

– Dificultan el testeo aislado.

Instancia:

Encapsulan estado por objeto.

Fáciles de razonar en términos de alcance y vida.

– Consumen más memoria si hay muchas instancias.

Cuándo usarlos

Usa miembros de instancia para datos que deben ser distintos en cada objeto.

Usa miembros estáticos para contadores globales, constantes compartidas, o cualquier dato/propiedad de clase que deba existir una sola vez en todo el programa.
