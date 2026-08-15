# Estrategia técnica

## Objetivo

Registrar las principales decisiones tecnológicas del proyecto y sus motivos.

Este documento define **con qué tecnologías se desarrollará el sistema**.  
La organización interna y las responsabilidades de los componentes se documentan en el documento de **Arquitectura**.

Las decisiones pueden cambiar durante el desarrollo si aparece información que justifique revisarlas.

---

# Stack tecnológico

## Backend

| Decisión | Tecnología | Estado |
|---|---|---|
| Lenguaje | TypeScript | Confirmada |
| Framework | NestJS | Confirmada |
| API | REST + JSON sobre HTTP | Propuesta |
| ORM | MikroORM | Propuesta |
| Base de datos | MySQL | Confirmada |
| Validación | DTOs + `class-validator` + `ValidationPipe` | Propuesta |
| Testing | Jest | Propuesta |
| Autenticación | JWT | Propuesta |
| Documentación API | Swagger / OpenAPI | Propuesta |

### Motivos principales

- **NestJS:** proporciona una estructura adecuada para desarrollar el backend y facilita la separación de responsabilidades.
- **TypeScript:** aporta tipado estático y se integra naturalmente con NestJS.
- **REST + JSON:** permite mantener frontend y backend desacoplados mediante una API HTTP sencilla.
- **MySQL:** se adapta al modelo relacional del sistema y el equipo posee experiencia previa.
- **MikroORM:** permite trabajar con MySQL desde TypeScript mediante un ORM y se integra con el stack seleccionado.
- **Jest:** permite implementar las pruebas requeridas por la cátedra dentro del ecosistema de NestJS.
- **JWT:** resulta adecuado para una aplicación con frontend y backend separados.
- **Swagger/OpenAPI:** facilita documentar y consultar el contrato de la API.

---

# Frontend

| Decisión | Tecnología | Estado |
|---|---|---|
| Framework | React + TypeScript | Propuesta |
| Estado | Hooks nativos de React | Propuesta |
| Estilos | Bootstrap | Propuesta |
| Testing de componentes | Vitest + React Testing Library | Propuesta |
| Testing E2E | Pendiente | Pendiente |

### Motivos principales

- **React:** permite construir la interfaz mediante componentes reutilizables y cumple con los requisitos del proyecto.
- **TypeScript:** permite representar de forma explícita los modelos y contratos utilizados por el frontend.
- **Hooks nativos:** inicialmente son suficientes para el alcance previsto y evitan agregar complejidad innecesaria.
- **Bootstrap:** facilita implementar una interfaz responsive y mobile-first, incluyendo los breakpoints requeridos.
- **Vitest + React Testing Library:** permiten probar componentes desde su comportamiento observable.

---

# Configuración y ambientes

## Variables de entorno

**Decisión:** utilizar variables de entorno mediante `.env`.

**Estado:** Propuesta.

Se utilizarán variables de entorno para separar la configuración del código fuente y evitar almacenar información sensible directamente en el repositorio.

Se mantendrá un archivo `.env.example` con las variables necesarias para ejecutar el proyecto.

---

# Testing

La estrategia de testing deberá cumplir como mínimo con los requisitos establecidos por la cátedra:

### Backend

- al menos un test automatizado por integrante;
- al menos un test de integración.

### Frontend

- al menos un test unitario de componente;
- al menos un test end-to-end.

Además de cumplir estos mínimos, se priorizarán pruebas sobre funcionalidades que contengan lógica de negocio relevante.

---

# Decisiones pendientes

Las siguientes decisiones se tomarán cuando exista suficiente información sobre el sistema:

- herramienta para testing E2E;
- integración concreta de Bootstrap con React;
- estrategia de deploy;
- configuración de ambientes de desarrollo, testing y producción;
- detalles adicionales de autenticación;
- decisiones tecnológicas que surjan durante la implementación.

---

# Relación con la arquitectura

La **Estrategia técnica** define principalmente:

> **¿Con qué tecnologías vamos a construir el sistema?**

La **Arquitectura** define principalmente:

> **¿Cómo vamos a organizar esas tecnologías para construir el sistema?**

Por ejemplo:

- Estrategia técnica → NestJS + MikroORM + MySQL.
- Arquitectura → backend organizado en capas y módulos.
- Estrategia técnica → React + Bootstrap.
- Arquitectura → organización de componentes, servicios y comunicación con la API.

Las decisiones arquitectónicas más detalladas se definirán a partir del modelo del sistema y de las necesidades que aparezcan durante el desarrollo.