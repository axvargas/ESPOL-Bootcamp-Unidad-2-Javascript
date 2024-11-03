---

# **Unidad 2: Funciones y Estructuras de Control**
---

### ¿Qué es una Función?

Una **función** en JavaScript es un bloque de código que realiza una tarea específica. Podemos "llamar" a la función en cualquier momento para ejecutar ese bloque de código. La función puede también recibir datos llamados **parámetros** y devolver un resultado con la palabra clave `return`.

Imagina que tienes una receta para hacer un batido. Cada vez que quieres un batido, sigues los pasos de esa receta. La función es como esa receta: la defines una vez, y luego puedes usarla todas las veces que quieras sin repetir el código.

---

### Dos Maneras de Definir una Función

1. **Función Tradicional**
2. **Función Flecha (Arrow Function)**

---

### 1. Función Tradicional

Se define usando la palabra clave `function`, seguida de un nombre para la función (como "nombreDeLaFuncion"), paréntesis para los parámetros, y llaves `{ }` para el código de la función.

```javascript
function sumar(a, b) {
    return a + b;
}

console.log(sumar(3, 4)); // 7
```

En este ejemplo:
- `sumar` es el nombre de la función.
- `(a, b)` son los parámetros, que representan los números que queremos sumar.
- `return a + b;` devuelve el resultado de sumar `a` y `b`.

---

### 2. Función Flecha (Arrow Function)

La **función flecha** es una manera más corta de escribir funciones. En lugar de `function`, usamos `=>` para definir la función.

```javascript
const sumar = (a, b) => a + b;

console.log(sumar(3, 4)); // 7
```

Es lo mismo que la función tradicional, pero en una forma más compacta. Notas:
- No usamos la palabra `function`.
- La flecha `=>` indica el inicio del bloque de código.
- Si solo hay una línea de código, podemos omitir las llaves `{ }` y el `return`.

---

### Resumen

Ambas formas hacen lo mismo: permiten escribir bloques de código reutilizables. La principal diferencia es que la **función flecha** es más corta, ideal para funciones simples y rápidas.

### Ejercicio
Crear una función que convierta una temperatura de Farenheita Celcius y otra funcion que convierta una temperatura de Celcius a Farenheit. La primera con función tradicional y la otra con función de flecha. Recuerda que para convertir de Fahrenheit a Celsius, simplemente reste 32 y multiplique por 0.5556 (o 5/9). Para convertir de Celsius a Fahrenheit, simplemente multiplique por 1.8 (o 9/5) y sume 32

---

#### **Estructuras de Control**
- **Condicionales (`if`, `else`, `switch`)**:
  - **If**: Se utiliza cuando se tienen dos caminos por donde puede ir el código, existe una condición la cual puede ser verdadera o falsa
    ```javascript
    if (condicion) {
      // código a ejecutar si la condición es verdadera
    } else {
      // código a ejecutar si la condición es falsa
    }
    ```
  - **Else If**: Se utiliza cuando hay múltiples condiciones que verificar 
    ```javascript
    if (condicion) {
      // código a ejecutar si la condición es verdadera
    } else if(condicion 2) {
      // código a ejecutar si la condición 2 es verdadera y las anteriores falsas
    } else if (condicion n) {
      // código a ejecutar si la condición n es verdadera y las anteriores falsas
    } else {
      // código a ejecutar todas las demás condiciones son falsas
    }
    ```
  - **Switch**: Se utiliza cuando hay múltiples condiciones que verificar y se quiere evitar el uso repetido de `if`-`else if`.
      ```javascript
      const color = "rojo";
    
      switch (color) {
        case "rojo":
          console.log("El color es rojo");
          break;
        case "azul":
          console.log("El color es azul");
          break;
        case "verde":
          console.log("El color es verde");
          break;
        default:
          console.log("No se reconoce el color");
      }
      ```
      El `switch` compara la expresión dentro del paréntesis (`color` en este caso) con cada `case`. Si encuentra una coincidencia, ejecuta el código correspondiente. Si ninguna condición es verdadera, ejecuta el bloque `default`.
- **Loops**:
  - **for**: Se usa cuando sabes cuántas veces quieres repetir algo.
  ```javascript
  for (let i = 0; i < 5; i++) {
    console.log(i);
  }
  ```
  - **while**: Se usa cuando no sabes cuántas veces se repetirá el ciclo.
  ```javascript
  let i = 0;
  while (i < 5) {
    console.log(i);
    i++;
  }
  ```
