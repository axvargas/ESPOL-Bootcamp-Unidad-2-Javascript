
# Unidad 4: Objetos en el Navegador, Debugging y DOM

## Elementos Clave del Navegador

1. **Inspector de Elementos (DevTools)**:
   - **Descripción**: Herramienta que permite a los desarrolladores inspeccionar el DOM y los estilos CSS aplicados a los elementos de una página web.
   - **Uso**: Se puede acceder haciendo clic derecho en un elemento de la página y seleccionando "Inspeccionar". Permite ver y editar el HTML y CSS en tiempo real, lo que facilita el diseño y la depuración.
   - **Ejemplo de Uso**: Si un botón no se muestra como se espera, el desarrollador puede inspeccionar el elemento para verificar su CSS y ver si hay estilos que lo ocultan o lo afectan.

2. **Consola**:
   - **Descripción**: Una de las herramientas más importantes para el desarrollo, la consola permite ejecutar código JavaScript directamente, así como ver mensajes de error y advertencias.
   - **Uso**: Los desarrolladores pueden escribir comandos y scripts, y ver el resultado inmediatamente. También es útil para depurar el código, ya que muestra errores y advertencias.
   - **Ejemplo de Uso**: Usar `console.log(variable)` para verificar el valor de una variable en un momento determinado de la ejecución del código.

3. **Panel de Red (Network)**:
   - **Descripción**: Permite monitorear todas las solicitudes de red realizadas por la página, incluidas las solicitudes de archivos HTML, CSS, JavaScript, imágenes y recursos de API.
   - **Uso**: Los desarrolladores pueden ver qué recursos se cargan, el tiempo que tardan en cargarse y el estado de cada solicitud (éxito o error).
   - **Ejemplo de Uso**: Si una imagen no se carga, el desarrollador puede comprobar en el panel de red si la solicitud se realizó correctamente y si se devolvió algún error (404, 500, etc.).

4. **Panel de Estilos (Styles)**:
   - **Descripción**: Muestra todos los estilos CSS aplicados a un elemento seleccionado. Permite modificar estilos y ver los cambios en tiempo real.
   - **Uso**: Ideal para experimentar con estilos, como cambiar colores, márgenes, o tamaños de fuente sin necesidad de editar los archivos CSS.
   - **Ejemplo de Uso**: Cambiar el color de fondo de un elemento directamente en el panel de estilos para ver cómo afecta el diseño.

5. **Panel de Fuentes (Sources)**:
   - **Descripción**: Permite explorar y editar los archivos JavaScript y CSS utilizados en la página.
   - **Uso**: Los desarrolladores pueden establecer puntos de interrupción (breakpoints) para depurar el código JavaScript, lo que les permite pausar la ejecución y examinar el estado de las variables.
   - **Ejemplo de Uso**: Colocar un breakpoint en una función para observar su comportamiento y el flujo de datos.

6. **Panel de Aplicación (Application)**:
   - **Descripción**: Ofrece información sobre las aplicaciones web que utilizan tecnologías como almacenamiento local (localStorage), cookies, bases de datos IndexedDB y otros recursos.
   - **Uso**: Permite a los desarrolladores ver y modificar datos almacenados por la aplicación web.
   - **Ejemplo de Uso**: Ver los elementos almacenados en `localStorage` para verificar el estado de la sesión del usuario.

7. **Panel de Performance**:
   - **Descripción**: Permite analizar el rendimiento de la aplicación web, incluidos tiempos de carga y eventos.
   - **Uso**: Se puede utilizar para identificar cuellos de botella en el rendimiento y optimizar la experiencia del usuario.
   - **Ejemplo de Uso**: Grabar un rendimiento y analizar las funciones que consumen más tiempo durante la ejecución.

### Resumen

Conocer y utilizar eficazmente las herramientas del navegador es fundamental para cualquier desarrollador junior. Estas herramientas ayudan no solo a depurar y optimizar aplicaciones, sino también a comprender cómo funcionan las páginas web a nivel técnico. Familiarizarse con estos elementos mejorará la eficiencia y la calidad del trabajo de un desarrollador en sus proyectos.

## Interacción con el DOM
### Estructura del DOM y Manipulación a través del Objeto `document`

El **Document Object Model (DOM)** es una representación estructurada de los documentos HTML y XML. Permite a los lenguajes de programación, como JavaScript, interactuar y manipular el contenido, la estructura y el estilo de un documento web de manera dinámica. El DOM se organiza en una estructura jerárquica, donde cada elemento del documento se representa como un objeto.

