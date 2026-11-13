# Registro de riesgos

**Borrador:** aplica a la prueba revisada en el commit `6f06b98bcb45433a29a5ed6a8a09820c340a2213` de Vértice. Probabilidad e impacto son estimaciones iniciales para priorizar, no mediciones. Sebastián figura como responsable provisional del seguimiento, sujeto a confirmación.

| # | Riesgo | Quién sale afectado | Probabilidad (B/M/A) | Impacto (B/M/A) | Mitigación | Estado | Responsable |
| --- | --- | --- | --- | --- | --- | --- | --- |
| R1 | Nombre, correo o detalles de solicitudes quedan en el navegador compartido y otra persona los ve. | Clientes y personas cuyos datos aparezcan en la solicitud. | M | A | Usar solo datos ficticios en pruebas; definir borrado, retención y protección antes de usar datos reales. | Pendiente | Sebastián, responsable provisional |
| R2 | Una recomendación de material o uso se interpreta como validación técnica y se fabrica una pieza inadecuada. | Cliente y personas que usen la pieza. | M | A | Mantener las sugerencias revisables y exigir revisión técnica del taller antes de cotizar o fabricar; comprobar ese flujo. | Pendiente | Sebastián, responsable provisional |
| R3 | Una solicitud contiene datos personales en texto libre y se envía a un webhook o servicio externo sin que se hayan definido destino, uso y conservación. | Cliente y otras personas mencionadas. | M | A | No usar datos reales en pruebas; identificar proveedores y flujo de datos, minimizar el contenido y revisar las condiciones antes de activar la integración. | Pendiente | Sebastián, responsable provisional |
| R4 | Los controles de acceso o la sincronización de solicitudes no funcionan como se espera y se exponen datos o se cree que quedaron guardados cuando no fue así. | Clientes y taller. | M | A | Verificar permisos y políticas en el servicio real, probar accesos por rol y mostrar errores de guardado antes de usar datos reales. | Pendiente | Sebastián, responsable provisional |

Las mitigaciones son acciones propuestas, no garantías de que ya existan. Revisar la valoración y asignar responsables definitivos cuando se confirme el alcance del proyecto.
