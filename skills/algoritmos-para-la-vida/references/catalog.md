# Catálogo inicial de heurísticas

Este catálogo organiza procedimientos de apoyo para decisiones cotidianas. Una
heurística es una regla práctica: reduce esfuerzo o estructura una decisión,
pero no garantiza el mejor resultado.

## Cómo leer una ficha

- **Problema:** qué tipo de situación reconoce.
- **Idea:** qué intercambio hace visible.
- **Procedimiento:** pasos mínimos para probarla.
- **Ejemplo:** una aplicación no técnica.
- **Información necesaria:** datos que cambian la recomendación.
- **Supuestos:** condiciones que deben revisarse.
- **Límites y riesgos:** cuándo puede fallar o causar daño.
- **Fuentes:** índices de `references/foundation.md`, donde se identifica cada
  referencia técnica y su uso dentro del skill.

## Taxonomía

| Dominio | Pregunta guía | Heurísticas iniciales |
|---|---|---|
| Elección y parada | ¿Cuándo sigo buscando y cuándo elijo? | calibración y umbral; umbral con información; satisficing; ordenar frente a buscar; odds especializado |
| Tiempo y atención | ¿En qué orden trabajo y cómo protejo la atención? | WSPT; fecha más próxima; Moore; batching; caché LRU; recortar backlog |
| Aprendizaje y exploración | ¿Cuánto experimento y cuánto uso lo conocido? | epsilon-greedy; UCB cualitativo; actualización bayesiana; regularización; búsqueda aproximada |
| Relaciones y recursos | ¿Cómo asigno recursos e influyo en reglas e incentivos? | reciprocidad; diseño de mecanismos; oferta veraz; auditoría de métricas; backoff/AIMD |

---

## 1. Elección y parada

### 1.1. Calibración y umbral de parada (regla del 37 %)

- **Problema:** hay una secuencia de opciones, solo se puede elegir una y las opciones rechazadas no vuelven.
- **Idea:** usar una primera parte para conocer el nivel de las opciones y después elegir la primera que supere la mejor referencia observada.
- **Objetivo formal:** maximizar la probabilidad de escoger la mejor opción en el problema de la secretaria, no maximizar satisfacción general ni minimizar el costo total de la búsqueda.
- **Procedimiento:** (1) estima el número total de oportunidades; (2) observa
  aproximadamente `1/e` de ellas sin comprometerte; si solo conoces el tiempo,
  úsalo como proxy únicamente cuando las oportunidades lleguen de forma
  aproximadamente uniforme durante un horizonte conocido; (3) registra la
  mejor referencia comparable; (4) acepta después la primera opción que la
  supere y cumpla las condiciones esenciales; (5) define antes de empezar una
  política de salida factible.
- **Política de salida:** si ninguna oportunidad posterior supera la referencia,
  aplica únicamente una alternativa que siga disponible: aceptar la última
  oportunidad si el proceso obliga a escoger, extender la búsqueda solo si es
  posible o terminar sin elegir. No supongas que puedes recuperar una opción
  rechazada.
- **Ejemplo:** en una búsqueda de vivienda de 30 días, usar los primeros días para calibrar precios y barrios; después elegir una opción que supere la referencia sin sacrificar seguridad o presupuesto.
- **Información necesaria:** duración de la búsqueda, posibilidad de volver atrás, criterios esenciales, costo de esperar y política de salida.
- **Supuestos:** orden razonablemente aleatorio, opciones comparables, decisión irrevocable, información principalmente ordinal y objetivo cercano a “la mejor opción”.
- **Límites y riesgos:** `37 %` no es una regla general para citas, empleo o compras; puede ser desastrosa si hay pocas opciones, alta urgencia, opción de volver, múltiples objetivos o una distribución sesgada.
- **Fuentes:** [2], [3], [4], [10], [11], [13], [14], [18].

### 1.2. Umbral con información completa

