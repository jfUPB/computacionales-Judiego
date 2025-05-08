![image](https://github.com/user-attachments/assets/11b090e9-50c8-4594-bc5d-51123a08439a)
![image](https://github.com/user-attachments/assets/98c52152-e795-4c6d-8c9a-2c0b314fc71c)

### Continuar
Reactiva la ejecución hasta el siguiente breakpoint o hasta el final del programa si no quedan más puntos de interrupción.
ejemplo: colocar un breakpoint en int a = 5; y pulsar F5, el programa se detiene ahí. Si vuelves a pulsar F5, continuará hasta el próximo breakpoint (por ejemplo, dentro de sum) o hasta que termine la ejecución y veas la salida en la consola.

### paso a paso 
 Ejecuta la línea actual y se detiene en la siguiente, sin entrar en llamadas a funciones.
 ejemplo: Si estoy en la línea std::cout << ... sum(a,b); y presiono F10, se calcula toda la llamada a sum internamente

 ### Entrar en la función
 Ejecuta la línea actual y, si hay una llamada a función, entra dentro de su cuerpo y se detiene en la primera línea de esa función.
 ejemplo: Con el cursor en sum(a, b) y pulsando F11, saltarás al primer renglón de int sum(int a, int b) para ver paso a paso cómo se suman a y b.

 ### Salir de la función
 Si estoy dentro de una función, ejecuta rápidamente hasta el punto donde fue llamada y se detiene justo después de la llamada.
 ejemplo: Después de investigar dentro de sum, pulsar Shift+F11 te llevará de vuelta al std::cout en main, justo tras recibir el valor retornado.

 ### Reiniciar
 Detiene la depuración actual y vuelve a iniciarla desde el principio
 ejemplo: Si quiero probar otra vez cambiando el valor de b a 10, uso Restart para volver a empezar sin tener que detener y luego volver a depurar manualmente.

 ### Detener depuración
 Finaliza inmediatamente la sesión de depuración actual, cerrando la consola y liberando recursos.
 pulsa Stop para regresar al modo edición normal.

 ### Breakpoints 
 Marca líneas donde la ejecución se detendrá automáticamente. Pulsar F9 sobre una línea añade o quita el breakpoint.
 Si quiero detener justo antes de llamar a sum, pongo un breakpoint en la línea int b = 7; para inspeccionar valores antes de la suma.
