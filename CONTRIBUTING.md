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