- **Problema:** se pueden estimar los valores de las opciones y el costo de esperar cambia con el tiempo.
- **Idea:** comparar cada opción con un umbral que depende de la información sobre futuras opciones, no aplicar una fase fija del 37 %.
- **Procedimiento:** (1) define si buscas maximizar o minimizar; (2) estima el rango y la distribución de resultados; (3) calcula un umbral cualitativo para el tiempo restante; (4) elige cuando la opción actual supera el umbral y satisface restricciones.
- **Ejemplo:** comprar un tiquete cuando el precio está por debajo de un límite razonable que se ajusta al día del viaje y a la probabilidad de encontrar algo mejor.
- **Información necesaria:** historial o referencia de precios, horizonte, probabilidad de cambio y costo de no comprar.
- **Supuestos:** información suficientemente confiable y opciones futuras comparables.
- **Límites y riesgos:** las estimaciones pueden ser falsas; un umbral no incorpora por sí solo preferencias, ansiedad, liquidez o consecuencias no monetarias.
- **Fuentes:** [11], [13], [14].

### 1.3. Satisficing: elegir una opción suficientemente buena

- **Problema:** buscar la mejor opción es costoso, pero se necesita alcanzar un estándar aceptable.
- **Idea:** sustituir “la número uno” por un umbral mínimo y relajar gradualmente el estándar si el tiempo se agota.
- **Procedimiento:** (1) define qué significa “suficientemente bueno”; (2) fija un umbral inicial; (3) amplía el conjunto de opciones aceptables solo cuando el costo de esperar lo justifique; (4) conserva las condiciones no negociables.
- **Ejemplo:** contratar a una persona que cumple las competencias esenciales y el presupuesto, sin prolongar indefinidamente la búsqueda por una candidata hipotéticamente perfecta.
- **Información necesaria:** condiciones indispensables, preferencias, tiempo restante y costo de una opción subóptima.
- **Supuestos:** la calidad puede evaluarse con criterios consistentes y hay más de un resultado aceptable.
- **Límites y riesgos:** rebajar el umbral bajo presión puede normalizar riesgos; no sirve para omitir controles legales, médicos o de seguridad.
- **Fuentes:** [27], [2], [3].

### 1.4. Ordenar frente a buscar

- **Problema:** hay que decidir si invertir tiempo en organizar información antes de consultarla.
- **Idea:** ordenar es una inversión que solo compensa si habrá suficientes búsquedas futuras.
- **Procedimiento:** (1) estima cuántas veces consultarás; (2) compara el costo de ordenar con el ahorro por consulta; (3) ordena solo si el uso esperado lo justifica; (4) usa búsqueda directa o una lista corta cuando el conjunto sea pequeño.
- **Ejemplo:** no clasificar cada documento doméstico por categorías complejas si solo se buscará una vez; sí crear un sistema simple para facturas consultadas cada mes.
- **Información necesaria:** tamaño del conjunto, frecuencia de consulta, costo de ordenar y posibilidad de cambios.
- **Supuestos:** el ordenamiento es estable y reduce efectivamente el tiempo de consulta.
- **Límites y riesgos:** la analogía técnica puede ignorar accesibilidad, memoria, colaboración y el valor de descubrir algo por accidente.
- **Fuentes:** [2], [3], [9].

### 1.5. Regla de odds para el último resultado favorable (referencia avanzada)

- **Problema:** se observan eventos binarios secuenciales y se quiere detenerse en el último éxito.
- **Idea:** sumar hacia atrás las probabilidades relativas de éxito para encontrar desde qué punto conviene aceptar el primer éxito.
- **Procedimiento formal:** para probabilidades independientes `p_i`, calcula `r_i = p_i / (1 - p_i)`; si la suma de odds alcanza al menos 1, identifica el último índice `s` para el que `r_s + ... + r_n >= 1` y acepta el primer éxito desde `s`; si la suma total es menor que 1, el umbral formal empieza al inicio. Solo calcula esto con probabilidades definidas y la ficha o fuente avanzada a la vista.
- **Ejemplo:** planificar una secuencia de revisiones donde solo interesa capturar el último resultado que cumple una condición previamente definida, no escoger la “mejor” opción humana.
- **Información necesaria:** probabilidades por etapa, independencia, secuencia fija y definición precisa de éxito.
- **Supuestos:** independencia, secuencia fija y objetivo explícito de detenerse en el último éxito.
- **Límites y riesgos:** no es una variante cotidiana de la regla del 37 %; no usar para decisiones humanas multidimensionales ni para justificar una cifra inventada. Si no se pueden estimar los `p_i`, usa una regla cualitativa y no la fórmula.
- **Fuentes:** [13].

---

## 2. Tiempo y atención

### 2.1. WSPT: peso o valor relativo dividido por duración

