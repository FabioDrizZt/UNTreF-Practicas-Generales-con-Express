# CRUD de Películas con Express, FS, JSON y Validación con Zod

## Descripción

Este proyecto es una API RESTful construida con **Node.js** y **Express** que permite realizar operaciones CRUD (Crear, Leer, Actualizar y Borrar) sobre una colección de películas almacenadas en un archivo JSON. Además, utiliza la librería **Zod** para validar los datos de entrada, asegurando que la información de las películas cumpla con ciertos requisitos antes de ser almacenada.

## Características principales

- **CRUD completo**: puedes crear, leer, actualizar y eliminar películas.
- **Persistencia en archivo**: los datos se guardan en un archivo `movies.json` usando el módulo nativo `fs` de Node.js.
- **Validación robusta**: se utiliza Zod para validar la estructura y los tipos de datos de cada película.
- **API RESTful**: endpoints claros y organizados para interactuar con los datos.

## Estructura del proyecto

```
.
├── data/
│   └── movies.json         # Archivo donde se almacenan las películas
├── schemas/
│   └── pelis.js            # Esquema de validación con Zod
├── server.js               # Lógica principal del servidor y rutas
├── package.json            # Dependencias y scripts
└── readme.md               # Este archivo
```

## Instalación

1. Clona el repositorio.
2. Instala las dependencias:
   ```bash
   npm install
   ```
3. Inicia el servidor:
   ```bash
   npm run dev
   ```
   El servidor estará disponible en [http://localhost:3000](http://localhost:3000).

## Endpoints principales

- `GET /peliculas`: Lista todas las películas o filtra por género usando el query param `genero`.
- `GET /peliculas/:id`: Obtiene una película por su ID.
- `POST /peliculas`: Crea una nueva película (requiere validación con Zod).
- `PATCH /peliculas/:id`: Modifica una película existente.
- `DELETE /peliculas/:id`: Elimina una película por su ID.

## Ejemplo de estructura de película

```json
{
  "id": "uuid-generado",
  "title": "Inception",
  "year": 2010,
  "director": "Christopher Nolan",
  "duration": 148,
  "poster": "https://ejemplo.com/poster.jpg",
  "genre": ["Action", "Adventure", "Sci-Fi"],
  "rate": 8.8
}
```

## Validación con Zod

El esquema de validación asegura que:

- `title`: string, mínimo 3 caracteres.
- `year`: número entero entre 1900 y 2050.
- `director`: string, mínimo 3 caracteres.
- `duration`: número entre 1 y 1000 minutos.
- `poster`: URL válida (opcional).
- `genre`: array de géneros válidos.
- `rate`: número entero entre 0 y 10 (por defecto 5).

Si los datos no cumplen con el esquema, la API responde con un error y detalles de la validación.

## ¿Por qué usar FS y JSON?

En vez de una base de datos, este proyecto utiliza el sistema de archivos (`fs`) para leer y escribir los datos en un archivo JSON. Esto es útil para proyectos pequeños, prototipos o para aprender cómo funciona la persistencia de datos de forma sencilla.

## ¿Por qué usar Zod?

Zod permite definir esquemas de validación de manera declarativa y sencilla, asegurando que los datos que llegan a la API sean correctos antes de ser procesados o almacenados.

## Conclusión

Este proyecto es ideal para aprender los fundamentos de una API RESTful, la manipulación de archivos en Node.js y la validación de datos en JavaScript. Es un excelente punto de partida antes de pasar a bases de datos más avanzadas.
