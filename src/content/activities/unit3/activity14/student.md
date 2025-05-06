### 1. ¿Qué aprendí en esta unidad?
En esta unidad profundicé en cómo C++ organiza la memoria y gestiona el ciclo de vida de los objetos. Comprendí la diferencia entre:

Stack vs. Heap: Vi en el depurador que un objeto declarado dentro de un bloque se crea y destruye automáticamente al entrar y salir de su scope (por ejemplo, Punto pBloque(100,200)), mientras que un objeto creado con new permanece vivo en el heap hasta que lo libero manualmente con delete.

Paso de parámetros por valor vs. por referencia vs. por puntero:

Por valor (void f(Punto p)): se crea una copia local; modificarla no afecta al original.

Por referencia (void f(Punto& p)): la función opera sobre el mismo objeto; vi que no se invocaba el destructor de copia.

Por puntero (void f(Punto* p)): sintaxis diferente pero mismo efecto que la referencia, y permite recibir nullptr.

Constructores y destructores: En cada ejemplo, colocaba mensajes en constructor y destructor, lo que me permitió ver en el orden exacto (en el output y en el depurador) cuándo se invocaban.

Variables estáticas de clase: Con la clase Contador o Tarea, comprobé que static int total vive en la sección de datos, compartido por todas las instancias, y no dentro de cada objeto.

Depuración: Aprendí a usar ventanas Locals, Watch y Memory en Visual Studio, poner breakpoints en la creación y destrucción de objetos, y a interpretar bytes en little‑endian para ver los valores de x e y.

### 2. Conceptos más desafiantes
Endianness y visualización de bytes en Memory: Al principio no entendía por qué los valores aparecían invertidos (0a 00 00 00 para el entero 10), hasta que confirmé little‑endian.

Lifetime de objetos dinámicos: Me costó recordar liberar siempre con el par correcto new[]/delete[] o new/delete, y distinguir fugas de accesos a memoria liberada.

Copy constructor vs. move constructor (aunque no lo cubrimos a fondo): al ver copias por valor me pregunté sobre optimizaciones de C++ moderno.

3. Estrategias utilizadas para comprenderlos
Experimentación práctica: Escribir código concreto, ejecutarlo y ver en el depurador.

Mensajes en constructor/destructor: Insertar cout para trazar exactamente cuándo nacen y mueren los objetos.

Lectura de documentación y ejemplos

### 4. Estrategias más efectivas
Depuración paso a paso en Visual Studio: Detenerme en cada línea clave y observar en Memory/Watches me dio la claridad más rápida.

### 5. Plan de acción para próximas unidades
Revisar y reprobar conceptos inmediatamente

Calendario de práctica

Dedicar dos sesiones semanales de 1 hora enfocadas en prácticas de Memory Management, usando ejemplos de leaks y acceso inválido.

Uso de herramientas de análisis

Aprender a usar Valgrind (o VS’s Diagnostic Tools) para detectar leaks y UBs.

Profundizar en constructores avanzados
