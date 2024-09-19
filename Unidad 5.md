---

### **Unidad 5: Plantillas y DOM**

#### **Uso de Plantillas en el DOM**
Las plantillas (templates) son útiles para generar HTML dinámico en aplicaciones interactivas. Puedes usar plantillas con JavaScript para crear contenido repetitivo basado en datos dinámicos.

**Ejemplo real: Creación de tarjetas de productos dinámicamente**
```html
<template id="product-template">
  <div class="product">
    <h2 class="product-name"></h2>
    <p class="product-description"></p>
    <span class="product-price"></span>
  </div>
</template>

<div id="product-list"></div>

<script>
  const products = [
    { name: 'Laptop', description: '15 pulgadas, 8GB RAM', price: 1000 },
    { name: 'Celular', description: 'Android 11, 64GB', price: 500 },
  ];

  const template = document.getElementById('product-template');
  const productList = document.getElementById('product-list');

  products.forEach(product => {
    const clone = template.content.cloneNode(true);
    clone.querySelector('.product-name').textContent = product.name;
    clone.querySelector('.product-description').textContent = product.description;
    clone.querySelector('.product-price').textContent = `$${product.price}`;
    productList.appendChild(clone);
  });
</script>
```

Este ejemplo se asemeja a una tienda online, donde se crean tarjetas de productos dinámicamente a partir de una lista de productos.
