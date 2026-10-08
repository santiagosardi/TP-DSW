# Metodología de trabajo

## Objetivo y equipo

El trabajo se organizó de forma incremental, incorporando funcionalidades y verificando su funcionamiento antes de ampliar el alcance. Los integrantes finales de la entrega son Santiago Sardi y Santino Ripacolli.

TP-DSW reúne la documentación académica. El código y sus verificaciones se mantienen en los repositorios separados de frontend y backend.

## Flujo de control de versiones

El flujo utilizado para integrar la implementación fue:

```text
feature/* → dev → main
```

- Las funcionalidades se trabajan en ramas específicas creadas desde `dev`.
- Los cambios terminados se integran en `dev` para comprobar su convivencia con el resto del sistema.
- La entrega estable se integra mediante un PR final de `dev` hacia `main`.
- `main` es la referencia de producción de los repositorios de implementación.

Los nombres de ramas y commits deben describir el propósito del cambio. Antes de un commit o merge se revisa el diff para detectar modificaciones ajenas a la tarea, archivos sensibles o cambios accidentales. Los PR deben explicar el cambio y las verificaciones realizadas.

## Verificación antes de integrar

Para cambios importantes de implementación se ejecutan los tests y el build correspondientes. Cuando el cambio afecta una interacción completa, se consideran las pruebas E2E aisladas y la validación manual pertinente.

Los criterios de revisión son:

- Cumplir el alcance de la tarea y mantener las funcionalidades existentes.
- Revisar errores de compilación y resultados de pruebas.
- Comprobar permisos y validaciones cuando se modifica un recurso protegido.
- Revisar la adaptación responsive cuando cambia la interfaz.
- Evitar incluir credenciales, secretos o cambios no relacionados.
- Actualizar la documentación afectada.

Para cambios exclusivamente documentales se revisan contenido, enlaces y formato del diff. No se ejecutan operaciones sobre bases de datos como parte de esa revisión.

## Acuerdos iniciales de organización

La propuesta metodológica inicial tomó referencias de Scrum y Unified Process: iteraciones aproximadas de dos semanas, reuniones semanales y responsabilidades compartidas. También propuso GitHub Issues, Projects, etiquetas y milestones para seguimiento, y WhatsApp para comunicación.

Se conservan como acuerdos de planificación, no como evidencia de cumplimiento de todas las reuniones, ceremonias o registros. Este documento no afirma una aplicación formal completa de esos marcos ni una utilización exhaustiva de cada herramienta.

## Dependencias y trazabilidad

Las implementaciones utilizan npm, sus manifiestos y archivos de bloqueo para mantener versiones reproducibles. Las nuevas dependencias se evalúan por necesidad, compatibilidad y complejidad añadida.

Git y los PR permiten revisar cambios y su contexto. Las decisiones relevantes se explican en la documentación y en las descripciones de los cambios, sin atribuir métricas de proceso que no estén respaldadas.

## Cierre

Los resultados de validación del producto se registran en el [README principal](../README.md) y en la [estrategia técnica](./estrategia-tecnica.md). Corresponden al estado validado al cierre y se distinguen de los acuerdos metodológicos iniciales.