- **Problema:** varias tareas compiten por una capacidad limitada y se quiere reducir pronto el tiempo de terminación ponderado.
- **Idea:** en el modelo formal, ordenar por `peso / duración` favorece tareas cortas con mayor peso; en la vida cotidiana, el valor relativo solo es un proxy y debe declararse como tal.
- **Procedimiento:** (1) estima duración y asigna un peso o valor relativo con un criterio explícito; (2) calcula aproximadamente `peso / duración` o, si no hay pesos formales, `valor relativo / duración`; (3) trabaja primero en las tareas con mayor razón; (4) revisa cuando cambien el plazo, la energía, las dependencias o el costo humano.
- **Ejemplo:** resolver primero un trámite de 20 minutos que evita una multa antes que perfeccionar durante tres horas un documento no urgente.
- **Información necesaria:** duración, peso o valor relativo, fecha límite, dependencias y costo de interrupción.
- **Supuestos:** el objetivo se aproxima a reducir el tiempo de terminación ponderado y las estimaciones son comparables; no se confunde valor subjetivo con el peso formal del modelo.
- **Límites y riesgos:** puede posponer tareas largas esenciales, trabajo de cuidado o tareas cuyo valor no cabe en una cifra. EDD o una revisión ética puede ser preferible si la urgencia, la equidad o las dependencias dominan.
- **Fuentes:** [2], [3], [19], [23].

### 2.2. EDD: fecha de entrega más próxima

- **Problema:** varias tareas tienen fechas límite y el retraso máximo importa.
- **Idea:** atender primero la fecha más próxima reduce el peor retraso en modelos de programación determinados.
- **Procedimiento:** (1) lista fechas reales; (2) separa tareas bloqueadas o dependientes; (3) prioriza la fecha más cercana; (4) reserva margen para imprevistos; (5) renegocia antes de incumplir.
- **Ejemplo:** preparar primero un documento cuyo plazo vence mañana, aunque otra tarea sea más interesante.
- **Información necesaria:** fechas, duración, dependencias, consecuencias del retraso y margen disponible.
- **Supuestos:** las fechas son comparables y el objetivo principal es controlar retrasos.
- **Límites y riesgos:** puede producir urgencia permanente y sacrificar trabajo importante sin fecha; no sustituye priorizar salud, descanso o compromisos éticos.
- **Fuentes:** [2], [4], [6], [23].

### 2.3. Moore: reducir el número de tareas atrasadas

- **Problema:** no es posible completar todo a tiempo y se quiere minimizar cuántas tareas quedan atrasadas.
- **Idea:** cuando una tarea provoca atraso, retirar temporalmente la tarea más larga puede conservar más entregas a tiempo.
- **Procedimiento:** ordenar por fecha; acumular tareas; si aparece atraso, identifica la tarea más larga y renegocia, delega o retírala; vuelve a insertar solo si la capacidad cambia.
- **Ejemplo:** ante una semana sobrecargada, proteger cuatro compromisos pequeños y renegociar el proyecto que requiere más horas.
- **Información necesaria:** duración, fechas, posibilidad de dividir o delegar y costo de retirar cada tarea.
- **Supuestos:** el objetivo es el número de tareas a tiempo, no el valor total ni la equidad de la carga.
- **Límites y riesgos:** una tarea larga puede ser la más importante; retirar tareas sin comunicarlo desplaza el costo a otras personas.
- **Fuentes:** [2], [13].

### 2.4. Batching y protección contra el cambio de contexto

- **Problema:** interrupciones y cambios frecuentes consumen la capacidad de terminar.
- **Idea:** agrupar actividades similares reduce el costo de cargar de nuevo el contexto mental.
- **Procedimiento:** (1) identifica interrupciones repetidas; (2) crea ventanas para correo, mensajes o reuniones; (3) termina una unidad razonable antes de cambiar; (4) conserva excepciones para urgencias reales; (5) revisa si el batching retrasa información crítica.
- **Ejemplo:** revisar mensajes dos o tres veces al día en lugar de interrumpir cada bloque de estudio.
- **Información necesaria:** frecuencia, costo de interrupción, urgencias y tamaño de una unidad de trabajo.
- **Supuestos:** las tareas toleran espera y el beneficio de continuidad supera el costo de responder más tarde.
- **Límites y riesgos:** aislarse puede perjudicar coordinación, cuidado o seguridad; no convertirlo en una regla rígida.
- **Fuentes:** [2], [3], [9].

