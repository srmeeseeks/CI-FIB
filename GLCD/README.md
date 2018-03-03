# GLCD

Versión de la GLCD del 2017-Q1

## Table of Contents

- [Source code](#source-code)
- [Schematic capture](#schematic-capture)

## Source code

```
/* Main.c file generated by New Project wizard
 *
 * Created:   8 oct. 2014 by Josep Fernandez
 * Processor: PIC18F4550
 * Compiler:  MPLAB XC8
 */

#include <xc.h>
#define _XTAL_FREQ 8000000  

#include <string.h>
#include "config.h"
#include "GLCD.h"

const char * s1 = "Hola CI \n";

void writeTxt(byte page, byte y, char * s) {
	int i=0;
	while (*s!='\n') { 
		putch(page, y+i, *(s++));
		i++;
	};
}	

void Saluda()
{
	writeTxt(6,1, s1);
}
  
void main(void)
 {
	PORTD=0; 		   //Donem uns valors inicials als ports
	PORTB=0;  
	TRISD = 0x00;		   //Configurem D i B de sortida
	TRISB = 0x00;
    
	GLCDinit();		   //Inicialitzem la pantalla
	clearGLCD(0,7,0,127);      //Borrem pantalla
	setStartLine(0);           //Definim inici

        Saluda();
        while (1);
}
```

## Schematic capture
![Screenshot](https://github.com/srmeeseeks/CI-FIB/blob/master/GLCD/GLCD.jpg)