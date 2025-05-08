### 1. ¿Qué ocurre al copiar un objeto en C++?
Se construye copia como una nueva instancia de Punto.

El copy constructor por defecto de C++ hace una copia “membro a membro”:

Para tipos triviales (int x, y), copia los valores.

Para std::string name, invoca su propio copy constructor, creando un buffer independiente.

Direcciones distintas

En el depurador verás que &original != &copia (ambos en el stack).

Si inspeccionas internamente el std::string, sus punteros internos también apuntan a regiones distintas.

Independencia total

Modificar copia.name, copia.x, copia.y no afecta a original.

### ¿Qué ocurre al “copiar” un objeto en C#?
Una referencia (puntero) al mismo objeto Punto que original.

¿Es una copia independiente de original?

C++: Sí, completamente independiente.

C#: No; es un alias al mismo objeto, cualquier cambio se refleja en ambas variables.
