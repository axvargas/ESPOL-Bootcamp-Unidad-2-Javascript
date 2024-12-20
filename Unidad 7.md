---

# **Unidad 7: Eventos y Callbacks**
## Eventos en el DOM

En JavaScript, un **evento** es una acción que ocurre en la página web y puede ser detectada por el navegador. Estos eventos incluyen cosas como hacer clic en un botón, pasar el mouse sobre una imagen, presionar una tecla en el teclado, o incluso cargar la página completa.

#### Ejemplos de eventos comunes:
- `click`: Se activa cuando el usuario hace clic en un elemento.
- `mouseover`: Se activa cuando el usuario coloca el puntero del mouse sobre un elemento.
- `mouseout`: Se activa cuando el puntero del mouse sale de un elemento.
- `keydown`: Se activa cuando una tecla del teclado es presionada.
- `load`: Se activa cuando un recurso como una página o imagen ha terminado de cargarse.

### Agregar Eventos en el DOM

Existen varias maneras de añadir eventos a los elementos del DOM. Aquí explicamos dos formas comunes: usando el atributo HTML y usando JavaScript (la forma recomendada).

#### 1. Usando el Atributo HTML `onclick` (no recomendado para proyectos grandes)

Puedes añadir eventos directamente en el HTML utilizando atributos como `onclick`, `onmouseover`, etc. Esto no es recomendable para aplicaciones grandes, ya que puede dificultar el mantenimiento del código.

```html
<button onclick="alert('¡Hola!')">Haz clic aquí</button>
```

#### 2. Usando `addEventListener` en JavaScript (recomendado)

La forma recomendada de manejar eventos en JavaScript es utilizando el método `addEventListener`. Esto permite separar el HTML y el JavaScript, lo cual facilita el mantenimiento y organización del código.

**Sintaxis básica**:
```javascript
elemento.addEventListener('tipoDeEvento', función);
```

**Ejemplo práctico:**
Supongamos que tienes un botón en tu HTML y deseas mostrar un mensaje cuando el usuario hace clic en él.

HTML:
```html
<button id="miBoton">Haz clic aquí</button>
```

JavaScript:
```javascript
// Seleccionamos el elemento botón
const boton = document.getElementById('miBoton');

// Agregamos un evento de clic al botón
boton.addEventListener('click', function() {
    alert('¡Has hecho clic en el botón!');
});
```

En este ejemplo:
- Seleccionamos el botón usando `document.getElementById`.
- Usamos `addEventListener` para agregar un evento de tipo `'click'` al botón.
- Especificamos la acción (una función) que queremos que ocurra al hacer clic.

### Ejemplo Completo: Modificar el DOM al Clic de un Botón

Supongamos que queremos cambiar el texto de un párrafo cada vez que el usuario hace clic en el botón.

HTML:
```html
<button id="miBoton">Haz clic aquí</button>
<p id="miParrafo">Texto original</p>
```

JavaScript:
```javascript
const boton = document.getElementById('miBoton');
const parrafo = document.getElementById('miParrafo');

boton.addEventListener('click', function() {
    parrafo.textContent = '¡El texto ha cambiado!';
});
```

En este caso:
- Cuando el usuario hace clic en el botón, el texto del párrafo cambia a "¡El texto ha cambiado!".
  
### Resumen

- **Eventos**: Permiten responder a las acciones del usuario.
- **`addEventListener`**: Método recomendado para manejar eventos, manteniendo el código organizado.
- **Aplicación**: Se puede modificar el contenido del DOM, cambiar estilos, o realizar casi cualquier operación en respuesta a eventos.


### **Menú de navegación que se muestra y se oculta al hacer clic en un botón**

En este ejemplo, crearemos un menú de navegación que se despliega y se oculta al hacer clic en un botón, utilizando JavaScript. Separaremos el CSS en su propio archivo y explicaremos el código JavaScript paso a paso para que sea fácil de seguir.

---

#### **Archivo HTML (`index.html`)**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Menú Desplegable</title>
  <link rel="stylesheet" href="style.css"> <!-- Enlace al archivo CSS -->
