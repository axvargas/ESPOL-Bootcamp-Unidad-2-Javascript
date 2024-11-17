# **Unidad 6: Funciones de Orden Superior**

## **Funciones de Orden Superior (HOF)**
Las **funciones de orden superior** en JavaScript son aquellas que pueden recibir otras funciones como argumentos, o devolver una función como resultado. Estas funciones son fundamentales en el desarrollo moderno, ya que permiten trabajar con estructuras de datos de manera eficiente y escribir código más claro y modular.

A continuación, se explican las funciones de orden superior más comunes: `forEach`, `map`, `filter`, `reduce`, y `sort`, con un ejemplo práctico para cada una.

---

### 1. `forEach`

La función `forEach` permite ejecutar una función específica para cada elemento en un array. No devuelve un nuevo array; simplemente recorre cada elemento.

#### Sintaxis

```javascript
array.forEach((element, index, array) => {
  // Código a ejecutar por cada elemento
});
```

#### Ejemplo real: Enviar correos a una lista de usuarios

Supongamos que tienes una lista de correos de usuarios y quieres imprimir un mensaje de notificación para cada uno:

```javascript
const usuarios = ["juan@mail.com", "ana@mail.com", "luis@mail.com"];

usuarios.forEach((correo) => {
    console.log(`Enviando notificación a ${correo}`);
});
```

**Salida:**

```
Enviando notificación a juan@mail.com
Enviando notificación a ana@mail.com
Enviando notificación a luis@mail.com
```

En un entorno real, esta lógica podría extenderse para enviar correos electrónicos a usuarios.

---

### 2. `map`

La función `map` crea un nuevo array con los resultados de aplicar una función a cada elemento del array original.

#### Sintaxis

```javascript
const nuevoArray = array.map((element, index, array) => {
  // Transformación del elemento
  return elementoModificado;
});
```

#### Ejemplo real: Convertir precios en dólares a otra moneda

Supongamos que tienes una lista de precios en dólares y quieres convertirlos a euros. Para esto, podríamos usar un `map` para hacer la conversión de cada precio.

```javascript
const preciosDolares = [10, 20, 30];
const tasaCambio = 0.85; // Suponiendo que 1 dólar = 0.85 euros

const preciosEuros = preciosDolares.map((precio) => precio * tasaCambio);

console.log(preciosEuros); // [8.5, 17, 25.5]
```

Aquí, `map` nos permite transformar el array de precios en dólares a euros con facilidad.

---

### 3. `filter`

La función `filter` crea un nuevo array con todos los elementos que cumplan con una condición específica.

#### Sintaxis

```javascript
const nuevoArray = array.filter((element, index, array) => {
  return condicion;
});
```

#### Ejemplo real: Filtrar productos disponibles en inventario

Supongamos que tienes una lista de productos y quieres obtener solo aquellos que están en stock (disponibles).

```javascript
const productos = [
    { nombre: "Laptop", enStock: true },
    { nombre: "Monitor", enStock: false },
    { nombre: "Teclado", enStock: true },
];

const productosDisponibles = productos.filter((producto) => producto.enStock);

console.log(productosDisponibles);
// [{ nombre: "Laptop", enStock: true }, { nombre: "Teclado", enStock: true }]
```

En este caso, `filter` nos ayuda a obtener un array de productos que están disponibles, algo común en tiendas en línea.

---

¡Claro! Vamos a desglosar **`reduce`** y **`sort`** para que se comprenda cada paso que realiza el código detrás de escena.

---

### 4. `reduce`

La función **`reduce`** permite “reducir” o combinar los elementos de un array en un solo valor, como la suma de números o la construcción de un objeto.

#### Sintaxis General

```javascript
const resultado = array.reduce((acumulador, elementoActual) => {
  return acumuladorModificado;
}, valorInicial);
```

- **`acumulador`**: el valor acumulado que se va construyendo a lo largo de la ejecución.
- **`elementoActual`**: el elemento actual que se está procesando.
- **`valorInicial`**: un valor opcional que define el valor inicial de `acumulador`. Si no se pasa, `reduce` usa el primer elemento del array como valor inicial y empieza desde el segundo elemento.

