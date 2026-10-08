# Propuesta inicial

Este documento conserva el propósito y el alcance planteados al comienzo del TP DSW 2026 y los distingue del resultado finalmente entregado.

## Motivación y problema

La propuesta inicial, denominada «DGame», buscaba asistir a quienes tienen muchas opciones de videojuegos y necesitan elegir qué jugar según sus preferencias, necesidades y disponibilidad, tanto individualmente como en grupo. La intención era reducir la dificultad de selección y organizar los juegos de interés.

## Alcance originalmente pensado

| Área | Propuesta inicial |
| --- | --- |
| CRUD simples | Usuario, Característica, Plataforma y Género |
| CRUD dependientes | Juego relacionado con géneros, plataformas y características; Colección asociada a Usuario |
| Listado y detalle | Búsqueda de juegos por nombre y consulta del detalle; listado de recomendaciones personalizadas |
| Casos de uso principales | Administrar biblioteca personal, generar recomendaciones y administrar colecciones |
| Ampliación prevista | Consultar un historial persistido de recomendaciones |
| Ideas voluntarias | Estadísticas personales, juegos recomendados más populares, valoración de recomendaciones y exportación PDF |

El historial persistido, las estadísticas adicionales, la valoración de recomendaciones y la exportación PDF **no se implementaron**. Se conservan aquí exclusivamente como ideas del alcance inicial.

El diseño evolucionó durante el desarrollo a partir de los modelos iniciales hasta el sistema finalmente implementado.

# Resultado final del proyecto

## Producto y equipo

El producto final se denomina **MyGameSearcher**. Permite descubrir videojuegos, organizar biblioteca y colecciones personales y obtener recomendaciones explicables.

Integrantes finales de la entrega:

- Santiago Sardi
- Santino Ripacolli

## Alcance implementado

- Registro, login, autenticación JWT y roles USER/ADMIN.
- Catálogo con búsqueda, filtros y detalle de juegos.
- Biblioteca personal con estados y favoritos.
- Colecciones personales.
- Recomendaciones calculadas dinámicamente, sin IA ni historial persistido.
- Administración protegida de juegos, géneros, plataformas y características.
- Interfaz responsive y despliegue online.

El catálogo final contiene 147 juegos, 13 géneros, 6 plataformas y 15 características. La recomendación utiliza coincidencias de géneros (+3), características (+2) y plataformas (+1), ponderadas por las preferencias, con mayor peso para favoritos y una explicación del resultado.

## Modelos finales

Los siguientes diagramas representan el diseño final documentado:

- [Modelo de dominio final](./ModeloDominio_DGame.png)
- [Modelo entidad-relación final](./Modelo_Entidad_Relacion.png)

## Implementación y entrega

La solución utiliza React/Vercel, NestJS/Render y MySQL/Aiven. El frontend se comunica mediante HTTPS, REST y JWT; el backend accede a la base mediante MikroORM y SSL.

- [Repositorio frontend](https://github.com/santiagosardi/mygamesearcher-frontend)
- [Repositorio backend](https://github.com/santiagosardi/mygamesearcher-backend)
- [Aplicación desplegada](https://mygamesearcher-frontend-fawn.vercel.app)
- [Backend desplegado](https://mygamesearcher-backend.onrender.com)

La [presentación del proyecto](./README.md) reúne las tecnologías, los resultados de testing al cierre y los enlaces de documentación. Este repositorio conserva la documentación académica; el código reside en los dos repositorios de implementación.
