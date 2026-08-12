
# Estrategia técnica

Nota:
Las decisiones marcadas como "Recomendación" representan propuestas técnicas evaluadas durante la planificación del proyecto. Podrán ser ajustadas luego de profundizar el conocimiento de las tecnologías involucradas, realizar pruebas de implementación y validar su adecuación durante el desarrollo.
## Backend

### Framework
Decisión:
NestJS

Motivo:
Se utilizará NestJS por ser un framework basado en Node.js orientado al desarrollo de aplicaciones backend estructuradas. Proporciona herramientas para la construcción de APIs, organización modular y separación de responsabilidades, facilitando la implementación de una arquitectura mantenible.

Además, su integración con TypeScript permite incorporar tipado estático y mejores herramientas de desarrollo, manteniendo compatibilidad con el ecosistema JavaScript requerido por la cátedra.

Criterio:
Se prioriza un framework que permita cumplir los requisitos técnicos del backend, facilite la organización del código y proporcione herramientas integradas para validación, testing y construcción de APIs.

### Comunicación Backend - Frontend

Decisión:
Comunicación mediante API REST utilizando JSON sobre HTTP. (Recomendación)

Motivo:
REST permite mantener desacoplados frontend y backend, estableciendo un contrato de comunicación independiente de la implementación interna de cada parte.

Este contrato define recursos, operaciones HTTP, formatos JSON de intercambio y códigos de respuesta, permitiendo que ambas aplicaciones evolucionen de manera independiente siempre que respeten la interfaz definida.

Además, es compatible con las tecnologías seleccionadas (NestJS y React) y cumple con el requisito de la cátedra de desarrollar frontend y backend como partes agnósticas entre sí comunicadas mediante una API.

### Persistencia

#### Base de datos (relacional)

Decisión:
MySQL

Alternativas evaluadas:
- MySQL
- PostgreSQL

Motivo:
Se utilizará MySQL debido a que permite implementar una persistencia relacional adecuada para el modelo del sistema, soportando relaciones entre entidades, restricciones de integridad y operaciones necesarias para la aplicación.

Además, cuenta con herramientas ORM compatibles con el ecosistema Node.js y NestJS, permitiendo separar la lógica de negocio del acceso a datos.

La experiencia previa del equipo utilizando esta tecnología permite reducir la curva de aprendizaje y disminuir riesgos durante el desarrollo, pudiendo concentrar esfuerzos en la construcción de las funcionalidades del sistema.

La base de datos será utilizada como un servicio externo con persistencia en disco, cumpliendo los requisitos de la cátedra. Esto permite soportar acceso concurrente de usuarios y evita depender de soluciones embebidas.

Criterio:
Se prioriza una tecnología conocida por el equipo que permita aplicar correctamente conceptos de modelado relacional, persistencia y arquitectura backend.

#### ORM

Alternativas evaluadas :
- TypeORM
- Prisma
- MikroORM

Decisión:
Prisma (Recomendación)

Motivo:
Prisma permite implementar la persistencia mediante un ORM, cumpliendo con el requisito de la cátedra de utilizar un mapper para acceder a la base de datos.

Proporciona una capa de acceso a datos tipada, basada en un esquema declarativo, que facilita la comunicación entre la aplicación y la base de datos relacional.

Será utilizado como mecanismo de persistencia dentro de la capa de acceso a datos, evitando que los servicios de negocio dependan directamente de detalles específicos del motor de base de datos.

Además, posee integración con aplicaciones desarrolladas en Node.js y permite trabajar con relaciones entre entidades, operaciones CRUD y una estructura compatible con una arquitectura por capas.

Criterio:
Se prioriza una herramienta que permita aplicar correctamente los conceptos de persistencia y arquitectura por capas, considerando:
- compatibilidad con bases de datos relacionales;
- soporte de relaciones entre entidades;
- integración con NestJS;
- facilidad de mantenimiento y claridad del código.

#### Validación y manejo de errores 

##### Validación de entrada

Alternativas evaluadas:
- Validación manual dentro de Services.
- DTOs con class-validator y ValidationPipe de NestJS.
- Validación mediante esquemas externos.

Decisión:
DTOs con class-validator utilizando ValidationPipe de NestJS. (Recomendación)

Motivo:
Permite validar la estructura y formato de los datos recibidos por la API antes de ejecutar la lógica de negocio, utilizando mecanismos integrados de NestJS.

Los DTOs permiten definir los contratos de entrada del sistema, mientras que ValidationPipe automatiza la aplicación de dichas reglas de validación.

Esta validación se complementará con las validaciones propias de la lógica de negocio dentro de los Services, evitando mezclar responsabilidades entre capas.

Criterio:
Se prioriza una solución declarativa, mantenible e integrada con NestJS.

##### Manejo de errores

