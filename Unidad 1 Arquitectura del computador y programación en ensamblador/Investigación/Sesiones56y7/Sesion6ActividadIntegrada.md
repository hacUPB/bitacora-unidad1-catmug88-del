# Sesión 6. Punteros, arreglos y relación entre direcciones de memoria y código de alto nivel

Traduce el código a lenguaje ensamblador usando punteros:

```
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```
Mi traducción:
```
@10
D=A
@a
M=D
@5
D=A
@b
M=D
@a
D=A
@p
M=D
@p
A=M
D=M
@b
M=D
(END)
@END
0;JMP
```

Explicación:
El programa inicia creando dos variables: a, con el valor 10, y b, con el valor 5. Luego crea un puntero p y le asigna la dirección de memoria de a, de manera que p queda apuntando a esa variable.

Después, el programa accede al contenido de la dirección almacenada en p, es decir, al valor de a, y copia ese valor en la variable b. Como a contiene el número 10, al finalizar la ejecución b deja de valer 5 y pasa a valer 10, mientras que a conserva su valor original.