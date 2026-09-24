# Coverage Decisions

## Riesgos que se probarán primero
1. Confirmación de compras sobre productos sin existencias reales (R1): Validar si la tienda permite adquirir productos o mascotas que no cuentan con stock disponible durante el checkout.   
2. Persistencia o exposición de credenciales y datos sensibles en texto plano (R3): Probar el flujo de registro e inicio de sesión para verificar que las contraseñas e información personal no queden expuestas en la URL, logs o respuestas del navegador.   
3. Falta de confirmación por correo o comprobante digital tras la orden (R5): Comprobar si el sistema genera un identificador de orden visible y comprobante transaccional tras finalizar la compra.

## ¿Por qué esos riesgos son prioridad?
Estos tres riesgos impactan de manera directa la experiencia inmediata del comprador y la viabilidad del canal web en producción. Atacar R1 evita el quiebre comercial de sobrevender mascotas o artículos que no se pueden entregar, protegiendo a la empresa de cancelaciones forzosas y disputas. Evaluar R3 es prioritario para salvaguardar la privacidad de los usuarios y mitigar incidentes de seguridad que puedan comprometer las cuentas de los clientes. Por último, priorizar R5 reduce la fricción posventa: sin una confirmación o comprobante claro, los usuarios saturan soporte o realizan pagos duplicados por incertidumbre. Además, estos tres riesgos se pueden validar funcionalmente de forma rápida en la web sin requerir infraestructura adicional.  

## Qué se probará menos o quedará fuera por ahora
- Caída del catálogo ante picos de concurrencia (R2): Pruebas de estrés y rendimiento masivo sobre la infraestructura del servidor web.   
- Desincronización de datos entre la interfaz web y los servicios de la API (R4): Pruebas de integración bidireccional entre la tienda web y la API Swagger pública.   - - Pruebas exhaustivas de compatibilidad visual en múltiples dispositivos móviles o navegadores heredados.

## Justificación de exclusiones
Postergar R2 (caída ante picos de concurrencia) es razonable porque las pruebas de carga y estrés requieren preparar entornos dedicados, scripts de rendimiento y herramientas específicas, lo cual dilata la validación funcional básica inicial que debe resolver un QA nuevo. Excluir por ahora R4 (desincronización web vs. API) se fundamenta en que, según el contexto del sistema, no hay confirmación oficial de que la aplicación web y la API Swagger pública compartan la misma base de datos o estén integradas. Invertir tiempo en contrastar datos entre dos sistemas que podrían ser independientes desviaría el foco de los flujos de negocio confirmados de la tienda web. Finalmente, estos detalles no impiden la concreción de las ventas y quedan en un nivel de prioridad bajo frente a los riesgos transaccionales.
