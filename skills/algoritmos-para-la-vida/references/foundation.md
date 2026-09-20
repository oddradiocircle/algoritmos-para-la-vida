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

## Referencias técnicas y de contexto

Las etiquetas numéricas usadas en las fichas corresponden a esta lista:

- **[1]** Stanford Computer Science, *A Guided Tour of Chapter 15: Multi-Armed Bandits: Exploration versus Exploitation*.
- **[2]** NYU Computer Science, *Algorithms and Everyday Life*.
- **[3]** Engineering for Data Science, *Algorithms to Live By*.
- **[4]** Summrize, *Algorithms to Live By by Brian Christian Book Summary*.
- **[10]** 80,000 Hours, entrevista a Brian Christian.
- **[11]** Henrik Singmann et al., *Full-Information Optimal-Stopping Problems: Providing People with the Optimal Policy does not Improve Performance*.
- **[12]** Thoughtful Technologist, *Overfitting... Echo Chambers*.
- **[13]** Cambridge, *Optimization and Control*.
- **[14]** Wikipedia en español, *Problema de la secretaria*.
- **[15]** Aprende Machine Learning, *Overfitting y underfitting*.
- **[18]** Wikipedia, *Secretary problem*.
- **[19]** IsMy.net, *Shortest Processing Time*.
- **[20]** Vivian Qu, *Simulated annealing: a life framework*.
- **[22]** Microsoft Learn, *The UCB1 Algorithm for Multi-Armed Bandit Problems*.
- **[23]** Matthijs Braspenning, *The Art of Scheduling*.
- **[24]** DZone, *The Fatal Flaws of Modern Algorithms*.
- **[25]** Atlantis Press, *The Review of Cooperation Mechanism of Repeated Game*.
- **[26]** Bohrium, *The Wisdom of Forgetting... LRU*.
- **[27]** Brera y Fu, *The satisficing secretary problem: when closed-form solutions meet simulated annealing*.
- **[28]** Aionlinecourse, *Upper Confidence Bound (UCB) Algorithm*.
- **[29]** Wikipedia, *Vickrey auction*.

Las fuentes secundarias sirven para contexto y explicación. Las afirmaciones
sobre salud, derecho, finanzas, seguridad, empleo, vivienda u otros asuntos de
alto impacto requieren fuentes actuales y especializadas.
