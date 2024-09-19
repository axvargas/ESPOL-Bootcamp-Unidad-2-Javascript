---

### **Unidad 2: Funciones y Estructuras de Control**

#### **Funciones**
Las funciones son bloques de código reutilizables que realizan una tarea específica.
- **Declaración de funciones**:
```javascript
function saludar(nombre) {
  return "Hola, " + nombre;
}
console.log(saludar("Ana"));  // Hola, Ana
```
- **Funciones flecha (arrow functions)**:
```javascript
const sumar = (a, b) => a + b;
console.log(sumar(2, 3));  // 5
```

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
