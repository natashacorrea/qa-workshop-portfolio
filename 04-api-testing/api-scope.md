# API Testing — Alcance

## API

Swagger Petstore

## Alcance funcional

Gestión de mascotas (pet).

## Operaciones seleccionadas

| Método HTTP | Endpoint | Propósito |
|---|---|---|
| POST | `/pet` | Crear una nueva mascota en el catálogo del sistema. |
| GET | `/pet/{petId}` | Consultar el detalle y estado actual de una mascota mediante su identificador. |
| PUT | `/pet` | Actualizar los datos de una mascota existente (nombre, categoría, estado). |
| DELETE | `/pet/{petId}` | Eliminar del registro una mascota existente. |

## Justificación
Se seleccionaron las cuatro operaciones fundamentales del ciclo de vida (CRUD) del recurso `pet`. Al ser PetStore una plataforma cuyo modelo de negocio se basa en la comercialización de animales, y más, la integridad y persistencia de estos datos es crítica. Si la API permite crear registros corruptos, no refleja actualizaciones o no elimina registros obsoletos, afecta directamente el inventario y la venta en los canales digitales.

## Condiciones de prueba identificadas
1. **Creación válida de entidad:** Creación exitosa enviando un payload JSON completo y bien formado (Código 200).
2. **Consulta por identificador existente:** Recuperación consistente de los datos creados previamente (Código 200).
3. **Consulta de entidad inexistente / no numerica:** Manejo de error al consultar un ID que no existe en el sistema (Código 400 / 404).
4. **Actualización de estado:** Modificación del estado de inventario de una mascota (`available` a `sold`) y verificación de persistencia (Código 200).
5. **Eliminación y confirmación de baja de registro:** Eliminación exitosa de una mascota existente (Código 200) y verificación subsiguiente de que el recurso ya no existe al consultarlo vía GET (Código 404).
6. **Eliminación sobre entidad inexistente:** Manejo de error al intentar borrar una mascota con un ID que no existe en la base de datos (Código 404 Not Found).

## Fuera de alcance

* Operaciones de carga masiva de imágenes (`POST /pet/{petId}/uploadImage`).
* Filtros de búsqueda masiva (`GET /pet/findByStatus`).
* Módulos de órdenes (`/store`) y usuarios (`/user`).
* Pruebas de rendimiento, estrés y concurrencia sobre los servidores públicos de Swagger.