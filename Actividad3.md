# Sesión 3: Instrucciones, ALU, registros, saltos y control de flujo en Hack

 - **Objetivo:** ¿Qué se buscaba aprender o lograr?
   - **Proceso:** Pasos que seguiste para completar la actividad
   - **Resultados:** Lo que obtuviste o lograste
   - **Aprendizaje:** Conceptos nuevos que adquiriste
   - **Dificultades y soluciones:** Obstáculos que encontraste y cómo los superaste
   - **Conclusiones:** Reflexión sobre la importancia de lo aprendido

## 🧐**🧪✍️** Ahora experimenta.

- Predicciones:
1. apunto la dirección del registro del computador hack destinado a la pantalla
2. guardo el numero de la dirección en el registro D
3. asigno una variable llamada i (se guarda en el registro numero 16)
4. guardo el numero de direccion de la pantalla en la variable
5. uso la etiqueta kbd para apuntar la dirección del registro del computdor hack aignado al teclado
6. guardo el contenido del registro (depende el numero de la tecla que se este presionando) en el registro D
7. instancio una variable llamada keypressed (registro 17)
8. uso una funcion jump para decirle a la cpu que salte a cuando use proximamente la etiqueta si el contenido del registro d es diferente a 0. en caso de que no sea asi el programa continua normal
9. apunto la direccion del registro en el cual se guardo la variable i que inicializamos hace un rato
10. anoto el contenido de la variable en el registro temporal D, aqui habiamos anotado el registro asignado a la pantalla
11. apunto la direccion de la pantalla otra vez
12. sumo el contenido de D que era el registro de la pantalla y se lo sumo al registro de la pantalla y lo guardo en D
13. instancio otra variable llamada readkeyboard (regustro 18)
14. le digo a la cpu con una funcion jump que salte al registro de la variable que cree si el registro de la pantalla multiplicado por dos es menor o igual al numero en d el cual si sera ya que asi lo programamos
15. apunto la direccion de la variable i
16. al contenido de la variable le resto 1
17. me ubico en la dirección igual al contenido de i, que es la direccion de la pantalla menos 1
18. borro el contenido del registro igualandolo a 0
19. aqui es donde le dije a la cpu que saltara (etiqueta readkeyboard.) en caso de cumplir la condicion
20. apunto la variable que cree
21. guardo el contenido de la variable en d
22. apunto la direccion del teclado y se la resto a d
23. aqui es a donde le dije que saltara en el punto 

## 📤 **Bitácora**

Reporta en tu bitácora de aprendizaje:

- Identifica una instrucción que use la ALU y explica qué hace.
r/ cuando resto y sumo contenidos estoy usando la alu, lo que hace la alu es usar lógica creada artificialmente con compuertas lógicas para sumar, restar y comparar valores.

- ¿Para qué sirve el registro PC?
r/ sirve para indicar por que paso del programa voy es decir que registro de la rom

- ¿Cuál es la diferencia entre @i y @READKEYBOARD?
r/ i es una variable que se guardo en el registro 16 de la ram mientras readkeyboard es una etiqueta que se usa para saltar a una parte del programa que tiene instrucciones especificas.

- Describe qué se necesita para leer el teclado y mostrar información en la pantalla.
r/ 

- Identifica un bucle en el programa y explica su funcionamiento.
- Identifica una condición en el programa y explica su funcionamiento.
