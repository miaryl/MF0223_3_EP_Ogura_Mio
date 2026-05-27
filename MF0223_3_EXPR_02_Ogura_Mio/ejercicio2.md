# EJERCICIO 2 — Administración de sistemas Linux y resolución de incidencias

Eres responsable de preparar la estructura de un entorno de desarrollo para un
equipo que trabaja en un proyecto web con frontend y backend.
Tu objetivo es configurar correctamente el entorno utilizando la terminal de Linux, gestionar
archivos y permisos, simular tareas reales de administración de sistemas y resolver incidencias
relacionadas con la organización del proyecto.

## 1. Estructura base del proyecto 

### 1.1 Crea una carpeta llamada dev_environment.

```bash
mkdir dev_environment
```

### 1.2. Dentro de ella, crea la siguiente estructura de directorios utilizando una única instrucción:

```
frontend/
├── public/
├── src/
│ ├── components/
│ ├── pages/
│ └── styles/
backend/
├── app/
├── config/
└── tests/
database/
└── migrations/
docs/
scripts/
```

```
mkdir -p frontend/public \
         frontend/src/components \
         frontend/src/pages \
         frontend/src/styles \
         backend/app \
         backend/config \
         backend/tests \
         database/migrations \
         docs \
         scripts
```

## 2. Inicialización de archivos / Inicialització de fitxers

Crea los siguientes archivos en las rutas indicadas:

### 2.1. Frontend

- index.html → frontend/public/
- App.js → frontend/src/
- main.css → frontend/src/styles/

```
touch frontend/public/index.html frontend/src/App.js frontend/src/styles/main.css
```

### 2.2. Backend

- server.js → backend/app/
- config.json → backend/config/
  
```
touch backend/app/server.js backend/config/config.json
```

### 2.3. General

- README.md → raíz del proyecto
- deploy.sh → scripts/

```
touch README.md scripts/deploy.sh
```
  
## 3. Contenido 

### 3.1. Instala el editor nano

```bash
apt update
apt install -y nano tree
```

### 3.2.Edita los archivos index.html, App.js y main.css utilizando Nano (El contenido no será evaluado)

```bash
nano frontend/public/index.html
nano frontend/src/App.js
nano frontend/src/styles/main.css
```
GUARDAR: `Ctl + O`

CERRAR: `Ctl + X`


## 4. Verificación y auditoría / Verificació i auditoria

### 4.1. Muestra el contenido del proyecto

`ls`

### 4.2.Muestra todos los archivos (incluidos ocultos) con detalle

`ls -l -h -a`

### 4.3.Muestra el contenido de frontend/src/

`ls frontend/src/`

## 5. Gestión de versiones 

### 5.1.Crea una carpeta backup/

`mkdir backup`

### 5.2.Copia completamente frontend/ dentro de backup/

`cp -r frontend backup/`

### 5.3.Copia server.js como server_backup.js dentro de backup/

`cp backend/app/server.js backup/server_backup.js`

## 6. Reorganización del proyecto / Reorganització del projecte

### 6.1 Mueve main.css a frontend/public/

`mv frontend/src/styles/main.css frontend/public/`

### 6.2 Renombra App.js a app.js

`mv frontend/src/App.js frontend/src/app.js`

### 6.3 Mueve config.json a backend/app/

`mv backend/config/config.json backend/app/`

## 7. Permisos y seguridad 

**Configura:**

### 7.1 deploy.sh → ejecutable solo para el propietario

`chmod 700 scripts/deploy.sh`

### 7.2 server.js → lectura/escritura propietario, solo lectura grupo

`chmod 640 backend/app/server.js`

### 7.3 README.md → solo lectura para todos Verifica los permisos.

`chmod 444 README.md`

## 8. Simulación de error y recuperación 

### 8.1 Elimina frontend/src/components/

`rm -rf frontend/src/components/`

### 8.2 Recupérala desde backup/

`cp -r backup/frontend/src/components frontend/src/`

## 9. Limpieza y verificación final 

### 1. Elimina la carpeta temp/

`rm -rf temp/`

### 2. Elimina server_backup.js

`rm -f backup/server_backup.js`

### 3. Muestra la estructura completa del proyecto

```
root@f8b5efb046b7:/dev_environment# tree
.
|-- README.md
|-- backend
|   |-- app
|   |   |-- config.json
|   |   `-- server.js
|   |-- config
|   `-- tests
|-- backup
|   `-- frontend
|       |-- public
|       |   `-- index.html
|       `-- src
|           |-- App.js
|           |-- components
|           |-- pages
|           `-- styles
|               `-- main.css
|-- database
|   `-- migrations
|-- docs
|-- frontend
|   |-- public
|   |   |-- index.html
|   |   `-- main.css
|   `-- src
|       |-- app.js
|       |-- components
|       |-- pages
|       `-- styles
`-- scripts
    `-- deploy.sh

21 directories, 10 files
```

### 4. Muestra la ruta actual

`pwd`

### 5. Muestra el historial de comandos

`history`