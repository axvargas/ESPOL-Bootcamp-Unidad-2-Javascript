### **Tarea 6: Mostrar el clima actual basado en la ubicación del usuario**

---

### **Propósito de la Tarea**

Esta tarea tiene como objetivos:  
1. Aprender a usar la API de geolocalización para obtener las coordenadas del usuario.  
2. Realizar solicitudes a una API externa (OpenWeatherMap) para recuperar información meteorológica.  
3. Mostrar datos dinámicos en pantalla y alternar entre unidades de temperatura (Celsius y Fahrenheit).  

---

### **Instrucciones Detalladas con Explicaciones**

#### **Parte 1: Preparar la clave y URL de la API**  

1. **Obtener la clave de la API (API Key):**
   - Sigue las instrucciones que se muestran en este video para obtener tu API Key gratis: https://www.youtube.com/watch?v=tPlD-CmH7H4
   - Ve a [OpenWeatherMap](https://openweathermap.org/api) y regístrate.  
   - Sustituye `"TU API KEY AQUÍ"` por tu clave en el código.  

   **Código Inicial:**  
   ```javascript
   const weatherAPIKey = "tu-clave-de-api"; // Sustituye con tu clave real
   const weatherAPIURL = `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API key}&units=metric`;
   ```

   **¿Por qué hacemos esto?**  
   La clave permite que OpenWeatherMap autorice tu solicitud y rastree tu uso de la API.  

---

#### **Parte 2: Crear la función de conversión de temperatura**

2. **Definir la función `celsiusToFahr`:**  
   Esta función convierte una temperatura de Celsius a Fahrenheit usando la fórmula:  
   \[
   F = (C \times 9/5) + 32
   \]

   **Código:**  
   ```javascript
   function celsiusToFahr(temperature) {
       let fahr = (temperature * 9 / 5) + 32;
       return fahr;
   }
   ```

   **Ejemplo de uso:**  
   ```javascript
   console.log(celsiusToFahr(25)); // Salida: 77
   ```

   **¿Por qué hacemos esto?**  
   Nos permite mostrar la temperatura en Fahrenheit si el usuario lo prefiere.  

---

#### **Parte 3: Obtener la ubicación del usuario**

3. **Usar la API de Geolocalización del navegador:**  
   La API de geolocalización proporciona la posición actual del usuario (latitud y longitud).  
   Se accede usando el método `navigator.geolocation.getCurrentPosition`.  

   **Código para obtener la posición del usuario:**  
   ```javascript
   navigator.geolocation.getCurrentPosition(position => {
       let latitude = position.coords.latitude; // Latitud del usuario
       let longitude = position.coords.longitude; // Longitud del usuario
   });
   ```

   **Explicación del código:**  
   - `getCurrentPosition` toma una función de *callback* que recibe un objeto `position` como argumento.  
   - Este objeto tiene una propiedad `coords` que incluye las coordenadas (latitud y longitud).  
   - Esas coordenadas se usan para construir la URL de la API meteorológica.  

   **Ejemplo:**  
   ```javascript
   navigator.geolocation.getCurrentPosition(position => {
       console.log("Latitud:", position.coords.latitude);
       console.log("Longitud:", position.coords.longitude);
   });
   ```

   **¿Qué pasa si la geolocalización falla?**  
   Debemos manejar errores mostrando un mensaje de advertencia o realizando una acción alternativa.  

---

#### **Parte 4: Solicitar datos a la API de OpenWeatherMap**

4. **Crear la URL completa con las coordenadas:**  
   Utilizamos las coordenadas obtenidas para construir la URL.  

   **Código:**  
   ```javascript
   let url = weatherAPIURL
       .replace("{lat}", latitude)
       .replace("{lon}", longitude)
       .replace("{API key}", weatherAPIKey);
   ```

5. **Hacer la solicitud a la API:**  
   Utilizamos el método `fetch` para enviar una solicitud a la URL generada.  

   **Código:**  
   ```javascript
   fetch(url)
       .then(response => response.json()) // Convertimos la respuesta a JSON
       .then(data => {
           const condition = data.weather[0].description; // Condición meteorológica
           const location = data.name; // Nombre de la ciudad
           const temperature = data.main.temp; // Temperatura en Celsius

           console.log(`El clima en ${location} es ${condition}, y la temperatura es ${temperature}°C`);
       });
   ```

   **Explicación del flujo:**  
   - `fetch(url)`: Envía una solicitud HTTP a la URL especificada.  
   - `.then(response => response.json())`: Convierte la respuesta a un formato que JavaScript pueda entender (JSON).  
   - `.then(data => {...})`: Maneja los datos de la API.  

   **¿Qué pasa si hay un error?**  
   Agregamos un bloque `.catch` para manejar errores en la solicitud.  

---

#### **Parte 5: Mostrar los datos en pantalla**

6. **Mostrar el clima en grados Celsius:**  
   Creamos un mensaje con los datos recuperados de la API y lo mostramos en un elemento `<p>`.  

   **Código:**  
   ```javascript
   let celsiusText = `The weather is ${condition} in ${location} and it's ${temperature.toFixed(1)}°C outside.`;
   document.querySelector("p#weather").innerHTML = celsiusText;
   ```

7. **Agregar funcionalidad para cambiar entre Celsius y Fahrenheit:**  
   Creamos un evento que detecta el clic en botones para alternar las unidades de temperatura.  

   **Código:**  
   ```javascript
   document.querySelector(".weather-group").addEventListener("click", function (e) {
       if (e.target.id === "celsius") {
           document.querySelector("p#weather").innerHTML = celsiusText;
       } else if (e.target.id === "fahr") {
           let fahrText = `The weather is ${condition} in ${location} and it's ${celsiusToFahr(temperature).toFixed(1)}°F outside.`;
           document.querySelector("p#weather").innerHTML = fahrText;
       }
   });
   ```

---

### **Código Completo**

```javascript
const weatherAPIKey = "TU API KEY AQUÍ";
const weatherAPIURL = `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API key}&units=metric`;

function celsiusToFahr(temperature) {
    return (temperature * 9 / 5) + 32;
}

function weatherHandler() {
    navigator.geolocation.getCurrentPosition(position => {
        let latitude = position.coords.latitude;
        let longitude = position.coords.longitude;

        let url = weatherAPIURL
            .replace("{lat}", latitude)
            .replace("{lon}", longitude)
            .replace("{API key}", weatherAPIKey);

        fetch(url)
            .then(response => response.json())
            .then(data => {
                const condition = data.weather[0].description;
                const location = data.name;
                const temperature = data.main.temp;

                let celsiusText = `The weather is ${condition} in ${location} and it's ${temperature.toFixed(1)}°C outside.`;
                let fahrText = `The weather is ${condition} in ${location} and it's ${celsiusToFahr(temperature).toFixed(1)}°F outside.`;

                document.querySelector("p#weather").innerHTML = celsiusText;

                document.querySelector(".weather-group").addEventListener("click", function (e) {
                    if (e.target.id === "celsius") {
                        document.querySelector("p#weather").innerHTML = celsiusText;
                    } else if (e.target.id === "fahr") {
                        document.querySelector("p#weather").innerHTML = fahrText;
                    }
                });
            })
            .catch(() => {
                document.querySelector("p#weather").innerHTML = "Unable to get the weather info. Try again later.";
            });
    });
}

weatherHandler();
```
--- 

### **Resultado Esperado**
1. Muestra el clima actual en la ubicación del usuario.  
2. Cambia entre Celsius y Fahrenheit al hacer clic en los botones correspondientes.  
3. Maneja errores si no es posible obtener los datos.
