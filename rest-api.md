# Especificación Técnica de Arquitectura: API REST v1.0

Este documento detalla el diseño de la interfaz de programación de aplicaciones (API) bajo el estilo arquitectónico REST para el sistema de gestión de tareas.

## 1. Diseño de Arquitectura y Estándares
La API está diseñada siguiendo los principios de transferencia de estado representacional (REST), asegurando escalabilidad y desacoplamiento entre el cliente y el servidor.
* **Protocolo:** HTTPS (TLS 1.3) para asegurar la integridad de los datos.
* **Formato de Intercambio:** JSON (JavaScript Object Notation).
* **Versionamiento:** Basado en URL (v1) para garantizar la compatibilidad hacia atrás.

## 2. Definición de Recursos y Endpoints

### A. Gestión de Tareas (Resources)
* **GET `/api/v1/tasks`**: Recupera una colección paginada de tareas. Soporta parámetros de filtrado por estado (`status`) y prioridad (`priority`).
* **POST `/api/v1/tasks`**: Crea un nuevo recurso. Requiere validación de esquema en el cuerpo de la petición.
* **GET `/api/v1/tasks/{id}`**: Recupera el detalle atómico de una tarea específica mediante su identificador único (UUID).
* **PUT/PATCH `/api/v1/tasks/{id}`**: Actualización total o parcial del estado de la tarea.
* **DELETE `/api/v1/tasks/{id}`**: Eliminación lógica del recurso.

## 3. Manejo de Respuestas y Códigos de Estado
Se implementan códigos de estado HTTP estándar para comunicar el resultado de las operaciones:
* **200 OK**: Operación exitosa con retorno de datos.
* **201 Created**: Recurso creado exitosamente (respuesta a POST).
* **400 Bad Request**: La petición es malformada o no cumple con las reglas de negocio.
* **401 Unauthorized**: Falta de credenciales de autenticación válidas.
* **404 Not Found**: El recurso solicitado no existe en la base de datos.
