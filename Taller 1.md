Aquí tienes un ejercicio práctico para que los alumnos puedan aplicar sus conocimientos sobre **Variables**, **Funciones**, **Objetos** y **Estructuras de Control**. Este ejercicio está diseñado para que simule un caso casi real que podrían enfrentar como desarrolladores junior. 

---

## Ejercicio: Gestión de Inventario de una Tienda

### Descripción

Vamos a crear un sistema sencillo de gestión de inventario para una tienda de electrónicos. Los alumnos deberán implementar funciones para añadir productos al inventario, actualizar las cantidades, calcular el valor total de los productos y buscar productos en el inventario. Este ejercicio les ayudará a practicar los conceptos básicos de variables, funciones, objetos y estructuras de control.

### Objetivo

Desarrollar un conjunto de funciones para gestionar productos en un inventario, utilizando objetos, variables y estructuras de control.

### Requisitos del Ejercicio

1. Crear un inventario inicial con algunos productos.
2. Permitir añadir nuevos productos.
3. Actualizar la cantidad de un producto existente.
4. Calcular el valor total del inventario.
5. Buscar un producto por nombre y mostrar información.

---

### Paso a Paso

**Paso 1**: Definir el Inventario Inicial

1. Crea un objeto `inventario` donde cada clave es el nombre del producto, y el valor es un objeto que contiene la cantidad y el precio del producto.
   

**Paso 2**: Crear una Función para Agregar Nuevos Productos

1. Define una función `agregarProducto` que acepte el nombre del producto, la cantidad y el precio como parámetros.
2. Si el producto no existe en el inventario, agrégalo como una nueva entrada.
3. Si el producto ya existe, muestra un mensaje diciendo que el producto ya existe.


**Paso 3**: Crear una Función para Actualizar la Cantidad de un Producto Existente

1. Define una función `actualizarCantidad` que acepte el nombre del producto y la cantidad como parámetros.
2. Si el producto existe en el inventario, actualiza su cantidad sumando la cantidad nueva a la existente.
3. Si el producto no existe, muestra un mensaje diciendo que el producto no fue encontrado.


**Paso 4**: Crear una Función para Calcular el Valor Total del Inventario

1. Define una función `calcularValorTotal` que recorra el inventario y sume el valor total de todos los productos (cantidad × precio).
2. Muestra el valor total al final.


**Paso 5**: Crear una Función para Buscar un Producto por Nombre

1. Define una función `buscarProducto` que acepte el nombre del producto como parámetro.
2. Si el producto existe, muestra su cantidad y precio.
3. Si el producto no existe, muestra un mensaje indicando que no se encontró.


---

### Ejercicio Completo: Escenario de Pruebas

1. **Inicializa el inventario** usando el objeto `inventario` del **Paso 1**.
2. **Agrega un nuevo producto** al inventario llamando a `agregarProducto`.
   - Ejemplo: `agregarProducto("Monitor", 15, 200);`
3. **Actualiza la cantidad** de un producto existente llamando a `actualizarCantidad`.
   - Ejemplo: `actualizarCantidad("Laptop", 5);`
4. **Calcula el valor total del inventario** llamando a `calcularValorTotal`.
5. **Busca un producto** en el inventario por nombre llamando a `buscarProducto`.
   - Ejemplo: `buscarProducto("Tablet");`

---

### Rúbrica de Evaluación (10 Puntos Totales)

1. **Definición de Variables y Objetos** - 2 puntos  
   - Correcta inicialización del inventario y estructura del objeto.

2. **Funciones** - 4 puntos  
   - Implementación correcta de cada función con sus respectivos parámetros y uso del inventario.
   - Mensajes de error o éxito en cada función (como cuando un producto ya existe).

3. **Estructuras de Control** - 2 puntos  
   - Uso correcto de `if/else` para verificar si el producto existe en cada función.
   - Uso de `for...in` en la función `calcularValorTotal`.

4. **Pruebas y Ejecución** - 2 puntos  
   - Probar cada función y demostrar su funcionamiento correcto.
   - Manejo adecuado de casos en los que un producto no existe o ya está en el inventario.

---

Con este ejercicio, los estudiantes practicarán cómo usar **variables**, **funciones**, **objetos** y **estructuras de control** en un contexto práctico de gestión de inventario.
