# Object.defineProperty()

> [!NOTE]
> ECMAScript 2009, la 5th edición de la especificación, JavaScript introdujo las siguientes propiedades nuevas en los objetos integrados que existen en la Edición 3

El método estático `Object.defineProperty()` define una nueva propiedad directamente en un objeto, o modifica una propiedad existente en un objeto y devuelve el objeto.

```js
var o = {};

Object.defineProperty(o, "a", {
    value: 37,
    writable: true,
    enumerable: true,
    configurable: true
});

o.b; // 'a' property exists in the o object and its value is 37
```

### Enumerable attribute

El atributo de propiedad `enumerable` define si la propiedad se considera mediante [Object.assign()]() o el operador [spread](). Para propiedades que no son de tipo [Symbol](), también define si se muestra en un bucle [for...in]() y en [Object.keys()]().

```js
var o = {};

Object.defineProperty(o, "a", {
    value: 1,
    enumerable: true
});

for (var i in o) {
  console.log(i); // Logs 'a' and 'd' (always in that order)
}

Object.keys(o); // ['a', 'd']
```

### Configurable attribute

El atributo `configurable` controla si la propiedad se puede eliminar del objeto y si sus atributos (**excepto** `value` y `writable`) se pueden cambiar.

```js
const o = {};
Object.defineProperty(o, "a", {
  get() {
    return 1;
  },
  configurable: false,
});

Object.defineProperty(o, "a", {
  set() {},
}); // throws a TypeError (set was undefined previously)

console.log(o.a); // 1
```

> [!CAUTION]
> ```js
> // You cannot try to mix both:
> Object.defineProperty(o, "conflict", {
>   value: 0x9f91102,
>   get() {
>     return 0xdeadbeef;
>   },
> });
> // throws a TypeError: value appears
> // only in data descriptors,
> // get appears only in accessor descriptors
> ```
