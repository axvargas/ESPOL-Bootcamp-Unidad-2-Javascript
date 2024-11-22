### **Tarea 4: Crear una galería de imágenes interactiva**  

---

### **Propósito de la tarea**  
El objetivo de esta tarea es que los estudiantes:  
1. **Aprendan a trabajar con arreglos en JavaScript** para almacenar datos estructurados como rutas y descripciones de imágenes.  
2. **Usen el DOM para crear y manipular elementos dinámicamente** (`createElement`, `appendChild`).  
3. **Apliquen eventos para crear interactividad**, como cambiar la imagen principal al hacer clic en una miniatura.  
4. **Entiendan cómo utilizar atributos personalizados en los elementos del DOM (`dataset`)** para gestionar el estado de la aplicación.  

---

### **Instrucciones Paso a Paso**

---

### **Parte 1: Crear el arreglo de imágenes**
1. **Crea un arreglo llamado `galleryImages`:**  
   - Declara una constante llamada `galleryImages` usando `const`.  
   - Este arreglo debe contener varios objetos, y cada objeto representará una imagen de la galería.  
   - Cada objeto debe incluir:  
     - Una propiedad `src` (ruta de la imagen).  
     - Una propiedad `alt` (texto alternativo para describir la imagen).  

   **Pasos a seguir:**  
   - Declara el arreglo:  
     ```javascript
     const galleryImages = [];
     ```  
   - Llena el arreglo con al menos 3 objetos. Cada objeto debe tener una propiedad `src` con la ruta de la imagen y una propiedad `alt` con la descripción de la imagen.  
   - Ejemplo de un objeto dentro del arreglo:  
     ```javascript
     { src: "./assets/gallery/image1.jpg", alt: "Thumbnail Image 1" }
     ```
   - **IMPORTANTE:** La información para llenar los objetos de galería de imágenes la puedes encontrar en las líneas 118-120. Una vez tengas el arreglo de objetos de galería de imágenes Debes dejar el tag `div` con classname `thumbnails` vacío por ende debes borrar las lineas 118 - 120:

     ![image](https://github.com/user-attachments/assets/833b4ee8-a2b3-4119-9585-739e254e4e51)


   **¿Por qué hacemos esto?**  
   Para almacenar todas las imágenes de la galería en un lugar centralizado y organizado. Esto facilita el acceso a los datos al construir dinámicamente los elementos del DOM.

---

### **Parte 2: Crear la función `galleryHandler`**
1. **Define una función llamada `galleryHandler`:**  
   - Esta función será responsable de inicializar la galería y generar la funcionalidad interactiva.

---

### **Parte 3: Seleccionar los elementos del DOM**
1. **Selecciona los elementos necesarios:**  
   - Dentro de la función `galleryHandler`, usa `document.querySelector` para seleccionar los siguientes elementos:  
     - La imagen principal, ubicada dentro del elemento con el id `gallery`:  
       ```javascript
       let mainImage = document.querySelector("#gallery > img");
       ```  
     - El contenedor de miniaturas, ubicado dentro del elemento con la clase `thumbnails`:  
       ```javascript
       let thumbnails = document.querySelector("#gallery .thumbnails");
       ```  

   **¿Por qué hacemos esto?**  
   Para poder manipular estos elementos más adelante, como cambiar la imagen principal y agregar miniaturas dinámicamente.

---

### **Parte 4: Configurar la imagen principal**
1. **Establece la imagen principal inicial:**  
   - Usa el primer objeto del arreglo `galleryImages` para establecer los atributos `src` y `alt` de la imagen principal:  
     ```javascript
     mainImage.src = galleryImages[0].src;
     mainImage.alt = galleryImages[0].alt;
     ```  

   **¿Por qué hacemos esto?**  
   Para mostrar una imagen inicial en la galería antes de que el usuario interactúe con ella.

---

### **Parte 5: Crear dinámicamente las miniaturas**
1. **Recorre el arreglo `galleryImages`:**  
   - Usa el método `forEach` para iterar sobre cada objeto en el arreglo.  
   - Por cada objeto:  
     - Crea un nuevo elemento `<img>` para representar una miniatura.  
     - Asigna los atributos `src` y `alt` del objeto al nuevo elemento.  
     - Usa el atributo `dataset.arrayIndex` para guardar el índice del objeto actual.  

   **Ejemplo de cómo crear una miniatura:**  
   ```javascript
   let thumb = document.createElement("img");
   thumb.src = image.src;
   thumb.alt = image.alt;
   thumb.dataset.arrayIndex = index;
   ```  

2. **Agrega funcionalidad a las miniaturas:**  
   - Usa `addEventListener` para detectar el evento `click` en cada miniatura.  
   - Al hacer clic en una miniatura:  
     - Obtén el índice de la imagen seleccionada usando `dataset.arrayIndex`.  
     - Actualiza la imagen principal con los datos de la miniatura seleccionada.  
     - Desmarca todas las miniaturas anteriores y marca la actual como seleccionada.  

   **Ejemplo de código dentro del evento `click`:**  
   ```javascript
   thumb.addEventListener("click", function (e) {
       let selectedIndex = e.target.dataset.arrayIndex;
       let selectedImage = galleryImages[selectedIndex];

       mainImage.src = selectedImage.src;
       mainImage.alt = selectedImage.alt;

       thumbnails.querySelectorAll("img").forEach(function (img) {
           img.dataset.selected = false;
       });
       e.target.dataset.selected = true;
   });
   ```  

3. **Agrega la miniatura al contenedor de miniaturas:**  
   - Usa `appendChild` para agregar cada miniatura creada al contenedor `thumbnails`.  
     ```javascript
     thumbnails.appendChild(thumb);
     ```  

---

### **Parte 6: Llamar a la función `galleryHandler`**
1. **Ejecuta la función al cargar la página:**  
   - Asegúrate de llamar a la función después de declararla para activar toda la lógica:  
     ```javascript
     galleryHandler();
     ```  

---

### **Explicación Final**
Con estos pasos, tus estudiantes podrán:  
- Crear un arreglo de objetos para almacenar datos estructurados.  
- Manipular el DOM para generar elementos dinámicamente y asignarles atributos.  
- Aplicar eventos a los elementos generados para crear interactividad.  
- Gestionar el estado de la aplicación utilizando atributos personalizados (`dataset`).  

Esto refuerza conceptos fundamentales como estructuras de datos, manejo del DOM y eventos, esenciales para el desarrollo web.