Alternativas evaluadas:
- Errores simples mediante Error estándar.
- Excepciones HTTP nativas de NestJS.
- Exception Filters personalizados.

Decisión propuesta:
Uso de excepciones HTTP nativas de NestJS. (Recomendación)

Motivo:
Las excepciones HTTP nativas de NestJS permiten representar errores de la API mediante códigos de estado HTTP adecuados y respuestas consistentes.

Esto facilita que el frontend pueda interpretar los resultados de las operaciones y mostrar información apropiada al usuario.

Los casos que requieran comportamientos más específicos podrán extenderse posteriormente mediante Exception Filters personalizados.

Criterio:
Se prioriza una solución integrada con NestJS, simple de mantener y suficiente para cumplir los requisitos del proyecto.

### Testing Backend

#### Herramienta

Alternativas evaluadas:
- Jest
- Vitest
- Mocha + Chai

Decisión:
Jest (Recomendación)

Motivo:
Jest posee integración con NestJS y TypeScript, permitiendo implementar pruebas unitarias y de integración con una configuración simple.

Además, cuenta con herramientas para ejecutar pruebas automatizadas, generar resultados reproducibles y mantener los tests integrados dentro del flujo de desarrollo del proyecto.

Criterio:
Se prioriza una herramienta compatible con el ecosistema seleccionado que facilite la implementación, ejecución y mantenimiento de pruebas automatizadas.

#### Estrategia de testing

Decisión:
Implementar pruebas automatizadas unitarias e integración sobre funcionalidades relevantes del backend. (Recomendación)

Las pruebas unitarias estarán orientadas a validar comportamientos aislados de componentes del backend, especialmente la lógica implementada en los Services.

Además, se implementará al menos un test de integración que valide la interacción entre distintas capas del sistema mediante la API.

Los tests serán ejecutados mediante scripts definidos en package.json, permitiendo reproducir la ejecución del entorno de desarrollo.

Criterio:
Se busca validar tanto el comportamiento aislado de componentes como la interacción entre las distintas capas del backend.

### Autenticación y autorización

#### Autenticación

Alternativas evaluadas:

- JWT con autenticación propia.
- OAuth mediante proveedor externo.
- Sesiones tradicionales.

Decisión:  
JWT con autenticación propia. (Recomendación)

Motivo:
JWT permite implementar autenticación basada en tokens dentro de una arquitectura API REST, manteniendo desacoplados frontend y backend.

El proceso de autenticación consistirá en validar las credenciales del usuario y emitir un token JWT que será enviado en solicitudes posteriores para identificar al usuario autenticado.

Esta alternativa se integra adecuadamente con NestJS y resulta suficiente para el alcance del sistema.

Criterio:  
Se prioriza una solución estándar, integrada con las tecnologías seleccionadas y suficiente para cumplir los requisitos del proyecto.

#### Autorización

Alternativas evaluadas:
- Roles simples asociados a Usuario.
- Sistema separado de roles y permisos.

Decisión:  
Sistema de autorización basado en roles simples asociados al usuario. (Recomendación)

Inicialmente no se implementará un sistema granular de permisos, debido al alcance del sistema. La autorización se resolverá mediante roles asociados al usuario.

Roles considerados:
- Usuario.
- Administrador.
Estos roles representan niveles de acceso generales del sistema y no permisos específicos sobre cada operación.

Motivo:
El uso de roles asociados al usuario permite definir diferentes niveles de acceso sin incorporar complejidad innecesaria mediante un sistema granular de permisos.

Los roles serán utilizados para restringir funcionalidades del sistema según el nivel de acceso requerido. La protección de rutas se implementará mediante mecanismos de autorización provistos por NestJS.

Este enfoque resulta suficiente para cumplir con los requisitos del proyecto y permite extender el modelo en caso de ser necesario.

Criterio:  
Se prioriza una solución sencilla y extensible, evitando agregar complejidad innecesaria.

### Documentación y configuración

#### Documentación de API

Alternativas evaluadas:
- Swagger/OpenAPI.
- Documentación manual mediante Markdown.

Decisión:
Swagger/OpenAPI utilizando integración con NestJS. (Recomendación)

Motivo:
Swagger/OpenAPI permite documentar la API REST mediante una especificación estándar, describiendo endpoints, parámetros, estructuras de datos y respuestas esperadas.

Su integración con NestJS facilita mantener la documentación cercana a la implementación del backend y permite que frontend y backend compartan una referencia común sobre el contrato de comunicación.

Criterio:
Se prioriza una herramienta estándar, compatible con NestJS y que facilite la comunicación entre los integrantes del equipo durante el desarrollo.

#### Configuración de ambientes

Alternativas evaluadas:
- Configuración mediante archivos `.env`.
- Configuración fija dentro del código.

