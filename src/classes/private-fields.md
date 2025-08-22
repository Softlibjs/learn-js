# Elementos privados en Clases

> [!NOTE]
> **ECMAScript 2022**, la 13ª edición de la especificación, introdujo los campos privados en las clases de JavaScript.

El acceso privado es el nivel de acceso menos permisivo. Solo se puede acceder a los miembros privados dentro del cuerpo de la clase o la estructura en la que se declaran.

Los elementos privados se crean mediante el prefijo hash `#` y no se pueden referenciar legalmente fuera de la clase. La encapsulación de privacidad de estos elementos de clase la aplica el propio JavaScript. La única forma de acceder a un elemento privado es mediante la [dot notation](), y solo se puede hacer dentro de la clase que lo define.

## Syntax

Es un error de sintaxis hacer referencia a nombres `#` desde fuera de la clase. También es un error de sintaxis hacer referencia a elementos privados que **no se declararon en el cuerpo de la clase** o intentar eliminar elementos declarados con "delete".

```js
class ClassWithPrivateField {
  // class body
  #privateField;

  constructor() {
    delete this.#privateField; // Syntax error -> attempt to remove a private element
    this.#undeclaredField = 42; // Syntax error -> not declared in the class body
  }
}

const instance = new ClassWithPrivateField();
instance.#privateField; // Syntax error -> cannot be legally referenced outside of the class
```

 ## Polyfills para diferentes versiones

Los elementos privados no eran nativos del lenguaje antes de que existiera esta sintaxis. En la herencia prototípica, su comportamiento puede emularse con objetos [WeakMap]() o [closures](), pero no se pueden comparar con la sintaxis `#` en términos de ergonomía.

### Emulando elementos privados con closures

Esta técnica utiliza el concepto de **cierre** (`closure`) para crear un alcance privado para las variables y los métodos, de forma que solo son accesibles a través de métodos públicos.

 ```js
// Clousere
const counter = (function () {
    let privateCounter = 0;
    function changeBy(val) {
        privateCounter += val;
    }

    return {
        increment() {
            changeBy(1);
        },
    
        decrement() {
            changeBy(-1);
        },
    
        value() {
            return privateCounter;
        },
    };
})();
```

### Emulando elementos privados con WeakMap

Esta técnica asocia elementos privados a una instancia de una clase usando un `WeakMap`.

```js
var Employee2;

{
    var privateScope = new WeakMap();

    Employee2 = function Employee2() {
        // inicializamos los campos privados
        privateScope.set(this, {
            name: "FirstName, LastName",
            salary: 100.0
        });
    };

    // Método público: GetName()
    Employee2.prototype.GetName = function() {
        return privateScope.get(this).name;
    };

    // Propiedad pública de solo lectura: Salary
    Object.defineProperty(Employee2.prototype, "Salary", {
        get: function get() {
            return privateScope.get(this).salary;
        }
    });
}

var emp = new Employee2();
console.log(emp.GetName());
console.log(emp.Salary);
console.log(emp.name);
console.log(emp.salary);
```
  
