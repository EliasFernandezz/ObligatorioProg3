# 🎙️ La Voz del Este — Sitio Web para Emisora de Radio (ASP.NET MVC)

🇪🇸 [Español](#-español) · 🇬🇧 [English](#-english)

---

# 🇪🇸 Español

Aplicación web desarrollada con **ASP.NET MVC** para la emisora de radio "La Voz del Este": muestra el programa en emisión, noticias, clima y cotizaciones, y permite a editores y administradores gestionar el contenido del sitio según los permisos de cada rol.

## Contexto

Proyecto académico grupal (obligatorio de **Programación 3**, 2025), desarrollado en **CEI** (Analista Programador), en convenio con la **Universidad CLAEH**, por un equipo de dos personas. El objetivo era cumplir los requerimientos de un cliente ficticio: un sitio con autenticación estable, gestión de contenido por roles, diseño responsive y una paleta de colores en tonos azules.

## Funcionalidades

- **Autenticación:** inicio de sesión con correo y contraseña, registro de usuarios y acceso como invitado. Al registrarse, el usuario recibe automáticamente el rol de cliente.
- **Validaciones de registro:** campos obligatorios, formato de correo, contraseña de 8 a 16 caracteres y **cédula uruguaya válida** (con cálculo del dígito verificador).
- **Roles y navegación dinámica:** la barra de navegación cambia según el rol (invitado, cliente, editor o administrador).
- **Gestión de usuarios (administrador):** listado, edición de datos y rol, y eliminación con confirmación mediante modales.
- **Permisos configurables:** cada acción (agregar, modificar o eliminar noticias, programas, conductores, patrocinadores, usuarios y comentarios) tiene un permiso que el administrador puede activar o desactivar por rol.
- **Gestión de contenido (editor y administrador):** CRUD de noticias, programas, horarios de programas, patrocinadores y conductores.
- **Validación de horarios:** el sistema impide cargar horarios que se superpongan con otros del mismo día.
- **Página de inicio:** muestra el programa que está al aire según el día y la hora actual, y todas las noticias publicadas.
- **Clima:** estado actual y pronóstico de 5 días para Maldonado (OpenWeatherMap), con registro de los datos en la base de datos sin duplicados.
- **Cotizaciones:** valor del dólar frente al peso uruguayo, el euro y el real (CurrencyLayer), con histórico en base de datos y caché de 30 minutos.
- **Diseño responsive** con Bootstrap, en tonos azules.

## Tecnologías

| Área | Herramientas |
|---|---|
| Framework | ASP.NET MVC 5 (.NET Framework 4.7.2), C# |
| Vistas | Razor, Bootstrap 5, jQuery, JavaScript |
| Datos | SQL Server, Entity Framework 6 (Database First) y ADO.NET |
| APIs | OpenWeatherMap, CurrencyLayer |
| Librerías | Newtonsoft.Json, RestSharp |
| Herramientas | Visual Studio, Git y GitHub (ramas `main`, `develop` y `feature`), Postman, QuickType |

## Mi aporte

- Desarrollé el registro y el inicio de sesión con sus validaciones, incluida la de cédula uruguaya.
- Implementé la gestión de usuarios y roles, con edición, eliminación con modales y la barra de navegación según el rol.
- Construí el sistema de permisos por rol, activables desde el panel de administración.
- Desarrollé la gestión de programas y de horarios, con validación de horarios superpuestos.
- Integré la API de clima (OpenWeatherMap), con almacenamiento en base de datos, y el programa en emisión de la página de inicio.
- Diseñé las pantallas de gestión del administrador y del editor.

## Cómo ejecutarlo

**Requisitos:** Visual Studio 2022 con la carga de trabajo *ASP.NET and web development*, .NET Framework 4.7.2 y SQL Server (Express o LocalDB) con SQL Server Management Studio.

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/EliasFernandezz/ObligatorioProg3.git
   ```
2. Crear en SQL Server una base de datos llamada `vozDelEsteBsd` e importar el script `database/vozDelEsteBsd.sql`.
3. En `obligatorioProg3/Web.config`, cambiar `data source` por el nombre de tu servidor SQL en las cadenas de conexión `vozDelEsteBsdEntities`, `ConexionAdoCotizacion` y `ConexionAdo`.
4. Configurar tus propias claves de API (ver más abajo).
5. Abrir `obligatorioProg3.sln` en Visual Studio, restaurar los paquetes NuGet y ejecutar con **F5**.

### Claves de API

La app necesita una clave propia para cada servicio (ambos tienen plan gratuito). Reemplazá el valor en los archivos indicados:

| Servicio | Archivos |
|---|---|
| [OpenWeatherMap](https://openweathermap.org/api) | `Controllers/ClimaController.cs` |
| [CurrencyLayer](https://currencylayer.com/) | `Controllers/CotizacionController.cs` y `Servicios/CurrencyService.cs` |

> Reemplazá los valores por tus propias claves de API.

## Estructura del proyecto

```
obligatorioProg3/
├── Controllers/        # Login, registro, usuarios, permisos, noticias, programas,
│                       # horarios, patrocinadores, conductores, clima y cotizaciones
├── Models/             # Modelo de datos (Entity Framework) y clases de las APIs
├── ViewModels/         # Modelos de vista (inicio y registro)
├── CustomValidations/  # Validación de cédula uruguaya y de horarios
├── Filtros/            # Filtro de cotizaciones con caché
├── Servicios/          # Servicio de consulta de cotizaciones
├── Views/              # Vistas Razor
└── App_Start/          # Rutas, bundles y filtros
```

## Documentación

El proyecto cuenta con documentación técnica completa: requerimientos funcionales y no funcionales, casos de uso, modelo entidad-relación, modelo relacional, diagrama de casos de uso, diagrama de clases y manual de usuario con capturas. [Documentacion](https://docs.google.com/document/d/1VUWL3H0I-DOoj7onenLFhmFfRSQR1iJaFIsEaQF2O94/edit?usp=sharing)

## Desafíos y aprendizajes

- Diseñar un sistema de roles y permisos configurable, en lugar de reglas fijas en el código.
- Consumir APIs externas y guardar sus datos en la base de datos sin duplicarlos.
- Crear validaciones personalizadas (cédula uruguaya y horarios superpuestos).
- Trabajar en equipo con Git y GitHub, usando ramas `main`, `develop` y `feature`.
- Aprender de forma autodidacta tecnologías nuevas y aplicarlas al proyecto.

## Mejoras futuras

- Guardar las contraseñas con hash y no en texto plano.
- Mover las claves de API y las cadenas de conexión fuera del repositorio.
- Completar el flujo de comentarios de los clientes en los programas.
- Unificar la lógica duplicada de cotizaciones en un único servicio.
- Agregar pruebas automatizadas.

## Equipo

- **Elías Fernández** — [GitHub](https://github.com/EliasFernandezz)
- **Catherine Sonderegger** — [GitHub](https://github.com/CathGirL1)

---

# 🇬🇧 English

A web application built with **ASP.NET MVC** for the radio station "La Voz del Este": it shows the program currently on air, news, weather and exchange rates, and lets editors and administrators manage the site's content according to each role's permissions.

## Context

Group academic project (**Programming 3** assignment, 2025), developed at **CEI** (Programmer Analyst program) in partnership with **Universidad CLAEH**, by a team of two. The goal was to meet the requirements of a fictional client: a site with stable authentication, role-based content management, responsive design and a blue color palette.

## Features

- **Authentication:** login with email and password, user registration and guest access. New users automatically get the client role.
- **Registration validations:** required fields, email format, a password of 8 to 16 characters and a **valid Uruguayan ID number** (including check digit calculation).
- **Roles and dynamic navigation:** the navigation bar changes depending on the role (guest, client, editor or administrator).
- **User management (administrator):** list, edit data and role, and delete with modal confirmation.
- **Configurable permissions:** every action (add, edit or delete news, programs, hosts, sponsors, users and comments) has a permission that the administrator can enable or disable per role.
- **Content management (editor and administrator):** CRUD for news, programs, program schedules, sponsors and hosts.
- **Schedule validation:** the system prevents schedules that overlap with others on the same day.
- **Home page:** shows the program on air based on the current day and time, and all published news.
- **Weather:** current conditions and a 5-day forecast for Maldonado (OpenWeatherMap), with the data stored in the database without duplicates.
- **Exchange rates:** value of the US dollar against the Uruguayan peso, euro and Brazilian real (CurrencyLayer), with history in the database and a 30-minute cache.
- **Responsive design** with Bootstrap, in blue tones.

## Tech Stack

| Area | Tools |
|---|---|
| Framework | ASP.NET MVC 5 (.NET Framework 4.7.2), C# |
| Views | Razor, Bootstrap 5, jQuery, JavaScript |
| Data | SQL Server, Entity Framework 6 (Database First) and ADO.NET |
| APIs | OpenWeatherMap, CurrencyLayer |
| Libraries | Newtonsoft.Json, RestSharp |
| Tooling | Visual Studio, Git and GitHub (`main`, `develop` and `feature` branches), Postman, QuickType |

## My Contribution

- Built sign-up and login with their validations, including the Uruguayan ID check.
- Implemented user and role management, with editing, deletion through modals and a role-based navigation bar.
- Built the role permission system, which can be toggled from the admin panel.
- Developed program and schedule management, with overlapping schedule validation.
- Integrated the weather API (OpenWeatherMap) with database storage, and the on-air program on the home page.
- Designed the admin and editor management screens.

## Getting Started

**Requirements:** Visual Studio 2022 with the *ASP.NET and web development* workload, .NET Framework 4.7.2 and SQL Server (Express or LocalDB) with SQL Server Management Studio.

1. Clone the repository:
   ```bash
   git clone https://github.com/EliasFernandezz/ObligatorioProg3.git
   ```
2. Create a SQL Server database named `vozDelEsteBsd` and import the `database/vozDelEsteBsd.sql` script.
3. In `obligatorioProg3/Web.config`, change `data source` to your SQL Server name in the `vozDelEsteBsdEntities`, `ConexionAdoCotizacion` and `ConexionAdo` connection strings.
4. Set up your own API keys (see below).
5. Open `obligatorioProg3.sln` in Visual Studio, restore the NuGet packages and run with **F5**.

### API Keys

The app needs your own key for each service (both offer a free tier). Replace the value in the files indicated:

| Service | Files |
|---|---|
| [OpenWeatherMap](https://openweathermap.org/api) | `Controllers/ClimaController.cs` |
| [CurrencyLayer](https://currencylayer.com/) | `Controllers/CotizacionController.cs` and `Servicios/CurrencyService.cs` |

> Replace the values with your own API keys.

## Project Structure

```
obligatorioProg3/
├── Controllers/        # Login, registration, users, permissions, news, programs,
│                       # schedules, sponsors, hosts, weather and exchange rates
├── Models/             # Data model (Entity Framework) and API classes
├── ViewModels/         # View models (home and registration)
├── CustomValidations/  # Uruguayan ID and schedule validation
├── Filtros/            # Exchange rate filter with cache
├── Servicios/          # Exchange rate query service
├── Views/              # Razor views
└── App_Start/          # Routes, bundles and filters
```

## Documentation

The project includes full technical documentation: functional and non-functional requirements, use cases, entity-relationship model, relational model, use case diagram, class diagram and a user manual with screenshots. [Documentation](https://docs.google.com/document/d/1VUWL3H0I-DOoj7onenLFhmFfRSQR1iJaFIsEaQF2O94/edit?usp=sharing)

## Challenges & Learnings

- Designing a configurable role and permission system instead of hard-coded rules.
- Consuming external APIs and storing their data in the database without duplicates.
- Building custom validations (Uruguayan ID number and overlapping schedules).
- Working as a team with Git and GitHub, using `main`, `develop` and `feature` branches.
- Learning new technologies independently and applying them to the project.

## Future Improvements

- Store passwords hashed instead of in plain text.
- Move API keys and connection strings out of the repository.
- Complete the clients' comment flow on programs.
- Unify the duplicated exchange rate logic into a single service.
- Add automated tests.

## Team

- **Elías Fernández** — [GitHub](https://github.com/EliasFernandezz)
- **Catherine Sonderegger** — [GitHub](https://github.com/CathGirL1)
