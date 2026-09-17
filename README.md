# LexIA Backend

Backend inicial de LexIA construido con:

- .NET 10
- ASP.NET Core Web API
- C# 14
- Entity Framework Core
- PostgreSQL
- ASP.NET Core Identity
- JWT
- Swagger/OpenAPI

## 1. Requisitos

- Visual Studio 2026 18.0 o superior
- Carga de trabajo "ASP.NET y desarrollo web"
- .NET 10 SDK
- PostgreSQL 16 o superior recomendado

## 2. Abrir el proyecto

Abra `LexIA.Backend.csproj` en Visual Studio 2026.

## 3. Configurar PostgreSQL

Cree una base de datos:

```sql
CREATE DATABASE lexia_db;
```

Edite `appsettings.json`:

```json
"DefaultConnection":
"Host=localhost;Port=5432;Database=lexia_db;Username=postgres;Password=TU_PASSWORD"
```

Cambie también la clave JWT por una cadena larga y aleatoria.

## 4. Crear la primera migración

En Visual Studio:

Tools > NuGet Package Manager > Package Manager Console

Ejecute:

```powershell
Add-Migration InitialCreate
Update-Database
```

También puede usar CLI:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

Si `dotnet ef` no está instalado:

```bash
dotnet tool install --global dotnet-ef
```

## 5. Ejecutar

Presione F5.

Abra:

`https://localhost:<puerto>/swagger`

## 6. Usuario inicial

Al ejecutarse por primera vez, el sistema crea:

Email:
`admin@lexia.local`

Contraseña:
`LexIA2026`

IMPORTANTE: cambie esa contraseña en un entorno real.

## 7. Probar login

POST `/api/auth/login`

```json
{
  "email": "admin@lexia.local",
  "password": "LexIA2026"
}
```

Copie el token JWT y utilícelo como:

`Authorization: Bearer <TOKEN>`

## Endpoints principales

- POST `/api/auth/login`
- POST `/api/auth/usuarios`
- GET/POST/PUT/DELETE `/api/clientes`
- GET/POST/PUT/DELETE `/api/expedientes`
- GET/POST `/api/actuaciones`
- GET/POST/PATCH `/api/tareas`
- GET `/api/dashboard`

## Próxima iteración recomendada

1. Documentos y almacenamiento de archivos.
2. Agenda y audiencias.
3. Auditoría automática mediante interceptor de EF.
4. DTOs de salida para evitar ciclos y exposición accidental.
5. FluentValidation.
6. Refresh tokens.
7. Recuperación/cambio de contraseña.
8. Pruebas unitarias e integración.
9. Docker Compose con PostgreSQL.
