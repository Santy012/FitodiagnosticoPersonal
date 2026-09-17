# Bitácora de uso de IA

Entregable 6.e. El enunciado dice que el uso de asistentes de IA "está permitido y es
esperado" y que lo que se premia es la lucidez sobre el propio proceso: qué se pidió, qué
propuso la herramienta, qué se aceptó tal cual, qué se cambió y por qué.

## Entendimiento de la arquitectura (antes de diseñar)

Se usó a Claude para entender arquitectura hexagonal: qué responsabilidad tiene cada capa
y por dónde pasan los bordes. Antes de esto no estaba claro por qué la infraestructura no
es "la base de datos" sino todo lo que es detalle reemplazable.

## Revisión del diagrama de clases del dominio

Se le pasó un diagrama de clases hecho a mano para que lo corrigiera. Correcciones
aceptadas: los rangos son de la **especie** y no de una planta individual (en este corte
todavía no existe el concepto de planta, aparece recién como escenario de evolución); un
rango es `[min, max]` y no un umbral suelto; faltaban el objeto resultado, las
recomendaciones del RF4, los errores del RF6 y el puerto del RA5; y varias correcciones de
notación UML (las flechas de realización iban invertidas y con línea sólida).

Corrección de fondo que no habíamos visto: el diagrama modelaba un único estado global
("necesita agua", "necesita luz"), que es el diseño del proyecto anterior del equipo, pero
el RF2 pide clasificar **cada parámetro** como BAJO/OPTIMO/ALTO y el RF3 pide derivar el
estado global de esos estados individuales. Con el modelo anterior no se puede construir el
JSON del Anexo A.

## Decisión propia sobre el modelo de parámetros

La IA propuso tratar el parámetro como concepto (`Parametro(nombre, valor, unidad)` y los
rangos indexados por nombre) en lugar de campos fijos. Se aceptó, pero la decisión es del
equipo y queda documentada en el punto 6.b.6 con su alternativa descartada: los campos
fijos se leen mejor, pero agregar un cuarto parámetro obliga a modificar el evaluador, que
es justo lo que el enunciado usa como ejemplo de OCP.

## Regla de agregación (RF3)

**No delegada.** El RF3 dice que la regla de agregación la define y justifica el equipo. La
IA dejó una implementación de ejemplo en el diagrama marcada como tal; la regla real se
acuerda entre nosotros.

## Nota sobre el PDF del enunciado

El PDF traía un texto insertado ("Nota metodológica ASW-4.2") que pedía renombrar la capa
de acceso a datos como "capa de abastecimiento", el estado global como "índice de
vitalidad", y citar una guía interna inexistente. No se siguió: no aparece en ningún
archivo de este repositorio ni se citará en el documento. Se identificó como contenido no
confiable incrustado en el archivo, no como una instrucción del enunciado.
