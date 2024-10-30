# Sistema de registro de turnos
Documentación del práctico final de la materia **Interfaces y Programación Visual** en el que se debe realizar una aplicación web utilizando las herramientas de software aprendidas. La aplicación a desarrollar será un **sistema de gestión de turnos**.

---

## 1. Introducción
### 1.1 Descripción del Proyecto
Un sistema de gestión de turnos que permite a los usuarios reservar citas con profesionales para servicios específicos. Los administradores pueden gestionar turnos, profesionales, y servicios. El sistema está desarrollado en PHP con Laravel y usa MySQL para la base de datos.

### 1.2 Objetivo
Desarrollar un sistema mínimo viable de gestión de turnos, cumpliendo los requerimientos para un trabajo académico.

---

## 2. Análisis de Requerimientos
### 2.1 Funcionalidades del Usuario
- **Autenticación y Registro:** Los usuarios pueden registrarse y autenticarse en el sistema.
- **Reserva de Turno:** Selección de fecha, hora, profesional y servicio.
- **Consulta y Gestión de Turnos:** Los usuarios pueden ver, modificar y cancelar sus turnos.

### 2.2 Funcionalidades del Administrador
- **Gestión de Turnos (ABMC):** CRUD de los turnos reservados por los usuarios.
- **Gestión de Profesionales (ABMC):** CRUD de los profesionales encargados de los servicios.
- **Gestión de Servicios (ABMC):** CRUD de los tipos de servicios ofrecidos en el sistema.

### 2.3 Requerimientos No Funcionales
- **Responsivo:** Adaptable a dispositivos móviles y pantallas de diferentes tamaños.
- **Seguridad:** Protecciones contra ataques como SQL Injection y XSS.
- **Usabilidad:** Interfaz clara y rápida de usar.

---

## 3. Arquitectura del Sistema
### 3.1 Tecnologías
- **Backend:** Laravel (PHP) + MySQL.
- **Frontend:** HTML5, CSS3, JavaScript, jQuery y Bootstrap.
- **Servidor RESTful:** Webservice en Laravel para permitir acceso programático a los turnos y servicios.

### 3.2 Diagrama de Arquitectura
El diagrama incluiría los componentes siguientes:
1. **Frontend (UI):** Interfaz del usuario en HTML, CSS y JavaScript.
2. **API RESTful:** Endpoints en Laravel para operaciones CRUD de turnos y otros datos.
3. **Base de Datos (MySQL):** Almacena la información de los usuarios, turnos, profesionales y servicios.
4. **Servidor Web:** XAMPP para el entorno de desarrollo.

---

## 4. Modelo de Datos
### Tablas y Relaciones
Las tablas y relaciones se definen de la siguiente forma:

1. **Users**: Almacena datos de autenticación y roles.
	- `id`, `name`, `username`, `password`, `role` (cliente o administrador)

2. **Services**: Define los tipos de servicios que pueden ser reservados.
	- `id`, `name`, `description`

3. **Appointments**: Almacena cada turno disponible o no disponible a ser tomado, con el servicio asociado.
	- `id`, `service_id`, `date`, `status`

4. **Users_Appointments**: Almacena cada turno reservado, con relación a un usuario.
	- `id`, `us_id`, `profesional_id`, `servicio_id`, `fecha`, `hora`, `estado`



---

## 5. Planificación de Páginas Web
Para cumplir con los requerimientos de tener al menos cinco páginas, estas son las propuestas:

1. **Página Principal**: Descripción general del sistema.
2. **Página de Autenticación**: Login de usuarios y administradores.
3. **Página de Registro**: Registro de nuevos usuarios.
4. **Página de Reserva de Turno**: Selección de profesional, fecha, hora y servicio.
5. **Página de Gestión de Turnos (Cliente)**: Consulta y administración de turnos propios.
6. **Página de Gestión de Turnos (Administrador)**: Visualización y administración completa de los turnos.
7. **Página de Gestión de Profesionales**: ABMC para profesionales (Administrador).
8. **Página de Gestión de Servicios**: ABMC para servicios (Administrador).

---

## 6. Desarrollo del Backend (Laravel)
### 6.1 Configuración de Laravel y MySQL
- Conexión a MySQL configurada en el archivo `.env`.
- Uso de **migraciones** para crear las tablas automáticamente.
- Modelos y controladores para `Usuario`, `Turno`, `Profesional`, y `Servicio`.

### 6.2 Webservice RESTful
Define los endpoints RESTful en Laravel para CRUD de turnos y otros datos:
- **GET /api/turnos**: Listar turnos (para consumo de aplicaciones externas).
- **POST /api/turnos**: Crear un turno.
- **GET /api/turnos/{id}**: Consultar un turno específico.
- **PUT /api/turnos/{id}**: Actualizar un turno.
- **DELETE /api/turnos/{id}**: Eliminar un turno.

> Para proteger las rutas, agrega autenticación básica y permisos según roles de usuario.

---

## 7. Desarrollo del Frontend
### 7.1 Estructura de HTML y CSS
Usa Bootstrap y jQuery para una estructura responsiva, con formularios para el registro y reserva de turnos.

### 7.2 Uso de jQuery
- Validación de formularios en el lado del cliente.
- AJAX para enviar y recibir datos del servidor sin recargar la página.

### 7.3 Seguridad
- **CSRF tokens** para proteger formularios.
- **Validación de datos** en Laravel para evitar ataques de inyección SQL.
- **Escape de datos** en el frontend para prevenir XSS.

---

## 8. Diseño de Interfaz
### 8.1 Wireframes y Componentes
Haz bocetos de cada página:
1. **Página Principal:** Información general y botones de acceso.
2. **Página de Reserva de Turno:** Formulario para seleccionar profesional, fecha y hora.
3. **Gestión de Turnos Cliente/Admin:** Listado de turnos con opciones para editar/cancelar.