</head>
<body>
  <header>
    <button id="menu-toggle">☰ Menú</button> <!-- Botón para mostrar/ocultar el menú -->
    <nav id="nav-menu" class="hidden">
      <ul>
        <li><a href="#home">Inicio</a></li>
        <li><a href="#about">Acerca de</a></li>
        <li><a href="#services">Servicios</a></li>
        <li><a href="#contact">Contacto</a></li>
      </ul>
    </nav>
  </header>
  <script src="script.js"></script> <!-- Enlace al archivo JavaScript -->
</body>
</html>
```

---

#### **Archivo CSS (`style.css`)**
```css
/* Estilos generales */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

/* Botón del menú */
#menu-toggle {
  background-color: #007BFF;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

/* Menú de navegación */
#nav-menu {
  background-color: #f8f9fa;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Lista del menú */
#nav-menu ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

/* Enlaces del menú */
#nav-menu li {
  margin: 10px 0;
}

#nav-menu a {
  text-decoration: none;
  color: #007BFF;
  font-size: 18px;
}

/* Ocultar el menú por defecto */
.hidden {
  display: none;
}
```

---

#### **Archivo JavaScript (`script.js`)**
```javascript
// Paso 1: Seleccionar los elementos del DOM
const menuToggle = document.getElementById('menu-toggle'); // Botón de menú
const navMenu = document.getElementById('nav-menu'); // Menú de navegación

// Paso 2: Agregar un event listener al botón
menuToggle.addEventListener('click', () => {
  // Paso 3: Alternar la clase "hidden" en el menú
  navMenu.classList.toggle('hidden');
});
```

---

### **Explicación paso a paso del código JavaScript:**

1. **Seleccionar los elementos del DOM:**
   ```javascript
   const menuToggle = document.getElementById('menu-toggle');
   const navMenu = document.getElementById('nav-menu');
   ```
   - Usamos `document.getElementById` para seleccionar el botón con ID `menu-toggle` y el menú con ID `nav-menu`.
   - Estas referencias nos permiten interactuar con estos elementos en el JavaScript.

2. **Agregar un `event listener` al botón:**
   ```javascript
   menuToggle.addEventListener('click', () => {
     // Código dentro del listener
   });
   ```
   - Asignamos un evento `click` al botón `menu-toggle`.
   - Cada vez que el botón sea presionado, se ejecutará la función definida dentro del `addEventListener`.

3. **Alternar la clase `hidden`:**
   ```javascript
   navMenu.classList.toggle('hidden');
   ```
   - Usamos el método `classList.toggle` para agregar o quitar la clase `hidden` del menú.
   - Si el menú tiene la clase `hidden`, se elimina (mostrando el menú).
   - Si no tiene la clase, se agrega (ocultando el menú).

---

### **Pasos para que los estudiantes implementen el proyecto:**

1. **Crear los archivos necesarios:**
   - Crea tres archivos: `index.html`, `style.css` y `script.js`.
   - Copia y pega el código anterior en los archivos correspondientes.

2. **Configurar el entorno local:**
   - Usa **Visual Studio Code** y ejecuta el archivo `index.html` con la extensión **Live Server** para ver los cambios en tiempo real.

3. **Paso a paso en el JavaScript:**
   - **Selecciona los elementos**: Usa `document.getElementById` para obtener referencias al botón y al menú.
   - **Agrega un evento**: Usa `addEventListener` para que el botón reaccione al clic.
   - **Alterna la clase**: Aplica `classList.toggle` para ocultar o mostrar el menú.

4. **Prueba el comportamiento:**
   - Haz clic en el botón y verifica que el menú se muestra y se oculta correctamente.

---

### Recursos Externos

1. [Mozilla Developer Network (MDN) - Introducción a los eventos en JavaScript](https://developer.mozilla.org/es/docs/Learn/JavaScript/Building_blocks/Events)
2. [JavaScript.info - Event handling](https://javascript.info/introduction-browser-events)

---

## Callbacks

Un **callback** en JavaScript es una función que se pasa como argumento a otra función y que se ejecuta después de que se completa una operación. Los callbacks son esenciales para manejar operaciones asincrónicas, como temporizadores, eventos del DOM y solicitudes de red. Son comunes en tareas en las que no se sabe con certeza cuánto tiempo tomará la ejecución, y el código necesita esperar a que se complete antes de continuar.

### ¿Por qué usar callbacks?

Los callbacks son útiles cuando una tarea lleva tiempo (como cargar datos de un servidor) y no quieres que el código se "congele" mientras espera. Con los callbacks, puedes decirle a JavaScript: "Sigue ejecutando el resto del código, y cuando esta tarea termine, ejecuta esta función".

### Ejemplo básico de callback

Veamos un ejemplo simple en el que usamos un callback con `setTimeout`, una función que ejecuta una acción después de un tiempo determinado:

```javascript
function saludo(callback) {
    console.log("Hola!");
    setTimeout(callback, 2000); // Espera 2 segundos antes de ejecutar el callback
}

