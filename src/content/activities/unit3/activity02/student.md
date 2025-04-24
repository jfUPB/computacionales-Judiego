``` cpp
#include <iostream>

using namespace std;

// Intento de swap por valor: no modifica las variables originales
void swapPorValor(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    // Dentro de esta función, a y b se intercambian, pero son copias
}

// Swap por referencia: modifica las variables originales
void swapPorReferencia(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

// Swap por puntero: modifica las variables originales a través de direcciones
void swapPorPuntero(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x, y;

    // 1) Swap por valor
    x = 5; y = 10;
    cout << "Antes de swapPorValor: x = " << x << ", y = " << y << endl;
    swapPorValor(x, y);
    cout << "Después de swapPorValor: x = " << x << ", y = " << y << endl;
    cout << endl;

    // 2) Swap por referencia
    x = 5; y = 10;
    cout << "Antes de swapPorReferencia: x = " << x << ", y = " << y << endl;
    swapPorReferencia(x, y);
    cout << "Después de swapPorReferencia: x = " << x << ", y = " << y << endl;
    cout << endl;

    // 3) Swap por puntero
    x = 5; y = 10;
    cout << "Antes de swapPorPuntero: x = " << x << ", y = " << y << endl;
    swapPorPuntero(&x, &y);
    cout << "Después de swapPorPuntero: x = " << x << ", y = " << y << endl;
    cout << endl;

    return 0;
}
```
## preguntas
1. ¿Por qué swapPorValor no logra intercambiar x e y en main()?
   Porque los parámetros a y b se reciben por valor: la función trabaja con copias locales de x e y, de modo que cualquier intercambio solo afecta a esas copias, no a las variables originales.

2. ¿Cómo y por qué logran swapPorReferencia y swapPorPuntero modificar las variables originales?
   - swapPorReferencia recibe referencias (alias) a x e y, así que a y b dentro de la función son nombres alternativos de las variables originales; intercambiarlos altera directamente x e y.
   - swapPorPuntero recibe punteros a x e y (direcciones de memoria). Mediante el operador de indirección (*) accede y modifica el contenido apuntado, cambiando el valor de las variables originales.

3. ¿Cuáles son las ventajas y consideraciones de usar referencias versus punteros en este caso?
   - Referencias:
      Sintaxis más limpia: se usan como variables normales sin operadores extra.
      Garantía de que no son nulas: siempre refieren a un objeto válido.
      No se pueden reseatear: un alias siempre apunta al mismo objeto.
   - Punteros:
      Más flexibles: pueden apuntar a distintas direcciones, incluso reasignarse.
      Pueden representar ausencia (nullptr) para indicar que no apuntan a ningún objeto.
      Requieren manejo explícito de la indirección (*), lo que puede ocasionar errores si no se controla (punteros nulos, aritmética de punteros, etc.).
