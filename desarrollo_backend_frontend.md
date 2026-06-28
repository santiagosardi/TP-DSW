# Desarrollo: Setup de Backend y Frontend

## Índice
1. [Creación de repositorios](#1-creación-de-repositorios)
2. [Setup del Backend](#2-setup-del-backend)
3. [Setup del Frontend](#3-setup-del-frontend)
4. [Estrategia de ramas](#4-estrategia-de-ramas)

---

## 1. Creación de repositorios

Se crearon dos repositorios en GitHub, uno para cada parte de la aplicación:

- `mygamesearcher-backend`
- `mygamesearcher-frontend`

La separación en dos repos responde al requisito de la cátedra de tener Frontend y Backend como aplicaciones agnósticas entre sí, comunicadas únicamente a través de una API.

---

## 2. Setup del Backend

### 2.1 Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/mygamesearcher-backend.git
cd mygamesearcher-backend
```

Clona el repo de GitHub a la máquina local y entra a la carpeta del proyecto.

### 2.2 Instalar el CLI de NestJS y crear el proyecto

```bash
npm i -g @nestjs/cli
nest new . --skip-git
```

- `npm i -g @nestjs/cli` — instala globalmente el CLI de NestJS, que permite usar el comando `nest` desde cualquier terminal.
- `nest new . --skip-git` — genera la estructura base del proyecto NestJS en la carpeta actual. El flag `--skip-git` evita que cree un repositorio git nuevo, ya que el repo fue clonado de GitHub.
- Se eligió `npm` como package manager cuando lo solicitó el CLI.

> **Nota:** el comando generó un conflicto con el `README.md` que GitHub crea automáticamente al crear el repo. Se eliminó ese archivo con `del README.md` y se volvió a correr el comando.

### 2.3 Instalar dependencias

```bash
npm install @nestjs/typeorm typeorm pg @nestjs/config class-validator class-transformer
```

| Paquete | Para qué sirve |
|:-|:-|
| `@nestjs/typeorm` + `typeorm` | ORM que permite interactuar con la base de datos usando clases TypeScript en lugar de SQL crudo |
| `pg` | Driver de PostgreSQL para Node.js, requerido por TypeORM para conectarse a la BD |
| `@nestjs/config` | Manejo de variables de entorno a través del archivo `.env` |
| `class-validator` + `class-transformer` | Validación de los datos que ingresan por la API (campos requeridos, tipos, formatos, etc.) |

### 2.4 Crear el archivo `.env`

```bash
New-Item .env
```

Archivo de variables de entorno con la configuración local de la base de datos. **No se sube al repositorio.**

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASS=tu_password
DB_NAME=mygamesearcher
PORT=3000
```

### 2.5 Crear el archivo `.env.example`

```bash
New-Item .env.example
```

Versión del `.env` sin valores reales. **Sí se sube al repositorio** para que los demás integrantes sepan qué variables necesitan configurar en su entorno local.

```env
DB_HOST=
DB_PORT=
DB_USER=
DB_PASS=
DB_NAME=
PORT=
```

### 2.6 Crear el archivo `.gitignore`

```bash
New-Item .gitignore
```

Indica a git qué archivos y carpetas no deben subirse al repositorio.

```
node_modules
dist
.env
```

- `node_modules` — carpeta con todas las dependencias instaladas, muy pesada y se regenera con `npm install`
- `dist` — carpeta con el código compilado, se genera al buildear
- `.env` — contiene credenciales y configuración local, nunca debe subirse

### 2.7 Crear la carpeta de documentación

```bash
mkdir docs
New-Item docs/README.md
```

Crea la carpeta `/docs` requerida por la cátedra para alojar toda la documentación del proyecto.

### 2.8 Actualizar el README.md raíz

Se reemplazó el contenido del `README.md` de la raíz con las instrucciones básicas de instalación:

```markdown
# MyGameSearcher - Backend

[Documentación](./docs/README.md)

## Instalación
1. Clonar el repo
2. `npm install`
3. Crear `.env` en base a `.env.example`
4. `npm run start:dev`
```

### 2.9 Primer commit y push

```bash
git add .
git commit -m "feat: initial NestJS project setup"
git push origin main
```

- `git add .` — agrega todos los archivos modificados/creados al staging area
- `git commit -m "..."` — guarda los cambios con un mensaje descriptivo
- `git push origin main` — sube los cambios a la rama `main` del repo remoto en GitHub

### 2.10 Crear la rama dev

```bash
git checkout -b dev
git push origin dev
```

- `git checkout -b dev` — crea y cambia a una nueva rama llamada `dev`
- `git push origin dev` — sube la rama al repo remoto

---

## 3. Setup del Frontend

### 3.1 Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/mygamesearcher-frontend.git
cd mygamesearcher-frontend
```

### 3.2 Crear el proyecto React con Vite

```bash
npm create vite@latest . -- --template react-ts
```

- **Vite** es una herramienta de desarrollo frontend muy rápida para crear y correr proyectos.
- El flag `--template react-ts` indica que el proyecto usará React con TypeScript.
- El `.` crea el proyecto en la carpeta actual.
- Se eligió **Oxlint** como linter (opción por defecto de Vite).

### 3.3 Instalar dependencias base

```bash
npm install
```

Instala todas las dependencias que Vite configuró automáticamente en el `package.json`. Siempre se corre después de crear o clonar un proyecto.

### 3.4 Instalar dependencias adicionales

```bash
npm install axios react-router-dom
```

| Paquete | Para qué sirve |
|:-|:-|
| `axios` | Cliente HTTP para hacer llamadas a la API del backend |
| `react-router-dom` | Manejo de rutas en el frontend (cada pantalla tiene su propia URL) |

### 3.5 Crear el archivo `.env`

```bash
New-Item .env
```

```env
VITE_API_URL=http://localhost:3000
```

Define la URL base del backend. Cuando el frontend necesite hacer una request, usará esta variable para saber a dónde apuntar. El prefijo `VITE_` es obligatorio para que Vite exponga la variable al código del proyecto.

### 3.6 Crear el archivo `.env.example`

```bash
New-Item .env.example
```

```env
VITE_API_URL=
```

### 3.7 Actualizar el `.gitignore`

Vite genera un `.gitignore` automáticamente. Se verificó que contenga `.env` y se agregó manualmente ya que no estaba incluido.

### 3.8 Crear la carpeta de documentación

```bash
mkdir docs
New-Item docs/README.md
```

### 3.9 Actualizar el README.md raíz

```markdown
# MyGameSearcher - Frontend

[Documentación](./docs/README.md)

## Instalación
1. Clonar el repo
2. `npm install`
3. Crear `.env` en base a `.env.example`
4. `npm run dev`
```

### 3.10 Primer commit y push

```bash
git add .
git commit -m "feat: initial React + Vite project setup"
git push origin main
```

### 3.11 Crear la rama dev

```bash
git checkout -b dev
git push origin dev
```

---

## 4. Estrategia de ramas

Ambos repositorios siguen la misma estructura de ramas:

| Rama | Uso |
|:-|:-|
| `main` | Versión estable del proyecto. Solo recibe merges desde `dev` cuando hay una versión funcional |
| `dev` | Rama de integración. Las features terminadas se mergean acá |
| `feature/nombre` | Una rama por cada feature nueva. Se crea desde `dev` y se mergea de vuelta a `dev` vía PR |

**Flujo de trabajo diario:**

```bash
# Arrancar una feature nueva
git checkout dev
git pull origin dev
git checkout -b feature/nombre-de-la-feature

# ... desarrollar ...

git add .
git commit -m "feat: descripción de lo que hice"
git push origin feature/nombre-de-la-feature

# Después abrir un Pull Request en GitHub: feature/... → dev
```

Esto permite que los docentes puedan ver el historial de PRs y evaluar la participación de cada integrante.
