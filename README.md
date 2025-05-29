

# Prueba Técnica Full Stack – CRUD de Usuarios, Roles y Variables

## Descripción

Este proyecto corresponde a una **prueba técnica** desarrollada con **.NET 8 (Web API)** para el backend, **Angular** para el frontend y **MariaDB** para la base de datos relacional.  
El objetivo es administrar **Usuarios**, **Roles** y **Variables** mediante CRUD completos, asegurando buenas prácticas y relaciones correctas entre entidades.

---

## Estructura de Carpetas


----------------------
/backend     → API .NET Core (WebAPI)
/frontend    → Angular (CRUD Frontend)

Tecnologías Utilizadas
----------------------
- Backend: .NET 8 WebAPI + Entity Framework Core
- Frontend: Angular 16+ (standalone)
- Base de datos: MariaDB 11.x

Instalación y Ejecución
-----------------------
1. Clonar el repositorio

    git clone <URL>
    cd <nombre>

2. Crear y configurar la base de datos

En tu consola de MariaDB:

    CREATE DATABASE IF NOT EXISTS appdb;
    USE appdb;

    CREATE TABLE Roles (
        Id INT AUTO_INCREMENT PRIMARY KEY,
        Nombre VARCHAR(50) NOT NULL
    );

    CREATE TABLE Usuarios (
        Id INT AUTO_INCREMENT PRIMARY KEY,
        Nombre VARCHAR(100) NOT NULL,
        Email VARCHAR(100) NOT NULL,
        RolId INT NOT NULL,
        FOREIGN KEY (RolId) REFERENCES Roles(Id)
    );

    CREATE TABLE Variables (
        Id INT AUTO_INCREMENT PRIMARY KEY,
        Nombre VARCHAR(100) NOT NULL,
        Valor VARCHAR(100) NOT NULL,
        Tipo INT NOT NULL
    );

3. Configura la conexión de la base de datos

Edita /backend/appsettings.json y cambia la cadena de conexión por tus credenciales:

    "ConnectionStrings": {
        "DefaultConnection": "server=localhost;database=appdb;user=root;password=TU_PASSWORD"
    },

4. Ejecutar el Backend

    cd backend
    dotnet restore
    dotnet run

La API quedará en: http://localhost:5010

5. Ejecutar el Frontend

    cd frontend
    npm install
    ng serve -o

La app abrirá en: http://localhost:4200

¿Qué puedes hacer?
------------------
- CRUD completo de Usuarios, Roles y Variables.
- Listar, crear, editar y eliminar registros.
- Los usuarios deben tener un Rol asignado (desplegable dinámico).
- Validación de campos en backend y frontend.
- El campo “Tipo” de Variables es numérico y lo define el usuario.

Notas
-----
- CORS está habilitado solo para localhost por facilidad de desarrollo.
- El foco está en funcionalidad, no en diseño visual avanzado.
- No incluye autenticación/autorización por alcance de la prueba técnica.

Contacto
--------

Desarrollado por:
Alan Medina Quiroga
alanm.q.4@gmail.com


