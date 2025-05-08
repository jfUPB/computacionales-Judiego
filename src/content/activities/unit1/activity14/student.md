### Error 1: Sintaxis equivocada en la operación de suma de registros

Recibí el mensaje “Invalid ASM value: M+D” al cargar el programa. El simulador no aceptaba M+D, así que revisé la especificación del lenguaje y confirmé que la forma correcta es D+M. Cambié todas las ocurrencias de M+D por D+M y el error desapareció.

la importancia de revisar la documentación más allá de suponer que ciertas expresiones funcionan; en Hack ASM, el orden de operandos importa.

### Error 2: Desbordamiento del contador al mover la línea

Al implementar el movimiento horizontal, la línea a veces saltaba fuera de la pantalla o se quedaba estática al llegar al borde. Descubrí que mi lógica de límite estaba invertida. Revisé paso a paso el valor de R1 en cada iteración, encontré que no estaba restableciendo correctamente la posición máxima, y reajusté las comparaciones.

### Importancia del debugging y técnicas usadas
El debugging es esencial para transformar un conjunto de instrucciones en un programa funcional. En el simulador Hack, utilicé:

Feedback visual inmediato: cada vez que guardaba la ROM y recargaba la pantalla, veía al instante si el pixel o la línea estaban donde debían.

Mensajes de error del ensamblador: me orientaron directamente a la línea de sintaxis equivocada

Comentarios temporales en el código: anotaba “// inicio del bucle”, “// comprobación de borde derecho” para saber en qué punto del flujo me encontraba.