Decisión:
Variables de entorno mediante `.env` utilizando el módulo de configuración de NestJS. (Recomendación)

Motivo:
Permite separar la configuración específica de cada ambiente de la lógica de aplicación, facilitando ejecutar el sistema en desarrollo, pruebas y producción con diferentes valores.

Además, evita almacenar información sensible dentro del código fuente y permite mantener una configuración reproducible mediante archivos de ejemplo y variables documentadas.

Consideraciones:
Los archivos con valores sensibles no serán incluidos en el repositorio. Se mantendrá un archivo `.env.example` con las variables necesarias para configurar el proyecto.

Criterio:
Se prioriza una solución mantenible y alineada con buenas prácticas de desarrollo backend.

## Infraestructura

### Deploy

Alternativas evaluadas:
- Plataformas cloud.
- Servidores propios.

Decisión:
Pendiente de definición.

Motivo:
El despliegue será definido durante etapas posteriores del desarrollo, considerando los requerimientos finales de la aplicación, disponibilidad de servicios y facilidad de mantenimiento.

Criterio:
Se priorizará una solución que permita ejecutar frontend, backend y base de datos de forma independiente, manteniendo la separación definida en la arquitectura.

## Frontend

### Framework

Alternativas evaluadas:
- React
- Angular

Decisión:
React (Recomendación)

Motivo:
React permite construir interfaces web mediante componentes reutilizables, facilitando la organización modular de la aplicación y la separación de responsabilidades dentro del frontend.

La utilización de TypeScript permite definir modelos y tipos de datos utilizados por la aplicación, mejorando la mantenibilidad y reduciendo errores durante el desarrollo.

Además, React permite implementar los requisitos del trabajo práctico relacionados con componentes, manejo de estado, eventos del usuario, comunicación entre componentes y consumo de APIs externas.

La experiencia previa del equipo y el material disponible durante la cursada permiten reducir la curva de aprendizaje y facilitar la implementación.

Criterio:
Se prioriza una tecnología que permita construir una interfaz modular, mantenible y compatible con los requisitos técnicos del trabajo práctico, considerando además la experiencia del equipo y el ecosistema disponible.

### Manejo de estado

Alternativas evaluadas:
- Estado local mediante hooks de React.
- Librerías externas de gestión de estado global.

Decisión:
Uso de hooks nativos de React para el manejo de estado. (Recomendación)

Motivo:
El alcance inicial del sistema no requiere una solución externa de gestión global de estado.

Los hooks provistos por React permiten manejar estados locales de componentes, efectos secundarios y lógica reutilizable, manteniendo una solución integrada con el framework y reduciendo complejidad innecesaria.

En caso de que el crecimiento de la aplicación requiera compartir estados complejos entre múltiples partes de la interfaz, podrá evaluarse la incorporación de una herramienta específica de gestión global.

Criterio:
Se prioriza una solución simple y suficiente para el alcance actual del sistema, manteniendo la posibilidad de evolución futura.

### Estilos y componentes visuales

#### Framework CSS

Alternativas evaluadas:

- Bootstrap
- Material UI (MUI)
- Tailwind CSS

Decisión:  
Bootstrap (Recomendación)

Motivo:
Bootstrap proporciona un conjunto de estilos, componentes reutilizables y un sistema de grillas responsive que facilita la construcción de interfaces consistentes y adaptables a diferentes tamaños de pantalla.

Su sistema de diseño permite aplicar una estrategia mobile-first, comenzando por estilos orientados a pantallas pequeñas y adaptando progresivamente la interfaz mediante breakpoints.

Además, su integración con React permite utilizar componentes visuales predefinidos o adaptarlos según las necesidades del sistema.

La experiencia previa del equipo con esta tecnología permite reducir la curva de aprendizaje y concentrar esfuerzos en la implementación de las funcionalidades del sistema.

Criterio:
Se prioriza una tecnología que facilite la construcción de una interfaz consistente, responsive y mantenible, permitiendo cumplir los requisitos de UX/UI, componentes visuales y estrategia mobile-first definidos por la cátedra.

### Testing Frontend

#### Herramienta

Alternativas evaluadas:
- Vitest
- Jest
- React Testing Library

Decisión:
Vitest + React Testing Library (Recomendación)

Motivo:
React Testing Library permite probar componentes desde la perspectiva del comportamiento esperado del usuario, evitando acoplar las pruebas a detalles internos de implementación.

Vitest proporciona una herramienta de ejecución de pruebas compatible con proyectos modernos basados en TypeScript y permite integrarse fácilmente con el ecosistema frontend.

Esta combinación permite implementar pruebas unitarias de componentes y mantener las pruebas integradas dentro del flujo de desarrollo.

Criterio:
Se prioriza una estrategia de testing orientada al comportamiento de la interfaz y compatible con las tecnologías seleccionadas.