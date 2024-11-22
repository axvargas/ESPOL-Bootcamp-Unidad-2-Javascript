### Tarea 7: Agregar el texto al pie de página (Footer)

---

### **Objetivo**  
Mostrar dinámicamente un texto en el pie de página que incluya el año actual y un mensaje predefinido:  
`Ⓒ [Año] - Todos los derechos reservados`

---

### **Guía para completar la tarea**

1. **Obtener el año actual de forma dinámica**  
   - Usa el objeto `Date` de JavaScript para obtener el año actual.  
   - Llama al método `getFullYear()` de una instancia de `Date` para extraer el año.

   **Concepto clave:**  
   ```javascript
   let currentYear = new Date().getFullYear();
   ```

2. **Seleccionar el elemento del pie de página**  
   - Usa `document.querySelector` para seleccionar la etiqueta `<footer>` de tu HTML.  
   - Asegúrate de que el selector coincida con el elemento `<footer>` existente en tu estructura HTML.

3. **Actualizar el contenido del pie de página**  
   - Modifica la propiedad `textContent` del footer para mostrar el año y el mensaje predefinido.  
   - Usa **template literals** (comillas invertidas ``) para combinar el año y el texto de manera sencilla.

   **Ejemplo de estructura:**  
   ```javascript
   footerElement.textContent = `Ⓒ ${currentYear} - Todos los derechos reservados`;
   ```

4. **Organizar el código en una función**  
   - Envuelve los pasos anteriores en una función para mantener el código limpio y reutilizable.  
   - Llama a esta función después de que el DOM esté completamente cargado.

5. **Verificar posibles problemas**  
   - Asegúrate de que el elemento `<footer>` exista antes de intentar actualizar su contenido para evitar errores en la consola.  
   - Revisa que el pie de página no contenga información importante que pueda ser sobrescrita.

6. **Buenas prácticas**  
   - Utiliza HTML semántico y documenta tu función para que otros puedan entender su propósito.  
   - Considera agregar un identificador único al footer para evitar problemas al seleccionar elementos.


Esto garantiza que el pie de página sea siempre preciso y fácil de mantener.
