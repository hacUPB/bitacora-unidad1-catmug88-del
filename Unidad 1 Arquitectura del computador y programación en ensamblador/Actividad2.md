# Sesión 2
## Modelo Hack y ciclo fetch-decode-execute
```
		@1
			D=A
			@2
			D=D+A
			@16
			M=D
(END)
			@END
			0;JMP
```

**¿Qué crees que haga este programa?**
Esta es mi explicación linea por linea:
1. `@1` Se llama la direccion del casillero numero 1 (A=1).
2. `D=A` El numero guardado en A fue el numero del casillero, en esta linea se guarda temporalmente en D (A=1 y D=1).
3. `@2`se llama al casillero 2 (A=2).
4. `D=D+A` Se toma el 1 guardado anteriormente en D, se le suma el 2 guardado en A y se guarda el resultado en d es decir en este momento dle programa D=3, como podemos evidenciar con este screenshot del simulador:
![alt text](image.png)
5. `@16` Se llama al casillero número 16
6. `M=D` Se toma el contenido guardado en D y se guarda en el casillero número 16.
7. `@END
			0;JMP` Fin del programa.

## Conceptos clave:
**Fetch (buscar):** la CPU obtiene (lee) la siguiente instrucción desde la memoria. El contador de programa (PC) indica dónde se encuentra esa instrucción en la memoria ROM.

**Decode (decodificar):** la CPU interpreta la instrucción que acaba de leer. Esto significa entender qué operación debe realizarse y qué datos o recursos necesita.

**Execute (ejecutar):** la CPU realiza la operación indicada. Por ejemplo, puede ser una operación matemática, mover datos entre registros, o acceder a la memoria.

## Preguntas en clase

`¿Qué sucede?` Se realiza el programa de la manera que anticipé.

``¿Qué valor se almacena en la dirección de memoria 16?`` 3

 ``¿Por qué crees que es ese valor?`` Porque después de realizar la operación matemática, llamamos al casillero 16 y con **M=D** guardamos el resultado de la operación dentro de este casillero. Según la explicación del profesor, M es el contenido del casillero que se haya llamado mas recientemente, se puede saber en que casillero se guardó viendo los registros, en específico el registro A, este dicta el número del casillero que esté seleccionado.

 ``¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute? `` Realmente cada 

 ``¿Qué cambios observas en el contenido de la memoria y los registros?``

 ## Conceptos de lenguaje ensamblador

 ![alt text](image-1.png)

 En esta imagen están los diferentes tipos de saltos, los cuales son muy importantes en la programación en lenguaje ensamblador ya que a partir de estos se pueden crear ciclos y condicionales en el programa. 