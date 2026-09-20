# Base conceptual

Este documento resume los conceptos y límites que sostienen el catálogo. No es
una receta para obtener decisiones óptimas. Sirve para interpretar cada ficha,
revisar sus supuestos y evitar una transferencia mecánica de modelos técnicos a
situaciones humanas.

## Alcance

Las decisiones cotidianas suelen tener tiempo, atención, información y capacidad
de cálculo limitados. Una regla puede ser razonable si considera el costo de
pensar, buscar, comparar y cambiar de opción. El resultado de aplicar una ficha
es una heurística revisable, no una garantía.

Los modelos se transfieren con cautela cuando hay objetivos múltiples,
reversibilidad, valores no cuantificables, efectos sobre otras personas,
asimetrías de poder o un entorno que cambia.

## Dominios

- **Elección y parada:** umbrales, búsqueda secuencial y decisiones sobre cuándo
  dejar de comparar.
- **Tiempo y atención:** orden de tareas, fechas límite, interrupciones,
  agrupación y capacidad limitada.
- **Aprendizaje y exploración:** equilibrio entre probar alternativas y usar lo
  que ya funciona, actualización de creencias y prevención del sobreajuste.
- **Relaciones y recursos:** cooperación repetida, incentivos, asignación,
  métricas, congestión y efectos sobre terceros.

## Límites de resultados formales

- **37 % / `1/e`:** solo corresponde aproximadamente al problema de la
  secretaria: horizonte conocido, orden aleatorio, información ordinal,
  ausencia de recuperación y objetivo de elegir la mejor opción. No es un
  porcentaje universal.
- **Gittins:** requiere un modelo definido de recompensas, horizonte y descuento.
  No es una recomendación cotidiana predeterminada.
- **Belady:** supone conocer el futuro. Es un límite teórico para comparar reglas,
  no una política aplicable directamente.
- **Bruss / odds:** requiere eventos binarios, probabilidades definidas e
  independencia. No debe calcularse a partir de una narración cotidiana.
- **UCB1:** requiere recompensas comparables, datos suficientes y un entorno
  aproximadamente estable. Para decisiones personales suele ser más seguro usar
  una exploración cualitativa o un experimento pequeño.
- **Recocido simulado y búsqueda aproximada:** pueden encontrar soluciones útiles,
  pero no garantizan la mejor solución y pueden optimizar una métrica incompleta.

## Reglas de aplicación

1. Define el objetivo antes de elegir la regla.
2. Separa hechos, supuestos, inferencias y recomendaciones.
3. Declara qué dato faltante podría cambiar la decisión.
4. Prefiere acciones pequeñas, reversibles y observables.
5. Revisa qué valores, personas o consecuencias quedan fuera de la métrica.
6. Usa rangos, escenarios o umbrales cualitativos cuando una cifra exacta no sea
   defendible.
7. En decisiones de alto impacto, verifica la información actual y busca apoyo
   profesional apropiado.

## Fuentes públicas

Las etiquetas numéricas usadas en las fichas corresponden a la bibliografía
normalizada de [`sources.md`](sources.md). Las referencias secundarias sirven
para contexto y explicación; las afirmaciones formales deben contrastarse con
la fuente primaria correspondiente. Para resultados de reemplazo de caché puede
consultarse también L. A. Bélády, *A Study of Replacement Algorithms for a
Virtual-Storage Computer*, [IEEE](https://ieeexplore.ieee.org/abstract/document/5388441).

Las afirmaciones sobre salud, derecho, finanzas, seguridad, empleo, vivienda u
otros asuntos de alto impacto requieren fuentes actuales y especializadas.