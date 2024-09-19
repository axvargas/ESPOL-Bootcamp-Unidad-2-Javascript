Aquí tienes la continuación con el **proyecto final** y su **solución**. El proyecto simula un caso de uso casi real que los estudiantes podrían enfrentar como desarrolladores de software junior. Vamos a diseñar una aplicación que gestione una lista de productos, sus precios y los almacene en el navegador. También tendrá una funcionalidad para interactuar con una API externa, realizar validaciones, filtrar datos y renderizarlos dinámicamente en el DOM.

---

### **Proyecto Final: Gestión de Inventario de Productos**

#### **Descripción del Proyecto:**
En este proyecto, los estudiantes desarrollarán una aplicación de gestión de inventario que permita:

1. Agregar nuevos productos con sus nombres y precios.
2. Validar los datos ingresados (nombre y precio) antes de agregarlos a la lista.
3. Guardar la lista de productos en el `localStorage` para mantener la persistencia de datos entre sesiones.
4. Mostrar los productos almacenados en el DOM en una tabla, permitiendo eliminar o editar productos.
5. Consumir una API externa que devuelva información sobre productos similares o relacionados, para ofrecer recomendaciones (por ejemplo, usando la API de FakeStore).
6. Filtrar los productos por precio, mostrando solo los productos que estén por debajo de un cierto umbral.
7. Mostrar gráficos con estadísticas simples (usando **Chart.js**) sobre el número de productos y los precios.

---

### **Requisitos del Proyecto:**
1. **Formulario de ingreso de productos**: Debe permitir a los usuarios agregar un producto con su nombre y precio.
2. **Validaciones**: El nombre debe ser alfanumérico y el precio un número mayor que cero.
3. **Almacenamiento local**: Guardar los productos en el `localStorage` para que persistan entre sesiones.
4. **Consumo de API externa**: Debe conectarse a la API `https://fakestoreapi.com/products` para obtener recomendaciones de productos.
5. **Interacción con el DOM**: Mostrar los productos en una tabla editable, permitiendo a los usuarios eliminar o editar productos.
6. **Filtro de productos**: Filtrar los productos por precio.
7. **Gráfico de productos**: Usar **Chart.js** para mostrar un gráfico con estadísticas (por ejemplo, cantidad de productos por rango de precio).

---

### **Instrucciones Paso a Paso:**

#### **Paso 1: Crear la estructura básica**
El proyecto tendrá un formulario simple para ingresar productos, una tabla para mostrarlos, un campo para buscar productos y un área para mostrar el gráfico.

**HTML Inicial**:
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gestión de Inventario</title>
</head>
<body>
  <h1>Gestión de Inventario de Productos</h1>

  <!-- Formulario para añadir productos -->
  <form id="product-form">
    <input type="text" id="product-name" placeholder="Nombre del producto" required>
    <input type="number" id="product-price" placeholder="Precio del producto" required>
    <button type="submit">Añadir Producto</button>
  </form>

  <!-- Filtro de productos por precio -->
  <label for="filter-price">Mostrar productos con precio menor a: </label>
  <input type="number" id="filter-price" placeholder="Ingrese un precio">

  <!-- Tabla de productos -->
  <table>
    <thead>
      <tr>
        <th>Nombre</th>
        <th>Precio</th>
        <th>Acciones</th>
      </tr>
    </thead>
    <tbody id="product-list">
      <!-- Los productos se mostrarán aquí -->
    </tbody>
  </table>

  <!-- Contenedor para el gráfico de productos -->
  <canvas id="productChart" width="400" height="200"></canvas>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="app.js"></script>
</body>
</html>
```

---

#### **Paso 2: Manejo de productos (DOM y `localStorage`)**
Debemos crear funciones para manejar los productos: agregar, eliminar, editar, y guardarlos en el `localStorage`.

```javascript
// Obtener elementos del DOM
const productForm = document.getElementById('product-form');
const productList = document.getElementById('product-list');
const filterPriceInput = document.getElementById('filter-price');

// Array para almacenar los productos
let products = [];

// Función para cargar productos desde localStorage
function loadProducts() {
  const storedProducts = localStorage.getItem('products');
  if (storedProducts) {
    products = JSON.parse(storedProducts);
    displayProducts(products);
  }
}

// Función para guardar productos en localStorage
function saveProducts() {
  localStorage.setItem('products', JSON.stringify(products));
}

