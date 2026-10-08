# MyGameSearcher

MyGameSearcher es una plataforma para descubrir videojuegos, organizar una biblioteca personal y colecciones, y recibir recomendaciones explicables según las preferencias del usuario.

Este repositorio, **TP-DSW**, reúne la documentación académica, la propuesta, las decisiones técnicas, la metodología y los diagramas. El código de implementación se mantiene en repositorios separados de frontend y backend.

## Integrantes

- Santiago Sardi
- Santino Ripacolli

## Enlaces

- [Aplicación web](https://mygamesearcher-frontend-fawn.vercel.app)
- [Backend desplegado](https://mygamesearcher-backend.onrender.com)
- [Repositorio frontend](https://github.com/santiagosardi/mygamesearcher-frontend)
- [Repositorio backend](https://github.com/santiagosardi/mygamesearcher-backend)

## Arquitectura

```text
React / Vercel
    ↓ HTTPS + REST API + JWT
NestJS / Render
    ↓ MikroORM + SSL
MySQL / Aiven
```

El frontend consume la API REST mediante Axios. El backend valida las solicitudes, aplica las reglas de negocio y accede a MySQL mediante MikroORM. Los repositorios de implementación publican producción desde `main`.

## Tecnologías

| Componente | Tecnologías |
| --- | --- |
| Frontend | React 19, TypeScript, Vite, React Router, Axios, Bootstrap y CSS tradicional |
| Backend | NestJS, TypeScript, REST API, MikroORM 7.2.3, mysql2, JWT y bcryptjs |
| Persistencia | MySQL en Aiven, con conexión SSL |
| Despliegue | Vercel para frontend y Render para backend |

## Funcionalidades y roles

- Registro, login y autenticación JWT.
- Catálogo con búsqueda, filtros y detalle de juegos.
- Biblioteca personal con favoritos y estados de juego.
- Colecciones personales de juegos.
- Recomendaciones determinísticas y explicables.
- CRUDs administrativos de juegos, géneros, plataformas y características.
- Interfaz adaptable a desktop, tablet y mobile.

El rol **USER** utiliza el catálogo y administra sus recursos personales. El rol **ADMIN** dispone además de las operaciones protegidas de administración del catálogo.

## Catálogo y recomendaciones

El catálogo al cierre contiene **147 juegos, 13 géneros, 6 plataformas y 15 características**.

Las recomendaciones **no utilizan inteligencia artificial**. Se calculan con un puntaje determinístico: género coincidente +3, característica coincidente +2 y plataforma coincidente +1, aplicados a los pesos acumulados de las preferencias. Los favoritos tienen mayor peso como fuente de preferencias. Cada resultado incluye motivos que explican su puntaje.

## Validación al cierre

Estos resultados corresponden al estado validado al cierre del proyecto; no representan una ejecución automática desde este repositorio documental.

| Área | Resultado |
| --- | --- |
| Frontend | 8 archivos Vitest, 91 tests aprobados |
| Backend | 14 suites Jest, 174 tests aprobados |
| E2E aislado | 7/7 escenarios Playwright aprobados |

La adaptación responsive se validó manualmente en anchos aproximados de **1440, 1024, 768 y 390 px**, cubriendo desktop, tablet y mobile.

## Documentación

- [Propuesta inicial y resultado final](./Proposal.md)
- [Guía técnica de frontend y backend](./desarrollo_backend_frontend.md)
- [Índice documental](./docs/README.md)
- [Estrategia técnica](./docs/estrategia-tecnica.md)
- [Metodología](./docs/metodologia.md)
- [Modelo de dominio: imagen histórica](./ModeloDominio_DGame.png)
- [DER: imagen histórica](./Modelo_Entidad_Relacion.png)

**Los diagramas existentes están pendientes de actualización y no deben interpretarse como el modelo final implementado.** Esta revisión actualiza únicamente la documentación Markdown.

Para instalar y ejecutar la aplicación, consultar los README de los repositorios de implementación enlazados arriba.