### 2.5. Caché LRU: conservar lo usado recientemente

- **Problema:** el espacio o la atención son limitados y se debe decidir qué mantener disponible.
- **Idea:** la actividad reciente puede indicar uso próximo; retirar lo menos usado libera capacidad.
- **Procedimiento:** (1) define el espacio limitado; (2) registra qué se usa; (3) mantiene accesible lo usado recientemente; (4) revisa periódicamente lo que no se usa; (5) conserva excepciones por valor, seguridad o memoria afectiva.
- **Ejemplo:** mantener a mano documentos de trámites activos y archivar los que no se consultan, sin eliminar documentos legales necesarios.
- **Información necesaria:** frecuencia y recencia de uso, costo de recuperar algo y valor de conservarlo.
- **Supuestos:** existe localidad temporal y lo usado recientemente volverá a usarse.
- **Límites y riesgos:** lo antiguo puede ser importante; la recencia no equivale a valor, prioridad ni verdad.
- **Fuentes:** [2], [3], [26].

### 2.6. Recortar el backlog cuando la cola deja de servir

- **Problema:** una lista o cola demasiado larga impide responder y oculta lo importante.
- **Idea:** descartar, delegar o cerrar entradas puede recuperar capacidad, igual que un sistema congestionado necesita liberar carga.
- **Procedimiento:** clasifica cada entrada como hacer, delegar, aplazar con fecha o cerrar; establece un límite visible; comunica lo que no se hará; revisa el límite en una fecha concreta.
- **Ejemplo:** cerrar suscripciones y solicitudes que ya no tienen valor en vez de mantener una lista imposible.
- **Información necesaria:** valor, fecha, dependencia, responsable y costo de mantener la entrada.
- **Supuestos:** las entradas pueden cerrarse o renegociarse sin consecuencias graves.
- **Límites y riesgos:** “cerrar” no debe ocultar obligaciones ni trasladar trabajo sin acuerdo.
- **Fuentes:** [2], [3].

---

## 3. Aprendizaje y exploración

### 3.1. Epsilon-greedy: experimentar con una frecuencia explícita

- **Problema:** ya existe una opción conocida, pero no se sabe si otra puede ser mejor.
- **Idea:** usar la opción que parece mejor la mayoría de las veces y reservar una proporción para probar alternativas.
- **Procedimiento:** (1) define una proporción inicial de experimentación; (2) prueba alternativas de bajo costo; (3) registra resultados; (4) reduce la exploración solo si el entorno es estable; (5) vuelve a explorar cuando cambien las condiciones.
- **Ejemplo:** usar el método de estudio habitual cuatro días y probar otro un día, comparando comprensión y esfuerzo.
- **Información necesaria:** resultado observable, costo de experimentar, horizonte y velocidad de cambio.
- **Supuestos:** la recompensa es medible y las pruebas son razonablemente comparables.
- **Límites y riesgos:** la aleatoriedad puede ser costosa; reducir `epsilon` automáticamente puede congelar una mala elección.
- **Fuentes:** [1], [22], [28].

### 3.2. UCB cualitativo: optimismo frente a la incertidumbre

- **Problema:** una alternativa tiene buen resultado observado y otra tiene pocos datos.
- **Idea:** evaluar el resultado esperado más un bono por incertidumbre, para no confundir falta de pruebas con falta de valor.
- **Procedimiento:** puntúa cada opción por resultado observado y confianza; aumenta la prioridad de las poco probadas; prueba primero si el costo es bajo; actualiza con resultados comparables.
- **Ejemplo:** no descartar un curso nuevo porque solo tiene dos reseñas; probar una unidad antes de inscribirse en un programa costoso.
- **Información necesaria:** resultados, cantidad de observaciones, variabilidad y costo de prueba.
- **Supuestos:** recompensas relativamente estables, observaciones comparables y ausencia de sesgo fuerte en la muestra.
- **Límites y riesgos:** el bono no debe inventar precisión; un entorno que cambia requiere exploración continua y no una garantía de UCB1.
- **Fuentes:** [1], [22], [28].

### 3.3. Actualización bayesiana cualitativa

