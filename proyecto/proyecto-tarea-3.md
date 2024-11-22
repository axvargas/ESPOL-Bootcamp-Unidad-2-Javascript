### Tarea: Mostrar la hora local actualizada cada segundo  

#### **Propósito de la tarea**  
El objetivo de esta tarea es enseñar a los estudiantes a:  
1. **Trabajar con el objeto `Date` para obtener la hora actual.**  
2. **Actualizar el contenido del DOM periódicamente usando `setInterval`.**  
3. **Manipular elementos del DOM utilizando atributos personalizados (`data-*`).**  
4. **Formatear números para mostrar siempre dos dígitos (por ejemplo, 03 en lugar de 3).**  

Esta funcionalidad es un excelente ejemplo de interacción dinámica en tiempo real con el usuario, ya que el reloj se actualiza cada segundo.

---

### **Instrucciones Paso a Paso**

1. **Comprender lo que se quiere lograr:**  
   - Mostrar la hora local del dispositivo en formato de 24 horas (**hh:mm:ss**) en la página.  
   - Actualizar el reloj automáticamente cada segundo para reflejar la hora actual.  
   - La hora, minutos y segundos deben aparecer dentro de etiquetas `<span>` con atributos `data-time=hours`, `data-time=minutes`, y `data-time=seconds`.  

   **Razón detrás de este paso:**  
   - Este tipo de funcionalidad mejora la experiencia del usuario y les ayuda a los estudiantes a practicar conceptos clave como el manejo de tiempo y manipulación del DOM.

---

2. **Crear una nueva función llamada `clockHandler`:**  
   - En tu archivo JavaScript, crea una función llamada **`clockHandler`**.  
   - Dentro de esta función, implementarás toda la lógica necesaria para mostrar y actualizar el reloj.  

   **Tip:**  
   - Nombres descriptivos para las funciones facilitan el entendimiento del código. `clockHandler` indica claramente que la función gestiona el reloj.  

---

3. **Establecer un intervalo para actualizar la hora:**  
   - Usa el método `setInterval` para ejecutar un bloque de código cada segundo (1000 milisegundos).  
   - Dentro del intervalo, obtendrás la hora actual utilizando `new Date()`. Guarda este valor en una variable llamada **`localTime`**.  

   **Razón detrás de este paso:**  
   - `setInterval` permite ejecutar un bloque de código repetidamente a intervalos definidos, lo que es ideal para actualizar el reloj cada segundo.  

---

4. **Seleccionar elementos del DOM:**  
   - Dentro del intervalo, selecciona los elementos `<span>` correspondientes a las horas, minutos y segundos usando `document.querySelector`.  
   - Selecciona:  
     - `span[data-time=hours]` para las horas.  
     - `span[data-time=minutes]` para los minutos.  
     - `span[data-time=seconds]` para los segundos.  
   - Guarda las referencias a estos elementos en variables llamadas **`hourSpan`**, **`minuteSpan`**, y **`secondSpan`**.  

   **Tip para los estudiantes:**  
   - Los atributos `data-*` son útiles para asignar información personalizada a los elementos del DOM y son fáciles de seleccionar con `querySelector`.  

---

5. **Actualizar el contenido del DOM:**  
   - Dentro del intervalo:  
     - Usa el método `getHours()` para obtener la hora del objeto `localTime`.  
     - Usa `getMinutes()` y `getSeconds()` para obtener los minutos y segundos, respectivamente.  
     - Actualiza el contenido de cada `<span>` usando la propiedad `textContent`.  

   **Tip:**  
   - Para garantizar que los números tengan siempre dos dígitos (por ejemplo, mostrar "03" en lugar de "3"), usa el método `padStart(2, "0")`.  

   **Razón detrás de este paso:**  
   - Manipular el contenido del DOM directamente permite que los cambios sean visibles en tiempo real en la página.  

---

6. **Llamar la función `clockHandler`:**  
   - Al final del archivo JavaScript, llama a la función **`clockHandler`** para que el reloj comience a actualizarse tan pronto como se cargue la página.  

   **Razón detrás de este paso:**  
   - Llamar a la función asegura que la funcionalidad esté activa inmediatamente.  

---

### **Pasos Resumidos para Implementar `clockHandler`**  

1. Crea una función llamada **`clockHandler`** en tu archivo JavaScript.  
2. Dentro de la función, utiliza `setInterval` para ejecutar un bloque de código cada segundo (1000 ms).  
3. Usa `new Date()` para obtener la hora actual y guárdala en una variable llamada **`localTime`**.  
4. Selecciona los elementos del DOM correspondientes a las horas, minutos y segundos usando `document.querySelector`.  
5. Actualiza el contenido de estos elementos usando `getHours()`, `getMinutes()`, y `getSeconds()` del objeto `localTime`. Asegúrate de formatear los números para que tengan dos dígitos utilizando `padStart`.  
6. Llama a la función `clockHandler` al final del archivo.  
