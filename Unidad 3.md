
---

### **Unidad 3: Programación Orientada a Objetos y Chart.js**

#### **Clases y Objetos**
JavaScript soporta programación orientada a objetos usando clases y herencia.
```javascript
class Animal {
  constructor(nombre) {
    this.nombre = nombre;
  }
  hacerSonido() {
    console.log(this.nombre + " hace un sonido.");
  }
}

class Perro extends Animal {
  hacerSonido() {
    console.log(this.nombre + " ladra.");
  }
}

const perro = new Perro("Rex");
perro.hacerSonido();  // Rex ladra.
```

#### **Uso de Chart.js**
`Chart.js` es una librería popular para crear gráficos interactivos. Aquí un ejemplo básico para crear un gráfico de barras:
```html
<canvas id="miGrafico"></canvas>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  const ctx = document.getElementById('miGrafico').getContext('2d');
  const myChart = new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['Rojo', 'Azul', 'Amarillo'],
      datasets: [{
        label: 'Colores favoritos',
        data: [12, 19, 3],
        backgroundColor: ['rgba(255, 99, 132)', 'rgba(54, 162, 235)', 'rgba(255, 206, 86)']
      }]
    }
  });
</script>
```

Tienes razón, faltó la estructura de control `switch`. Aquí la agrego en la **Unidad 2** dentro de las estructuras de control.
