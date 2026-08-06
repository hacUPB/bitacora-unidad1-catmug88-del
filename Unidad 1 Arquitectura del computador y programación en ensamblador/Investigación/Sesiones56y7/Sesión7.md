## Sesión 7.

### Autoevaluación

**Mirando hacia adentro: autoevaluación de conceptos y proceso**

El objetivo de esta actividad es doble. Primero, que puedas recuperar de tu memoria los conceptos fundamentales de la unidad sin ayuda de tus notas. Este proceso de “recordar” es una de las formas más efectivas de fortalecer tu memoria a largo plazo. Segundo, que reflexiones sobre *cómo* has aprendido, para que puedas identificar qué estrategias te funcionan mejor.

En la primera sesión hablamos de la arquitectura del computador hack de 16 bits de nand2 tetris, la cual consiste en una cpu y una memoria y unos buses que comunica ambas partes. Dentro de la cpu está la ALU es decir la unidad de logica y aritmetica la cual procesa todas las instrucciones de razonamiento logico utilizando compuertas lógicas básicas y asi logra hacer calculos complejos como suma, restas, contar, comparar entre muchas otras. Dentro de la memoria esta la RAM o random access memory la cual contiene registros en los cuales se almacenan datos, tambien tiene registros destinados a variables, la pantalla y el teclado.
Además esta la ROM o read only memory la cual contiene las instrucciones que se programan en ensamblador.

En la segunda sesión profundizamos en las diferentes tipos de instrucciones en lenguaje ensamblador, lo mas basico que mas tarde usariamos para crear: condicionales, ciclos, punteros, arreglos y programas complejos. 

Casilleros:
A - la direccion a la que este apuntando la cpu en la Ram 
D - casillero temporal para guardar datos y aplicar instrucciones lógicas
PC - program counter, cuenta el paso o instruccion que se haya ejecutado mas recientemente

Tipos de instrucciones:
1. Adress (@): estas se utilizan para apuntar a un registro especifico en la RAM
2. Lógicas (ALU): Usando +, - y = puedes realizar operaciónes lógicas, pero no puedes usar números a excepcion del 0 y 1, de querer operar con un número grande, debes apuntar a cierta direccion en la RAM y guardarla en el casillero temporal D, para despues operar con este. (o usar una variable)
3. Etiquetas: Usando @ para apuntar a cierta instruccion, y () para nombrar el lugar donde esta escrito el codigo, puedes crear ciclos, bucles y condicionales con esto.
4. JMP: sirve para decirle a la cpu que salte hasta cierta isntruccion. Existen varios tipos de jump: D;JLT(lower than) D;JGT(greater than) D;JNE (not equal) D;JEQ (equal) D;JLE (lower or equal) D;JGE (greater or equal). Aquí le estarias diciendo a la cpu que compare el valor de D respecto a 0 y dependiendo de eso salta o no a la instruccion llamada previamente con @.

En las siguientes sesiones compartimos sobre el lenguaje máquina o binario y de como se utiliza para referirse a más numeros incluso números negativos. También discutimos términos aprendidos previamente en POO como arreglos, punteros y de como aplicarlos en el computador hack de nand2tetris.