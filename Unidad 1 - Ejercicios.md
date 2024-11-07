### Ejercicio 1: Lista de Compras

**Descripción**: Crea una lista de compras básica y calcula el costo total.

1. Declara variables para al menos 5 productos y sus precios, utilizando números decimales.
2. Usa una variable para almacenar el nombre de cada producto y otra para su precio. Ejemplo: `let producto1 = "Manzanas"; let precio1 = 1.2;`
3. Calcula el costo total sumando todos los precios y almacénalo en una nueva variable.
4. Muestra el nombre de cada producto y su precio, seguido del costo total en la consola.

**Objetivo**: Practicar variables y números.

---

### Ejercicio 2: Perfil de Usuario

**Descripción**: Crea un perfil de usuario con información básica y genera una descripción.

1. Declara variables para almacenar el nombre del usuario, la edad, el país y un pasatiempo favorito.
2. Usa una plantilla de cadena (template literal) para generar un mensaje que describa al usuario. Por ejemplo: `"Hola, soy [nombre], tengo [edad] años, soy de [país] y me gusta [pasatiempo]."`
3. Muestra el mensaje en la consola.

**Objetivo**: Practicar cadenas y concatenación con template literals.

---

### Ejercicio 3: Calculadora de Conversión de Temperatura

**Descripción**: Crea una calculadora que convierta de grados Celsius a Fahrenheit.

1. Declara una variable `temperaturaCelsius` y asígnale un valor numérico.
2. Crea una fórmula para convertir de Celsius a Fahrenheit: `Fahrenheit = Celsius * 9/5 + 32`.
3. Muestra el resultado en la consola en un mensaje como `"La temperatura es [resultado]° Fahrenheit"`.

**Objetivo**: Practicar operaciones matemáticas con variables.

---

### Ejercicio 4: Calculadora de Edad en Días

**Descripción**: Calcula cuántos días ha vivido un usuario.

1. Declara una variable `edad` y asígnale un valor numérico (edad en años).
2. Calcula el total de días que ha vivido la persona multiplicando la edad por 365.
3. Muestra el resultado en la consola en un mensaje como `"Has vivido aproximadamente [resultado] días"`.

**Objetivo**: Practicar operaciones matemáticas y asignación de variables.

---

### Ejercicio 5: Formato de Fecha Completa

**Descripción**: Muestra la fecha en un formato legible usando variables para cada parte de la fecha.

1. Declara variables `dia`, `mes` y `anio`, y asígnales valores que representen una fecha.
2. Crea una variable `fechaCompleta` que una estas variables en un formato de fecha legible. Ejemplo: `"25 de diciembre de 2023"`.
3. Muestra el resultado en la consola.

**Objetivo**: Practicar variables, cadenas y concatenación para formatear datos.


---

### Ejercicio 6: Inventario de Productos

**Descripción**: Vas a crear un sistema simple para administrar el inventario de una tienda.

#### Requerimientos
1. Crea un objeto `producto` con propiedades `nombre`, `precio` y `cantidad`.
2. Declara un arreglo `inventario` vacío para almacenar los productos.
3. Crea una función `agregarProducto` que tome el nombre, precio y cantidad de un producto y lo agregue al inventario.
4. Crea otra función `calcularValorTotal` que devuelva el valor total del inventario sumando el precio y cantidad de cada producto.

---

### Ejercicio 7: Calculadora de Promedios

**Descripción**: Desarrolla una calculadora que saque el promedio de calificaciones de un grupo de estudiantes.

#### Requerimientos
1. Crea un arreglo `alumnos` que contenga varios objetos con propiedades `nombre` y `calificaciones` (un arreglo de números).
2. Crea una función `calcularPromedios` que reciba el arreglo de alumnos y devuelva un objeto que contenga el nombre de cada alumno y su promedio de calificaciones.

---

### Ejercicio 8: Gestión de Tareas

**Descripción**: Implementa una gestión de tareas para un proyecto en el cual puedas agregar y completar tareas.

#### Requerimientos
1. Declara un arreglo `tareas` vacío para almacenar las tareas.
2. Crea una función `agregarTarea` que reciba el nombre de una tarea y la agregue al arreglo `tareas` como un objeto con las propiedades `nombre` y `completada` (inicialmente en `false`).
3. Crea una función `marcarComoCompletada` que reciba el nombre de una tarea y la marque como completada.
4. Crea una función `listarTareas` que muestre todas las tareas y su estado (completada o pendiente).

---

### Ejercicio 9: Sistema de Reservas

**Descripción**: Diseña un sistema de reservas para un restaurante donde se pueda ver la disponibilidad de mesas y realizar reservas.

#### Requerimientos
1. Crea un arreglo `mesas` que contenga 10 mesas (objetos) con propiedades `numero` (1 a 10) y `disponible` (inicialmente en `true`).
2. Crea una función `reservarMesa` que tome el número de una mesa y la marque como no disponible si está libre.
3. Crea una función `mostrarMesasDisponibles` que muestre las mesas disponibles para reservar.

---

### Ejercicio 10: Carrito de Compras

**Descripción**: Diseña un sistema de carrito de compras que permita agregar productos, ver el carrito y calcular el total de la compra.

#### Requerimientos
1. Declara un arreglo `carrito` vacío para almacenar los productos.
2. Crea una función `agregarAlCarrito` que tome el nombre del producto, su precio y cantidad, y lo agregue al carrito.
3. Crea una función `calcularTotalCarrito` que devuelva el precio total de todos los productos en el carrito.
4. Crea una función `mostrarCarrito` que liste todos los productos en el carrito y el total de la compra.