#### Ejemplo: Calcular el total de ventas

Supongamos que queremos calcular el total de ventas en un día:

```javascript
const ventas = [100, 200, 300, 400];

const totalVentas = ventas.reduce((acumulador, venta) => acumulador + venta, 0);

console.log(totalVentas); // 1000
```

##### Paso a Paso del Ejemplo

1. **Valor inicial (`acumulador = 0`)**: La función `reduce` comienza con `acumulador` igual a 0 (el valor inicial que le dimos).
  
2. **Primera Iteración (`venta = 100`)**:
   - `acumulador` es 0.
   - `venta` es 100.
   - **Nuevo `acumulador = 0 + 100 = 100`**.

3. **Segunda Iteración (`venta = 200`)**:
   - `acumulador` ahora es 100.
   - `venta` es 200.
   - **Nuevo `acumulador = 100 + 200 = 300`**.

4. **Tercera Iteración (`venta = 300`)**:
   - `acumulador` es 300.
   - `venta` es 300.
   - **Nuevo `acumulador = 300 + 300 = 600`**.

5. **Cuarta Iteración (`venta = 400`)**:
   - `acumulador` es 600.
   - `venta` es 400.
   - **Nuevo `acumulador = 600 + 400 = 1000`**.

Después de procesar todos los elementos, `reduce` devuelve el valor final del `acumulador`, que es **1000**.

---

### 5. `sort`

La función **`sort`** se usa para ordenar los elementos de un array. Esta función modifica el array original y ordena los elementos en función de una función de comparación que tú defines.

#### Sintaxis General

```javascript
array.sort((a, b) => {
  // Si la función devuelve un valor negativo, `a` va antes que `b`.
  // Si la función devuelve un valor positivo, `b` va antes que `a`.
  // Si la función devuelve 0, no cambia el orden de `a` y `b`.
});
```

#### Ejemplo: Ordenar productos por precio de menor a mayor

Vamos a ordenar una lista de productos de menor a mayor precio:

```javascript
const productos = [
    { nombre: "Laptop", precio: 1000 },
    { nombre: "Monitor", precio: 200 },
    { nombre: "Teclado", precio: 50 },
];

productos.sort((a, b) => a.precio - b.precio);

console.log(productos);
// [
//   { nombre: "Teclado", precio: 50 },
//   { nombre: "Monitor", precio: 200 },
//   { nombre: "Laptop", precio: 1000 }
// ]
```

##### Paso a Paso del Ejemplo

1. **Comparación de elementos**: `sort` utiliza la función `(a, b) => a.precio - b.precio` para determinar el orden de cada par de elementos `a` y `b` en el array.
  
2. **Primera Comparación (Laptop y Monitor)**:
   - Precio de `Laptop` es 1000, y precio de `Monitor` es 200.
   - `1000 - 200 = 800` → Resultado positivo: `Laptop` debe ir después de `Monitor`.

3. **Segunda Comparación (Laptop y Teclado)**:
   - Precio de `Laptop` es 1000, y precio de `Teclado` es 50.
   - `1000 - 50 = 950` → Resultado positivo: `Laptop` debe ir después de `Teclado`.

4. **Tercera Comparación (Monitor y Teclado)**:
   - Precio de `Monitor` es 200, y precio de `Teclado` es 50.
   - `200 - 50 = 150` → Resultado positivo: `Monitor` debe ir después de `Teclado`.

Después de todas las comparaciones, `sort` organiza el array de modo que el producto con menor precio (`Teclado`) aparece primero, seguido de `Monitor`, y finalmente `Laptop`. El array resultante tiene los productos ordenados de menor a mayor precio.

--- 

### Resumen

Estas funciones de orden superior (`forEach`, `map`, `filter`, `reduce`, `sort`) son poderosas herramientas en JavaScript, especialmente para manejar y manipular datos en aplicaciones reales. Permiten escribir código conciso y eficiente para tareas comunes, como filtrar listas, transformar datos, y calcular valores agregados.
