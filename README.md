# ✅ Todo App

Una aplicación de gestión de tareas (TodoMVC) construida con **Vanilla JavaScript** y **Vite**, sin frameworks externos. Permite crear, completar, filtrar y eliminar tareas, con persistencia de datos en `localStorage`.


## 🚀 Demo 

👉 [Probar App](https://todo-app-andresmdevco.netlify.app/)


## 🛠 Tecnologías

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
- [`uuid`](https://www.npmjs.com/package/uuid) — Generación de IDs únicos para cada tarea
- `localStorage` — Persistencia del estado entre sesiones



## ⚙️ Cómo ejecutar el proyecto

```bash
# 1. Clonar el repositorio
git clone https://github.com/andresmdevco/todo-app.git
cd todo-app

# 2. Instalar dependencias
npm install

# 3. Iniciar el servidor de desarrollo
npm run dev

# 4. Abrir la URL de **localhost** que aparece en la terminal.

```



## 🧠 Arquitectura

La aplicación sigue una arquitectura modular basada en separación de responsabilidades:

### `store/todo.store.js`
Centraliza el **estado de la aplicación** y toda la lógica de negocio. Expone métodos para:

| Método | Descripción |
|---|---|
| `initStore()` | Inicializa el store cargando el estado desde `localStorage` |
| `getTodos(filter)` | Retorna los todos según el filtro activo (`All`, `Completed`, `Pending`) |
| `addTodo(description)` | Crea y agrega un nuevo todo |
| `toggleTodo(todoId)` | Alterna el estado `done` de un todo |
| `deleteTodo(todoId)` | Elimina un todo por su ID |
| `deleteCompleted()` | Elimina todos los todos completados |
| `setFilter(filter)` | Establece el filtro activo |
| `getCurrentFilter()` | Retorna el filtro actualmente activo |

### `todos/models/todo.model.js`
Define la clase `Todo` con los campos:
- `id` — UUID único generado automáticamente
- `description` — Texto de la tarea
- `done` — Estado de completado (`false` por defecto)
- `createdAt` — Fecha de creación

### `todos/use-cases/`
Funciones puras responsables del **renderizado en el DOM**:
- `createTodoHTML(todo)` — Crea y retorna un elemento `<li>` para un todo
- `renderTodos(elementId, todos)` — Renderiza la lista completa de todos en el contenedor indicado
- `renderPending(elementId)` — Actualiza el contador de tareas pendientes

### `todos/app.js`
Componente principal que:
1. Inserta el HTML de la UI en el DOM
2. Escucha eventos del usuario (teclado, clics, filtros)
3. Llama al store para modificar el estado
4. Llama a los use-cases para actualizar la vista



## ✨ Funcionalidades

- ➕ Agregar tareas presionando `Enter`
- ✔️ Marcar tareas como completadas
- 🗑️ Eliminar tareas individuales
- 🧹 Borrar todas las tareas completadas de una vez
- 🔍 Filtrar tareas por: **Todos**, **Pendientes**, **Completados**
- 💾 Persistencia automática en `localStorage`
