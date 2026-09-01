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