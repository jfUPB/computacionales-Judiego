### Nivel de comodidad con la arquitectura Hack y su lenguaje ensamblador:
La verdad, al principio me sentí muy perdido. Aunque sabía que la pantalla empezaba en 16384 y el teclado en 24576, me llevó un buen rato entender cómo escribir un bit en la posición correcta. Por ejemplo, tardé en identificar por qué al usar M+D el simulador me marcaba error y tuve que repasar la sintaxis hasta caer en D+M.

### Conceptos más desafiantes

Desplazar bits dentro de un word de 16 bits
Me costó trabajo visualizar cómo un valor de 1 se convertía en 2, 4, 8, … hasta 2^15. Al principio colocaba mal los saltos y el contador, y cada vez que veía un pixel movido un lugar de más, tenía que retroceder paso a paso en mi bucle para encontrar el fallo.

Máscaras y operaciones lógicas para detectar teclas
Pensé que leer la flecha derecha sería tan sencillo como comparar D;JGT, pero descubrí que el registro KBD guarda todo el código ASCII, y tuve que ensayar con D=D&A para aislar el bit correcto. Ver la línea que no respondía o se desplazaba un pixel de más me frustró hasta que encontré la máscara adecuada.

### Estrategias que resultaron más efectivas
Anotar cada paso: Aunque terminé presentando el código limpio, mientras avanzaba escribía comentarios en el .asm como “// inicializa contador” o “// borra línea anterior”. Esos recordatorios me ayudaron a no perder el hilo cuando el programa crecía en complejidad.
