
---

### **1. ¿Qué es un puntero en C++?**

En C++, un **puntero** es una variable que guarda la **dirección de memoria** de otra variable. Esto significa que, en lugar de contener un valor directo, un puntero "apunta" a la ubicación de esa otra variable en la memoria.

---

### **2. Declaración de un puntero**

Para declarar un puntero, utilizamos `*` después del tipo de dato.

```cpp
int *p; // Aquí, 'p' es un puntero a un entero
```

### **3. Asignar una dirección a un puntero**

Para hacer que el puntero apunte a una variable, usamos el operador `&` (dirección de).

```cpp
int numero = 10;
int *p = &numero; // 'p' guarda la dirección de 'numero'
```

Aquí, `p` ahora contiene la dirección en memoria de `numero`, no el valor `10`, sino la "ubicación" donde está `10`.

### **4. Acceder al valor usando el puntero (Desreferenciación)**

Para obtener el valor al que apunta el puntero, usamos `*` antes del nombre del puntero.

```cpp
std::cout << *p << std::endl; // Imprime el valor de 'numero' (10)
```

En este caso, `*p` significa "el valor al que apunta `p`", que es `10` en este ejemplo.

---

## **Ejemplo completo en C++: Cambiar el valor de una variable usando un puntero**

```cpp
#include <iostream>

void cambiarValor(int *ptr) {
    *ptr = 20; // Cambia el valor en la dirección de memoria de 'ptr'
}

int main() {
    int numero = 5;
    std::cout << "Antes: " << numero << std::endl; // Imprime 5
    
    cambiarValor(&numero); // Pasamos la dirección de 'numero' a la función
    
    std::cout << "Después: " << numero << std::endl; // Imprime 20
    return 0;
}
```

### **Explicación paso a paso:**

1. **Declaramos `numero`** con un valor inicial de `5`.
2. Mostramos el valor de `numero` en la pantalla antes del cambio; imprime `5`.
3. Llamamos a la función `cambiarValor` y le enviamos la **dirección de `numero`** usando `&numero`.
4. En la función, `ptr` ahora apunta a la dirección de `numero`. Por lo tanto, `*ptr = 20;` cambia el valor almacenado en esa dirección a `20`.
5. De vuelta en `main`, imprimimos el valor de `numero` después de la llamada a la función, y ahora muestra `20`.

### **¿Por qué funciona esto?**

Porque `ptr` en la función `cambiarValor` tiene la **dirección de `numero`**, y al modificar `*ptr`, estamos modificando directamente el valor de `numero`.

---

## **Resumen en C++**

1. Un **puntero** es una variable que guarda una **dirección de memoria**.
2. Para declarar un puntero, usamos `*` (`int *p`).
3. Para obtener la **dirección de una variable**, usamos `&` (`&numero`).
4. Para **acceder al valor** al que apunta un puntero, usamos `*` antes del nombre del puntero (`*p`).

---

### **1. ¿Qué es una `struct`?**

En C++, una `struct` (o **estructura**) es una manera de agrupar varios datos de diferentes tipos en una sola unidad. Piensa en ella como un contenedor que te permite crear tu propio "tipo de dato" combinando varios atributos (como enteros, cadenas, etc.) que tienen relación entre sí.

### **2. ¿Para qué sirve una `struct`?**

Una `struct` es útil cuando necesitas manejar datos relacionados en un solo objeto. Por ejemplo, si estás trabajando con datos de personas, puedes crear una `struct` que agrupe el nombre, la edad, y la dirección de cada persona.

### **3. Declaración de una `struct`**

Para declarar una `struct`, usamos la palabra clave `struct`, seguida del nombre de la estructura, luego definimos las variables (o **miembros**) dentro de ella.

```cpp
struct Persona {
    std::string nombre;
    int edad;
    std::string direccion;
};
```

Aquí, `Persona` es una `struct` que tiene tres miembros: `nombre`, `edad` y `direccion`.

---

## **Ejemplo paso a paso de cómo usar `struct`**

Vamos a crear un programa en C++ que use una `struct` para almacenar y mostrar la información de una persona.

```cpp
#include <iostream>
#include <string>

// Definimos la struct Persona
struct Persona {
    std::string nombre;
    int edad;
    std::string direccion;
};

int main() {
    // Creamos una variable de tipo Persona
    Persona persona1;

    // Asignamos valores a los miembros de persona1
    persona1.nombre = "Juan Perez";
    persona1.edad = 30;
    persona1.direccion = "123 Calle Falsa";

    // Mostramos los valores
    std::cout << "Nombre: " << persona1.nombre << std::endl;
    std::cout << "Edad: " << persona1.edad << std::endl;
    std::cout << "Direccion: " << persona1.direccion << std::endl;

    return 0;
}
```