// Función para mostrar los productos en la tabla
function displayProducts(productsToDisplay) {
  productList.innerHTML = '';
  productsToDisplay.forEach((product, index) => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${product.name}</td>
      <td>$${product.price.toFixed(2)}</td>
      <td>
        <button onclick="editProduct(${index})">Editar</button>
        <button onclick="deleteProduct(${index})">Eliminar</button>
      </td>
    `;
    productList.appendChild(row);
  });
}

// Función para añadir un nuevo producto
function addProduct(event) {
  event.preventDefault();
  
  const productName = document.getElementById('product-name').value;
  const productPrice = parseFloat(document.getElementById('product-price').value);

  if (productName && productPrice > 0) {
    products.push({ name: productName, price: productPrice });
    saveProducts();
    displayProducts(products);
    productForm.reset();  // Limpiar el formulario
  } else {
    alert('Por favor ingresa un nombre válido y un precio mayor que 0.');
  }
}

// Función para eliminar un producto
function deleteProduct(index) {
  products.splice(index, 1);
  saveProducts();
  displayProducts(products);
}

// Función para editar un producto
function editProduct(index) {
  const product = products[index];
  document.getElementById('product-name').value = product.name;
  document.getElementById('product-price').value = product.price;
  products.splice(index, 1);  // Remover producto para actualizar
}

// Función para filtrar productos por precio
function filterProducts() {
  const filterPrice = parseFloat(filterPriceInput.value);
  if (filterPrice) {
    const filteredProducts = products.filter(product => product.price <= filterPrice);
    displayProducts(filteredProducts);
  } else {
    displayProducts(products);
  }
}

// Eventos
productForm.addEventListener('submit', addProduct);
filterPriceInput.addEventListener('input', filterProducts);

// Cargar productos al iniciar
loadProducts();
```

---

#### **Paso 3: Gráfico de productos con Chart.js**
Añadimos un gráfico para visualizar la distribución de precios de los productos usando **Chart.js**.

```javascript
// Función para actualizar el gráfico de productos
function updateChart() {
  const productPrices = products.map(product => product.price);
  const productNames = products.map(product => product.name);

  const ctx = document.getElementById('productChart').getContext('2d');
  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: productNames,
      datasets: [{
        label: 'Precios de Productos',
        data: productPrices,
        backgroundColor: 'rgba(75, 192, 192, 0.2)',
        borderColor: 'rgba(75, 192, 192, 1)',
        borderWidth: 1
      }]
    },
    options: {
      scales: {
        y: {
          beginAtZero: true
        }
      }
    }
  });
}

// Llamar a updateChart después de agregar/eliminar productos
function addProduct(event) {
  event.preventDefault();
  // (Código de agregar producto)
  updateChart();
}

function deleteProduct(index) {
  // (Código de eliminar producto)
  updateChart();
}

// Llamar updateChart al cargar productos
loadProducts();
updateChart();
```

---

#### **Paso 4: Consumo de API Externa**
Finalmente, añadimos la funcionalidad para consultar productos relacionados desde una API externa.

```javascript
// Función para obtener recomendaciones de productos desde la API
function fetchProductRecommendations() {
  fetch('https://fakestoreapi.com/products')
    .then(response => response.json())
    .then(data => {
      console.log('Productos recomendados:', data);
      // Mostrar recomendaciones o realizar otra acción con los datos
    })
    .catch(error => console.error('Error al obtener recomendaciones:', error));
}

// Llamar a la función para obtener productos recomendados
fetchProductRecommendations();
```

---

### **Solución Final:**
Este proyecto simula la construcción de una pequeña aplicación web que utiliza:

1. **Interacción con el DOM**: Para añadir, editar, y eliminar productos.
2. **Persistencia de datos**: Con `localStorage` para mantener los productos entre sesiones.
3. **Validación de datos**: Asegurando que los productos ingresados tienen valores válidos.
4. **Consumo de una API**: Para obtener productos recomendados, simulando el consumo de servicios web externos.
5. **Visualización de datos**: Usando **Chart.js

** para mostrar estadísticas de los productos.
6. **Filtros**: Para que el usuario pueda buscar productos por precio, emulando una funcionalidad común en aplicaciones de inventario o e-commerce.

Este tipo de proyecto introduce a los estudiantes a situaciones comunes en el desarrollo de aplicaciones web, como trabajar con APIs, manipular el DOM, manejar datos dinámicos y realizar validaciones, lo que es esencial para un entorno laboral.