#### Estructura del DOM

1. **Documento**: El nodo raíz que representa el documento completo.
2. **Elementos**: Cada etiqueta HTML (como `<div>`, `<p>`, `<h1>`, etc.) se convierte en un nodo de elemento.
3. **Atributos**: Cada atributo de un elemento (como `id`, `class`, `src`, etc.) se representa como un nodo hijo del nodo de elemento.
4. **Texto**: El texto dentro de los elementos es un nodo hijo del nodo de elemento que lo contiene.

Por ejemplo, en el siguiente HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Mi página</title>
</head>
<body>
    <h1 id="titulo">Bienvenido a mi página</h1>
    <p class="contenido">Este es un párrafo de contenido.</p>
    <ul>
        <li>Elemento 1</li>
        <li>Elemento 2</li>
        <li>Elemento 3</li>
    </ul>
</body>
</html>
```

La estructura del DOM sería algo así:

```
Document
 └── html
     └── head
     └── body
         ├── h1 (id="titulo")
         ├── p (class="contenido")
         └── ul
             ├── li
             ├── li
             └── li
```

### Interactuando con el DOM a Través del Objeto `document`

El objeto `document` es el punto de entrada para manipular el DOM. A través de `document`, podemos acceder, modificar y eliminar elementos en el documento.

#### Métodos de Selección de Elementos

1. **`getElementById`**: Selecciona un elemento por su `id`.

   ```javascript
   const titulo = document.getElementById('titulo');
   console.log(titulo.innerHTML); // "Bienvenido a mi página"
   ```

2. **`getElementsByClassName`**: Selecciona elementos por su clase (devuelve una colección de nodos).

   ```javascript
   const parrafos = document.getElementsByClassName('contenido');
   console.log(parrafos[0].innerHTML); // "Este es un párrafo de contenido."
   ```

3. **`getElementsByTagName`**: Selecciona elementos por su nombre de etiqueta.

   ```javascript
   const items = document.getElementsByTagName('li');
   console.log(items.length); // 3
   ```

4. **`querySelector`**: Selecciona el primer elemento que coincide con un selector CSS.

   ```javascript
   const primerItem = document.querySelector('li');
   console.log(primerItem.innerHTML); // "Elemento 1"
   ```

5. **`querySelectorAll`**: Selecciona todos los elementos que coinciden con un selector CSS (devuelve una NodeList).

   ```javascript
   const todosLosItems = document.querySelectorAll('li');
   todosLosItems.forEach(item => console.log(item.innerHTML));
   ```

### Modificar el `innerHTML`

El `innerHTML` es una propiedad que permite obtener o establecer el contenido HTML de un elemento. Esto significa que puedes cambiar lo que se muestra en la página.

```javascript
const contenido = document.querySelector('.contenido');
contenido.innerHTML = 'Este contenido ha sido modificado.'; // Cambia el contenido del párrafo
```

### Recorrer Elementos

Una vez que hemos seleccionado elementos, podemos recorrerlos y manipularlos. Aquí hay algunas maneras de hacerlo:

1. **Usando un bucle `for`**:

   ```javascript
   const items = document.getElementsByTagName('li');
   for (let i = 0; i < items.length; i++) {
       console.log(items[i].innerHTML); // Imprime el contenido de cada elemento
   }
   ```

2. **Usando `forEach` con NodeList**:

   ```javascript
   const items = document.querySelectorAll('li');
   items.forEach(item => {
       console.log(item.innerHTML); // Imprime el contenido de cada elemento
   });
   ```

3. **Usando `for...of`**:

   ```javascript
   const items = document.querySelectorAll('li');
   for (const item of items) {
       console.log(item.innerHTML); // Imprime el contenido de cada elemento
   }
   ```

### Resumen

- El DOM es una representación estructurada de documentos HTML y XML.
- `document` permite interactuar con el DOM.
- Métodos como `getElementById`, `getElementsByClassName`, `getElementsByTagName`, `querySelector`, y `querySelectorAll` se utilizan para seleccionar elementos.
- El `innerHTML` permite modificar el contenido de los elementos seleccionados.
- Se pueden recorrer los elementos seleccionados utilizando bucles.


### Ejemplo de HTML

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo de querySelector</title>
    <style>
        .destacado {
            color: red;
        }
    </style>
</head>
<body>
    <h1 class="titulo">Bienvenido a mi página</h1>
    <p class="contenido">Este es un párrafo de contenido.</p>
    <p class="contenido destacado">Este es un párrafo destacado.</p>
    <ul>
        <li class="item">Elemento 1</li>
        <li class="item">Elemento 2</li>
        <li class="item destacado">Elemento 3</li>
    </ul>
    <button id="miBoton">Click aquí</button>
    <script src="script.js"></script>
</body>
</html>
```

