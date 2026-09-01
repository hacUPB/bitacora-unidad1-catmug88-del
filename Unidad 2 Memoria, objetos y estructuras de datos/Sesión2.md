# Actividad 3: Mapa de memoria de un programa escrito en C++

Revisando el código:
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;
// Variables globales
int global_inicializada = 42;
int global_no_inicializada;
// Constante global
const char* const mensaje_ro = "Hola, memoria de solo lectura";
// Función de ejemplo que muestra la dirección de su variable local estática
void funcionConStatic() {
	static int var_estatica = 100;
	cout << "Dirección de var_estatica (static): " << &var_estatica << endl;
	}
// Función que asigna memoria dinámica (heap)
int* crearArrayHeap(int tam) {
	int* arr = new int[tam];
	for (int i = 0; i < tam; i++) {
		arr[i] = i;
		}    return arr;
	}
// Una función simple para representar el código (se encontrará en la región de código)
int suma(int a, int b) {
		int c = a + b; // "c" es una variable local (stack)
		return c;
}
int main() {
// Variable local (stack)
		int a = 10;
		int b = 20;
		int c = suma(a, b);
    cout << "Resultado de suma(a, b): " << c << endl;
    cout << "Dirección de variable local 'a': " << &a << endl;
    cout << "Dirección de variable local 'b': " << &b << endl;
    cout << "Dirección de la variable local 'c' (resultado): " << &c << endl;
    // Variables globales
    cout << "Dirección de 'global_inicializada': " << &global_inicializada << endl;
    cout << "Dirección de 'global_no_inicializada': " << &global_no_inicializada << endl;
    // Constante global (solo lectura)
    cout << "Dirección de 'mensaje_ro' (zona de solo lectura): " << static_cast<const void*>(mensaje_ro) << endl;
    // Llamada a función que tiene variable estática
    funcionConStatic();
    // Uso del Heap: asignación dinámica
    int tamArray = 10;
    int* arrayHeap = crearArrayHeap(tamArray);
    cout << "Dirección del primer elemento del array asignado en Heap: " << arrayHeap << endl;
    for (int i = 0; i < tamArray; i++) {
		    cout << "arrayHeap[" << i << "] = " << arrayHeap[i] << " en " << (arrayHeap + i) << endl;
		    }
		delete[] arrayHeap; // Liberamos la memoria dinámica
    return 0;
    }
```

Crea el mapa de memoria ubicando cada variable y funcion dentro de su respectiva sección:

### Sección 1: segmento de código 
- void funcionConStatic()
- int* crearArrayHeap(int tam)
- int suma(int a, int b)
- int main()

### Sección 2: variables globales y estáticas
- int global_inicializada = 42;
- int global_no_inicializada;
- static int var_estatica = 100;

### Sección 3: Stack
- int a = 10;
int b = 20;
int c = suma(a, b);
int tamArray = 10;
int* arrayHeap = crearArrayHeap(tamArray);

### Sección 4: Heap
arrayHeap está en el stack y la memoria dinámica a la que apunta está en el heap

# Actividad 4: Experimentos

### Experimento 1: modificar el segmento de texto
``` cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main() {
		// Variable local (stack)
		int a = 10;
		int b = 20;
    /**********************************************************
    EXPERIMENTO 1
    ***********************************************************/
    void* ptr = reinterpret_cast<void*>(&main);
    cout << "Voy a modificar la memoria en la dirección: " << ptr << endl;
    *reinterpret_cast<int*>(ptr) = 0;
    /********************************************************/
    return 0;
    }
```
¿Qué ocurre? ¿Por qué?

R/ En este código se intenta modificar la memoria donde está almacenada la función main() pero eso es imposible porque el segmento de código solo permite leer y ejecutar las instrucciones, pero no modificarlas. Por eso el programa puede terminar con una violación de acceso o un error de memoria.

### Experimento 2: modificar el segmento de datos (constante global):
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;
// Constante global
const char* const mensaje_ro = "Hola, memoria de solo lectura";

int main() {
		// Variable local (stack)
		int a = 10;
		int b = 20;

    /**********************************************************
    EXPERIMENTO 2
    ***********************************************************/
    char* ptr = (char*)&mensaje_ro;
    cout << "Voy a modificar la memoria en la dirección: " << ptr << endl;
    *ptr = 0;
    /********************************************************/
    return 0;
    }
```
¿Qué ocurre? ¿Por qué?

R/ En este código se intenta modificar la memoria de la constante global mensaje_ro. Primero se obtiene su dirección y luego se intenta cambiar su contenido a 0. Esto puede provocar un error porque la constante y, especialmente, el texto al que apunta se encuentran en una zona de memoria que normalmente no permite escritura. Por eso el programa puede terminar con una violación de acceso o un error de memoria.

### Experimento 3: modificar el segmento de datos (variables globales):
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;
// Variables globales
int global_inicializada = 42;
int global_no_inicializada;

int main() {    // Variable local (stack)
		int a = 10;
		int b = 20;

    /**********************************************************
    EXPERIMENTO 3
    ***********************************************************/
    cout << "global_inicializada: " << global_inicializada << endl;
    cout << "global_no_inicializada: " << global_no_inicializada << endl;

    global_inicializada = 69;
    global_no_inicializada = 666;
    cout << "global_inicializada: " << global_inicializada << endl;
    cout << "global_no_inicializada: " << global_no_inicializada << endl;
    /********************************************************/
    return 0;
    }
```
¿Qué ocurre? ¿Por qué?

R/ En este código hay dos variables globales, una de valor 42 y otra sin valor, primero se muestran sus valores y después se modifican a 69 y 666.

 Esto funciona normalmente porque las variables globales se almacenan en una zona de la memoria que permite cambiar sus valores durante la ejecución del programa.

### Experimento 4: modificar la variable local estática de una función por fuera de ella:
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;
// Función de ejemplo que muestra la dirección de su variable local estática
void funcionConStatic() {
		static int var_estatica = 100;
		cout << "Dirección de var_estatica (static): " << &var_estatica << endl;
}

int main() {    // Variable local (stack)
		int a = 10;
		int b = 20;
    /**********************************************************
    EXPERIMENTO 4
    ***********************************************************/
    var_estatica = 42;
    cout << "var_estatica: " << var_estatica << endl;
    /********************************************************/
    return 0;
    }
```
R/ Este programa no va a correr por que primero inicializa una variable static int, que aunque sea estatica y esto significa que siga existiendo durante todo el programa sigue teniendo una restriccion y es que ningun otro metodo puede acceder a ella incluyendo al main, y despues en el main intenta cambiarla pero como no existe en ese método pues va a salir un error.