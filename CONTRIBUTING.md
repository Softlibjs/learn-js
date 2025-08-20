# Pautas para Contribuir

¡Gracias por tu interés en contribuir a este proyecto! Para mantener el historial de cambios claro y coherente, te pedimos que sigas las siguientes pautas.

## Estilo de Commits

Utilizamos la convención de **Conventional Commits** para los mensajes de commit. Esto nos ayuda a automatizar la documentación de cambios y a entender el propósito de cada commit de un vistazo.

Cada mensaje de commit debe tener la siguiente estructura:

`<tipo>[opcional](ámbito): <descripción>`

### Tipos de Commit

Elige uno de los siguientes tipos para categorizar tu cambio:

* `feat`: Un nuevo "feature" o funcionalidad.
* `fix`: Una corrección de un error.
* `docs`: Cambios en la documentación (como el `README.md` o el `CONTRIBUTING.md`).
* `style`: Cambios que no afectan la lógica del código (formato, espacios en blanco, etc.).
* `refactor`: Un cambio en el código que no corrige un error ni añade una funcionalidad.
* `test`: Añadir o corregir pruebas.
* `chore`: Otros cambios en la construcción o herramientas auxiliares, como la configuración de Git.

### Ejemplo de un Commit

```bash
git commit -m "docs: Add a contributing guide"
```

## Estructura de carpetas propuesta

Cada directorio principal dentro de `src` contendrá un archivo `README.md` que servirá como una página de inicio para esa sección, además de los archivos de cada artículo.

```
learn-js/
├── README.md             <- Página principal del blog
├── CONTRIBUTING.md       <- Guía de contribución
├── src/
│   ├── built-in-objects/
│   │   ├── README.md     <- Índice de la sección
│   │   ├── date.md       <- Artículo sobre el objeto Date
│   │   └── json.md       <- Artículo sobre el objeto JSON
│   ├── expressions-and-operators/
│   │   ├── README.md
│   │   ├── arithmetic-operators.md
│   │   └── logical-operators.md
│   ├── statements-and-declarations/
│   │   ├── README.md
│   │   ├── conditionals.md
│   │   └── loops.md
│   ├── functions/
│   │   ├── README.md
│   │   ├── arrow-functions.md
│   │   └── hoisting.md
│   ├── classes/
│   │   ├── README.md
│   │   ├── classes-intro.md
│   │   └── inheritance.md
│   ├── regular-expressions/
│   │   ├── README.md
│   │   └── regex-intro.md
│   ├── errors/
│   │   ├── README.md
│   │   └── try-catch.md
│   └── misc/
│       ├── README.md
│       └── promises.md
```

### Explicación de la estructura

  * **`src/`:** El directorio principal para toda la documentación.
  * **`built-in-objects/`:** Aquí puedes documentar los objetos globales de JavaScript como `Date`, `JSON`, `Math`, etc.
  * **`expressions-and-operators/`:** Ideal para explicar operadores (`+`, `-`, `===`) y expresiones.
  * **`statements-and-declarations/`:** Para temas como bucles (`for`, `while`), condicionales (`if/else`) y declaraciones de variables (`let`, `const`, `var`).
  * **`functions/`:** Una sección dedicada a las funciones, incluyendo temas como `arrow functions` y `closures`.
  * **`classes/`:** Para la programación orientada a objetos en JavaScript.
  * **`regular-expressions/`:** Todo sobre cómo usar expresiones regulares.
  * **`errors/`:** Para documentar el manejo de errores (`try...catch`, `Error`).
  * **`misc/`:** Una sección para temas variados que no encajen en las otras categorías, como `promises` o `async/await`.

## Estructura de Contenido

Cada artículo debe seguir el siguiente formato para mantener la consistencia y legibilidad.

- **Título Principal (`#`)**: El título del artículo.
- **Subtítulos (`##`)**: Secciones principales del artículo.
- **Bloques de Código**: Usa la etiqueta de lenguaje para un correcto resaltado de sintaxis, por ejemplo: ` ```javascript `.

Ejemplo de un artículo:

```markdown
  # Título del Artículo
  
  Una breve descripción del tema.
  
  ## Concepto Principal
  
  Una explicación detallada del concepto.
  
  ## Ejemplos de Código
  
  ---javascript
    // Código de ejemplo
    const ejemplo = "Hola";
  ---
  ## Polyfills para diferentes versiones
  
  ### ES3
  
  Aquí puedes describir y dar ejemplos de polyfills para características de **ECMAScript 3** que son comunes en navegadores antiguos.
  
  ### ES5
  
  Explica cómo se pueden "polyfill" características de **ECMAScript 5**, como `Array.prototype.forEach`.
  
  ---javascript
    // Ejemplo de polyfill para forEach si no existe
    if (!Array.prototype.forEach) {
      Array.prototype.forEach = function(callback, thisArg) {
        // Implementación del polyfill
      };
    }
  ---
```
