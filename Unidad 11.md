# **Unidad 11: Typescript**
---

## **¿Qué es TypeScript?**
### **Definición**
- **TypeScript** es un lenguaje de programación desarrollado por Microsoft.
- Es un **superset de JavaScript**, lo que significa que extiende las funcionalidades de JavaScript. Todo el código JavaScript es válido en TypeScript.
- Añade **tipado estático** y características avanzadas como interfaces, tipos genéricos y módulos.

### **¿Por qué usar TypeScript?**
1. **Detección de errores antes de ejecutar el código**: 
   - TypeScript detecta errores en el código durante el desarrollo, no cuando lo ejecutas.
2. **Código más fácil de entender y mantener**:
   - Al usar tipos, puedes saber qué valores se esperan en las variables y funciones.
3. **Compatible con JavaScript**:
   - TypeScript se compila a JavaScript, por lo que puedes usarlo en cualquier entorno donde JavaScript funcione.

---

## **Tu primer programa en TypeScript**
Escribe el siguiente código:
   ```typescript
   let message: string = "¡Hola, TypeScript!";
   console.log(message);
   ```


## **¿Qué es el tipado estático?**
### **En JavaScript (sin tipado estático):**
- Puedes declarar una variable sin definir qué tipo de valor puede contener:
  ```javascript
  let variable = "Soy un string";
  variable = 123; // Esto no da error en JavaScript
  ```

### **En TypeScript (con tipado estático):**
- Debes especificar el tipo de dato:
  ```typescript
  let variable: string = "Soy un string";
//   variable = 123; // Esto genera un error
  ```

### **Ventajas del tipado estático:**
1. **Evita errores comunes**: Si intentas asignar un valor incorrecto, TypeScript te avisa.
2. **Documentación implícita**: Otros desarrolladores saben qué tipo de datos espera tu código.

---

## **Tipos básicos en TypeScript**
| **Tipo**       | **Ejemplo**                   |
|-----------------|-------------------------------|
| **string**      | `let name: string = "Ana";`  |
| **number**      | `let age: number = 25;`      |
| **boolean**     | `let isStudent: boolean = true;` |
| **any**         | `let random: any = "Hola";`  |
| **array**       | `let numbers: number[] = [1, 2, 3];` |

---

## **Ejemplo: Usando varios tipos**
### Código:
```typescript
let name: string = "Juan";
let age: number = 30;
let isStudent: boolean = true;

console.log(`Mi nombre es ${name}, tengo ${age} años, y ${isStudent ? "soy estudiante" : "no soy estudiante"}.`);
```
### Salida:
```
Mi nombre es Juan, tengo 30 años, y soy estudiante.
```

---

## **Funciones en TypeScript**
### **Declarar tipos en funciones**
```typescript
function greet(name: string): string {
  return `Hola, ${name}!`;
}

let greeting = greet("Luis");
console.log(greeting); // Hola, Luis!
```
- **`name: string`**: Especifica que el parámetro `name` debe ser un string.
- **`: string`**: Indica que la función devolverá un string.

---

## **Objetos en TypeScript**
### **Definir tipos para objetos**
```typescript
let user: { name: string; age: number } = {
  name: "María",
  age: 25
};

console.log(`El usuario ${user.name} tiene ${user.age} años.`);
```

### **Con interfaces**
- Las interfaces permiten definir estructuras reutilizables para objetos.
```typescript
interface User {
  name: string;
  age: number;
}

let user: User = { name: "Pedro", age: 40 };
console.log(`El usuario ${user.name} tiene ${user.age} años.`);
```

---

## **Actividad práctica**
1. Crea un archivo llamado `intro.ts`.
2. Define las siguientes variables:
   - Una cadena para el nombre de un estudiante.
   - Un número para la edad.
   - Un booleano para indicar si está inscrito en un curso.
3. Escribe una función que tome estos valores como parámetros y devuelva una cadena que diga:
   - `"El estudiante [nombre] tiene [edad] años y [está / no está] inscrito en un curso."`
4. Compila y ejecuta tu programa.

---

## **Resumen**
- **TypeScript** mejora JavaScript al añadir tipado estático y herramientas avanzadas.
- Es ideal para proyectos grandes porque ayuda a prevenir errores y hace que el código sea más legible.
