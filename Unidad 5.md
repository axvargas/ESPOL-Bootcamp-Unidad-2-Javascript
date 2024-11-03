---

### **Unidad 5: Plantillas**

Las **plantillas en JavaScript** permiten crear contenido dinámico y estructurado de forma eficiente. Usando plantillas, puedes generar elementos HTML de manera programática y añadirlos al DOM. 

Aquí vamos a ver cómo hacerlo con un ejemplo práctico donde agregamos imágenes a un contenedor `<div>` en una lista dinámica, usando `querySelector`, `createElement`, y `appendChild`.

### Ejemplo práctico: Agregar una lista de imágenes a un `<div>`

Supongamos que queremos mostrar una lista de imágenes (como una galería) en nuestra página web. Las imágenes se agregarán a un `<div id="galeria">` en el HTML. En este caso, usaremos una lista de URLs de imágenes y generaremos dinámicamente los elementos `<img>` para cada URL. 

#### Paso 1: Crear el contenedor en HTML

Nuestro HTML inicial tiene un `<div>` vacío donde se añadirán las imágenes:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Imágenes</title>
</head>
<body>
    <h1>Galería de Imágenes</h1>
    <div id="galeria"></div>

    <script src="script.js"></script>
</body>
</html>
```

#### Paso 2: Crear la plantilla dinámica en JavaScript

En `script.js`, primero crearemos un array de URLs de imágenes, luego usaremos `createElement` para crear cada imagen y `appendChild` para añadirlas al `<div id="galeria">`.

```javascript
// Lista de URLs de las imágenes
const imagenes = [
    "https://via.placeholder.com/150/0000FF", // Cambia estos enlaces por tus propias imágenes
    "https://via.placeholder.com/150/FF0000",
    "https://via.placeholder.com/150/00FF00",
    "https://via.placeholder.com/150/FFFF00",
];

// Seleccionamos el contenedor donde vamos a añadir las imágenes
const galeria = document.querySelector("#galeria");

// Función para agregar las imágenes a la galería
function cargarGaleria(imagenes) {
    imagenes.forEach((url) => {
        // Creamos un elemento <img>
        const img = document.createElement("img");

        // Establecemos la URL de la imagen
        img.src = url;

        // Añadimos clases para estilos (opcional)
        img.classList.add("imagen-galeria");

        // Añadimos la imagen al contenedor de la galería
        galeria.appendChild(img);
    });
}

// Llamamos a la función para cargar la galería de imágenes
cargarGaleria(imagenes);
```

En este código:

1. **Array de URLs de imágenes**: Creamos un array `imagenes` que contiene las URLs de cada imagen a mostrar en la galería.
2. **Selector de contenedor**: Usamos `querySelector` para seleccionar el `<div>` con el id `"galeria"` donde se añadirán las imágenes.
3. **Creación de cada imagen**: Recorremos el array `imagenes` con `forEach`. Para cada URL:
   - Creamos un elemento `<img>` con `createElement`.
   - Asignamos la URL de la imagen a `img.src`.
   - Agregamos la imagen al contenedor con `appendChild`.
4. **Función `cargarGaleria`**: Esta función permite que las imágenes se carguen cuando se llama, manteniendo el código organizado.

#### Paso 3: Estilizar las imágenes (opcional)

Para hacer que la galería se vea mejor, puedes añadir algo de CSS para las imágenes:

```css
#galeria {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.imagen-galeria {
    width: 150px;
    height: auto;
    border-radius: 8px;
}
```

### Explicación del flujo

- Al cargar la página, el script `script.js` selecciona el contenedor `#galeria`.
- La función `cargarGaleria` recorre el array `imagenes`, creando y añadiendo cada `<img>` dentro del contenedor.
- Esto permite cargar dinámicamente una galería de imágenes sin tener que escribir manualmente cada imagen en HTML.

### Resultado

El navegador muestra todas las imágenes del array en el `<div id="galeria">`. Esto es especialmente útil en aplicaciones web que requieren manejar listas de datos de manera dinámica, como galerías de productos o vistas de imágenes en miniatura.

### Recursos adicionales

1. [MDN - Document.createElement](https://developer.mozilla.org/es/docs/Web/API/Document/createElement)
2. [JavaScript.info - Manipulación del DOM](https://javascript.info/modifying-document)
