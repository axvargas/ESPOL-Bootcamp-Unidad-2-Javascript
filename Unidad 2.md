---

# **Unidad 2: Funciones y Estructuras de Control**
---

## ¿Qué es una Función?

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

## Estructuras de control
---

### 1. **`if` / `else if` / `else`** - Estructura Condicional

La estructura `if` evalúa una condición: si es verdadera, ejecuta un bloque de código; si es falsa, puede ejecutar otro bloque con `else`.

#### Ejemplo: Verificar si una tienda está abierta

Imagina que quieres saber si una tienda está abierta o cerrada en función de la hora actual.

```javascript
const horaActual = 14; // 14 representa las 2:00 p.m.

if (horaActual >= 9 && horaActual < 18) {
    console.log("La tienda está abierta");
} else {
    console.log("La tienda está cerrada");
}

// Resultado: "La tienda está abierta"
```

**Explicación**: Aquí, la tienda abre de 9 a.m. a 6 p.m. Si la hora actual está en este rango, muestra "abierta", y si no, muestra "cerrada".

---

### 2. **`switch`** - Condicional Múltiple

El `switch` es útil cuando tienes muchas condiciones que comparar con un solo valor.

#### Ejemplo: Selección de idioma en una aplicación

Supón que el usuario elige un idioma para la aplicación, y según el idioma se muestra un saludo.

```javascript
const idioma = "es";

switch (idioma) {
    case "es":
        console.log("Hola");
        break;
    case "en":
        console.log("Hello");
        break;
    case "fr":
        console.log("Bonjour");
        break;
    default:
        console.log("Idioma no soportado");
}

// Resultado: "Hola"
```

**Explicación**: Dependiendo del valor de `idioma`, el código muestra un saludo en español, inglés o francés. Si el idioma no es reconocido, muestra un mensaje por defecto.

---

### 3. **`for`** - Bucle con Número Fijo de Iteraciones

El bucle `for` repite un bloque de código un número específico de veces.

#### Ejemplo: Enviar recordatorios de pago

Imagina que tienes una lista de usuarios y quieres enviar un mensaje de recordatorio a cada uno.

```javascript
const usuarios = ["Ana", "Carlos", "Luisa"];

for (let i = 0; i < usuarios.length; i++) {
    console.log(`Recordatorio de pago enviado a ${usuarios[i]}`);
}

// Resultado:
// "Recordatorio de pago enviado a Ana"
// "Recordatorio de pago enviado a Carlos"
// "Recordatorio de pago enviado a Luisa"
```

**Explicación**: El bucle recorre la lista de usuarios y envía un mensaje personalizado a cada uno.

---

### 4. **`for...of`** - Bucle para Arreglos y Colecciones

`for...of` permite recorrer los elementos de un arreglo directamente.

#### Ejemplo: Listar productos en una tienda

```javascript
const productos = ["Laptop", "Tablet", "Teléfono"];

for (const producto of productos) {
    console.log(`Producto disponible: ${producto}`);
}

// Resultado:
// "Producto disponible: Laptop"
// "Producto disponible: Tablet"
// "Producto disponible: Teléfono"
```

**Explicación**: `for...of` es una forma simple de recorrer cada producto sin necesidad de manejar el índice del arreglo.

---

### 5. **`for...in`** - Bucle para Propiedades de un Objeto

`for...in` es ideal para iterar sobre las propiedades de un objeto.

#### Ejemplo: Mostrar la información de un usuario

```javascript
const usuario = {
    nombre: "Pedro",
    edad: 30,
    email: "pedro@example.com"
};

for (const propiedad in usuario) {
    console.log(`${propiedad}: ${usuario[propiedad]}`);
}

// Resultado:
// "nombre: Pedro"
// "edad: 30"
// "email: pedro@example.com"
```

**Explicación**: Aquí usamos `for...in` para recorrer cada propiedad del objeto `usuario` y mostrar sus valores.

---

### 6. **`while`** - Bucle Indeterminado

El `while` repite un bloque de código mientras una condición sea verdadera.

#### Ejemplo: Hacer intentos para conectarse a un servidor

Imagina que intentas conectar a un servidor y deseas seguir intentándolo hasta que se logre.

```javascript
let conectado = false;
let intentos = 0;

while (!conectado && intentos < 5) {
    console.log("Intentando conectar...");
    intentos++;
    
    // Simulación de conexión exitosa en el tercer intento
    if (intentos === 3) {
        conectado = true;
        console.log("Conexión exitosa!");
    }
}

// Resultado:
// "Intentando conectar..."
// "Intentando conectar..."
// "Intentando conectar..."
// "Conexión exitosa!"
```

**Explicación**: Se sigue intentando conectar hasta que se logra o se han hecho 5 intentos. En este caso, simulamos una conexión exitosa en el tercer intento.

---

### 7. **`do...while`** - Bucle que Ejecuta al Menos Una Vez

`do...while` es similar a `while`, pero garantiza que el bloque de código se ejecute al menos una vez.

#### Ejemplo: Preguntar la contraseña hasta que sea correcta

```javascript
let contraseñaCorrecta = "1234";
let intento;

do {
    intento = prompt("Introduce tu contraseña:");
} while (intento !== contraseñaCorrecta);

console.log("Acceso concedido");
```

**Explicación**: Este bucle sigue pidiendo la contraseña hasta que el usuario ingrese la correcta. El código dentro del `do` se ejecuta al menos una vez, aunque la contraseña sea correcta desde el principio.

---

### 8. **`break` y `continue`** - Control de Flujo dentro de Bucles

- **`break`**: Detiene completamente el bucle.
- **`continue`**: Salta a la siguiente iteración sin terminar el bucle.

#### Ejemplo: Revisar pedidos y detenerse al encontrar uno con error

```javascript
const pedidos = [
    { id: 1, estado: "completo" },
    { id: 2, estado: "completo" },
    { id: 3, estado: "error" },
    { id: 4, estado: "completo" }
];

for (const pedido of pedidos) {
    if (pedido.estado === "error") {
        console.log(`Pedido ${pedido.id} tiene un error. Revisión detenida.`);
        break;
    }
    console.log(`Pedido ${pedido.id} revisado correctamente.`);
}

// Resultado:
// "Pedido 1 revisado correctamente."
// "Pedido 2 revisado correctamente."
// "Pedido 3 tiene un error. Revisión detenida."
```

**Explicación**: Aquí, el `break` se usa para detener el proceso al encontrar un pedido con estado "error".

---

### Resumen

Las estructuras de control permiten que el código sea más dinámico y flexible:
- **`if / else if / else`**: Toma decisiones en función de condiciones.
- **`switch`**: Útil para múltiples condiciones sobre una misma variable.
- **`for`, `for...of`, `for...in`**: Bucle para iteraciones específicas o sobre elementos de arreglos/propiedades.
- **`while`, `do...while`**: Bucle condicional, se repite mientras la condición sea verdadera.
- **`break` y `continue`**: Controlan el flujo dentro de bucles.

Estos ejemplos simulan situaciones que se pueden encontrar en el día a día de un programador junior en un entorno de trabajo.
