## Sesión 7.

### Autoevaluación

**Mirando hacia adentro: autoevaluación de conceptos y proceso**

El objetivo de esta actividad es doble. Primero, que puedas recuperar de tu memoria los conceptos fundamentales de la unidad sin ayuda de tus notas. Este proceso de “recordar” es una de las formas más efectivas de fortalecer tu memoria a largo plazo. Segundo, que reflexiones sobre *cómo* has aprendido, para que puedas identificar qué estrategias te funcionan mejor.

### Resumen general:

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

## Preguntas
## Parte 1: Conceptos del computador Hack

**1. Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?**

El ciclo Fetch-Decode-Execute es el proceso que sigue el computador para ejecutar instrucciones. En la fase de **Fetch**, el computador busca en la memoria la siguiente instrucción que debe ejecutar. En la fase de **Decode**, interpreta esa instrucción para entender qué operación debe realizar y qué componentes debe utilizar. En la fase de **Execute**, realiza la operación indicada, como una suma, una transferencia de datos o un salto.

El **Program Counter (PC)** es el encargado de guardar la dirección de la siguiente instrucción que debe ejecutarse. Después de cada instrucción, el PC normalmente aumenta para continuar con la siguiente, pero puede cambiar si ocurre un salto o una condición que modifica el flujo del programa.

---

**2. ¿Cuál es la diferencia fundamental entre una instrucción-A y una instrucción-C en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.**

La instrucción-A se utiliza principalmente para seleccionar una dirección de memoria o cargar un valor en el registro A. Es una instrucción que permite indicar dónde se encuentra un dato que se quiere utilizar.

La instrucción-C es la que realiza operaciones o acciones dentro del computador, como cálculos en la ALU, movimientos de datos entre registros y saltos en el programa.

Un ejemplo de instrucción-A sería cargar la dirección de una variable en memoria. Un ejemplo de instrucción-C sería realizar una suma entre valores almacenados en registros o guardar un resultado en memoria.

---

**3. Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU.**

El registro **D** es un registro utilizado principalmente para almacenar datos temporales y resultados de operaciones. Sirve como un espacio de almacenamiento rápido para que la computadora pueda trabajar con valores.

El registro **A** puede almacenar valores o direcciones de memoria. Es importante porque permite acceder a posiciones específicas de la memoria RAM.

La **ALU** es la unidad encargada de realizar operaciones matemáticas y lógicas, como sumas, restas, negaciones y comparaciones. Es el componente que procesa los datos y genera resultados.

---

**4. ¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo.**

Un salto condicional en Hack se realiza mediante una instrucción que evalúa el resultado almacenado en la ALU y decide si debe cambiar la dirección de ejecución. Por ejemplo, si se quiere saltar cuando un valor es mayor que cero, primero se coloca ese valor en el registro correspondiente, luego la computadora revisa la condición y, si se cumple, modifica el PC para ir a otra parte del programa.

---

**5. ¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo.**

Un loop se implementa usando etiquetas y saltos. El programa marca un punto de inicio y al final del ciclo realiza un salto que vuelve a ese punto. Dentro del ciclo se modifica una variable que controla la repetición. Por ejemplo, un contador puede comenzar con un valor determinado, disminuir en cada repetición y cuando llega a cero se realiza un salto para salir del ciclo.

---

**6. ¿Cuál es la diferencia entre la instrucción D=M y M=D?**

La diferencia está en la dirección del movimiento de datos. En la instrucción **D=M**, el valor almacenado en la memoria se copia hacia el registro D. En cambio, en **M=D**, el valor que está en el registro D se copia hacia la memoria. Una lee un dato de memoria y la otra escribe un dato en memoria.

---

**7. Describe brevemente qué se necesita para leer un valor del teclado (KBD) y para pintar un pixel en la pantalla (SCREEN).**

Para leer un valor del teclado se debe acceder a la dirección de memoria asociada al teclado, donde el computador almacena la información de la tecla presionada.

