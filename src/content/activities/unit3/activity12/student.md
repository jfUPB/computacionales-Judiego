### Ciclo de vida de un objeto en el stack vs. en el heap

En C++, los objetos pueden tener diferentes duraciones de vida dependiendo de cómo se crean:

Objetos en el stack (automáticos): Se crean automáticamente cuando se declara una variable dentro de un bloque de código (como una función o un bloque {}). Su memoria se asigna en la pila (stack) y se libera automáticamente al salir del bloque. Esto significa que su constructor se llama al entrar en el bloque y su destructor se invoca al salir del mismo.

Objetos en el heap (dinámicos): Se crean utilizando el operador new, lo que asigna memoria en el montón (heap). Estos objetos persisten más allá del bloque en el que se crean y deben ser liberados manualmente utilizando el operador delete. Si no se libera la memoria, se produce una fuga de memoria.

### ¿Compila? ¿Por qué?
No, el segundo ejemplo no compila. El puntero pBloque2 se declara dentro del segundo bloque, por lo que su ámbito está limitado a ese bloque. Al intentar acceder a pBloque2 fuera de su ámbito para llamar a pBloque2->imprimir(); y delete pBloque2;, el compilador genera un error porque pBloque2 no está definido en ese contexto.

### Modificación del programa:
declarar pBloque2 fuera del bloque e inicializarlo dentro
Al declarar Punto* pBloque2 = nullptr; fuera del bloque y luego asignarle una instancia de Punto dentro del bloque con pBloque2 = new Punto(500, 600);, el programa compila y funciona correctamente. Esto se debe a que pBloque2 tiene un ámbito que abarca todo el main, y aunque la instancia de Punto se crea dentro de un bloque, su dirección se almacena en pBloque2, que es accesible fuera del bloque.

### ¿Por qué pBloque se destruye al salir del bloque y pBloque2 no?
pBloque es un objeto creado en el stack dentro de un bloque, por lo que su destructor se llama automáticamente al salir del bloque, liberando la memoria asociada.

En cambio, pBloque2 es un puntero a un objeto creado dinámicamente en el heap. Aunque el puntero pBloque2 puede tener un ámbito limitado, el objeto al que apunta permanece en memoria hasta que se llama explícitamente a delete pBloque2;.

Es importante destacar que pBloque2 es un puntero (una variable que almacena una dirección de memoria) que reside en el stack, mientras que el objeto Punto al que apunta se encuentra en el heap

Punto* pBloque2 = nullptr;
{
    pBloque2 = new Punto(500, 600);
    pBloque2->imprimir();
}
pBloque2->imprimir();
delete pBloque2;
