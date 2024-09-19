---

### **Unidad 1: Introducción - Objetos y Arreglos**

#### **¿Qué es JavaScript?**
JavaScript es un lenguaje de programación interpretado, ligero y orientado a objetos, utilizado principalmente para crear páginas web interactivas. Fue creado por Brendan Eich en 1995 y ha evolucionado significativamente desde entonces, convirtiéndose en un pilar fundamental del desarrollo web moderno.

#### **Tipos de Datos Primitivos**
JavaScript tiene varios tipos de datos primitivos:
- `number`: Números (enteros o flotantes).
- `string`: Cadenas de texto.
- `boolean`: Valores lógicos (`true` o `false`).
- `null`: Representa "ningún valor".
- `undefined`: Indica que una variable no ha sido asignada.
- `symbol`: Un valor único que no puede ser replicado.
  
#### **Objetos**
Los objetos son colecciones de pares clave-valor. Cada propiedad de un objeto tiene un nombre (clave) y un valor.
```javascript
const persona = {
  nombre: "Juan",
  edad: 30,
  saludar: function() {
    console.log("Hola, soy " + this.nombre);
  }
};

persona.saludar();  // Hola, soy Juan
```

#### **Arreglos**
Un arreglo es una lista ordenada de elementos que pueden ser de cualquier tipo de dato.
```javascript
const numeros = [1, 2, 3, 4, 5];
console.log(numeros[0]);  // 1
```

Los arreglos tienen métodos útiles como:
- `push()`: Agrega un elemento al final del arreglo.
- `pop()`: Elimina el último elemento.
- `map()`, `filter()`, `reduce()`: Métodos avanzados para transformar o reducir arreglos.

