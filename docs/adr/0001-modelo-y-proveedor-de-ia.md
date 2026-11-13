# ADR-0001: Herramientas de IA y selección del proveedor

- Estado: Propuesto
- Fecha: 2026-11-13
- Decide: Sebastián, responsable del proyecto (propuesta pendiente de confirmar).

## Contexto

Vértice está probando un asistente para orientar solicitudes de impresión 3D. El stack y los requisitos finales siguen pendientes; necesitamos distinguir una simulación de una integración real.

## Decisión

Para desarrollar y documentar se utiliza Codex con revisión humana; Sebastián decide qué cambios aceptar. En la prueba revisada, el asistente puede enviar la descripción a un webhook n8n configurado y, si no obtiene una respuesta válida, usa reglas locales. No se identificó en ese código qué modelo o proveedor hay detrás del webhook ni se verificó que esté activo.

La elección de modelo, proveedor, costo, tratamiento de datos y ubicación de credenciales queda pendiente. Antes de integrar un modelo se propone evaluar necesidad, calidad, privacidad, costo y restricciones del curso; las credenciales privadas deberán permanecer en el servidor.

## Alternativas descartadas

- Declarar un modelo específico como elegido sin verificar el flujo y sus condiciones: daría una impresión falsa de implementación.
- Enviar datos reales durante las pruebas sin conocer su destino y tratamiento: expondría información innecesariamente.

## Consecuencias

Las reglas locales permiten explorar el flujo sin demostrar capacidades de un modelo. El costo mensual del eventual proveedor y el comportamiento final ante fallos siguen sin determinar.

## Cómo se verifica

En el commit `6f06b98bcb45433a29a5ed6a8a09820c340a2213` de Vértice, revisar `experimentos/stack-mvp/frontend/src/lib/aiAssistantService.ts`. Cuando exista una integración, revisar además su configuración de servidor, proveedor, datos enviados y pruebas; no publicar credenciales.