- **Problema:** llega evidencia nueva sobre una creencia o una opción incierta.
- **Idea:** combinar una expectativa inicial con la calidad y fuerza de la evidencia, en vez de reaccionar como si cada dato fuera concluyente.
- **Procedimiento:** (1) declara la creencia inicial; (2) estima cuán compatible es la evidencia con cada explicación; (3) ajusta la confianza proporcionalmente; (4) registra qué evidencia podría cambiarla otra vez.
- **Ejemplo:** actualizar la confianza en que una técnica de aprendizaje funciona después de varias sesiones comparables, sin concluir por una sola sesión buena o mala.
- **Información necesaria:** hipótesis, evidencia, confiabilidad de la fuente y alternativas plausibles.
- **Supuestos:** las hipótesis están definidas y la evidencia aporta información relevante.
- **Límites y riesgos:** los sesgos iniciales pueden dominar; no usar una probabilidad subjetiva para dar apariencia científica a una intuición.
- **Fuentes:** [2], [3], [12].

### 3.4. Regularización y parada temprana contra el sobreajuste

- **Problema:** una regla explica muy bien experiencias pasadas, pero puede fallar en situaciones nuevas.
- **Idea:** limitar complejidad y detener la optimización antes de ajustar el ruido.
- **Procedimiento:** (1) separa señales estables de detalles accidentales; (2) usa pocas variables relevantes; (3) prueba la regla en casos distintos; (4) detén la búsqueda cuando las mejoras sean marginales; (5) conserva una revisión humana.
- **Ejemplo:** no elegir una carrera por una única experiencia excepcional ni construir una rutina con veinte condiciones que solo funcionó una semana.
- **Información necesaria:** muestra de experiencias, casos nuevos, variables usadas y costo de complejidad.
- **Supuestos:** hay riesgo de confundir ruido con patrón y se pueden observar casos fuera de la muestra inicial.
- **Límites y riesgos:** simplificar demasiado puede ignorar diferencias importantes; “parar pronto” no es excusa para no aprender.
- **Fuentes:** [2], [12], [15].

### 3.5. Hill climbing: mejorar una opción cercana

- **Problema:** hay muchas combinaciones y calcular la mejor solución sería demasiado costoso.
- **Idea:** empezar con una opción viable y conservar cambios cercanos que mejoren el criterio elegido.
- **Procedimiento:** (1) define una función de calidad; (2) elige una solución inicial; (3) genera una alternativa cercana; (4) conserva la mejora; (5) detén la búsqueda cuando no haya mejora suficiente o se alcance el límite de tiempo.
- **Ejemplo:** reorganizar una habitación cambiando un mueble cada vez y conservar los cambios que mejoren circulación, luz y costo.
- **Información necesaria:** criterio de calidad, variaciones posibles, solución inicial, costo de probar y límite de búsqueda.
- **Supuestos:** las variaciones cercanas son informativas y una mejora local tiene algún valor práctico.
- **Límites y riesgos:** puede quedarse en un óptimo local; la métrica elegida puede omitir bienestar, accesibilidad o justicia.
- **Fuentes:** [2], [20].

### 3.6. Monte Carlo: comparar muestras de escenarios

- **Problema:** no se puede conocer con exactitud el resultado de muchas combinaciones o escenarios inciertos.
- **Idea:** muestrear alternativas o futuros plausibles y observar qué opciones funcionan de forma suficientemente robusta.
- **Procedimiento:** (1) define escenarios y variables inciertas; (2) genera una muestra razonable; (3) registra resultados y variabilidad; (4) compara desempeño promedio y casos malos; (5) elige solo si la conclusión resiste cambios plausibles.
- **Ejemplo:** probar distintas rutas y horarios de un viaje con retrasos posibles antes de decidir, en lugar de optimizar una sola predicción.
- **Información necesaria:** escenarios, rangos o distribuciones justificables, criterio de calidad y costo de simular o probar.
- **Supuestos:** los escenarios representan razonablemente la incertidumbre y las muestras no ocultan riesgos extremos.
- **Límites y riesgos:** simular entradas inventadas produce una precisión falsa; un promedio favorable puede ocultar resultados inaceptables.
- **Fuentes:** [2], [27].

### 3.7. Recocido simulado: explorar antes de estabilizar

