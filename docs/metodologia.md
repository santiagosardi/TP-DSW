# Metodología de Trabajo

## Objetivo

El presente documento establece la metodología de trabajo acordada por el equipo para el desarrollo del proyecto. Su propósito es definir un proceso común de organización, desarrollo y seguimiento que facilite la coordinación entre los integrantes, promueva la calidad del software y permita avanzar de forma ordenada e incremental.

---

# Metodología de desarrollo

El proyecto se desarrollará siguiendo un enfoque **iterativo e incremental**, inspirado en los principios de **Scrum** y del **Unified Process (UP)**.

El desarrollo se organizará en iteraciones de aproximadamente dos semanas. Al finalizar cada iteración se espera obtener un incremento funcional del sistema, incorporando nuevas capacidades o mejorando las existentes.

La planificación podrá ajustarse durante el desarrollo en función del avance del proyecto, los cambios de alcance o las dificultades técnicas que surjan.

---

# Organización del equipo

Todos los integrantes participarán activamente en el análisis, diseño, implementación y validación del sistema.

Las responsabilidades de planificación, seguimiento, desarrollo y revisión del código serán compartidas por el equipo, procurando una distribución equilibrada de las tareas y fomentando la colaboración entre sus integrantes.

Las decisiones técnicas relevantes se consensuarán entre todos los miembros del equipo.

---

# Herramientas de trabajo

Se utilizarán las siguientes herramientas durante el desarrollo del proyecto:

| Herramienta          | Propósito                                                           |
| -------------------- | ------------------------------------------------------------------- |
| Git                  | Control de versiones                                                |
| GitHub               | Repositorio del proyecto                                            |
| GitHub Projects      | Gestión y seguimiento de tareas                                     |
| GitHub Issues        | Registro y planificación de funcionalidades, mejoras y correcciones |
| GitHub Pull Requests | Revisión e integración de cambios                                   |
| WhatsApp             | Comunicación cotidiana del equipo                                   |

---

# Reuniones

El equipo realizará una reunión semanal para revisar el estado del proyecto, analizar el avance de las tareas en curso, resolver inconvenientes y acordar los objetivos de la siguiente iteración.

En caso de ser necesario, podrán realizarse reuniones adicionales para coordinar actividades específicas o resolver bloqueos que afecten el desarrollo.

---

# Gestión de tareas

Las funcionalidades, mejoras y correcciones se administrarán mediante **GitHub Issues**.

Cada Issue representará una unidad de trabajo concreta y contendrá, cuando corresponda:

- descripción de la tarea;
- criterios de finalización;
- responsable asignado;
- estado de avance.

Las Issues podrán organizarse mediante Labels para clasificarlas y mediante Milestones para representar entregas u objetivos importantes del proyecto.

El seguimiento general del proyecto se realizará utilizando **GitHub Projects**.

---

# Control de versiones

El proyecto utilizará Git como sistema de control de versiones y GitHub como plataforma de almacenamiento y colaboración.

El objetivo es mantener un historial claro del desarrollo, permitir la colaboración entre integrantes y asegurar la trazabilidad de los cambios realizados.

## Organización de ramas

La rama `main` contendrá únicamente versiones estables del sistema.

Cada nueva funcionalidad, mejora o corrección se desarrollará en una rama independiente creada a partir de `main`.

Las ramas seguirán una convención descriptiva:

- `feature/nombre-funcionalidad`
- `fix/nombre-correccion`
- `docs/nombre-documentacion`

Ejemplos:

- `feature/crud-juego`
- `feature/recomendaciones`
- `fix/validacion-email`

## Pull Requests

Los cambios no se integrarán directamente sobre `main`.

Una vez finalizada una tarea, se realizará una Pull Request para revisar los cambios antes de incorporarlos a la rama principal.

Cada Pull Request deberá:

- describir los cambios realizados;
- relacionarse con la Issue correspondiente;
- permitir revisar el código antes de integrarlo.

## Commits

Los commits deberán representar cambios concretos y mantener una descripción clara del objetivo realizado.

Se evitarán commits demasiado grandes que mezclen múltiples funcionalidades diferentes.

Ejemplos:

- `Agregar entidad Juego`
- `Implementar endpoint POST juegos`
- `Corregir validación de usuario`

---

# Gestión de dependencias

Las dependencias del proyecto serán administradas mediante los gestores
correspondientes a cada tecnología utilizada.

En el backend se utilizará el gestor de paquetes de Node.js mediante
el archivo `package.json`, donde se registrarán las dependencias necesarias
para ejecución, desarrollo y testing.

Las versiones de las dependencias serán controladas mediante el archivo
de bloqueo generado por el gestor de paquetes (`package-lock.json`),
permitiendo reproducir el entorno de desarrollo entre los integrantes
del equipo.

La incorporación de nuevas dependencias deberá evaluarse previamente,
considerando:

- necesidad real dentro del proyecto;
- compatibilidad con las tecnologías existentes;
- mantenimiento y soporte de la herramienta;
- impacto sobre la complejidad del sistema.

---

# Definición de Terminado (Definition of Done)

Una tarea se considerará finalizada cuando cumpla, como mínimo, las siguientes condiciones:

- la funcionalidad implementada cumple con los requisitos definidos;
- el código compila y funciona correctamente;
- no introduce errores conocidos en funcionalidades existentes;
- los cambios fueron integrados mediante una Pull Request;
- la Issue correspondiente puede cerrarse.

---

# Comunicación

La comunicación cotidiana del equipo se realizará mediante WhatsApp.

Las decisiones relevantes relacionadas con el desarrollo del proyecto quedarán registradas en GitHub mediante Issues, Pull Requests o documentación cuando resulte necesario.
