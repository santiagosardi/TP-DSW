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

Las Issues podrán organizarse mediante **Labels** para agrupar funcionalidades relacionadas y mediante **Milestones** para representar los objetivos de cada iteración.

El seguimiento general del proyecto se realizará utilizando **GitHub Projects**.

---

# Flujo de trabajo con Git

La rama `main` contendrá únicamente versiones estables del proyecto.

Cada nueva funcionalidad, mejora o corrección se desarrollará en una rama independiente creada a partir de `main`, siguiendo una convención de nombres descriptiva, por ejemplo:

- `feature/crud-juego`
- `feature/crud-usuario`
- `feature/recomendaciones`
- `fix/validacion-email`

Una vez finalizado el desarrollo de una tarea, los cambios se integrarán mediante una **Pull Request**, la cual permitirá revisar el código antes de incorporarlo a la rama principal.

No se realizarán modificaciones directamente sobre la rama `main`.

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
