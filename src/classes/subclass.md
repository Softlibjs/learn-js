# Subclass

> [!NOTE]
> ECMAScript 2015, la 6th edición de la especificación, JavaScript introdujo las definiciones de clases sintácticas.

Cualquier constructor que pueda llamarse con [`new`]() y tenga la propiedad [`prototype `]() puede ser candidato para la clase padre.

```js
function OldStyleClass() {
  this.someProperty = 1;
}
OldStyleClass.prototype.someMethod = function () {};

class ChildClass extends OldStyleClass {}
```
> [!NOTE]
> Todos los objetos de JavaScript heredan de `Object.prototype` de forma predeterminada.

## La herencia y la cadena de prototipos

Para construir cadenas de prototipos más largas, podemos establecer el `[[Prototipo]]` de `Constructor.prototype` a través de la función `Object.setPrototypeOf()`.

```js
function Base() {}
function Derived() {}
// Set the `[[Prototype]]` of `Derived.prototype`
// to `Base.prototype`
Object.setPrototypeOf(Derived.prototype, Base.prototype);

const obj = new Derived();
// obj ---> Derived.prototype ---> Base.prototype ---> Object.prototype ---> null
```

> [!NOTE]
> En términos de clase, esto es equivalente a utilizar la sintaxis `extends`.

