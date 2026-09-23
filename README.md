# 🧪 Date Lab System - Backend (Appointment Lab API)

API RESTful de backend desarrollada en **Node.js**, **Express 5**, **Knex.js** y **Objection.js** sobre **PostgreSQL**, diseñada para la gestión de sedes, agendamiento de citas médicas y administración de análisis de laboratorio clínico.

---

## 📌 1. Problema
El agendamiento de citas y la gestión de muestras en laboratorios clínicos a menudo se realiza en sistemas desorganizados o sin un backend escalable, lo que genera conflictos de horarios dobles, falta de trazabilidad en las sedes de atención y lentitud al procesar solicitudes de pacientes y personal médico.

---

## 🎯 2. Objetivo
Desarrollar un servicio backend (*API RESTful*) robusto, modular y de alto rendimiento utilizando Express 5 y el ORM Objection.js con Knex.js. El sistema permite administrar las sedes del laboratorio (*branches*), usuarios, servicios de análisis clínicos y la programación eficiente de citas médicas con persistencia en PostgreSQL.

---

## 🛠️ 3. Stack
- **Runtime & Entorno**: Node.js (CommonJS, `>=18.x`)
- **Framework Web HTTP**: Express 5 (`express ^5.2.1`)
- **Base de Datos Relacional**: PostgreSQL (`pg ^8.20.0`)
- **Query Builder & ORM**: Knex.js (`knex ^3.2.5`) y Objection.js (`objection ^3.1.5`)
- **Middleware & Pool**: Morgan (`morgan ^1.10.1`), Tarn (`tarn ^3.0.2` para pool de conexiones)
- **Herramientas de Desarrollo**: Nodemon (`nodemon ^3.1.14` para hot-reloading)

---

## 📐 4. Arquitectura
La aplicación sigue una arquitectura limpia para servicios REST API en Node.js:

```text
appointment_lab_system_back-1/
├── migrations/               # Scripts de migraciones de esquemas SQL con Knex.js
│   └── 20260325020625_create-table-sede.js # Migración de la tabla de sedes clínicas
├── src/
│   ├── config/               # Configuración de conexiones e infraestructura
│   │   └── db.js             # Inicialización de la conexión Knex/Objection.js
│   └── app.js                # Configuración de Express, middlewares y enrutamiento
├── index.js                  # Punto de entrada y arranque del servidor HTTP (Puerto 3000)
├── knexfile.js               # Configuración de entornos de base de datos (dev, staging, prod)
└── package.json              # Gestión de dependencias y scripts (migrate, rollback, dev)
```

---

## ⚙️ 5. Funcionalidades
- 🏥 **Gestión de Sedes de Atencion**: Control de ubicaciones, direcciones y estado de operabilidad de sedes clínicas (`sede`).
- 📅 **Servicios de Agendamiento**: Endpoints API RESTful para la creación, consulta y actualización de citas de laboratorio.
- 🗄️ **Migraciones de Base de Datos**: Control de versiones de esquema en PostgreSQL mediante comandos Knex (`migrate:latest` y `migrate:rollback`).
- ⚡ **Pool de Conexiones Optimizado**: Conexión eficiente a la base de datos relacional mediante la librería Tarn.
- 🔄 **Entorno de Desarrollo Dinámico**: Recarga automática de cambios en tiempo real con Nodemon.

---

## 📊 6. Estado Actual
🟢 **En Desarrollo / Base Funcional (v1.0.0)**: API backend estructurada en Express 5 con ORM Objection.js configurado, soporte para PostgreSQL y scripts de migración ejecutables.

---

## 🖼️ 7. Capturas

> *Sección reservada para diagramas de arquitectura de base de datos o capturas de pruebas de endpoints en Postman / Insomnia.*

---

## 🚀 8. Cómo Ejecutarlo

### Requisitos previos
- **Node.js**: Versión 18.x o superior.
- **npm**: Versión 6.x o superior.
- **PostgreSQL**: Versión 12.x o superior con la base de datos `appointment_lab` creada.

### Pasos de instalación y ejecución
1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/RomelAnte/date_lab_system_back.git
   cd date_lab_system_back
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   ```

3. **Configurar la base de datos PostgreSQL**:
   Abre el archivo [`knexfile.js`](file:///C:/Users/User/Documents/GitHub/appointment_lab_system_back-1/knexfile.js) y ajusta tus credenciales locales:
   ```javascript
   development: {
     client: 'postgresql',
     connection: {
       database: 'appointment_lab',
       user: 'postgres',
       password: 'tu_password'
     }
   }
   ```

4. **Ejecutar las migraciones de base de datos**:
   ```bash
   npm run migrate
   ```

5. **Iniciar el servidor backend**:
   ```bash
   npm run dev
   ```
   El servidor estará escuchando en `http://localhost:3000`.

---

## 🗺️ 9. Roadmap
- [ ] Implementar autenticación y autorización segura con JWT (JSON Web Tokens) y contraseñas cifradas con `bcrypt`.
- [ ] Definición completa de los modelos de Objection.js para `Usuario`, `Cita`, `Examen` y `Sede`.
- [ ] Integración de documentación interactiva de la API con Swagger / OpenAPI.
- [ ] Servicio de notificaciones por correo electrónico (Nodemailer / SendGrid) para confirmación de citas.
- [ ] Pruebas unitarias e integración con Jest y Supertest.
