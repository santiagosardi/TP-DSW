# Estrategia técnica

Este documento registra las decisiones de la implementación final de MyGameSearcher y sus motivos. La configuración operativa se resume en la [guía técnica](../desarrollo_backend_frontend.md).

## Tecnologías elegidas

| Área | Tecnología | Motivo |
| --- | --- | --- |
| Interfaz | React 19 y TypeScript | Componentes reutilizables y contratos tipados |
| Herramientas frontend | Vite | Desarrollo y compilación de la aplicación |
| Navegación | React Router | Organización de las vistas y rutas del cliente |
| Cliente HTTP | Axios | Consumo de la API REST |
| Estilos | Bootstrap y CSS tradicional | Componentes visuales y adaptación responsive |
| Backend | NestJS y TypeScript | Organización por módulos y separación de responsabilidades |
| API | REST con JSON | Comunicación sencilla entre implementaciones separadas |
| Persistencia | MikroORM 7.2.3, mysql2 y MySQL | Mapeo de entidades y relaciones a una base relacional |
| Autenticación | JWT y bcryptjs | Identificación mediante tokens y almacenamiento de hashes de contraseñas |

## Arquitectura y despliegue

```text
React / Vercel
    ↓ HTTPS + REST API + JWT
NestJS / Render
    ↓ MikroORM + SSL
MySQL / Aiven
```

El frontend presenta la información y envía solicitudes. En el backend, los controladores reciben las peticiones, los DTOs y ValidationPipe validan los datos y los servicios resuelven las reglas de negocio. MikroORM gestiona la persistencia y las relaciones. Las migraciones versionan el esquema y el seed carga el catálogo.

Vercel aloja el frontend, Render ejecuta el backend y Aiven proporciona MySQL. La configuración varía por entorno mediante variables, sin incorporar secretos al código. El deploy de las implementaciones se realiza desde `main`.

## Seguridad

- JWT identifica al usuario en las solicitudes autenticadas.
- Los guards protegen rutas y verifican los permisos de los roles USER y ADMIN.
- Los recursos personales se asocian al usuario autenticado; las operaciones administrativas requieren autorización.
- bcryptjs genera y verifica hashes de contraseñas. Las contraseñas no se almacenan en texto plano y los hashes no deben formar parte de respuestas públicas.
- Las credenciales y secretos se configuran por entorno.
- HTTPS protege la comunicación pública y SSL protege la conexión del backend con Aiven.
- CORS utiliza `FRONTEND_ORIGIN` para permitir el origen configurado del frontend; no reemplaza la autenticación ni la autorización.

## Recomendaciones sin IA

Las recomendaciones se calculan dinámicamente: no se persisten como una entidad ni utilizan inteligencia artificial.

Se acumulan preferencias a partir de los juegos de referencia. Los favoritos tienen mayor peso cuando forman parte de esa fuente. Para cada candidato se suman los aportes:

| Coincidencia | Aporte |
| --- | --- |
| Género | 3 × peso acumulado del género |
| Característica | 2 × peso acumulado de la característica |
| Plataforma | 1 × peso acumulado de la plataforma |

El resultado incluye el puntaje y motivos comprensibles. Con los mismos datos de entrada, el cálculo produce el mismo resultado. Esta decisión permite explicar y verificar las recomendaciones sin introducir modelos de aprendizaje automático.

## Testing y validación al cierre

| Área | Herramienta | Resultado validado |
| --- | --- | --- |
| Frontend | Vitest | 8 archivos, 91 tests aprobados |
| Backend | Jest | 14 suites, 174 tests aprobados |
| E2E aislado | Playwright | 7/7 escenarios aprobados |

Estos valores corresponden al cierre del proyecto. La infraestructura E2E se mantiene separada del entorno de producción. Los comandos y requisitos para repetir las pruebas pertenecen a los repositorios de implementación.

## Diseño responsive

La interfaz utiliza Bootstrap, CSS, Grid/Flexbox y media queries para adaptarse a desktop, tablet y mobile. Se prioriza el contenido esencial en pantallas pequeñas y se busca evitar el scroll horizontal.

La validación manual al cierre cubrió anchos aproximados de 1440, 1024, 768 y 390 px. Esta comprobación complementa las pruebas automatizadas; no implica cobertura de todos los dispositivos posibles.

## Modelos y documentación

El dominio final se organiza alrededor de Juego, Genero, Plataforma, Caracteristica, Usuario, Biblioteca y Coleccion. Biblioteca vincula un usuario con un juego y agrega estado y favorito; Coleccion agrupa juegos de un usuario.

El [modelo de dominio final](../ModeloDominio_DGame.png) documenta las entidades y asociaciones del negocio; el [modelo entidad-relación final](../Modelo_Entidad_Relacion.png) documenta las tablas, claves y relaciones del esquema implementado. Para la implementación y el contrato de la API, consultar el [repositorio backend](https://github.com/santiagosardi/mygamesearcher-backend) y el [repositorio frontend](https://github.com/santiagosardi/mygamesearcher-frontend).
