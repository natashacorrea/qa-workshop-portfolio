# Charters

## Charter 1

**Título:** Validación del cálculo financiero y manipulación de cantidades en el carrito de compras

**Misión:**  
Explorar la pantalla del carrito de compras y la actualización de artículos seleccionados usando entradas manuales de datos anómalos en el campo de cantidad (valores negativos, cero, decimales, texto alfanumérico y números excesivamente grandes) combinados con la acción de actualizar el carrito (Update Cart), para descubrir si el sistema permite corromper el cálculo del subtotal, generar montos de compra negativos o en cero, o provocar caídas no controladas en la aplicación web

**Área principal explorada:** 
Carrito de compras y motor de cálculo de subtotales/totales.

## Charter 2

**Título:** Seguridad, persistencia y control de entradas en el flujo de autenticación y registro de usuario

**Misión:** 
Explorar el flujo de creación de cuenta y el inicio de sesión usando técnicas de análisis de valores límite, omisión de campos obligatorios, inyección de caracteres especiales e inspección de la URL y herramientas de desarrollo del navegador, para descubrir si existen credenciales o información confidencial expuestas en texto plano, si se permite el registro de usuarios duplicados o con datos corruptos, o si ocurren fallas críticas de validación en la plataforma.

**Área principal explorada:** 
Módulo de gestión de usuarios, formularios de registro y proceso de inicio de sesión
