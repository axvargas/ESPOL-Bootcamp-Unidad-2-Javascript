---

### **Unidad 7: Funciones de Orden Superior**

#### **Funciones de Orden Superior (HOF)**
Una función de orden superior es una función que puede recibir otras funciones como argumentos o devolver funciones.

**Ejemplo real: Uso de `map`, `filter` y `reduce` para procesar datos**
En un escenario laboral, podrías necesitar transformar, filtrar y reducir datos, como procesar una lista de transacciones financieras.

```javascript
const transacciones = [
  { tipo: 'ingreso', monto: 100 },
  { tipo: 'gasto', monto: 50 },
  { tipo: 'ingreso', monto: 300 },
  { tipo: 'gasto', monto: 120 }
];

// Usar map para obtener solo los montos
const montos = transacciones.map(transaccion => transaccion.monto);
console.log(montos);  // [100, 50, 300, 120]

// Usar filter para obtener solo los ingresos
const ingresos = transacciones.filter(transaccion => transaccion.tipo === 'ingreso');
console.log(ingresos);  // [{tipo: 'ingreso', monto: 100}, {tipo: 'ingreso', monto: 300}]

// Usar reduce para obtener el balance total
const balanceTotal = transacciones.reduce((total, transaccion) => {
  return transaccion.tipo === 'ingreso' ? total + transaccion.monto : total - transaccion.monto;
}, 0);

console.log(balanceTotal);  // 230
```

Este ejemplo muestra cómo transformar datos financieros, algo común en el desarrollo de aplicaciones de gestión o contabilidad.

#### **Uso de funciones como argumentos**
Las funciones de orden superior son fundamentales para manejar operaciones asincrónicas o tareas repetitivas.

**Ejemplo real: Función `forEach` para procesar un conjunto de usuarios**
```javascript
const usuarios = ['Ana', 'Pedro', 'Luis', 'Maria'];

usuarios.forEach((usuario, index) => {
  console.log(`Usuario ${index + 1}: ${usuario}`);
});
```

Esto puede ser útil en un sistema de administración de usuarios, donde se necesita realizar una operación sobre cada usuario.
