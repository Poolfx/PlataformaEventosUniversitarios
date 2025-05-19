# PlataformaEventosUniversitarios# Plataforma de Organización de Eventos Universitarios

## Descripción

Este proyecto es una **Plataforma de Organización de Eventos Universitarios** que permite a organizaciones estudiantiles y administradores crear, publicar y gestionar eventos académicos, culturales y recreativos. Los estudiantes pueden registrarse, controlar aforos en tiempo real, y descargar certificados digitales de asistencia.

## Tabla de Contenidos

- [PlataformaEventosUniversitarios# Plataforma de Organización de Eventos Universitarios](#plataformaeventosuniversitarios-plataforma-de-organización-de-eventos-universitarios)
  - [Descripción](#descripción)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [Características](#características)
  - [Tecnologías](#tecnologías)
  - [Arquitectura](#arquitectura)
  - [Instalación](#instalación)
    - [Prerrequisitos](#prerrequisitos)
    - [Clonar repositorios](#clonar-repositorios)
    - [Configuración](#configuración)
    - [Ejecución](#ejecución)
  - [Uso](#uso)
  - [Estructura de Carpetas](#estructura-de-carpetas)
  - [Contribuir](#contribuir)
  - [Equipo](#equipo)
  - [Licencia](#licencia)

## Características

* CRUD de eventos con definición de fecha, lugar y aforo
* Registro y control de asistentes
* Dashboard de control de aforo en tiempo real
* Generación de certificados PDF de asistencia
* Notificaciones automáticas por correo electrónico
* Autenticación y autorización segura (SSO o JWT)

## Tecnologías

* **Frontend:** Next.js (React + TypeScript)
* **Backend:** ASP.NET Core Web API (C#)
* **Base de Datos:** PostgreSQL
* **Mensajería:** RabbitMQ o Kafka
* **Contenedores y Orquestación:** Docker, Kubernetes

## Arquitectura

La solución sigue una **arquitectura en capas**:

1. **Presentación (Frontend):** Next.js
2. **Capa de Aplicación/API (Controllers):** ASP.NET Core Web API
3. **Lógica de Negocio (Services):** Clases C# encargadas de las reglas de negocio
4. **Persistencia (Data):** Entity Framework Core + PostgreSQL
5. **Integraciones y Mensajería:** Bus de mensajes para notificaciones y generación asíncrona de certificados

> Diagrama de Contexto:
>
> ```mermaid
> flowchart TB
>   Usuario-->|Interfaz|Frontend
>   Frontend-->APIGateway
>   APIGateway-->ServicioEventos
>   APIGateway-->ServicioUsuarios
>   APIGateway-->ServicioInscripciones
>   APIGateway-->ServicioCertificados
>   ServicioInscripciones-->BaseDatos
>   ServicioCertificados-->BaseDatos
>   Notificaciones-->SMTP
> ```

## Instalación

### Prerrequisitos

* Node.js >= 14
* .NET SDK >= 6.0
* PostgreSQL
* Docker y kubectl (opcional)

### Clonar repositorios

```bash
https://github.com/Poolfx/PlataformaEventosUniversitarios
```

### Configuración

1. Crear base de datos PostgreSQL y actualizar cadena de conexión en `backend/appsettings.json`.
2. Configurar variables de entorno para RabbitMQ/Kafka y SMTP.

### Ejecución

```bash
# Backend
dotnet build backend
dotnet run --project backend/DS-uees-now-ws.csproj

# Frontend
cd frontend
npm install
npm run dev
```

Accede a [http://localhost:3000](http://localhost:3000) para ver la aplicación.

## Uso

1. Registrar una cuenta o iniciar sesión con credenciales institucionales.
2. Navegar al panel de organizadores para crear y editar eventos.
3. Los estudiantes pueden inscribirse desde el catálogo de eventos.
4. Ver el dashboard de aforo en tiempo real.
5. Descargar certificados PDF tras asistir.

## Estructura de Carpetas

```
├── frontend/             # Next.js App
│   ├── pages/
│   ├── components/
│   └── public/
├── backend/              # ASP.NET Core Web API
│   ├── Controllers/
│   ├── Services/
│   ├── Data/
│   └── Models/
└── docs/                 # Documentación y diagramas
```

## Contribuir

1. Crear branch `feature/nombre-descriptivo` desde `develop`.
2. Seguir [Conventional Commits](https://www.conventionalcommits.org).
3. Abrir Pull Request hacia `develop` y asignar revisores.

## Equipo

* **Carlos G. Orellana Chumbay** – Frontend y UX
* **Paul R. Torres Rueda** – Backend y API
* **Kevin A. Soriano Domínguez** – Modelado de datos y UML
* **Jose M. Arias Zavala** – Requerimientos y documentación

## Licencia

Este proyecto está bajo la licencia MIT. Véase el archivo [LICENSE](LICENSE) para más detalles.
