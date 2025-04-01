using System;

class ejercicio9
{
    static int[] SCREEN = new int[8192]; // 512 * 256 / 16
    static int KBD = 0; // Simula la entrada del teclado
    static int RAM16;

    static void Main()
    {
        RAM16 = 16384; // RAM[16] <- 16384

        while (true) // Simula el loop del programa
        {
            int value = SCREEN[0]; // Leer el primer valor de SCREEN
            if (value != 0)
            {
                RAM16 = 0;
                continue; // Reinicia el loop si SCREEN[0] != 0
            }

            int temp = RAM16 - 16384;
            if (temp <= 0)
            {
                SCREEN[4] = 0; // Guarda 0 en SCREEN[4]
                continue; // Reinicia el loop
            }

            RAM16 -= 1;
            int temp2 = RAM16 - 16384;
            if (temp2 >= 0)
            {
                SCREEN[4] = temp2;
                continue;
            }

            RAM16 += 1;
        }
    }
}
