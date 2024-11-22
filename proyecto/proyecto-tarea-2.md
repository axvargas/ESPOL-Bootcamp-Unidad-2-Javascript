### Tarea: Implementar un saludo dinámico basado en la hora del día  

#### **Propósito de la Tarea**  
El propósito de esta tarea es mostrar un mensaje de saludo que cambie dinámicamente dependiendo de la hora del día en que el usuario visite la página. Esta funcionalidad permite que los estudiantes practiquen el uso de:  
1. **Obtener la hora actual usando objetos de fecha en JavaScript (`Date`).**  
2. **Usar estructuras de control condicionales (`if`, `else if`, `else`).**  
3. **Manipular elementos del DOM para mostrar contenido dinámico.**

---

### **Instrucciones Paso a Paso**  

1. **Comprender lo que se quiere lograr:**  
   - Mostrar un saludo como **"Good morning!"**, **"Good afternoon!"**, o **"Good evening!"** dependiendo de la hora actual.  
   - El saludo debe mostrarse en el elemento del HTML con el `id` **`greeting`**.  

   **Razón detrás de este paso:**  
   - Adaptar el contenido de la página al contexto del usuario (en este caso, la hora del día) mejora la experiencia del usuario.  

---

2. **Crear una nueva función llamada `greetingHandler`:**  
   - En tu archivo JavaScript, crea una función con el nombre **`greetingHandler`**.  
   - Dentro de esta función implementarás toda la lógica para determinar y mostrar el saludo.  

   **Tip:**  
   - Usa nombres descriptivos para las funciones, como en este caso, porque ayudan a entender el propósito del código.  

---

3. **Obtener la hora actual:**  
   - Dentro de la función, usa el constructor `Date` para obtener la hora actual del sistema.  
   - Declara una variable llamada **`currentHour`** para almacenar la hora actual, utilizando el método `.getHours()`.  

   **Razón detrás de este paso:**  
   - La función `getHours()` devuelve un número entre 0 y 23 que representa la hora actual en formato de 24 horas. Este valor será usado para determinar qué saludo mostrar.  

---

4. **Definir el mensaje de saludo:**  
   - Declara una variable llamada **`greetingText`** que almacenará el saludo dinámico.  
   - Usa una estructura condicional `if-else if-else` para asignar el valor adecuado a `greetingText`:  
     - Si la hora es menor a 12, el mensaje será **"Good morning!"**.  
     - Si la hora es entre 12 y 19, el mensaje será **"Good afternoon!"**.  
     - Si la hora es entre 19 y 23, el mensaje será **"Good evening!"**.  
     - Si por alguna razón no entra en las categorías anteriores, el mensaje será **"Welcome!"**.  

   **Tip para los estudiantes:**  
   - Asegúrate de respetar los límites de las horas en cada condición y escribe los rangos claramente en tus comentarios para evitar confusiones.  

---

5. **Actualizar el contenido en el DOM:**  
   - Usa el método `document.querySelector` para seleccionar el elemento del HTML con el `id` **`greeting`**.  
   - Actualiza su contenido usando la propiedad `innerHTML` y asignándole el valor de **`greetingText`**.  

   **Razón detrás de este paso:**  
   - La manipulación del DOM es fundamental para que los cambios realizados en el código JavaScript sean visibles para el usuario en la página web.  

---

6. **Llamar la función `greetingHandler`:**  
   - Al final de tu archivo de JavaScript, llama a la función `greetingHandler` para que el saludo se genere automáticamente cuando se cargue la página.  

   **Razón detrás de este paso:**  
   - Llamar a la función asegura que el saludo se muestre inmediatamente al cargar la página, sin que el usuario tenga que realizar ninguna acción.  

---

### **Pasos Resumidos para Implementar `greetingHandler`**  

1. Crea una función llamada **`greetingHandler`** en tu archivo JavaScript.  
2. Declara una variable **`currentHour`** y usa `new Date().getHours()` para obtener la hora actual.  
3. Declara una variable **`greetingText`** que contendrá el mensaje dinámico.  
4. Usa una estructura `if-else if-else` para asignar un saludo apropiado a la variable `greetingText` basándote en la hora:  
   - Hora < 12: **"Good morning!"**  
   - 12 ≤ Hora < 19: **"Good afternoon!"**  
   - 19 ≤ Hora < 24: **"Good evening!"**  
   - Por defecto: **"Welcome!"**  
5. Selecciona el elemento del DOM con el `id` **`greeting`** y actualiza su contenido con el saludo.  
6. Llama a la función **`greetingHandler`** al final del archivo para que la funcionalidad esté activa al cargar la página.  