- **Problema:** una búsqueda local mejora al principio, pero queda atrapada en una solución que no es suficientemente buena.
- **Idea:** aceptar ocasionalmente una alternativa peor al inicio para explorar; reducir gradualmente esa tolerancia para estabilizarse después.
- **Procedimiento:** (1) define el criterio y una solución inicial; (2) prueba cambios cercanos; (3) al comienzo permite algunos retrocesos si abren regiones nuevas; (4) reduce esa tolerancia con un calendario explícito; (5) detén la búsqueda con un límite y revisa la solución humana resultante.
- **Ejemplo:** probar varias distribuciones de una mudanza, incluso una temporalmente peor, antes de quedarse con una que equilibre circulación, costo y esfuerzo.
- **Información necesaria:** criterio de calidad, alternativas vecinas, calendario de exploración, costo de probar y límite de búsqueda.
- **Supuestos:** las alternativas cercanas pueden revelar soluciones mejores y existe margen para experimentar.
- **Límites y riesgos:** puede aceptar una solución inferior, consumir recursos o legitimar una métrica estrecha; no garantiza la solución global.
- **Fuentes:** [20], [27].

---

## 4. Relaciones y recursos

### 4.1. Cooperación repetida y reciprocidad

- **Problema:** las mismas personas interactúan varias veces y sus decisiones afectan la cooperación futura.
- **Idea:** la reputación, la respuesta proporcional y la posibilidad de continuar pueden hacer sostenible la cooperación.
- **Procedimiento:** acuerda expectativas; empieza cooperando cuando sea seguro; responde a incumplimientos de forma proporcional; repara cuando la otra parte corrige; establece una salida ante abuso persistente.
- **Ejemplo:** repartir tareas domésticas con un acuerdo visible y revisar el reparto cuando una persona no puede cumplir, en vez de convertir un incumplimiento aislado en una guerra.
- **Información necesaria:** repetición, capacidad de comunicación, reciprocidad, consecuencias y asimetrías de poder.
- **Supuestos:** hay interacción futura y posibilidad de observar o explicar las acciones.
- **Límites y riesgos:** reciprocidad no justifica represalias; no usarla para permanecer en relaciones inseguras o abusivas.
- **Fuentes:** [25], [2].

### 4.2. Diseño de mecanismos e incentivos

- **Problema:** una regla o métrica produce conductas distintas de las intenciones declaradas.
- **Idea:** cambiar la estructura del juego puede ser más efectivo que pedir a cada persona que se esfuerce más.
- **Procedimiento:** (1) define el resultado deseado; (2) identifica lo que cada participante gana o pierde; (3) busca efectos secundarios; (4) prueba reglas pequeñas y reversibles; (5) revisa quién asume los costos.
- **Ejemplo:** un equipo que mide solo número de tareas puede mejorar la métrica y empeorar la calidad; añadir revisión y satisfacción cambia el incentivo.
- **Información necesaria:** participantes, reglas, recompensas, costos, información asimétrica y efectos sobre terceros.
- **Supuestos:** las personas responden al entorno de incentivos y las reglas pueden modificarse.
- **Límites y riesgos:** no todo comportamiento es reducible a incentivos; diseñar reglas sin participación puede ser injusto.
- **Fuentes:** [2], [3], [10], [25].

### 4.3. Oferta veraz como reducción de complejidad (Vickrey)

- **Problema:** negociar exige adivinar cuánto ofrecer y qué ofrecerán las demás personas.
- **Idea:** algunos mecanismos pueden alinear la acción estratégica con la valoración real y reducir la necesidad de razonamiento recursivo.
- **Procedimiento:** solo aplicar si las reglas están formalizadas; define el valor máximo que aceptarías; no lo aumentes para ganar; verifica precio, garantías y posibilidad de retiro.
- **Ejemplo:** usar un límite honesto en una subasta de objetos, sin seguir pujando por superar a otra persona.
- **Información necesaria:** valor propio, reglas de pago, participantes y consecuencias de ganar.
- **Supuestos:** subasta cerrada de segundo precio, valoración privada, ausencia de colusión, reglas de pago verificables, capacidad real de pagar la oferta y bienes compatibles con el modelo.
- **Límites y riesgos:** la mayoría de negociaciones no son subastas de Vickrey; información incompleta, colusión o reglas distintas invalidan la conclusión.
- **Fuentes:** [2], [29].

