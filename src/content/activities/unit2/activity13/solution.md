## Lo que aprendí en esta unidad
En esta unidad aprendí a programar en lenguaje ensamblador Hack y a traducir conceptos de alto nivel a instrucciones de bajo nivel y me permitió entender cómo funciona una computadora a nivel de hardware, especialmente en la gestión de memoria y ejecución de instrucciones.

Un ejemplo de lo que aprendí fue la manipulación de arreglos usando punteros. En un lenguaje de alto nivel como C, acceder a elementos de un arreglo y modificarlos es sencillo, pero en ensamblador se requiere calcular manualmente la dirección de memoria y modificar los valores directamente. Implementé un programa donde un puntero recorría un arreglo y duplicaba cada uno de sus valores.

Otro concepto clave que aprendí fue la implementación de funciones en ensamblador, necesite manejo de saltos y la simulación de parámetros y retornos de valor. Diseñé una función de suma que recibía dos parámetros y retornaba el resultado, implementando un mecanismo de salto a una dirección de retorno.

## Conceptos más desafiantes de la unidad
Uno de los conceptos más difíciles fue el uso de punteros para manipular variables y arreglos. En lenguajes de alto nivel, las operaciones con punteros son fáciles de manejar pero en ensamblador fue mas dificil calcular manualmente las direcciones y asegurarse de modificar la memoria correcta.

Otro concepto fue la simulación de funciones con parámetros y valores de retorno porque las funciones tienen un mecanismo claro para pasar argumentos y recibir resultados y en ensamblador tuve que simular este comportamiento usando registros y saltos condicionales.

## Estrategias utilizadas para comprender los conceptos desafiantes
Para entender mejor estos temas, utilicé varias estrategias:

Dividí cada ejercicio en pasos más pequeños para entender su funcionamiento antes de escribir código en ensamblador. Usé el simulador Hack para visualizar la ejecución de cada instrucción y verificar que los valores en memoria eran los esperados.

 y añadí notas en cada línea de código ensamblador para entender qué hacía cada instrucción y evitar confusiones.

## Estrategias más efectivas
Las estrategias más útiles fueron la simulación paso a paso y la comparación con código en alto nivel. Ver la ejecución en el simulador me permitió corregir errores rápidamente y asegurarme de que las instrucciones estaban funcionando correctamente. También, al escribir primero el código en C, tuve una referencia clara de la lógica que debía implementar en ensamblador, lo que facilitó la traducción.
