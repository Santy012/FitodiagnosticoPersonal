# Documento de arquitectura — Corte 1

> Máximo 8 páginas (entregable 6.b). Este archivo es el esqueleto de trabajo: cada sección
> dice qué tiene que contener y en qué estado está. Se redacta a partir del análisis del
> propio código, no del enunciado.

**Equipo:** _(nombres)_
**Repositorio:** https://github.com/Santy012/FitodiagnosticoPersonal

---

## 1. Diagrama de paquetes / componentes

> Debe corresponder **uno a uno** con la estructura real del repositorio. El enunciado
> advierte que un diagrama que no coincida con el código se califica como no entregado.

**Estado: pendiente.** Se dibuja cuando la estructura de paquetes esté congelada, y se
vuelve a verificar contra el repositorio antes de entregar.

---

## 2. Diagrama de secuencia

> Recorrido completo de una petición de diagnóstico, desde el `fetch` del front hasta la
> respuesta, nombrando las clases o módulos reales que participan.

**Estado: primera versión hecha** — ver `secuencia-diagnostico.png` (fuente editable en
`secuencia-diagnostico.mermaid`). Incluye los tres caminos: éxito, especie no registrada y
parámetro inválido.

Pendiente: volver a revisarlo cuando el código exista, para que los nombres de clase del
diagrama sean exactamente los del repositorio.

---

## 3. Tabla de responsabilidades por capa

> Qué hace cada capa, qué tiene **prohibido** hacer, y de qué depende.

**Estado: pendiente.** Es diseño puro, se puede escribir completo antes de programar.

| Capa | Qué hace | Qué tiene prohibido | De qué depende |
|---|---|---|---|
| web | | | |
| aplicación | | | |
| dominio | | | |
| infraestructura | | | |

---

## 4. Justificación SOLID

> Para cada uno de los cinco principios: dónde se aplicó y qué habría pasado de no
> aplicarlo, **citando archivo y línea** del repositorio propio.

**Estado: pendiente** — requiere que el código exista. Las decisiones ya están tomadas;
falta anclarlas a archivo y línea.

| Principio | Dónde se aplicó (archivo:línea) | Qué habría pasado sin aplicarlo |
|---|---|---|
| SRP | | |
| OCP | | |
| LSP | | |
| ISP | | |
| DIP | | |

---

## 5. Plan de evolución

> Máximo 2 páginas. Para cada escenario: qué componentes se **agregan**, cuáles se
> **modifican** y cuáles **no se tocan**.

**Estado: pendiente.** Es diseño puro, se puede escribir ya.

1. Las mediciones dejan de llegar por HTTP y llegan por MQTT desde un ESP32.
2. La tabla de referencia migra de CSV a una base de datos relacional.
3. Aparecen usuarios, cada uno con varias plantas.
4. Se agrega gamificación (puntos, rachas, niveles) sobre el cuidado de la planta.

---

## 6. Decisiones y alternativas descartadas

> Al menos tres decisiones de diseño, cada una con la alternativa que se consideró y la
> razón del descarte.

**Estado: en curso.** Candidatas ya identificadas:

1. **Parámetros como concepto vs. campos fijos.** Modelar `Parametro(nombre, valor, unidad)`
   y guardar los rangos indexados por nombre, en lugar de tener `temperatura`, `humedad` y
   `luz` como campos de `Especie`. Alternativa descartada: campos fijos, más legibles pero
   obligan a tocar el evaluador al agregar un cuarto parámetro.
2. **Regla de agregación como abstracción.** _(pendiente de definir con el equipo — el RF3
   dice que la regla la define y justifica el equipo)._
3. **Divergencia respecto al proyecto original del equipo.** Ver
   `comparacion-con-proyecto-original.md`.
