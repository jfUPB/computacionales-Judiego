// --------------------------------------------------
// Main loop: leer teclado y llamar a pantalla
// --------------------------------------------------
(START)
    @KBD        // 24576: registro del teclado
    D=M         // D = Tecla pulsada (0 si no hay tecla)
    @KEY
    M=D         // KEY ← D

    // CALL pantalla
    @pantalla
    0;JMP
(ret_pant)
    @START
    0;JMP

// --------------------------------------------------
// Función pantalla(valor en KEY)
// --------------------------------------------------
(pantalla)
    @KEY
    D=M         // D = valor pasado

    // if (valor == 'p') goto PAINT
    @80
    D=D-A
    @PAINT
    D;JEQ

    // if (valor == 'b') goto CLEAR
    @KEY
    D=M
    @66
    D=D-A
    @CLEAR
    D;JEQ

    // else: return
    @ret_pant
    0;JMP

// --------------------------------------------------
// Pinta la pantalla: fija todos los bits de SCREEN a 1
// --------------------------------------------------
(PAINT)
    @16384
    D=A         // D = dirección inicial de SCREEN
    @PTR
    M=D         // PTR ← 16384

(PaintLoop)
    @PTR
    A=M
    M=-1        // M[PTR] = 0xFFFF
    @PTR
    M=M+1      // PTR++
    // fin cuando PTR == 24576 (16384 + 8192 palabras)
    @24576
    D=M
    @PTR
    D=D-M
    @PaintLoop
    D;JGT      // mientras PTR < 24576

    // retorno
    @ret_pant
    0;JMP

// --------------------------------------------------
// Borra la pantalla: fija todos los bits de SCREEN a 0
// --------------------------------------------------
(CLEAR)
    @16384
    D=A
    @PTR
    M=D        // PTR ← 16384

(ClearLoop)
    @PTR
    A=M
    M=0        // M[PTR] = 0
    @PTR
    M=M+1      // PTR++
    // fin cuando PTR == 24576
    @24576
    D=M
    @PTR
    D=D-M
    @ClearLoop
    D;JGT      // mientras PTR < 24576

    // retorno
    @ret_pant
    0;JMP

// --------------------------------------------------
// Variables en RAM
// --------------------------------------------------
    // KEY  = R13
    // PTR  = R14
    // (R15 libre para usos futuros)
(KEY)   @R13
        M=0
(PTR)   @R14
        M=0
