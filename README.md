# fitodiagnostico — Corte 1, Arquitectura de Software

Universidad Sergio Arboleda · Semestre 2026-03

Servicio de diagnóstico del estado de plantas: dada una medición (humedad del sustrato,
nivel de luz y temperatura) y una especie registrada, clasifica cada parámetro contra los
rangos de referencia de esa especie, deriva un estado global y devuelve una recomendación
por cada parámetro fuera de rango.

## Estado del proyecto

En diseño. Todavía no hay código: primero se cierran los diagramas y el documento de
arquitectura, y el código se escribe contra ese diseño.

| Entregable | Estado |
|---|---|
| 6.a Repositorio con historial incremental | en curso |
| 6.b.1 Diagrama de paquetes / componentes | pendiente |
| 6.b.2 Diagrama de secuencia | primera versión |
| 6.b.3 Tabla de responsabilidades por capa | pendiente |
| 6.b.4 Justificación SOLID (archivo y línea) | pendiente (requiere código) |
| 6.b.5 Plan de evolución | pendiente |
| 6.b.6 Decisiones y alternativas descartadas | en curso |
| 6.c Front web funcional | pendiente |
| 6.d Pruebas unitarias del dominio (mínimo 6) | pendiente |
| 6.e Bitácora de uso de IA | en curso |

## Contenido

- `docs/documento-arquitectura.md` — el documento del entregable 6.b.
- `docs/modelo-dominio.mermaid` / `.png` — modelo de dominio (material de apoyo).
- `docs/secuencia-diagnostico.mermaid` / `.png` — entregable 6.b.2.
- `docs/comparacion-con-proyecto-original.md` — en qué se aparta el proyecto previo del
  equipo de lo que pide este enunciado.
- `bitacora-ia.md` — entregable 6.e.

Los diagramas se editan en su `.mermaid` (draw.io los importa desde
*Arrange > Insert > Advanced > Mermaid*) y el `.png` se regenera a partir del fuente, para
que el diagrama versionado y la imagen del documento nunca se separen.

## Ejecución

Pendiente: se documenta aquí cuando exista el backend y el front, como pide el entregable 6.a.
