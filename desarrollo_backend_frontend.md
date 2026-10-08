# Guía técnica de frontend y backend

Esta guía describe el sistema final de MyGameSearcher. TP-DSW contiene documentación académica; la instalación y ejecución se realizan en los repositorios de implementación, no en este repositorio.

## Componentes y comunicación

| Componente | Responsabilidad | Implementación |
| --- | --- | --- |
| Frontend | Interfaz, navegación y consumo de la API | React 19, TypeScript, Vite, React Router y Axios; Bootstrap y CSS tradicional |
| Backend | Validación, autenticación, autorización y reglas de negocio | NestJS, TypeScript, MikroORM 7.2.3 y mysql2 |
| Base de datos | Persistencia del catálogo y recursos de usuarios | MySQL |

La comunicación utiliza una API REST con JSON. Axios envía las solicitudes y, en las operaciones autenticadas, el token JWT mediante `Authorization: Bearer <token>`. El backend comprueba la identidad y los permisos; la interfaz no sustituye estos controles.

## Desarrollo local

El frontend utiliza normalmente `http://localhost:5173` y el backend `http://localhost:3000`. La URL de la API se configura en el frontend y el origen permitido se configura en el backend.

Consultar las instrucciones y los scripts vigentes de cada implementación:

- [README del frontend](https://github.com/santiagosardi/mygamesearcher-frontend#readme)
- [README del backend](https://github.com/santiagosardi/mygamesearcher-backend#readme)

Esas guías son la referencia para instalar dependencias, preparar el entorno, ejecutar la aplicación, aplicar migraciones y utilizar seeds. No es necesario volver a generar proyectos NestJS o Vite.

## Variables de entorno

Cada repositorio de implementación documenta sus variables de ejemplo. Las credenciales y secretos deben configurarse fuera del código versionado.

### Backend

| Variable | Uso |
| --- | --- |
| `NODE_ENV` | Identifica el entorno de ejecución |
| `PORT` | Puerto HTTP del servidor; en desarrollo se utiliza normalmente 3000 |
| `DB_HOST` | Host de MySQL |
| `DB_PORT` | Puerto de MySQL |
| `DB_USER` | Usuario de conexión |
| `DB_PASS` | Contraseña de conexión; se conserva este nombre exacto |
| `DB_NAME` | Base de datos utilizada |
| `DB_SSL` | Activa SSL cuando el entorno lo requiere; el entorno local puede funcionar sin SSL |
| `DB_SSL_CA` | Certificado CA para verificar la conexión SSL; configurar su contenido fuera del repositorio |
| `JWT_SECRET` | Secreto utilizado para la firma y validación de JWT |
| `FRONTEND_ORIGIN` | Origen exacto autorizado por CORS; localhost en desarrollo y URL HTTPS del frontend en producción |

No deben publicarse contraseñas, secretos JWT ni el contenido de la CA. Las variables exclusivas de E2E o de creación de administrador se consultan en la documentación del backend y no se confunden con la configuración normal de la aplicación.

### Frontend

| Variable | Uso |
| --- | --- |
| `VITE_API_URL` | URL base de la API: backend local en desarrollo y backend HTTPS en producción |

Las variables `VITE_*` se incorporan al cliente: no deben contener secretos.

## Producción

```text
React / Vercel → HTTPS REST + JWT → NestJS / Render → MikroORM + SSL → MySQL / Aiven
```

- [Frontend en Vercel](https://mygamesearcher-frontend-fawn.vercel.app)
- [Backend en Render](https://mygamesearcher-backend.onrender.com)
- Base MySQL alojada en Aiven, accesible por el backend mediante SSL.

Los repositorios de implementación publican desde `main`. Las migraciones mantienen la estructura de la base y el seed carga el catálogo; sus comandos y condiciones de uso se documentan en el backend. No deben ejecutarse como parte de una revisión de documentación.

## Documentación relacionada

- [Estrategia técnica y seguridad](./docs/estrategia-tecnica.md)
- [Metodología y flujo de integración](./docs/metodologia.md)
- [Presentación y validación al cierre](./README.md)
