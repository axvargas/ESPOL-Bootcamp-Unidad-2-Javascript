# **Unidad 9: Local Storage**

**Local Storage** es una funcionalidad del navegador que permite almacenar datos clave-valor de manera persistente en el dispositivo del usuario. Los datos permanecen incluso después de que el navegador se cierra, a menos que el usuario los elimine manualmente o el código lo haga. Es útil para guardar configuraciones, preferencias de usuario, datos temporales, entre otros.

---

### **¿Para qué sirve Local Storage?**
- **Persistir información localmente** sin necesidad de una base de datos externa.
- **Guardar preferencias** del usuario, como el tema oscuro/claro.
- **Almacenar datos temporales** como el contenido de un carrito de compras o formularios parcialmente completados.
- **Optimizar el rendimiento** al reducir solicitudes a un servidor.

---

### **Ejemplo Real: Guardar el tema seleccionado por el usuario (claro u oscuro)**

**Escenario real**: Un desarrollador junior trabaja en una aplicación que permite a los usuarios cambiar entre un tema claro y oscuro. El tema debe persistir incluso cuando el usuario cierre y vuelva a abrir el navegador.

---

### **Paso a Paso para Implementar Local Storage**

#### **1. Configuración del Proyecto**
1. Crea una carpeta para el proyecto, por ejemplo, `local-storage-theme`.
2. Dentro de la carpeta, crea los siguientes archivos:
   - `index.html`: Contendrá el código HTML.
   - `styles.css`: Contendrá los estilos para los temas claro y oscuro.
   - `app.js`: Contendrá el código JavaScript.

---

#### **2. Código HTML**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tema Oscuro/Claro</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Elige un tema</h1>
    <button id="toggleTheme">Cambiar Tema</button>
  </div>
  <script src="app.js"></script>
</body>
</html>
```

---

#### **3. Código CSS**
```css
:root {
  --bg-color-light: #ffffff;
  --text-color-light: #000000;
  --bg-color-dark: #121212;
  --text-color-dark: #ffffff;
}

body.light-theme {
  background-color: var(--bg-color-light);
  color: var(--text-color-light);
}

body.dark-theme {
  background-color: var(--bg-color-dark);
  color: var(--text-color-dark);
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
```

---

#### **4. Código JavaScript**
```javascript
// Paso 1: Obtener referencia al botón
const toggleThemeButton = document.getElementById('toggleTheme');

// Paso 2: Leer el tema actual desde Local Storage (si existe)
const savedTheme = localStorage.getItem('theme');

// Paso 3: Aplicar el tema guardado, o establecer uno por defecto
if (savedTheme) {
  document.body.classList.add(savedTheme);
} else {
  document.body.classList.add('light-theme');
}

// Paso 4: Función para alternar entre temas
function toggleTheme() {
  // Alternar las clases del cuerpo
  if (document.body.classList.contains('light-theme')) {
    document.body.classList.remove('light-theme');
    document.body.classList.add('dark-theme');
    localStorage.setItem('theme', 'dark-theme'); // Guardar tema oscuro
  } else {
    document.body.classList.remove('dark-theme');
    document.body.classList.add('light-theme');
    localStorage.setItem('theme', 'light-theme'); // Guardar tema claro
  }
}

// Paso 5: Agregar Event Listener al botón
toggleThemeButton.addEventListener('click', toggleTheme);
```

---

### **Explicación Paso a Paso**

#### **HTML**
1. Estructuramos el documento HTML.
2. Creamos un botón con el id `toggleTheme` para cambiar entre los temas claro y oscuro.

#### **CSS**
1. Definimos variables CSS para los colores del tema claro y oscuro.
2. Creamos dos clases principales: `light-theme` y `dark-theme`, para manejar los colores de fondo y texto.

#### **JavaScript**
1. **Obtenemos el botón** del DOM usando `getElementById`.
2. **Leemos el tema guardado** del `localStorage` usando `localStorage.getItem('theme')`. Si no hay tema guardado, usamos un tema por defecto (`light-theme`).
3. **Aplicamos el tema** al cuerpo del documento usando `classList.add`.
4. **Creamos una función para alternar temas**:
   - Si el tema actual es claro, lo cambiamos a oscuro.
   - Si el tema actual es oscuro, lo cambiamos a claro.
   - Guardamos el tema actual en el `localStorage` para que persista.
5. **Agregamos un Event Listener al botón** para que ejecute la función al hacer clic.

---

### **Prueba del Ejemplo**
1. **Abre el proyecto en tu navegador**.
2. Haz clic en el botón **"Cambiar Tema"** y observa cómo cambia entre el tema claro y oscuro.
3. **Refresca el navegador**. El tema seleccionado debe persistir, ya que se guarda en el `localStorage`.

---

### **Conclusión**
Este ejemplo es práctico y refleja un problema real que un desarrollador junior podría enfrentar. **Local Storage** es una herramienta poderosa para almacenar datos simples en el navegador y mejorar la experiencia del usuario.
