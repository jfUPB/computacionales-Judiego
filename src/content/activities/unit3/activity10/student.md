Después de llamar a la función por valor (void cambiarNombre(Punto p, string nuevoNombre)):

Se crea una copia de original en la pila de la función; eso invoca el constructor de copia implícito.

Al salir de la función, esa copia (que internamente había cambiado su nombre a “cambiado”) se destruye, por eso ves el mensaje
“Destructor: Punto cambiado(70, 80) destruido.”

El objeto original de main no se modifica, porque solo trabajaste sobre la copia.

original sigue existiendo tras la llamada porque su ciclo de vida abarca todo el main. La versión por valor no toca a original, solo crea y destruye una instancia temporal dentro de la función.

Con el depurador:

&original vive en el stack de main.

El parámetro p vive en el stack de cambiarNombre, en una dirección diferente.

No son el mismo objeto: ocupan posiciones de memoria distintas.

Al cambiar la función a recibir por referencia (void cambiarNombre(Punto& p, string nuevoNombre)):

Ya no se crea copia alguna.

p es un alias a original, de modo que modificar p.name altera directamente original.name.

No ves ningún mensaje de destructor intermedio porque no hubo objeto copia.

Al cambiar la función a recibir un puntero (void cambiarNombre(Punto* p, string nuevoNombre) y llamarla con &original):

Tampoco se crea copia.

p es un puntero que apunta a original; p->name = … modifica el objeto real.

El comportamiento es equivalente al paso por referencia, con la diferencia de la sintaxis explícita del puntero.

Diferencias entre pasar por valor, referencia y puntero:

Por valor: se copia todo el objeto (mayor sobrecarga), modificaciones no afectan al original, la copia se destruye al salir de la función.

Por referencia: no hay copia, no se incurre en sobrecarga, modificas el objeto original directamente, sintaxis parecida al paso por valor.

Por puntero: tampoco hay copia, modificas el original, pero la sintaxis deja claro que trabajas con una dirección y permite pasar nullptr si quisieras.
