![image](https://github.com/user-attachments/assets/4f2c3122-80b2-414f-8ee8-633bde70d5b5)
``` bash
+------------------------------------------------------+
| 0x7FFFFFFFE4A8 – 0x7FFFFFFFE4A0  Stack               |
|   – &c (variable local c)       = 0x7FFFFFFFE4A0     |
|   – &b (variable local b)       = 0x7FFFFFFFE4A4     |
|   – &a (variable local a)       = 0x7FFFFFFFE4A8 ← breakpoint aquí
+------------------------------------------------------+
| 0x00603000 – …                Heap                  |
|   – arrayHeap (puntero al primer elemento) = 0x00603010
+------------------------------------------------------+
| 0x00602000 – 0x00602FFF     Datos estáticos         |
|   – global_inicializada            = 0x00602010     |
|   – global_no_inicializada         = 0x00602014     |
|   – var_estatica (static)          = 0x00602018     |
+------------------------------------------------------+
| 0x00601000                .rodata (solo lectura)    |
|   – mensaje_ro (“Hola, memoria…”) = 0x00601020     |
+------------------------------------------------------+
| 0x00400000 – 0x0040FFFF     Segmento de código      |
|   – dirección base del programa    = 0x00400000     |
|   – &suma                           = 0x00400580     |
|   – &funcionConStatic               = 0x00400620     |
+------------------------------------------------------+
```
