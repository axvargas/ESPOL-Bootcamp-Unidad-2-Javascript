
---

### **Unidad 8: Fetch – JSON y XML – Consumo de Servicios**

#### **Uso de `fetch` para consumir APIs**
`fetch` es una API moderna para hacer peticiones HTTP en JavaScript. Se utiliza para consumir servicios web que devuelven datos en formato JSON o XML.

**Ejemplo real: Consumiendo una API REST**
Supongamos que necesitas consumir una API que devuelve información sobre productos en una tienda online.

```javascript
fetch('https://fakestoreapi.com/products')
  .then(response => response.json())
  .then(data => {
    data.forEach(producto => {
      console.log(`Producto: ${producto.title} - Precio: $${producto.price}`);
    });
  })
  .catch(error => {
    console.error('Error al consumir la API:', error);
  });
```

Este código hace una petición a una API y procesa los resultados, algo muy común en aplicaciones que consumen servicios externos.

#### **Procesando JSON y XML**
Aunque JSON es más común hoy en día, es posible que en proyectos antiguos encuentres servicios que devuelven XML.

**Ejemplo real: Procesando XML**
```javascript
const xmlString = `
<productos>
  <producto>
    <nombre>Laptop</nombre>
    <precio>1000</precio>
  </producto>
  <producto>
    <nombre>Celular</nombre>
    <precio>500</precio>
  </producto>
</productos>
`;

const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlString, 'application/xml');
const productos = xmlDoc.getElementsByTagName('producto');

for (let i = 0; i < productos.length; i++) {
  const nombre = productos[i].getElementsByTagName('nombre')[0].textContent;
  const precio = productos[i].getElementsByTagName('precio')[0].textContent;
  console.log(`Producto: ${nombre} - Precio: $${precio}`);
}
```

Este ejemplo muestra cómo manejar XML en caso de que necesites integrar datos de un sistema legado.