### **Explicación paso a paso:**

1. **Definimos la `struct`** `Persona` con tres miembros:
   - `nombre` (de tipo `std::string`)
   - `edad` (de tipo `int`)
   - `direccion` (de tipo `std::string`)

2. En `main`, creamos una variable llamada `persona1` de tipo `Persona`. Esta variable tiene tres atributos: `nombre`, `edad` y `direccion`.

3. **Asignamos valores** a cada miembro de `persona1`:
   - `persona1.nombre = "Juan Perez";`
   - `persona1.edad = 30;`
   - `persona1.direccion = "123 Calle Falsa";`

4. **Mostramos los valores** usando `std::cout` para acceder a cada miembro de `persona1` con la sintaxis `persona1.nombre`, `persona1.edad` y `persona1.direccion`.

---

### **4. Inicialización de `struct` con lista de inicialización**

También puedes inicializar una `struct` directamente al declararla:

```cpp
Persona persona2 = {"Maria Gomez", 25, "456 Avenida Siempre Viva"};
```

Esto le da a `persona2` un `nombre`, `edad`, y `direccion` de inmediato.

---

### **5. Uso de `struct` en funciones**

Las `struct` también pueden pasarse a funciones como parámetros. Aquí tienes un ejemplo de una función que recibe una `Persona` y muestra su información.

```cpp
#include <iostream>
#include <string>

struct Persona {
    std::string nombre;
    int edad;
    std::string direccion;
};

void mostrarPersona(const Persona &p) {
    std::cout << "Nombre: " << p.nombre << std::endl;
    std::cout << "Edad: " << p.edad << std::endl;
    std::cout << "Direccion: " << p.direccion << std::endl;
}

int main() {
    Persona persona1 = {"Ana Lopez", 28, "789 Calle Luna"};

    mostrarPersona(persona1);

    return 0;
}
```

### **Explicación paso a paso:**

1. Definimos la función `mostrarPersona` que recibe una `Persona` como parámetro. Usamos `const Persona &p` para que la función no copie `persona1`, sino que solo lea los datos.
   
2. Dentro de `mostrarPersona`, accedemos a los miembros de `p` (`p.nombre`, `p.edad`, `p.direccion`) y los imprimimos.

3. En `main`, creamos `persona1` e inicializamos sus valores. Luego llamamos a `mostrarPersona(persona1);`, que imprime la información de `persona1`.

---

### **6. `struct` con punteros**

A veces, usamos punteros para manipular `struct` directamente en memoria. Aquí tienes un ejemplo.

```cpp
#include <iostream>
#include <string>

struct Persona {
    std::string nombre;
    int edad;
    std::string direccion;
};

void actualizarEdad(Persona *p, int nuevaEdad) {
    p->edad = nuevaEdad; // Usamos '->' para acceder al miembro edad a través del puntero
}

int main() {
    Persona persona1 = {"Carlos Ruiz", 40, "1010 Camino Verde"};
    
    std::cout << "Edad antes de actualizar: " << persona1.edad << std::endl;
    actualizarEdad(&persona1, 45);
    std::cout << "Edad después de actualizar: " << persona1.edad << std::endl;

    return 0;
}
```

### **Explicación paso a paso:**

1. Definimos la función `actualizarEdad`, que recibe un puntero `Persona *p` y un `int` para la nueva edad.
2. Dentro de la función, usamos `p->edad = nuevaEdad;` para cambiar la edad de `persona1` a `45`.
3. En `main`, imprimimos la edad antes y después de llamar a `actualizarEdad` con el puntero `&persona1`.

---

## **Resumen**

1. **¿Qué es una `struct`?** Es una manera de agrupar varios datos de diferentes tipos en una sola unidad.
2. **Declaración de una `struct`:** Definimos los miembros dentro de `struct NombreStruct`.
3. **Acceso a miembros:** Usamos `.` para acceder a los miembros (`persona1.nombre`).
4. **Punteros a `struct`:** Podemos usar `->` para acceder a miembros a través de punteros.
5. **Usar `struct` en funciones:** Podemos pasar `struct` a funciones para manipular datos.

---
