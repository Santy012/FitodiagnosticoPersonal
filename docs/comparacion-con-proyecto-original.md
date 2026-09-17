# Comparación entre el proyecto original del equipo y lo que pide el enunciado

Este documento existe porque los diagramas de `docs/` describen el diseño que exige el
enunciado del Corte 1, y **ese diseño no es el que implementa el proyecto que el equipo ya
tenía construido** (`fitodiagnostico-original`). Las diferencias no son de nombres: son
estructurales.

Se deja escrito porque es materia prima directa del entregable 6.b.6 (decisiones y
alternativas descartadas) y porque el 6.b.1 advierte que un diagrama que no coincida con
el código se califica como no entregado.

## Diferencias verificadas contra el código

| Tema | Lo que pide el enunciado | Lo que hace el proyecto original |
|---|---|---|
| Clasificación por parámetro (RF2) | Cada parámetro se clasifica como `BAJO`, `OPTIMO` o `ALTO` | No existe. No hay ningún tipo que represente el estado de un parámetro individual |
| Estado global (RF3) | Se *deriva* de los estados individuales con una regla de agregación que el equipo justifica | `EvaluadorDeEstado` recorre estrategias y devuelve la primera que aplica: `NECESITA_AGUA`, `NECESITA_LUZ`, `NECESITA_ABRIGO` u `OPTIMO` |
| Recomendaciones (RF4) | Una recomendación textual **por cada** parámetro fuera de rango | `Diagnostico.detalle` es un único `String`, el de la estrategia ganadora |
| Listado de especies (RF5) | `GET /api/v1/especies` con sus rangos | No existe ningún controlador para esto |
| Método y cuerpo (Anexo A) | `POST` con cuerpo JSON | `GET` con parámetros de consulta (`@ModelAttribute SolicitudDiagnostico`) |
| Forma de la respuesta | `{especie, estado, parametros[], recomendaciones[]}` | `{especie, lectura, estado, detalle, evaluadoEn}` |
| Cuerpo de error (RF6) | `{error, mensaje, detalle}` uniforme | RFC 7807 `ProblemDetail` (`application/problem+json`) |
| Cuarto parámetro, p. ej. pH (OCP) | No debería obligar a modificar el evaluador | `Especie` es un record con `Rango temperatura, Rango humedad, Rango luz` como campos fijos: agregar pH obliga a cambiar el record y todo lo que lo construye o lo lee |

Sobre el cuerpo de error hay un matiz a favor del proyecto original: el Anexo A dice
explícitamente que el contrato es "una sugerencia razonable, no una imposición" y que el
equipo puede modificarlo mientras lo justifique y mantenga uniforme el cuerpo de error del
RF6. `ProblemDetail` es un estándar y es defendible. Las otras diferencias no tienen esa
salida, porque no vienen del Anexo sino de los requisitos funcionales.

## Consecuencia práctica

No se pueden reutilizar los mismos diagramas para los dos proyectos. O el diseño
documentado se ajusta al código original, o el código se ajusta al diseño que el enunciado
pide. Es una decisión del equipo, no una de redacción del documento.
