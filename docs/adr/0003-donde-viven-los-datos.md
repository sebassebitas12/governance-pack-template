# ADR-0003: Ubicación de los datos durante las pruebas

- Estado: Propuesto
- Fecha: 2026-11-13
- Decide: Sebastián, responsable del proyecto (propuesta pendiente de confirmar).

## Contexto

La prueba maneja datos como nombre, correo y descripción de la solicitud. El inventario identifica sus posibles ubicaciones; el stack definitivo y los controles reales todavía deben confirmarse.

## Decisión

Usar únicamente datos ficticios durante las pruebas. Sebastián indica que la intención es usar Supabase para almacenar los datos del proyecto, pero aún no se ha implementado ni probado esa integración. La región, los permisos y la política de conservación y eliminación quedan por definir; no se debe presentar Supabase como almacenamiento operativo.

Antes de trabajar con datos reales, definir ubicación, permisos, conservación, eliminación y destino de los datos, y verificar los controles.

En el código revisado, el navegador guarda borradores y solicitudes en almacenamiento local; la API demo guarda solicitudes en memoria y las pierde al reiniciarse. También existe código que intenta sincronizar solicitudes con una dirección de Supabase y un webhook n8n opcional que puede recibir la descripción. La existencia de ese código no equivale a una integración implementada o probada: no se verificó si algún servicio recibe datos ni en qué región opera.

## Alternativas descartadas

- Usar datos reales antes de comprobar accesos y destinos: podría exponer información personal.
- Dar por definitiva la ubicación de datos a partir de una variable o archivo de ejemplo: no confirma la configuración real.

## Consecuencias

Los datos del navegador pueden permanecer hasta que se borren; los de memoria de la API demo desaparecen al reiniciarla. Los plazos de servicios externos, el acceso efectivo, las transferencias y los mecanismos de eliminación siguen pendientes. El proyecto debe revisar las obligaciones aplicables de la Ley 8968 antes de tratar datos personales reales.

## Cómo se verifica

En el commit `6f06b98bcb45433a29a5ed6a8a09820c340a2213` de Vértice, revisar `experimentos/stack-mvp/frontend/src/lib/requestDraftStore.ts`, `requestsStore.ts`, `aiAssistantService.ts` y `experimentos/stack-mvp/api/server.js`. La migración SQL describe políticas propuestas, pero no demuestra su aplicación en el servicio: comprobar configuración y permisos efectivos por separado.
