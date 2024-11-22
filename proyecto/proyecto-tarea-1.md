
### Tarea 1: Mostrar y ocultar el menú de navegación utilizando JavaScript  

#### **Propósito de la Tarea**  
El propósito de esta tarea es implementar la funcionalidad para **mostrar y ocultar el menú de navegación** cuando el usuario haga clic en los botones correspondientes. Esta tarea permite comprender conceptos básicos de manipulación del DOM y manejo de eventos en JavaScript.  

---

### **Instrucciones Paso a Paso**  

1. **Entender lo que se quiere lograr:**  
   - Debes permitir que el usuario **abra** el menú al hacer clic en un botón (que ya está creado en el HTML y tiene el `id` **`open-nav-menu`**).  
   - Debes permitir que el usuario **cierre** el menú al hacer clic en otro botón (ya creado en el HTML con el `id` **`close-nav-menu`**).  
   - Para esto, agregarás y eliminarás dinámicamente una clase llamada **`nav-open`** al contenedor principal del menú (que tiene una clase CSS predefinida llamada **`wrapper`**).  

---

2. **Crear la función principal**  
   - En tu archivo de JavaScript, escribe una función que llame **`menuHandler`**. Esta función se encargará de implementar toda la funcionalidad.  
   - La idea detrás de una función es organizar el código para que sea más fácil de mantener y entender.  

---

3. **Declarar variables para los elementos del DOM**  
   Dentro de la función **`menuHandler`**, sigue estos pasos para identificar y guardar los elementos con los que trabajarás:  
   - Crea una variable llamada **`openButton`** y usa `document.querySelector` para seleccionar el botón con el `id` **`open-nav-menu`**.  
   - Crea una variable llamada **`closeButton`** y selecciona el botón con el `id` **`close-nav-menu`**.  
   - Crea una variable llamada **`menuWrapper`** para seleccionar el contenedor del menú (que tiene la clase **`wrapper`** en el HTML).  

   **Código aproximado:**  
   ```javascript
   const openButton = document.querySelector("#open-nav-menu");
   const closeButton = document.querySelector("#close-nav-menu");
   const menuWrapper = document.querySelector("header nav .wrapper");
   ```

---

4. **Agregar escuchadores de eventos (event listeners)**  
   - Usa el método `addEventListener` para agregar eventos de clic a los botones.  
   - Cuando el usuario haga clic en el botón de abrir menú (**`openButton`**):  
     - Escribe una función anónima que agregue la clase **`nav-open`** al elemento guardado en **`menuWrapper`**.  
   - Cuando el usuario haga clic en el botón de cerrar menú (**`closeButton`**):  
     - Escribe una función anónima que elimine la clase **`nav-open`** del elemento guardado en **`menuWrapper`**.
    
   **Código aproximado:**  
     ```javascript
     openButton.addEventListener("click", function () {
         // añadir del classList de menuWrapper la clase nav-open
     });
  
     closeButton.addEventListener("click", function () {
         // remover del classList de menuWrapper la clase nav-open
     });
     ```
   **Razón detrás de este paso:**  
   - Los **event listeners** permiten que el navegador "escuche" las interacciones del usuario (como clics). En este caso, estamos conectando el clic en los botones a acciones específicas: abrir o cerrar el menú.

---

5. **Probar el código paso a paso**  
   - Primero, asegura que al hacer clic en el botón de abrir menú, el contenedor del menú recibe la clase **`nav-open`**.  
   - Luego, verifica que al hacer clic en el botón de cerrar menú, esa clase desaparezca del contenedor.  

   **Tip para los estudiantes:**  
   - Usa la consola del navegador (F12 en la mayoría de navegadores) para verificar que los selectores están funcionando correctamente y que las clases se están agregando o eliminando como esperas.

---

6. **Llamar la función `menuHandler` en el flujo del proyecto**  
   - Al final de tu archivo de JavaScript, llama a la función `menuHandler` para que esta se ejecute cuando cargue la página.  
   - Esto asegura que los botones estén listos para responder a los clics desde el momento en que la página se muestra al usuario.

   **Razón detrás de este paso:**  
   - Si no llamas a la función, los event listeners no estarán activos y los botones no tendrán ninguna funcionalidad.

---

### **Pasos Resumidos para Implementar `menuHandler`**  

1. **Crea la función `menuHandler`.**  
2. Declara tres variables:  
   - Una para el botón de abrir menú (`openButton`),  
   - Una para el botón de cerrar menú (`closeButton`),  
   - Y una para el contenedor del menú (`menuWrapper`).  
3. Usa `addEventListener` en los botones:  
   - En el botón de abrir, agrega la clase `nav-open` al contenedor.  
   - En el botón de cerrar, elimina la clase `nav-open` del contenedor.  
4. Llama a la función `menuHandler` al final de tu archivo.  
