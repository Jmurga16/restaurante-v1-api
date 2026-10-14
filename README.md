# Restaurante · API

API REST para la gestión de un restaurante: categorías, encargados, menús, platos, recetas e ingredientes.
Es el backend de [restaurante-v1-web](https://github.com/josemurgadev/restaurante-v1-web) (Angular 19).

## Stack

- **.NET 8** · ASP.NET Core **Minimal API**
- **Dapper** + Dapper.FluentMap sobre **SQL Server** (consultas en procedimientos almacenados)
- **Swagger / OpenAPI** para documentar y probar los endpoints

## Endpoints

CRUD completo (`GET`, `GET /{id}`, `POST`, `PUT /{id}`, `DELETE /{id}`) para:

| Recurso | Ruta base | Extra |
|---|---|---|
| Categorías | `/categoria` | |
| Encargados | `/encargado` | `GET /encargado-categorias` |
| Menús | `/menu` | `GET /menu-plato` (platos de cada menú) |
| Platos | `/plato` | `GET /plato/{platoId}/receta` |
| Recetas | `/receta` | |
| Ingredientes | `/ingredientes` | |

## Estructura

```
├── Program.cs     # Registro de servicios, Swagger, CORS y endpoints
├── Endpoints/     # Definición de rutas por recurso (Minimal API)
├── Services/      # Lógica de aplicación
├── Data/          # Repositorios con Dapper + scripts SQL de la base
├── Mappers/       # Mapeo columnas ↔ modelos con Dapper.FluentMap
└── Models/        # Entidades de dominio
```

## Ejecutar en local

Requiere .NET 8 SDK y SQL Server.

1. Crear la base `DBLosAromos` con los scripts de `Data/Scripts/` (o restaurar uno de los `.bacpac`).
2. Ajustar `ConnectionStrings:DefaultConnection` en `appsettings.json`.
3. Ejecutar:

```bash
dotnet run
```

Swagger queda disponible en `/swagger` en el entorno de desarrollo.

---

Desarrollado por **José Murga** · [josemurga.dev](https://josemurga.dev)
