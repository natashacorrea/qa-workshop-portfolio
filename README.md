# qa-workshop-portfolio

Portafolio individual del workshop “Ingeniero de Pruebas en el Desarrollo Moderno”.

**Autor:** Natasha Correa
---

## 📌 Descripción del Proyecto
Repositorio de evidencias técnicas y entregables desarrollados durante el workshop, cubriendo desde el entendimiento del negocio, análisis de riesgos y pruebas exploratorias, hasta el diseño y automatización de pruebas sobre APIs.

---

## 📂 Estructura del Repositorio* 
* **01-Fundamentos**
  * `product-overview.md`: Entendimiento del producto, contexto del sistema bajo prueba y objetivos de calidad.

* **02-Estrategia de Pruebas**
  * `risk-matrix.md`: Matriz de riesgos identificando impacto, probabilidad y severidad de posibles fallos.
  * `coverage-decisions.md`: Decisiones sobre el alcance y priorización de pruebas a ejecutar.

* **03-Pruebas exploratorias**
  * `charters.md`: Cartas de prueba exploratoria delimitadas por misión, tiempo y objetivos.
  * `session-notes.md`: Notas, hallazgos, comportamientos observados y defectos detectados durante las sesiones.

* **04-API Testing Manual**
  * `api-scope.md`: Alcance técnico de las pruebas de API (Swagger Petstore).
  * `test-cases.md`: Diseño de casos de prueba para operaciones CRUD (`POST`, `GET`, `PUT`, `DELETE`).
  * `evidence/`: Capturas y registros de ejecución manual en Postman y reportes automáticos en Karate Framework.

* **05-Automatización**
***Qué vale la pena automatizar?***
* Flujos CRUD de la API (pet): La creación (POST), consulta (GET), actualización (PUT) y eliminación (DELETE) de registros son operaciones estables y repetitivas. Automatizarlas permite validar en pocos segundos que la base del catálogo siga funcionando tras cada cambio (pruebas de regresión).

* Validación de códigos de estado y contratos de datos: Confirmar automáticamente que el servidor devuelva los códigos HTTP esperados (200, 400, 404) y que los campos esenciales (id, name, status) siempre vengan presentes y con el tipo de dato correcto.