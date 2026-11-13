# ADR-0002: La asistencia propone; las personas confirman y cotizan

- Estado: Propuesto
- Fecha: 2026-11-13
- Decide: Sebastián, responsable del proyecto (propuesta pendiente de confirmar).

## Contexto

La prueba de Vértice ayuda a describir piezas para impresión 3D. Puede sugerir materiales y productos; una recomendación incorrecta podría afectar la seguridad o utilidad de la pieza. El stack y la integración definitiva de IA aún no están definidos.

## Decisión

Se propone que la asistencia solo sugiera opciones y preguntas, sin asegurar que una pieza es segura o adecuada. La persona cliente revisa y puede aceptar, editar o deshacer las sugerencias antes de confirmar la solicitud. Una persona del taller revisa la viabilidad y define la cotización; el cliente decide si la acepta. No se propone que la IA cierre ventas ni apruebe cotizaciones por sí sola.

La experiencia de captura sigue en investigación: se puede explorar que el cliente describa su necesidad con sus palabras, que el asistente prepare un borrador con lo expresado y pregunte de manera gradual por lo que falte. Poder responder «no sé» y dejar medidas pendientes son propuestas, no funciones verificadas ni un diseño definitivo.

En la prueba revisada, el análisis usa reglas locales cuando no se obtiene una respuesta del webhook n8n; esto no demuestra que haya un modelo conectado. Las sugerencias se aplican mediante una acción en la interfaz y la solicitud se crea al enviar el formulario. Estas observaciones son lectura de código, no una prueba de funcionamiento completo ni de controles efectivos de acceso.

## Alternativas descartadas

- Aplicar sugerencias y enviar una solicitud sin intervención de la persona: podría registrar datos o elecciones que no aprobó.
- Dejar que el asistente establezca una cotización definitiva: una sugerencia no sustituye la revisión técnica del taller.

## Consecuencias

La revisión humana toma tiempo y requiere explicar las limitaciones de las sugerencias. Reduce el riesgo de que una recomendación se tome como una decisión final, pero no elimina errores ni sustituye controles técnicos.

## Cómo se verifica

En el commit `6f06b98bcb45433a29a5ed6a8a09820c340a2213` de Vértice, revisar `experimentos/stack-mvp/frontend/src/pages/RequestPage.tsx` y `src/lib/aiAssistantService.ts`: el primero contiene las acciones de analizar, aplicar, deshacer y enviar; el segundo muestra el webhook opcional y las reglas locales.

Queda pendiente probar el recorrido completo, validar los permisos del taller y comprobar con pruebas que ninguna integración futura pueda enviar solicitudes o cotizar sin la intervención definida. La propuesta debe revisarse cuando se confirme el stack y la rúbrica.
