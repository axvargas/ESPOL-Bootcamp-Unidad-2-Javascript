# **Unidad 10: Mapas y Datatables**
---

### **HTML**
Save this as `index.html`.
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Breweries Map & DataTable</title>
  <link rel="stylesheet" href="style.css">
  <!-- DataTables CSS -->
  <link rel="stylesheet" href="https://cdn.datatables.net/1.13.6/css/jquery.dataTables.min.css">
  <!-- Mapbox CSS -->
  <link href="https://api.mapbox.com/mapbox-gl-js/v2.15.0/mapbox-gl.css" rel="stylesheet">
</head>
<body>
  <h1>Breweries DataTable and Map</h1>
  <table id="breweriesTable">
    <thead>
      <tr>
        <th>Name</th>
        <th>Type</th>
        <th>City</th>
        <th>State</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <div id="map"></div>

  <!-- JQuery -->
  <script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>
  <!-- DataTables JS -->
  <script src="https://cdn.datatables.net/1.13.6/js/jquery.dataTables.min.js"></script>
  <!-- Mapbox GL JS -->
  <script src="https://api.mapbox.com/mapbox-gl-js/v2.15.0/mapbox-gl.js"></script>
  <!-- Main Script -->
  <script src="script.js"></script>
</body>
</html>
```

---

### **CSS**
Save this as `style.css`.
```css
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

#breweriesTable {
  width: 100%;
  margin-bottom: 20px;
}

#map {
  width: 100%;
  height: 500px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

@media (max-width: 768px) {
  h1 {
    font-size: 24px;
  }
}
```

---

### **JavaScript**
Save this as `script.js`.

### **1. Configuración del token de Mapbox**
```javascript
mapboxgl.accessToken = 'pk.eyJ1IjoiYW5kcmVzeGF2aWVyOTkiLCJhIjoiY20zbWUyMWdqMTFzZDJrcHhidjlhZjFwaCJ9.JxyJSYQBmQI77epaw4xUaQ';
```
- **¿Qué hace?**
  - Se establece un token de acceso para Mapbox. Este token es como una clave que autentica tu aplicación para usar los servicios de Mapbox.
  - **Mapbox** es una biblioteca que permite mostrar mapas interactivos en aplicaciones web.

- **¿Por qué es importante?**
  - Sin este token, no puedes usar los servicios de Mapbox en tu proyecto.

---

### **2. Crear el mapa inicial**
```javascript
const map = new mapboxgl.Map({
  container: 'map', // ID del contenedor HTML donde se renderiza el mapa
  style: 'mapbox://styles/mapbox/streets-v11', // Estilo visual del mapa
  center: [-78.52495, -0.22985], // Coordenadas iniciales (longitud, latitud)
  zoom: 3 // Nivel inicial de zoom
});
```
- **¿Qué hace?**
  - Crea un mapa interactivo y lo coloca en el contenedor HTML con el ID `map`.
  - Usa el estilo `streets-v11`, que muestra un mapa con calles y nombres.
  - Inicialmente, el mapa está centrado en las coordenadas **[-78.52495, -0.22985]**, que corresponde a Quito, Ecuador, y tiene un nivel de zoom moderado (3).

- **Desglose:**
  - `container`: ID del elemento HTML donde se mostrará el mapa.
  - `style`: Tipo de mapa que quieres usar (calles, satélite, etc.).
  - `center`: Coordenadas geográficas iniciales del mapa.
  - `zoom`: Qué tan cerca o lejos se verá el mapa al cargar.

---

### **3. Obtener datos de una API (fetchBreweries)**
```javascript
const fetchBreweries = async () => {
  const url = 'https://api.openbrewerydb.org/breweries?per_page=10';
  try {
    const response = await fetch(url); // Llama a la API para obtener datos
    const breweries = await response.json(); // Convierte la respuesta a JSON
    return breweries; // Devuelve los datos
  } catch (error) {
    console.error('Error fetching breweries:', error);
  }
};
```
- **¿Qué hace?**
  - Llama a la API **Open Brewery DB** para obtener una lista de 10 cervecerías.
  - Usa la función `fetch` para realizar la solicitud HTTP.

- **Desglose:**
  - `fetch(url)`: Envía una solicitud al servidor.
  - `response.json()`: Convierte la respuesta en un objeto JSON legible por JavaScript.
  - `return breweries`: Devuelve los datos para usarlos más tarde.
  - `try...catch`: Muestra un error si la solicitud falla.

---

### **4. Población de la tabla (populateDataTable)**
```javascript
function populateDataTable(data) {
  new DataTable('#geoTable', {
    data: data,
    columns: [
      { data: 'name', title: 'Name' },
      { data: 'brewery_type', title: 'Type' },
      { data: 'city', title: 'City' },
      { data: 'state', title: 'State' },
      { data: 'latitude', title: 'Latitude' },
      { data: 'longitude', title: 'Longitude' },
    ],
  });
}
```
- **¿Qué hace?**
  - Usa la biblioteca **DataTables.js** para mostrar los datos de las cervecerías en una tabla interactiva.
  - Mapea cada columna de la tabla a una propiedad del objeto `data`.

- **Desglose:**
  - `#geoTable`: ID del elemento HTML donde se mostrará la tabla.
  - `data`: Datos de las cervecerías (devueltos por `fetchBreweries`).
  - `columns`: Define qué campos de los datos se mostrarán en la tabla.

---

### **5. Agregar marcadores en el mapa (addMarkers)**
```javascript
function addMarkers(data) {
  data.forEach(brewery => {
    if (brewery.latitude && brewery.longitude) {
      new mapboxgl.Marker()
        .setLngLat([brewery.longitude, brewery.latitude])
        .setPopup(new mapboxgl.Popup().setHTML(`
          <h3>${brewery.name}</h3>
          <p>${brewery.city}, ${brewery.state}</p>
          <a href="${brewery.website}" target="_blank">Website</a>
        `))
        .addTo(map);
    }
  });

  const bounds = new mapboxgl.LngLatBounds();
  data.forEach(brewery => {
    if (brewery.latitude && brewery.longitude) {
      bounds.extend([brewery.longitude, brewery.latitude]);
    }
  });
  map.fitBounds(bounds, { padding: 40 });
}
```
- **¿Qué hace?**
  - Crea un marcador para cada cervecería y lo coloca en el mapa usando sus coordenadas.
  - Añade un popup al marcador con información de la cervecería.
  - Ajusta la vista del mapa para que todos los marcadores sean visibles.

- **Desglose:**
  - `new mapboxgl.Marker()`: Crea un nuevo marcador.
  - `.setLngLat([longitud, latitud])`: Define la posición del marcador.
  - `.setPopup()`: Añade un cuadro informativo al marcador.
  - `.addTo(map)`: Coloca el marcador en el mapa.
  - `LngLatBounds`: Calcula los límites para que el mapa incluya todos los marcadores.
  - `map.fitBounds(bounds)`: Ajusta el mapa para que muestre todos los marcadores con un margen.

---

### **6. Inicialización del proyecto**
```javascript
(async function initializeApp() {
  const data = await fetchBreweries(); // Obtiene los datos
  populateDataTable(data); // Llena la tabla
  addMarkers(data); // Coloca los marcadores en el mapa
})();
```
- **¿Qué hace?**
  - Llama a las funciones principales en el orden correcto:
    1. Obtiene los datos de la API.
    2. Llena la tabla interactiva con los datos.
    3. Coloca los marcadores en el mapa.
  - Usa una función **asíncrona** para garantizar que los datos se obtengan antes de usarlos.
