# **Unidad 8: Fetch – JSON y XML – Consumo de Servicios**
Claro, vamos a detallar el funcionamiento de la función `fetch` en JavaScript y cómo utilizarla con APIs reales. Aquí te presento una explicación general sobre `fetch`, seguida de ejemplos prácticos con APIs gratuitas en formato JSON y XML, además de un ejemplo con paginación.

---

## ¿Qué es `fetch`?

La función `fetch` en JavaScript permite hacer solicitudes HTTP asíncronas para obtener o enviar datos a un servidor. Es comúnmente utilizada para consumir APIs REST y puede manejar respuestas en varios formatos (JSON, XML, texto, etc.). `fetch` devuelve una **promesa** que resuelve en la respuesta de la solicitud.

### Sintaxis básica de `fetch`

```javascript
fetch(url)
  .then(response => {
    // Manejo de la respuesta
  })
  .catch(error => {
    // Manejo de errores
  });
```

1. **URL**: `fetch` toma como argumento la URL de la API que queremos consumir.
2. **Promesa de respuesta**: `fetch` devuelve una promesa que, al resolverse, contiene el objeto `response`.
3. **Conversión de formato**: Una vez obtenida la respuesta, generalmente convertimos el contenido con métodos como `.json()` o `.text()`.

---

## Ejemplo 1: Consumo de API JSON (API de usuarios aleatorios)

Para un ejemplo práctico, usaremos la API gratuita [Random User](https://randomuser.me/), que devuelve datos de usuarios aleatorios en JSON. Este escenario es común cuando queremos obtener una lista de usuarios en una aplicación.

### Pasos para usar la API

1. No se requiere API Key ni configuración adicional.
2. Utiliza la URL de la API para obtener usuarios en formato JSON.

### Código paso a paso

```javascript
// URL de la API de usuarios aleatorios
const url = "https://randomuser.me/api/?results=5";

fetch(url)
  .then(response => {
    // Comprobamos si la respuesta es exitosa
    if (!response.ok) {
      throw new Error("Error en la respuesta de la API");
    }
    // Convertimos la respuesta a formato JSON
    return response.json();
  })
  .then(data => {
    console.log("Usuarios aleatorios:", data.results);
    data.results.forEach(user => {
      console.log(`Nombre: ${user.name.first} ${user.name.last}, País: ${user.location.country}`);
    });
  })
  .catch(error => {
    console.error("Hubo un problema con la solicitud fetch:", error);
  });
```

### Explicación paso a paso

1. **Llamada a `fetch`**: Conectamos con la API usando la URL de `https://randomuser.me/api/?results=5`, que devuelve 5 usuarios aleatorios.
2. **Verificación de respuesta**: Verificamos si la respuesta es correcta. Si no lo es, arrojamos un error.
3. **Conversión a JSON**: Convertimos la respuesta en JSON usando `response.json()`.
4. **Procesamiento de datos**: Iteramos sobre `data.results` para mostrar el nombre completo y país de cada usuario.

---

## Ejemplo 2: Consumo de API XML (API de Noticias del Banco Central Europeo)

Para este ejemplo, usaremos la API del Banco Central Europeo, que proporciona datos en XML. Este ejemplo simula el consumo de noticias o datos financieros en una aplicación empresarial.

### Pasos para usar la API

1. No se requiere autenticación.
2. La API devuelve un feed de noticias en XML.

### Código paso a paso

```javascript
// URL de la API de noticias en formato XML
const url = "https://www.ecb.europa.eu/rss/fxref-usd.html";

fetch(url)
  .then(response => {
    if (!response.ok) {
      throw new Error("Error en la respuesta de la API");
    }
    return response.text(); // Convertimos la respuesta a texto para manejar XML
  })
  .then(data => {
    // Parseamos el XML usando DOMParser
    const parser = new DOMParser();
    const xmlDoc = parser.parseFromString(data, "application/xml");

    // Seleccionamos todos los elementos <item> que representan noticias
    const items = xmlDoc.querySelectorAll("item");
    items.forEach((item, index) => {
      const title = item.querySelector("title").textContent;
      const link = item.querySelector("link").textContent;
      console.log(`Noticia ${index + 1}: ${title} - Enlace: ${link}`);
    });
  })
  .catch(error => {
    console.error("Hubo un problema con la solicitud fetch:", error);
  });
```

### Explicación paso a paso

1. **Llamada a `fetch`**: Conectamos con la API del Banco Central Europeo.
2. **Conversión a texto**: Usamos `response.text()` porque la respuesta está en XML.
3. **Parseo de XML**: Usamos `DOMParser` para convertir el texto XML en un documento que se puede manipular.
4. **Extracción de datos**: Seleccionamos los elementos `<item>`, y de cada uno extraemos `title` y `link` para mostrar las noticias.

---

## Ejemplo 3: Consumo de una API JSON con Paginación (API de películas)

Para este ejemplo, utilizaremos la API de [The Movie Database (TMDb)](https://developers.themoviedb.org/3/getting-started/introduction) para obtener una lista de películas. La API de TMDb permite cargar datos paginados, ideal para aprender a manejar datos en listas grandes. **Nota:** Necesitarás una API Key gratuita.

### Pasos para usar la API

1. Regístrate en [TMDb](https://www.themoviedb.org/) y obtén tu API Key.
2. Usa la URL base de la API junto con la API Key para obtener los datos de películas populares.
3. Implementa paginación para cargar más resultados.

### Código paso a paso

```javascript
// Configuración de API Key y URL base
const apiKey = "TU_API_KEY"; // Reemplaza con tu API Key
const urlBase = `https://api.themoviedb.org/3/movie/popular?api_key=${apiKey}&page=`;

let currentPage = 1;
const moviesContainer = document.getElementById("movies");

// Función para cargar películas de una página específica
function loadMovies(page) {
  fetch(`${urlBase}${page}`)
    .then(response => {
      if (!response.ok) {
        throw new Error("Error en la respuesta de la API");
      }
      return response.json();
    })
    .then(data => {
      data.results.forEach(movie => {
        const movieElement = document.createElement("div");
        movieElement.textContent = `Película: ${movie.title} - Fecha de lanzamiento: ${movie.release_date}`;
        moviesContainer.appendChild(movieElement);
      });

      // Mostrar botón para cargar la siguiente página si hay más películas
      const nextPageButton = document.getElementById("nextPage");
      nextPageButton.style.display = data.page < data.total_pages ? "block" : "none";
    })
    .catch(error => {
      console.error("Hubo un problema con la solicitud fetch:", error);
    });
}

// Cargar la primera página al iniciar
loadMovies(currentPage);

// Evento para cargar la siguiente página
document.getElementById("nextPage").addEventListener("click", () => {
  currentPage += 1;
  loadMovies(currentPage);
});
```

### HTML para visualizar el contenido

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lista de Películas Populares</title>
</head>
<body>
  <h1>Películas Populares</h1>
  <div id="movies"></div>
  <button id="nextPage">Cargar Siguiente Página</button>
  <script src="script.js"></script>
</body>
</html>
```

### Explicación paso a paso

1. **API Key**: Configuramos la clave para autenticar la solicitud.
2. **Paginación inicial**: Comenzamos desde `currentPage = 1`.
3. **Solicitud a la API**: Usamos `fetch` para obtener los datos de la página actual.
4. **Mostrar datos**: Creamos elementos `div` por cada película para mostrar el título y la fecha de lanzamiento.
5. **Control de paginación**: Si existen más páginas, mostramos el botón de “Cargar Siguiente Página” para seguir trayendo datos.