Para pintar un pixel en la pantalla se debe modificar la memoria asociada a la pantalla. Cada posición de esa memoria representa una parte de la imagen, por lo que al cambiar sus valores se pueden encender o apagar píxeles.

---

**8. Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack.**

En Hack, un puntero se representa almacenando una dirección de memoria dentro de una variable. El puntero no guarda directamente el dato, sino la ubicación donde se encuentra ese dato.

Para asignar un puntero a una variable, primero se guarda la dirección de esa variable. Luego, para modificar el contenido al que apunta el puntero, se utiliza esa dirección almacenada para acceder a la memoria y cambiar su valor.

---

**9. ¿Cómo implementarías el acceso a un elemento de un arreglo, como arr[j], en lenguaje ensamblador?**

Para acceder a un elemento de un arreglo se necesita conocer la dirección base del arreglo, que corresponde a la posición donde comienza el primer elemento. Luego se suma el índice del elemento que se quiere buscar. El resultado de esa suma indica la dirección exacta donde se encuentra el dato.

La dirección base indica el inicio del arreglo y el índice indica cuántas posiciones se deben avanzar para encontrar el elemento deseado.

---

# Parte 2: Reflexión sobre tu proceso (metacognición)

**1. ¿Cuál fue el concepto o actividad más desafiante de esta unidad para ti y por qué?**

El concepto más desafiante fue traducir programas de un lenguaje de alto nivel como C++ a ensamblador Hack, especialmente porque en C++ existen instrucciones más sencillas como ciclos, arreglos y punteros, mientras que en ensamblador se deben construir manualmente mediante operaciones básicas y manejo de memoria.

---

**2. La metodología de “predecir, ejecutar, observar y reflexionar” fue central en nuestras actividades. ¿En qué momento te resultó más útil?**

Fue más útil al trabajar con programas en ensamblador donde era difícil saber qué estaba ocurriendo solamente leyendo las instrucciones. Al observar los resultados después de ejecutar el programa se podía comparar con la predicción inicial y entender mejor cómo funcionaba cada instrucción.

---

**3. Describe un momento “¡Aha!” que hayas tenido durante esta unidad.**

Un momento importante fue entender que estructuras como los ciclos y los arreglos de C++ no existen directamente en ensamblador, sino que deben construirse usando saltos, etiquetas y operaciones con memoria. Comprender esa relación ayudó a ver cómo funcionan realmente los programas a bajo nivel.

---

**4. Pensando en la próxima unidad, ¿qué harás diferente en tu proceso de estudio?**

Intentaría practicar más con ejercicios pequeños antes de hacer programas completos, entendiendo primero cada instrucción individualmente y luego combinándolas. También revisaría más los errores para entender por qué ocurren.

---

**5. ¿Cuál fue el concepto más abstracto o difícil de traducir de C++ a ensamblador en esta unidad?**

El concepto más difícil fue el de los punteros, porque en C++ se manejan de forma sencilla, pero en ensamblador se debe trabajar directamente con direcciones de memoria. Para entenderlo fue necesario relacionar los punteros con posiciones específicas donde se almacenan los datos.

---

**6. En la actividad de arreglos se sugirió construir el programa paso a paso mediante pruebas. ¿Cómo te ayudó este enfoque?**

Ayudó a dividir un problema grande en partes más pequeñas. En lugar de intentar hacer todo el programa de una vez, se podía verificar primero que funcionara la creación del arreglo, luego el ciclo y finalmente la suma. Esto facilitó encontrar errores y entender cada parte.

---

**7. ¿Qué concepto de bajo nivel te sientes más seguro de poder identificar cuando lo veas implementado en C++?**

Me siento más seguro identificando los ciclos y las operaciones con variables, porque ahora entiendo que detrás de ellos existen comparaciones, saltos y movimientos de datos en memoria. También tengo una mejor idea de cómo los arreglos y punteros utilizan direcciones de memoria internamente.
