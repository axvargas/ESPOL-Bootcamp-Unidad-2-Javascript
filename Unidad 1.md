# **Unidad 1: Introducción - Variables, Objetos y Arreglos**


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

## **Tipos de Datos en JavaScript**

1. **Número (`number`)**
2. **Cadena de texto (`string`)**
3. **Booleano (`boolean`)**
4. **Nulo (`null`)**
5. **Indefinido (`undefined`)**
6. **Símbolo (`symbol`)**
7. **Objeto (`object`)**
8. **Arreglo (`array`)** - Un tipo especial de objeto
9. **Función (`function`)** - Otro tipo especial de objeto

---

### **1. Números (`number`)**

Los números en JavaScript incluyen tanto enteros como decimales.

**Funciones útiles**:
- `Math.round()`: Redondea un número al entero más cercano.
- `Math.floor()`: Redondea hacia abajo.
- `Math.ceil()`: Redondea hacia arriba.
- `Math.random()`: Genera un número aleatorio entre 0 y 1.
- `toFixed()`: Redondea un número a un número fijo de decimales.

**Ejemplo práctico**:
```javascript
let precio = 199.99;
console.log(precio.toFixed(1)); // "200.0"
console.log(Math.round(precio)); // 200
console.log(Math.random() * 10); // Número aleatorio entre 0 y 10
```

**Recurso externo**: [MDN - Números en JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Numbers_and_dates)

---

### **2. Cadenas de texto (`string`)**

Una cadena es una secuencia de caracteres utilizada para representar texto.

**Funciones útiles**:
- `length`: Devuelve la longitud de la cadena.
- `toUpperCase()`: Convierte la cadena a mayúsculas.
- `toLowerCase()`: Convierte la cadena a minúsculas.
- `includes()`: Verifica si la cadena contiene otra cadena.
- `slice()`: Extrae una parte de la cadena.
- `trim()`: Elimina los espacios en blanco al inicio y al final de la cadena.

**Ejemplo práctico**:
```javascript
let mensaje = "  Hola, Mundo!  ";
console.log(mensaje.trim().toUpperCase()); // "HOLA, MUNDO!"
console.log(mensaje.includes("Mundo")); // true
```

**Recurso externo**: [MDN - Strings en JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Strings_and_Text)

---

### **3. Booleano (`boolean`)**

Los booleanos representan valores de verdad, `true` o `false`.

**Funciones útiles**:
- `Boolean()`: Convierte otros valores a booleanos.
- Operadores de comparación (`===`, `!==`, `<`, `>`, etc.): Para evaluar condiciones.

**Ejemplo práctico**:
```javascript
let edad = 18;
let esMayorDeEdad = edad >= 18;
console.log(esMayorDeEdad); // true

let mensaje = " ";
console.log(Boolean(mensaje)); // true, ya que la cadena no está vacía
```

**Recurso externo**: [MDN - Booleanos en JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Boolean)

---

### **4. Nulo (`null`)**

`null` es un valor especial que indica la ausencia intencional de un objeto o valor.

**Usos comunes**:
- Es útil para inicializar variables que luego se espera que almacenen un objeto.
- Verificar si un valor es `null` antes de realizar operaciones con él.

**Ejemplo práctico**:
```javascript
let usuario = null; // Usuario aún no está definido
if (usuario === null) {
    console.log("No se ha iniciado sesión");
} else {
    console.log("Bienvenido " + usuario);
}
```

**Recurso externo**: [MDN - Null](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/null)

---

### **5. Indefinido (`undefined`)**

`undefined` indica que una variable ha sido declarada, pero no tiene un valor asignado.

**Usos comunes**:
- Comprobar si una variable no tiene un valor asignado.
- Las funciones que no retornan un valor explícito devuelven `undefined`.

**Ejemplo práctico**:
```javascript
let cliente;
console.log(cliente); // undefined, no tiene un valor asignado

function saludar() {}
console.log(saludar()); // undefined, ya que no retorna un valor
```

**Recurso externo**: [MDN - Undefined](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/undefined)

---

### **6. Símbolo (`symbol`)**

Un `symbol` es un valor único y no mutable, útil para identificar propiedades de objetos sin riesgo de colisión.

**Usos comunes**:
- Para crear claves de propiedad únicas en objetos.

**Ejemplo práctico**:
```javascript
let id = Symbol("id");
let usuario = {
  [id]: 123
};
console.log(usuario[id]); // 123
```

**Recurso externo**: [MDN - Symbol](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Symbol)

---

### **7. Objeto (`object`)**

Un `object` es una colección de propiedades, donde cada propiedad tiene un nombre (clave) y un valor.

**Funciones útiles**:
- `Object.keys()`: Devuelve las claves del objeto.
- `Object.values()`: Devuelve los valores del objeto.
- `Object.entries()`: Devuelve pares clave-valor como un arreglo.

**Ejemplo práctico**:
```javascript
let persona = { nombre: "Ana", edad: 30 };
console.log(Object.keys(persona)); // ["nombre", "edad"]
console.log(Object.values(persona)); // ["Ana", 30]
```

**Recurso externo**: [MDN - Object](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Object)

---

### **8. Arreglo (`array`)**

Un `array` es un tipo especial de objeto que permite almacenar múltiples valores en un solo contenedor.

**Funciones útiles**:
- `push()`: Agrega un elemento al final.
- `pop()`: Elimina el último elemento.
- `map()`: Aplica una función a cada elemento y retorna un nuevo array.
- `filter()`: Filtra elementos según una condición.

**Ejemplo práctico**:
```javascript
let numeros = [1, 2, 3, 4];
numeros.push(5); // [1, 2, 3, 4, 5]
let pares = numeros.filter(num => num % 2 === 0); // [2, 4]
```

**Recurso externo**: [MDN - Array](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

### **9. Función (`function`)**

Una `function` es un bloque de código diseñado para realizar una tarea específica.

**Funciones útiles**:
- `call()`, `apply()`: Ejecutan una función con un contexto específico.
- `bind()`: Crea una nueva función con un contexto fijo.

**Ejemplo práctico**:
```javascript
function saludar(nombre) {
    return `Hola, ${nombre}!`;
}

console.log(saludar("Pedro")); // "Hola, Pedro!"
```

**Recurso externo**: [MDN - Funciones](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Functions)


