---

### **Unidad 1: Introducción - Objetos y Arreglos**

#### **¿Qué es JavaScript?**
JavaScript es un lenguaje de programación interpretado, ligero y orientado a objetos, utilizado principalmente para crear páginas web interactivas. Fue creado por Brendan Eich en 1995 y ha evolucionado significativamente desde entonces, convirtiéndose en un pilar fundamental del desarrollo web moderno.

Claro, aquí tienes una explicación sobre variables en JavaScript, incluyendo las mejores prácticas para nombrarlas, su propósito y las palabras reservadas para su declaración, junto con sus diferencias y usos.

---

## **Variables en JavaScript**

### **¿Qué es una variable?**
Una variable es un espacio en la memoria que permite almacenar y manipular datos en un programa. Las variables pueden almacenar diferentes tipos de datos, como números, texto, objetos y funciones, lo que facilita el procesamiento y la reutilización de información a lo largo del código.

### **¿Para qué sirven las variables?**
Las variables son fundamentales en cualquier lenguaje de programación, ya que permiten:
- Almacenar datos de forma temporal.
- Reutilizar valores en distintas partes del código.
- Hacer que el código sea más legible y fácil de mantener.
- Manipular datos dinámicamente, ya que el valor de una variable puede cambiar a medida que el programa se ejecuta.

### **Nombrando variables: Buenas prácticas**
Nombrar variables de manera adecuada es crucial para escribir código claro y comprensible. Algunas recomendaciones para nombrar variables son:

1. **Usar nombres descriptivos**: El nombre debe reflejar el propósito de la variable.
   ```javascript
   let numeroDeEstudiantes = 30;
   let nombreDelProducto = "Camiseta";
   ```

2. **Seguir la convención camelCase**: Esta es la convención estándar en JavaScript. La primera palabra va en minúscula, y cada palabra subsecuente comienza con mayúscula.
   ```javascript
   let totalDeVentas = 500;
   let nombreUsuario = "Juan";
   ```

3. **Evitar nombres ambiguos o muy cortos**: Usar nombres de una o dos letras solo es recomendable para variables temporales en estructuras de control.
   ```javascript
   // Mejor evitar nombres como estos:
   let x = 10;
   let y = "Juan";

   // Mejor usarlos para índices o variables temporales
   for (let i = 0; i < 10; i++) { /* ... */ }
   ```

4. **Evitar palabras reservadas**: No se pueden usar palabras clave del lenguaje como `if`, `while`, `for`, etc., para nombrar variables.

---

### **Palabras reservadas para declarar variables en JavaScript**

En JavaScript, se usan tres palabras clave principales para declarar variables: `var`, `let` y `const`. Cada una tiene características diferentes y se recomienda usarlas de acuerdo con el contexto del código.

#### 1. **`var`** 
   - **Uso**: Fue la palabra reservada original en JavaScript para declarar variables, aunque actualmente está en desuso en favor de `let` y `const`.
   - **Alcance (Scope)**: Tiene alcance de función, lo que significa que solo es accesible dentro de la función en la que se declara.
   - **Hoisting**: Las variables declaradas con `var` se "elevarán" o moverán al inicio de su contexto de ejecución. Esto significa que puedes declarar la variable en cualquier lugar de la función, aunque esté después de su uso.
   - **Ejemplo**:
     ```javascript
     function ejemplo() {
       console.log(miVariable); // undefined
       var miVariable = 10;
     }
     ```

#### 2. **`let`**
   - **Uso**: Es la forma moderna de declarar variables en JavaScript y debe usarse cuando el valor de la variable cambiará a lo largo del programa.
   - **Alcance (Scope)**: Tiene alcance de bloque, es decir, solo es accesible dentro del bloque `{}` en el que se declara, como en una función, un ciclo o un condicional.
   - **Hoisting**: `let` también sufre de hoisting, pero no se inicializa, por lo que el acceso antes de la declaración dará un error de referencia (`ReferenceError`).
   - **Ejemplo**:
     ```javascript
     if (true) {
       let edad = 25;
       console.log(edad); // 25
     }
     console.log(edad); // ReferenceError: edad is not defined
     ```

#### 3. **`const`**
   - **Uso**: Se usa para declarar variables cuyo valor no cambiará durante la ejecución del programa. Es ideal para valores constantes o cuando quieres evitar reasignar un valor accidentalmente.
   - **Alcance (Scope)**: También tiene alcance de bloque, como `let`.
   - **Inmutabilidad**: La referencia de una variable `const` no puede cambiar, pero si almacena un objeto o un arreglo, sus propiedades internas aún pueden modificarse.
   - **Hoisting**: Similar a `let`, pero sin inicialización automática.
   - **Ejemplo**:
     ```javascript
     const nombre = "Pedro";
     nombre = "Juan"; // TypeError: Assignment to constant variable.
     
     const carrito = [];
     carrito.push("Producto 1"); // Esto es válido
     console.log(carrito); // ["Producto 1"]
     ```

### **Resumen de las diferencias**

| Característica      | `var`                  | `let`                  | `const`               |
|---------------------|------------------------|------------------------|-----------------------|
| Alcance (Scope)     | Función                | Bloque                 | Bloque                |
| Hoisting            | Sí (se inicializa como `undefined`) | Sí (no inicializa) | Sí (no inicializa)   |
| Reasignación        | Sí                     | Sí                     | No                   |
| Inmutabilidad       | No                     | No                     | Sí (referencia inmutable) |

---

### **Ejemplo práctico**

Supongamos que estamos desarrollando una pequeña aplicación que calcula el total de ventas de un día. Podemos usar `let` para la variable `ventasDiarias` que cambiará con cada venta registrada, y `const` para `IVA`, que es una constante.

```javascript
const IVA = 0.12; // 12% de IVA, valor constante
let ventasDiarias = 0;

function registrarVenta(precioProducto) {
  ventasDiarias += precioProducto;
  console.log(`Venta registrada. Total ventas: $${ventasDiarias}`);
}

registrarVenta(100); // Venta registrada. Total ventas: $100
registrarVenta(50);  // Venta registrada. Total ventas: $150
```

### **Enlaces para profundizar**

- [JavaScript.info - Variables](https://javascript.info/variables)
- [MDN Web Docs - var, let, const](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Grammar_and_types#Declaraci%C3%B3n_de_variables)

--- 

#### **Tipos de Datos Primitivos**
JavaScript tiene varios tipos de datos primitivos:
- `number`: Números (enteros o flotantes).
- `string`: Cadenas de texto.
- `boolean`: Valores lógicos (`true` o `false`).
- `null`: Representa "ningún valor".
- `undefined`: Indica que una variable no ha sido asignada.
- `symbol`: Un valor único que no puede ser replicado.
  
#### **Objetos**
Los objetos son colecciones de pares clave-valor. Cada propiedad de un objeto tiene un nombre (clave) y un valor.
```javascript
const persona = {
  nombre: "Juan",
  edad: 30,
  saludar: function() {
    console.log("Hola, soy " + this.nombre);
  }
};

persona.saludar();  // Hola, soy Juan
```

#### **Arreglos**
Un arreglo es una lista ordenada de elementos que pueden ser de cualquier tipo de dato.
```javascript
const numeros = [1, 2, 3, 4, 5];
console.log(numeros[0]);  // 1
```

Los arreglos tienen métodos útiles como:
- `push()`: Agrega un elemento al final del arreglo.
- `pop()`: Elimina el último elemento.
- `map()`, `filter()`, `reduce()`: Métodos avanzados para transformar o reducir arreglos.