function despedida() {
    console.log("Adiós!");
}

saludo(despedida); // Ejecuta "Hola!" y luego, después de 2 segundos, ejecuta "Adiós!"
```

En este ejemplo:
- `saludo` se ejecuta primero y muestra "Hola!" en la consola.
- Después de 2 segundos, `despedida` (el callback) se ejecuta y muestra "Adiós!".

### Ejemplo práctico de callback: Simulando una solicitud de datos al servidor

Imaginemos un caso típico al que se enfrentaría un desarrollador junior: cargar datos de una base de datos o servidor. A menudo, la obtención de datos tarda algunos segundos, por lo que usamos callbacks para manejar lo que sucede después de que los datos se obtienen.

Supongamos que tenemos una función `obtenerUsuario` que simula la obtención de los datos de un usuario desde un servidor. Cuando los datos llegan, se llama a un callback que muestra la información del usuario.

```javascript
function obtenerUsuario(callback) {
    console.log("Obteniendo datos del usuario...");

    // Simulamos una solicitud con setTimeout
    setTimeout(function() {
        const usuario = {
            nombre: "María Pérez",
            edad: 28,
            email: "maria.perez@email.com"
        };

        // Llamamos al callback con el usuario como argumento
        callback(usuario);
    }, 3000); // Simula un retraso de 3 segundos
}

function mostrarUsuario(usuario) {
    console.log("Datos del usuario:");
    console.log("Nombre:", usuario.nombre);
    console.log("Edad:", usuario.edad);
    console.log("Email:", usuario.email);
}

// Llamamos a obtenerUsuario, pasándole mostrarUsuario como callback
obtenerUsuario(mostrarUsuario);
```

En este ejemplo:
1. `obtenerUsuario` simula una solicitud al servidor y tarda 3 segundos en "obtener" los datos del usuario.
2. Después de esos 3 segundos, `obtenerUsuario` llama al callback `mostrarUsuario`, pasando los datos del usuario como argumento.
3. `mostrarUsuario` recibe el objeto `usuario` y muestra la información en la consola.

Este enfoque permite que `obtenerUsuario` maneje el tiempo de espera y que `mostrarUsuario` solo se ejecute una vez que los datos estén listos.

### Explicación detallada del flujo:

- **Inicio**: `obtenerUsuario` se llama y comienza a simular la obtención de datos.
- **Espera de 3 segundos**: Durante este tiempo, otros códigos en el programa pueden seguir ejecutándose sin interferir con esta operación asincrónica.
- **Llamada al callback**: Cuando los datos están listos, `obtenerUsuario` llama a `mostrarUsuario`, pasándole los datos obtenidos como parámetro.
- **Salida en consola**: `mostrarUsuario` muestra los datos, finalizando el flujo.

### Resumen

Los **callbacks** son funciones esenciales para manejar tareas asincrónicas y permiten que el código continúe ejecutándose mientras se espera una tarea, sin que se congele o bloquee la interfaz de usuario. Con callbacks, puedes asegurarte de que el código se ejecute en el momento adecuado, especialmente después de tareas que toman tiempo.

### Recursos externos

1. [Callbacks en JavaScript - MDN](https://developer.mozilla.org/es/docs/Glossary/Callback_function)
2. [JavaScript.info - Introducción a los callbacks](https://javascript.info/callbacks) 