### 4.4. Auditoría de métricas y ley de Goodhart

- **Problema:** una medida se convierte en objetivo y deja de representar el resultado que importaba.
- **Idea:** toda métrica es un indicador parcial; al optimizarla, las personas pueden aprender a jugar con ella.
- **Procedimiento:** (1) escribe el objetivo real; (2) lista qué mide y qué excluye la métrica; (3) imagina cómo cumplirla sin lograr el objetivo; (4) añade controles cualitativos o métricas de daño; (5) revisa periódicamente.
- **Ejemplo:** medir solo horas estudiadas puede aumentar el tiempo sentado sin aumentar aprendizaje; añadir recuperación y comprensión evita premiar el agotamiento.
- **Información necesaria:** objetivo, métrica, conductas incentivadas, casos de gaming y efectos no deseados.
- **Supuestos:** el indicador es un proxy imperfecto y las personas adaptan su conducta a los incentivos.
- **Límites y riesgos:** añadir demasiadas métricas produce burocracia y thrashing; no todo valor debe cuantificarse.
- **Fuentes:** [2], [12], [24].

### 4.5. Backoff y AIMD: reducir carga y volver gradualmente

- **Problema:** varios participantes solicitan atención o recursos hasta generar congestión.
- **Idea:** ante señales de saturación conviene retroceder; cuando hay capacidad, aumentar gradualmente en lugar de volver de golpe.
- **Procedimiento:** define señales de saturación; pausa o reduce solicitudes; espera un intervalo creciente si el problema persiste; reanuda con incrementos pequeños; establece límites y una vía de urgencia.
- **Ejemplo:** acordar que una conversación difícil se pausa 30 minutos y se retoma después, en vez de enviar mensajes cada vez más frecuentes.
- **Información necesaria:** capacidad, señal de saturación, costo de esperar, tasa de recuperación y prioridad.
- **Supuestos:** la congestión es temporal y la reducción de carga permite recuperación.
- **Límites y riesgos:** puede parecer evasión o castigo; no usarlo para ignorar una emergencia ni para controlar unilateralmente a otra persona.
- **Fuentes:** [2], [3].

---

## Índice por tipo de problema

| Si el caso principal es… | Empezar por… | Comparar con… |
|---|---|---|
| Seguir buscando o elegir | calibración y umbral | umbral con información; satisficing |
| Encontrar lo suficientemente bueno | satisficing | parada estricta |
| Ordenar información | ordenar frente a buscar | caché LRU |
| Muchas tareas y poco tiempo | WSPT | EDD o Moore |
| Muchas interrupciones | batching | recortar backlog |
| Mantener cosas accesibles | LRU | ordenar frente a buscar |
| Probar alternativas | epsilon-greedy | UCB cualitativo |
| Cambiar una creencia | actualización bayesiana | regularización contra una sola experiencia |
| Optimizar una regla pasada | regularización | búsqueda aproximada |
| Coordinar repetidamente | cooperación y reciprocidad | diseño de incentivos |
| Definir una métrica | auditoría de Goodhart | diseño de mecanismos |
| Saturación o exceso de solicitudes | backoff/AIMD | batching y límites |

## Criterios para escoger o comparar heurísticas

1. **Objetivo:** ¿busca la mejor opción, una opción suficiente, rapidez, aprendizaje, equidad o estabilidad?
2. **Horizonte:** ¿la decisión es única, repetida o reversible?
3. **Información:** ¿hay datos completos, rankings relativos, evidencia parcial o solo intuiciones?
4. **Estabilidad:** ¿las recompensas y preferencias permanecen o cambian?
5. **Costo de error:** ¿es pequeño, reversible o de alto impacto?
6. **Costo de aplicar la regla:** ¿pensarla y medirla consume más que la mejora esperada?
7. **Personas afectadas:** ¿la regla distribuye costos, crea incentivos o requiere consentimiento?
8. **Valor omitido:** ¿qué dimensión importante no captura la métrica?
9. **Simplicidad y explicación:** ¿la persona puede ejecutar y revisar la regla?
10. **Punto de revisión:** ¿cuándo se comprobará si la heurística está funcionando?

Cuando dos heurísticas parezcan razonables, el skill debe explicar la diferencia de objetivo o supuesto y recomendar una prueba pequeña, reversible y explícita, en lugar de presentar una ganadora universal.
