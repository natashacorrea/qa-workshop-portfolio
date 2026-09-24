# Risk Matrix

| ID | Riesgo | Impacto | Probabilidad | Nivel | Justificación |
|----|--------|---------|--------------|-------|---------------|
| R1 | Confirmación de compras sobre productos sin existencias reales | Alto | Alta | Alto | Porque si el comercio electronico no bloquea el stock durante el checkout puede provocar sobreventas, cancelaciones forzosas y daño a la reputación comercial |
| R2 | Caída del catálogo ante picos de concurrencia | Critico | Alta | Alto | Si el catálogo web experimenta lentitud excesiva o respuestas con error 500 durante campañas promocionales o tráfico pico, los usuarios no lograran navegar ni pagar, paralizando las ventas directas. |
| R3 | Persistencia o exposición de credenciales y datos sensibles en texto plano | Alto | Medio | Alto | Porque el registro maneja información confidencial y si se exponen parametros o logs sin cifrados vulnerabiliza la cuenta del usuario |
| R4 | Desincronización de datos entre la interfaz web y los servicios de la API | Medio | Alto | Medio | No hay confirmación de que esten integrados, y si existen diferencias en estados de catalogo o inventario pueden mostrar información inconsistentes |
| R5 | Falta de confirmación por correo o comprobante digital tras la orden | Medio | Media | Medio | Si no hay un comprobante o correo de confirmación el usuario puede asumir que la compra falló, y puede generar solicitudes duplicadas o saturar los canales de atención al cliente |