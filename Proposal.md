## Trabajo Practico Desarrollo de Software 2026

### Grupo
#### Integrantes

* 53725 - Sardi Nieva, Santiago
* 52158 - Ripacolli Fuentes, Santino Jorge
* 54191 - Petazzi Cardetti, Juan Cruz

### Repositorios
* [frontend app](http://hyperlinkToGihubOrGitlab)
* [backend app](http://hyperlinkToGihubOrGitlab)
*Nota*: si utiliza un monorepo indicar un solo link con fullstack app.

### Buscador de juegos en base a gustos
#### Descripción
* My Game Searcher es una aplicación orientada a usuarios que utilizan los videojuegos como medio de entretenimiento pero no saben qué jugar. El sistema permite ingresar información básica, como los géneros y caracteristicas de juegos preferidos (Historia, RPG, Competitivo, etc) y el dispositivo utilizado (por ejemplo, PC o consola), y a partir de estos datos genera entre 1 y 3 recomendaciones de videojuegos adaptadas a las preferencias del usuario. El objetivo principal del sistema es facilitar la toma de decisión del usuario, ofreciendo sugerencias personalizadas en base a sus gustos y limitaciones tecnológicas.

### Modelo

....

### Alcance Funcional 

El sistema permite a los usuarios interactuar con una plataforma de recomendación de videojuegos, brindando funcionalidades orientadas a la carga de datos, gestión de preferencias y obtención de recomendaciones personalizadas.

|nro|Funcion|
|:-|:-|
|1|Registrar, modificar y eliminar videojuegos|
|2|Registrar y gestionar usuarios dentro del sistema|
|3|Clasificar los videojuegos según género y plataforma|
|4|Visualizar listados de videojuegos filtrados según distintos criterios|
|5|Consultar el detalle completo de cada videojuego|
|6|Generar recomendaciones personalizadas en base a los gustos del usuario y su plataforma|

### Alcance Mínimo

|Req|Detalle|
|CRUD Simple|1. Caracteristicas <br>. Plataforma <br>. Juego|



## Alcance Funcional 

### Alcance Mínimo


Regularidad:
|Req|Detalle|
|:-|:-|
|CRUD simple|1. CRUD Genero<br>2. CRUD Plataforma<br>3. CRUD Caracteristica|
|CRUD dependiente|1. CRUD Juego {depende de} CRUD Genero, CRUD Plataforma<br>2. CRUD Usuario {depende de} CRUD Plataforma|
|Listado<br>+<br>detalle| 1. Listado de juegos filtrado por género y plataforma, muestra nombre, género y plataforma => detalle muestra datos completos del juego<br> 2. Listado de recomendaciones del usuario filtrado por fecha, muestra nombre del juego, géneros y plataforma recomendada => detalle muestra la búsqueda realizada y los juegos sugeridos|
|CUU/Epic|1. Registrar usuario y configurar preferencias<br>2. Generar recomendaciones personalizadas de juegos|


Adicionales para Aprobación
|Req|Detalle|
|:-|:-|
|CRUD |1. CRUD Genero<br>2. CRUD Plataforma<br>3. CRUD Caracteristica<br>4. CRUD Juego<br>5. CRUD Usuario|
|CUU/Epic|1. Registrar usuario y configurar preferencias<br>2. Generar recomendaciones personalizadas de juegos<br>3. Administrar catálogo de juegos (carga y edición por admin)|


### Alcance Adicional Voluntario

*Nota*: El Alcance Adicional Voluntario es opcional, pero ayuda a que la funcionalidad del sistema esté completa y será considerado en la nota en función de su complejidad y esfuerzo.

|Req|Detalle|
|:-|:-|
|Listados |1. Juegos más recomendados filtrado por género, muestra nombre, plataforma y cantidad de veces recomendado <br>2.  Historial de búsquedas del usuario, muestra fecha, preferencias ingresadas y juegos sugeridos|
|CUU/Epic|1. Marcar juego como "ya jugado" o "me interesa"<br>2. Calificar una recomendación recibida|
|Otros|1. Envío de recomendación por email al usuario|



