# API REST - Tienda Perú

API REST desarrollada con **Node.js**, **Express** y **MySQL** para compartir los datos de una tienda: productos, clientes y proveedores. Cada módulo ofrece las 5 operaciones CRUD (listar, obtener, crear, actualizar, eliminar).

## Tecnologías
- Node.js v20 o superior
- Express 5
- dotenv (variables de entorno)
- nodemon (desarrollo)

## Estructura del proyecto
```
api-productos/
├── db.sql
├── package.json
├── .env.example
├── .gitignore
└── src/
    ├── server.js
    ├── app.js
    ├── config/
    │   ├── env.js
    │   └── database.js
    ├── controllers/
    │   ├── producto.controller.js
    │   ├── cliente.controller.js
    │   └── proveedor.controller.js
    └── routes/
        ├── index.js
        ├── producto.routes.js
        ├── cliente.routes.js
        └── proveedor.routes.js
```

## Instalación
1. Instalar Node.js (v20 o superior) y MySQL.
2. Clonar el repositorio e instalar dependencias:
   ```bash
   git clone <URL_DEL_REPOSITORIO>
   cd api-productos
   npm install
   ```
3. Crear manualmente el archivo `.env` en la raíz (puede copiar `.env.example`):
   ```bash
   PORT=3000
   DB_HOST=localhost
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=
   DB_NAME=tiendaperu
   DB_CONNECTION_LIMIT=10
   ```
4. Ejecutar el script `db.sql` en MySQL (crea la base `tiendaperu`, las tablas `productos`, `clientes`, `proveedores` y 3 registros de prueba en cada una).
5. Iniciar el proyecto:
   ```bash
   node src/server
   ```
   Servidor disponible en `http://localhost:3000`.

## Modelo de datos
| Tabla | Campos |
|-------|--------|
| productos | id, marca, descripcion, precio, stock, create_at, update_at |
| clientes | id, apellidos, nombres, telefono, direccion, email, create_at, updated_at |
| proveedores | id, razonsocial, contacto, ruc, direccion, create_at, updated_at |

## Endpoints
| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | `/api/productos` · `/api/clientes` · `/api/proveedores` | Listar |
| GET | `/api/{modulo}/:id` | Obtener por ID |
| POST | `/api/{modulo}` | Crear |
| PUT | `/api/{modulo}/:id` | Actualizar |
| DELETE | `/api/{modulo}/:id` | Eliminar |

### Ejemplo: crear cliente (`POST /api/clientes`)
```json
{
  "apellidos": "Perez Soto",
  "nombres": "Ana",
  "telefono": "987654321",
  "direccion": "Av. Central 100",
  "email": "ana@gmail.com"
}
```

### Ejemplo: crear proveedor (`POST /api/proveedores`)
```json
{
  "razonsocial": "Distribuidora Andina S.A.C.",
  "contacto": "Pedro Rojas",
  "ruc": "20456789012",
  "direccion": "Jr. Comercio 250, Lima"
}
```

### Códigos de respuesta
`200` OK · `201` creado · `400` datos inválidos · `404` no encontrado · `409` duplicado (email / RUC) · `500` error del servidor

## Pruebas
Use **Postman** o un cliente similar: [Descargar Postman](https://www.postman.com/product/api-client/)

## Autor
Nayeli lucero quintana meneses 