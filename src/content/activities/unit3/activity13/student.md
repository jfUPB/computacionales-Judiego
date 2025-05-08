```cpp
#include <iostream>
#include <string>
using namespace std;

class Tarea {
public:
    string nombre;              // atributo de instancia
    bool completada;            // atributo de instancia
    static int totalTareas;     // atributo estático

    // Constructor
    Tarea(const string& _nombre, bool _completada = false)
      : nombre(_nombre), completada(_completada)
    {
        totalTareas++;
        cout << "Constructor: Tarea \"" << nombre
             << "\" creada. TotalTareas = " << totalTareas << endl;
    }

    // Destructor
    ~Tarea() {
        cout << "Destructor: Tarea \"" << nombre << "\" destruida." << endl;
    }

    // Método para marcar completada
    void marcar() {
        completada = true;
    }

    // Imprimir estado
    void imprimir() const {
        cout << "Tarea \"" << nombre << "\" – "
             << (completada ? "✓ completada" : "✗ pendiente")
             << endl;
    }
};

// Definición del miembro estático
int Tarea::totalTareas = 0;

// Función que recibe Tarea **por valor**
void procesarPorValor(Tarea t) {
    cout << "[procesarPorValor] Antes de marcar: ";
    t.imprimir();
    t.marcar();
    cout << "[procesarPorValor] Después de marcar: ";
    t.imprimir();
    // Al salir, se destruye la copia ‘t’
}

// Función que recibe Tarea 
void procesarPorRef(Tarea& t) {
    cout << "[procesarPorRef] Antes de marcar: ";
    t.imprimir();
    t.marcar();
    cout << "[procesarPorRef] Después de marcar: ";
    t.imprimir();
    // No hay copia: modifica el objeto original
}

int main() {
    cout << "=== Creación en stack ===" << endl;
    Tarea t1("Comprar leche");         // stack
    t1.imprimir();

    cout << "\n=== Paso por valor ===" << endl;
    procesarPorValor(t1);
    cout << "Estado de t1 tras procesarPorValor: ";
    t1.imprimir();                     // sigue sin completarse

    cout << "\n=== Paso por referencia ===" << endl;
    procesarPorRef(t1);
    cout << "Estado de t1 tras procesarPorRef: ";
    t1.imprimir();                     // ahora sí está completada

    cout << "\n=== Creación dinámica (heap) ===" << endl;
    Tarea* pT2 = new Tarea("Limpiar casa");  // heap
    pT2->imprimir();

    cout << "\n=== Uso de puntero y delete ===" << endl;
    pT2->marcar();
    pT2->imprimir();
    delete pT2;                        // invoca destructor

    cout << "\n=== Estado final de totalTareas ===" << endl;
    cout << "Tarea::totalTareas = " << Tarea::totalTareas << endl;

    return 0;
}
```

