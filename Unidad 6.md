---

### **Unidad 6: Contexto de Ejecución, Callbacks y Eventos**

#### **Contexto de Ejecución**
El contexto de ejecución es fundamental para entender el comportamiento de las funciones y el manejo de `this` en JavaScript.

**Ejemplo real: Uso de `this` en objetos y funciones**
```javascript
const persona = {
  nombre: 'Carlos',
  edad: 30,
  mostrarInfo: function() {
    console.log(`Nombre: ${this.nombre}, Edad: ${this.edad}`);
  }
};

persona.mostrarInfo();  // Nombre: Carlos, Edad: 30

const mostrar = persona.mostrarInfo;
mostrar();  // undefined, undefined - `this` ya no apunta al objeto original
```

Para evitar perder el contexto de `this`, podemos usar `bind`:
```javascript
const mostrarBind = persona.mostrarInfo.bind(persona);
mostrarBind();  // Nombre: Carlos, Edad: 30
```

#### **Callbacks**
Los callbacks son funciones que se pasan como argumentos para ser ejecutadas más tarde.

**Ejemplo real: Simulación de una llamada a la API**
```javascript
function getDataFromAPI(callback) {
  setTimeout(() => {
    const data = { user: 'Maria', age: 25 };
    callback(data);
  }, 1000);
}

function displayData(data) {
  console.log(`Usuario: ${data.user}, Edad: ${data.age}`);
}

getDataFromAPI(displayData);
```

Este patrón es útil para manejar operaciones asíncronas como peticiones a una API en el frontend.

#### **Eventos**
Los eventos son esenciales para interactuar con el DOM.

**Ejemplo real: Validación de un formulario**
```html
<form id="user-form">
  <label for="name">Nombre:</label>
  <input type="text" id="name" required>
  <button type="submit">Enviar</button>
</form>

<script>
  document.getElementById('user-form').addEventListener('submit', function(event) {
    const nameInput = document.getElementById('name');
    if (nameInput.value === '') {
      alert('El nombre es requerido');
      event.preventDefault();  // Previene el envío del formulario
    }
  });
</script>
```

Este ejemplo demuestra cómo manejar eventos para validar un formulario en una aplicación web.
