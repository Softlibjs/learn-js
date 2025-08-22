# Ámbito y Cierre

> [!NOTE]
> ECMAScript 2015, la 6th edición de la especificación, JavaScript introdujo las declaraciones `let` y `const`.

Tradicionalmente (antes de ES6), las variables de JavaScript solo tenían dos tipos de ámbito: *function scope* y *global scope*. Las variables declaradas con `var` tienen ámbito de función o global, **dependiendo de si se declaran dentro o fuera de una función**.

## Closures

En JavaScript, los cierres se crean cada vez que se crea una función. Un cierre es la combinación de una función y el entorno léxico en el que se **declaró** dicha función. Este entorno consta de todas las variables que estaban dentro del alcance al momento de crear el cierre.

```js
function makeFunc() {
    var name = "Mozilla";
    function displayName() {
        console.log(name);
    }
    return displayName;
}

var myFunc = makeFunc();
myFunc();
```

En algunos lenguajes de programación, las variables locales dentro de una función existen únicamente mientras dura su ejecución. Una vez que `makeFunc()` termina de ejecutarse, cabría esperar que la variable `name` ya no fuera accesible. Sin embargo, dado que el código sigue funcionando correctamente, esto obviamente no ocurre en JavaScript.

## IIFE

Las IIFE (Immediately Invoked Function Expression) son un patrón común utilizado para ejecutar arbitrariamente muchas declaraciones en su propio ámbito (y posiblemente devolver un valor), **en una ubicación que requiere una sola expresión**.

```js
// standard IIFE
(function () {
  // statements…
})();
```

## WeakMap 

En comparación con un cierre, el mismo WeakMap se puede reutilizar para todas las instancias creadas a partir de un constructor, lo que lo hace más eficiente en el uso de la memoria y permite que diferentes instancias de la misma clase lean los miembros privados de cada una.

```js
var Thing;

{
    var privateScope = new WeakMap();
    var counter = 0;

    Thing = function Thing1() {
        this.someProperty = "foo";
        privateScope.set(this, {
            hidden: ++counter
        });
    };

    Thing.prototype.showPublic = function() {
        return this.someProperty;
    };

    Thing.prototype.showPrivate = function() {
        return privateScope.get(this).hidden;
    };
}

console.log(typeof privateScope);
// "undefined"

var thing = new Thing();

console.log(thing);
// Thing {someProperty: "foo"}

thing.showPublic();
// "foo"

thing.showPrivate();
// 1
```

> [!NOTE]
> Sin embargo, debido a que los bloques no crean ámbitos para `var`, las declaraciones `var` aquí en realidad crean una variable global.
> ```js
> var x = 1;
> {
>     var x = 2;
> }
> console.log(x); // 2
> ```

##  Inheritance and the prototype chain

Como se mencionó anteriormente, cada instancia de función gestiona su propio alcance y cierre. Por lo tanto, no es recomendable crear funciones innecesariamente dentro de otras funciones si los cierres no son necesarios para una tarea específica, ya que esto afectará negativamente el rendimiento del script, tanto en términos de velocidad de procesamiento como de consumo de memoria.

```js
function MyObject(name, message) {
  this.name = name.toString();
  this.message = message.toString();
}
MyObject.prototype.getName = function () {
  return this.name;
};
MyObject.prototype.getMessage = function () {
  return this.message;
};
```