### Uso de `querySelector`

El método `querySelector` selecciona el primer elemento que coincide con el selector CSS proporcionado. Aquí algunos ejemplos de cómo utilizarlo con el HTML anterior:

1. **Seleccionar por ID**:

   ```javascript
   const boton = document.querySelector('#miBoton');
   console.log(boton); // Selecciona el botón con id="miBoton"
   ```

2. **Seleccionar por clase**:

   ```javascript
   const parrafoDestacado = document.querySelector('.destacado');
   console.log(parrafoDestacado.innerHTML); // "Este es un párrafo destacado."
   ```

3. **Seleccionar por etiqueta**:

   ```javascript
   const primerParrafo = document.querySelector('p');
   console.log(primerParrafo.innerHTML); // "Este es un párrafo de contenido."
   ```

4. **Seleccionar un elemento dentro de otro**:

   ```javascript
   const primerItem = document.querySelector('ul .item'); // Selecciona el primer .item dentro de ul
   console.log(primerItem.innerHTML); // "Elemento 1"
   ```

5. **Seleccionar por atributos**:

   ```javascript
   const elementoDestacado = document.querySelector('li[item="Elemento 3"]');
   console.log(elementoDestacado.innerHTML); // Este código fallará porque no hay tal atributo "item"
   ```

### Uso de `querySelectorAll`

El método `querySelectorAll` selecciona todos los elementos que coinciden con el selector CSS proporcionado y devuelve una NodeList. A continuación se presentan ejemplos utilizando el HTML anterior:

1. **Seleccionar todos los elementos de clase "contenido"**:

   ```javascript
   const parrafos = document.querySelectorAll('.contenido');
   parrafos.forEach(parrafo => {
       console.log(parrafo.innerHTML); // Imprime el contenido de todos los párrafos con clase "contenido"
   });
   ```

2. **Seleccionar todos los elementos de la lista "item"**:

   ```javascript
   const items = document.querySelectorAll('.item');
   items.forEach(item => {
       console.log(item.innerHTML); // Imprime el contenido de cada item
   });
   ```

3. **Seleccionar todos los elementos destacados**:

   ```javascript
   const destacados = document.querySelectorAll('.destacado');
   destacados.forEach(destacado => {
       console.log(destacado.innerHTML); // Imprime el contenido de los elementos destacados
   });
   ```

4. **Seleccionar múltiples selectores**:

   ```javascript
   const elementos = document.querySelectorAll('.contenido, .item');
   elementos.forEach(elemento => {
       console.log(elemento.innerHTML); // Imprime el contenido de todos los elementos con clase "contenido" y "item"
   });
   ```

### Ejemplos Prácticos

#### Ejemplo 1: Modificar el contenido de un párrafo destacado

```javascript
const parrafoDestacado = document.querySelector('.destacado');
parrafoDestacado.innerHTML = 'Este párrafo ha sido modificado con querySelector.'; // Cambia el contenido del párrafo destacado
```

#### Ejemplo 2: Añadir un evento a un botón

```javascript
const boton = document.querySelector('#miBoton');
boton.addEventListener('click', () => {
    alert('¡Botón clickeado!'); // Muestra un mensaje al hacer clic en el botón
});
```

### Resumen

- **`querySelector`**: Selecciona el primer elemento que coincide con el selector CSS.
- **`querySelectorAll`**: Selecciona todos los elementos que coinciden con el selector CSS y devuelve una NodeList.
- Se pueden utilizar selectores de CSS para seleccionar elementos por ID, clase, etiqueta, atributos, y combinaciones de estos.

### Código de clase
```javascript
const boton = document.querySelector('#miBoton');

const cambiarColor = (colorEnviado) => {
  // obtener todos los elementos con la clase "destacado"
  const elementos = document.querySelectorAll('.destacado');
  // iterar sobre los elementos y aplicar el estilo de color azul

  const primerElemento = elementos[0];
  let nuevoColor;
  if (primerElemento.style.color === 'red')
    nuevoColor = colorEnviado;
  else {
    nuevoColor = 'red';
  }

  elementos.forEach(elemento => {
    elemento.style.color = nuevoColor;
  });
}


boton.addEventListener('click', ()=>{
  cambiarColor('green')
});
```
