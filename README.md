
# Project Title
## 📦 Framework MVC en PHP – Guía de Uso

Este framework MVC en PHP está pensado como base para desarrollar aplicaciones web utilizando:

PHP orientado a objetos

Patrón MVC

Autoload con Composer

Middleware de sesión

ORM Eloquent

### El objetivo es clonar el framework y adaptarlo fácilmente a cualquier proyecto.

🧱 Requisitos

PHP ≥ 8.0

Composer

Servidor web (Apache recomendado)

MySQL / MariaDB

## 🚀 Pasos para iniciar un nuevo proyecto
### 1️⃣ Clonar el framework
```
git clone https://github.com/tu-repo/framework-mvc.git project-name
cd project-name
```
### 2️⃣ Configurar el archivo config.php

Editar el fichero:

/config/config.php


Modificar los datos de conexión a la base de datos:
```
define('DB_DRIVER', 'mysql');
define('DB_HOST', 'localhost');
define('DB_NAME', 'projectgest');
define('DB_USER', 'root');
define('DB_PASS', '');
define(constant_name: 'BASE_URL', '/tu_proyecto/');  
```

📌 Este archivo es específico de cada proyecto.

### 3️⃣ Configurar composer.json

Editar el fichero composer.json y cambiar:
```
{
  "name": "tu-usuario/projectgest",
  "description": "Aplicación de gestión de proyectos",
  "autoload": {
    "psr-4": {
      "App\\": "src/",
      "Core\\": "core/"
    }
  },
  "require": {
    "illuminate/database": "^10.0"
  }
}
```

🔹 Cambiar:
```
name
description
```

### 4️⃣ Instalar dependencias

Ejecutar:
```
composer install
```

Esto:

1.Instala Eloquent

2.Genera la carpeta vendor/

3.Genera el autoload


## 🧭 Estructura del Framework

/public

     ├── index.php

     └── .htaccess

/core

     ├── Router.php
     ├── Controller.php
     └── Middleware.php

/src

    ├── Controllers
    ├── Models
    └── Views

/config

    └── database.php

config.php

## 🔐 Middleware y Autenticación

El framework incluye un Middleware de sesión que controla el acceso a las rutas.

## 🔓 Controladores públicos por defecto

Actualmente, el framework permite acceso sin autenticación a:

HomeController

AuthController

Esto permite:

* Landing pública

* Login

* Registro

Tambien se puede habilitar el acceso a nivel de métodos del controlador

## 🔒 Controladores protegidos

Cualquier otro controlador requiere sesión activa.

Si un usuario intenta acceder sin estar autenticado:

Será redirigido a la ruta raíz /

## 🛠️ Cambiar controladores públicos

Para modificar qué controladores son públicos, editar:

/core/Middleware.php


Ejemplo:
```
$publicControllers = [
    'HomeController',
    'AuthController'
];
```

Añade o elimina controladores según las necesidades del proyecto.

## 🧩 Crear una nueva aplicación

Una vez configurado el framework:

### 1️⃣ Crear los modelos
/src/Models

Ejemplo:
```
class Project extends Model {}
```

### 2️⃣ Crear los controladores
/src/Controllers

Ejemplo:
```
class ProjectController extends Controller {}
```

### 3️⃣ Crear las vistas
/src/Views

Organizadas por carpetas según el controlador.

### 🧠 Convenciones importantes

* Controladores terminan en Controller
* Métodos por defecto: index()
* Tablas en plural (Eloquent)
* Clave primaria: id (aunque se puede poner otra (Eloquent))

Campos: (Gestionados por Eloquent)
```
created_at
updated_at
``
## ⚠️ Errores comunes

* ❌ No ejecutar composer install
* ❌ No configurar config.php
* ❌ No respetar convenciones de Eloquent

## 📚 Filosofía del Framework

Este framework está pensado para:

* Aprender MVC
* Entender cómo funcionan frameworks reales
* Usarse como base para proyectos pequeños y medianos
```
“Primero entiendes el framework, luego usas Laravel.”
```
