### **Tarea 6: Crear un sistema interactivo para listar y filtrar productos**  

---

### **Propósito de la tarea**  

Con esta tarea, los estudiantes aprenderán a:  
1. Manipular datos dinámicamente con arreglos y métodos como `filter` y `forEach`.  
2. Generar elementos HTML dinámicamente basados en datos del arreglo `products`.  
3. Incorporar interactividad mediante eventos (`click`) para filtrar y actualizar contenido en la página.  

---

### **Instrucciones Paso a Paso con Ejemplos**  

#### **Parte 1: Crear el arreglo de productos**  

1. **Crea un arreglo llamado `products`:**  
   - Declara una constante llamada `products` usando `const`.  
   - Este arreglo almacenará información sobre productos como el título, autor, precio e imagen.  

   **Ejemplo del arreglo:**  
   ```javascript
   const products = [
    {
      title: "AstroFiction",
      author: "John Doe",
      price: 49.9,
      image: "./assets/products/img6.png"
    },
    {
      title: "Space Odissey",
      author: "Marie Anne",
      price: 35,
      image: "./assets/products/img1.png"
    },
    {
      title: "Doomed City",
      author: "Jason Cobert",
      price: 0,
      image: "./assets/products/img2.png"
    },
    {
      title: "Black Dog",
      author: "John Doe",
      price: 85.35,
      image: "./assets/products/img3.png"
    },
    {
      title: "My Little Robot",
      author: "Pedro Paulo",
      price: 0,
      image: "./assets/products/img5.png"
    },
    {
      title: "Garden Girl",
      author: "Ankit Patel",
      price: 45,
      image: "./assets/products/img4.png"
    }
   ];
   ```
   - **IMPORTANTE:** Una vez que tengas el arreglo, borrar las líneas que se muestran a continuación en el archivo .html 
   ![image](https://github.com/user-attachments/assets/21806135-4a1c-4a4a-be55-e16ea7281c0c)

  
   **¿Por qué hacemos esto?**  
   Esto nos permite organizar la información de los productos en una estructura reutilizable y fácil de manipular.  

---

#### **Parte 2: Crear la función `populateProducts`**  

2. **Define una función llamada `populateProducts`:**  
   - La función recibirá como parámetro un arreglo de productos.  
   - Generará dinámicamente los elementos HTML necesarios para mostrar los productos en pantalla.  

3. **Pasos dentro de la función:**  

   - **Selecciona el contenedor principal:**  
     ```javascript
     let productsSection = document.querySelector(".products-area");
     ```  
     Esto selecciona el área donde se mostrarán los productos.  

   - **Limpia el contenido anterior del contenedor:**  
     ```javascript
     productsSection.textContent = "";
     ```  
     Esto asegura que no se acumulen productos al actualizar la lista.  

   - **Recorre el arreglo de productos:**  
     Usa `forEach` para iterar sobre cada producto.  

   - **Crea dinámicamente los elementos HTML:**  
     ```javascript
     products.forEach(function (product) {
         let productElm = document.createElement("div");
         productElm.classList.add("product-item");

         let productImage = document.createElement("img");
         productImage.src = product.image;
         productImage.alt = "Imagen de " + product.title;

         let productDetails = document.createElement("div");
         productDetails.classList.add("product-details");

         let productTitle = document.createElement("h3");
         productTitle.textContent = product.title;

         let productPrice = document.createElement("p");
         productPrice.textContent = product.price > 0 ? `$${product.price}` : "Gratis";

         productDetails.append(productTitle);
         productDetails.append(productPrice);
         productElm.append(productImage);
         productElm.append(productDetails);
         productsSection.append(productElm);
     });
     ```  

   **¿Por qué hacemos esto?**  
   Generar HTML dinámicamente te permite construir páginas más flexibles y reusables que se adaptan a los datos de entrada.  

---

#### **Parte 3: Crear la función `productsHandler`**  

1. **Define la función principal:**  
   - Esta función manejará el filtrado y la visualización de productos.  

2. **Filtra los productos por categorías:**  
   ```javascript
   let freeProducts = products.filter(item => item.price === 0);
   let paidProducts = products.filter(item => item.price > 0);
   ```  
   Esto genera dos listas: productos gratuitos y productos de pago.  

3. **Muestra inicialmente todos los productos:**  
   ```javascript
   populateProducts(products);
   ```  

4. **Actualiza las etiquetas con el conteo de productos:**  
   ```javascript
   document.querySelector(".products-filter label[for=all] span.product-amount").textContent = products.length;
   document.querySelector(".products-filter label[for=free] span.product-amount").textContent = freeProducts.length;
   document.querySelector(".products-filter label[for=paid] span.product-amount").textContent = paidProducts.length;
   ```  

5. **Agrega el evento de clic al filtro:**  
   ```javascript
   document.querySelector(".products-filter").addEventListener("click", function (e) {
       if (e.target.id === "all") {
           populateProducts(products);
       } else if (e.target.id === "free") {
           populateProducts(freeProducts);
       } else if (e.target.id === "paid") {
           populateProducts(paidProducts);
       }
   });
   ```  

**Ejemplo del inicio de la función completa:**  
```javascript
function productsHandler() {
    let freeProducts = products.filter(item => item.price === 0);
    let paidProducts = products.filter(item => item.price > 0);

    populateProducts(products);

    document.querySelector(".products-filter").addEventListener("click", function (e) {
        if (e.target.id === "all") {
            populateProducts(products);
        } else if (e.target.id === "free") {
            populateProducts(freeProducts);
        } else if (e.target.id === "paid") {
            populateProducts(paidProducts);
        }
    });
}
```  

**¿Por qué hacemos esto?**  
Para permitir a los usuarios interactuar con el contenido de la página de manera dinámica, mostrando solo lo que les interesa.  

---

### **Paso Final: Ejecutar la función `productsHandler`**

1. Llama a la función `productsHandler` al final del script:  
   ```javascript
   productsHandler();
   ```  

Esto inicializará todo el sistema de productos y permitirá a los usuarios ver y filtrar la lista desde el principio.
