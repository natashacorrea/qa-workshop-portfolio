# Sesión 1

## Charter

Explorar la pantalla del carrito de compras y la actualización de artículos seleccionados usando entradas manuales de datos anómalos en el campo de cantidad (valores negativos, cero, decimales, texto alfanumérico y números excesivamente grandes) combinados con la acción de actualizar el carrito (Update Cart), para descubrir si el sistema permite corromper el cálculo del subtotal, generar montos de compra negativos o en cero, o provocar caídas no controladas en la aplicación web.

## ÁREAS

JPetStore Demo
- URL: https://petstore.octoperf.com/actions/Catalog.action
- Plataforma: Navegador Google Chrome en Windows 11 (Escritorio)
- Módulo: Shopping Cart y actualización de líneas de pedido

## INICIO

24/09/2026 17:00

## TESTER

Natasha Correa

## DESGLOSE DE TAREAS

- Duración:
30 minutos
- Diseño y Ejecución de Pruebas:
65% pruebas manuales en el input y recalculando los subtotales
- Investigación y Reporte de Defectos:
20% Validación de montos y documentación de errores
- Preparación de la Sesión:
15% apertura de tienda, seleccion y agregado al carrito

## ARCHIVOS DE DATOS

- Identificadores de producto: Pez Ángel (EST-1), Golden Retriever (EST-28)

- Valores de entrada probados:

1. Valores negativos y nulos: 0, -1

2. Caracteres no numéricos: abc, @#!

3. Desbordamiento numérico: 9999999999

4. Valores válidos de control: 1, 3

## NOTAS DE PRUEBA

- Al agregar una mascota por primera vez, el sistema asigna por defecto una cantidad de 1 y calcula el subtotal multiplicando correctamente el precio unitario por la cantidad.

- Al ingresar 0 o -1 y presionar Update Cart, el sistema elimina automáticamente el producto de la tabla del carrito.

- Tras eliminarse el producto por ingresar 0 o -1, si el usuario intenta buscar nuevamente la misma mascota en el catálogo y hacer clic en Add to Cart, el sistema falla silenciosamente: no vuelve a añadir el producto al carrito, bloqueando la compra de ese ítem en la sesión actual.

- Al ingresar caracteres alfabéticos o especiales (ej. abc) o números desbordados (ej. 9999999999) y presionar Update Cart, la aplicación no arroja una pantalla de error ni cae con HTTP 500; implementa un manejo que revierte el campo al último valor numérico válido previo.

- No existen mensajes de advertencia visuales (feedback o toasts) que expliquen al usuario por qué su entrada no numérica fue revertida o por qué el producto fue removido al colocar cero.

## LISTA DE RIESGOS 

- Bloqueo irreversible de conversión: Si un usuario comete un error tipográfico ingresando 0 al querer limpiar o ajustar la cantidad, queda incapacitado de comprar ese producto a menos que limpie cookies o cierre su sesión, derivando en pérdida directa de ventas.

- Falta de feedback al usuario: Revertir o eliminar productos de manera silenciosa sin un mensaje de alerta genera confusión y fricción en la experiencia de compra.

## DEFECTOS (BUGS) 

### BUG-01: Bloqueo de producto en la sesión tras eliminación por cantidad inválida (0 o negativa)

Pasos para reproducir:

Ingresar al catálogo y agrega un producto al carrito (ej. Pez Ángel).
En el campo de cantidad del carrito, ingresar 0 o -1.
Hacer clic en Update Cart (el ítem desaparece del carrito).
Regresar al catálogo, seleccionar el mismo producto y presionar Add to Cart.
Resultado esperado: El producto debe volver a añadirse al carrito con cantidad 1.

Resultado obtenido: El carrito permanece vacío. El sistema no permite volver a agregar ese artículo en la sesión activa.

## INCIDENTES (ISSUES) 

- No hay documentación funcional que aclare si eliminar el ítem automáticamente ante un valor 0 es el comportamiento esperado por diseño, o si debería requerir una confirmación explícita mediante el enlace Remove. 

- Se desconoce si el bloqueo para re-agregar el producto es un problema de persistencia en la cookie de sesión del navegador o un bloqueo a nivel de caché en el servidor.