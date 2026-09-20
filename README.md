# Algoritmos para la vida

[![skills.sh](https://img.shields.io/badge/skills.sh-compatible-2563EB?style=flat-square)](https://skills.sh/)
[![Licencia MIT](https://img.shields.io/badge/licencia-MIT-2563EB?style=flat-square)](LICENSE)

Hay decisiones que no necesitan una fórmula perfecta, sino una forma más clara
de mirarlas.

**Algoritmos para la vida** es un skill en español para usar con agentes de IA.
Lleva heurísticas y conceptos de ciencias de la computación a decisiones
cotidianas: elegir entre varias opciones, saber cuándo dejar de buscar, ordenar
tareas, experimentar sin abandonar lo que ya funciona, cuidar la atención o
revisar una regla que no está dando el resultado esperado.

No decide por ti. Te ayuda a hacer visibles el objetivo, las alternativas, las
restricciones, los supuestos, la incertidumbre, el costo de equivocarte y el
momento en que conviene volver a revisar la decisión.

**No necesitas saber programar.**

[**Descargar el ZIP**](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/latest/download/algoritmos-para-la-vida-skill.zip)
·
[**Ver el SKILL.md**](skills/algoritmos-para-la-vida/SKILL.md)
·
[**Explorar el catálogo**](skills/algoritmos-para-la-vida/references/catalog.md)
·
[**Último release**](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/latest)

---

## Pruébalo en 30 segundos

Después de instalar el skill, prueba algo como:

> Tengo 30 días para buscar vivienda y las opciones pueden desaparecer. No
> quiero comparar para siempre. Ayúdame a definir cuándo dejar de buscar.

El skill debería ayudarte a distinguir qué sabes de lo que estás suponiendo,
preguntar solo por la información que pueda cambiar la decisión y escoger una
heurística apropiada sin aplicar automáticamente una fórmula.

También puedes probar:

> Tengo cinco tareas con duraciones y fechas distintas. ¿Qué criterio debería
> usar para decidir por cuál empezar?

> Quiero probar una forma nueva de estudiar sin abandonar inmediatamente la que
> ya me funciona. ¿Cómo puedo hacer un experimento pequeño?

> Explícame qué es satisficing y cuándo puede servirme.

---

## Instalación rápida

### ChatGPT

Descarga el [ZIP del último release](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/latest/download/algoritmos-para-la-vida-skill.zip).

En ChatGPT:

1. Abre **Plugins** desde la barra lateral.
2. Entra a **Skills**.
3. Selecciona **Create → Upload from your computer**.
4. Sube el ZIP.

La disponibilidad de Skills depende del producto, la cuenta y la configuración
del espacio de trabajo.

Consulta la [guía oficial de Skills en ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).

### Claude

Descarga el [ZIP del último release](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/latest/download/algoritmos-para-la-vida-skill.zip).

En Claude:

1. Abre **Customize → Skills**.
2. Selecciona **+ → Create skill**.
3. Elige **Upload a skill**.
4. Sube el ZIP.
5. Activa el skill.

Las habilidades personalizadas quedan asociadas inicialmente a tu cuenta. Su
disponibilidad puede depender del plan y de la configuración de la organización.

### Hermes Desktop

Hermes Desktop tiene una sección **Skills** para explorar e instalar skills del
catálogo disponible:

1. Abre **Skills**.
2. Busca el skill.
3. Selecciona **Install**.

Consulta la [documentación de Hermes Desktop](https://hermes-agent.nousresearch.com/docs/user-guide/desktop/).

---

## Instalación estándar con `npx skills`

Para agentes de terminal, esta es la ruta recomendada:

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida
```

Para instalarlo globalmente y tenerlo disponible en tus proyectos:

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --global
```

También puedes indicar explícitamente un agente:

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --agent <identificador>
```

Entre los agentes compatibles se encuentran **Claude Code, Codex, Cursor, Cline,
OpenCode, Roo Code, Windsurf y Hermes Agent**, además de otros destinos del
ecosistema Agent Skills.

Consulta la [documentación de skills.sh](https://www.skills.sh/).

### Hermes Agent

Hermes integra `skills.sh` y también permite instalar directamente desde este
repositorio. La ruta estándar recomendada es:

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --agent hermes
```

Si prefieres el instalador nativo de Hermes:

```bash
hermes skills install oddradiocircle/algoritmos-para-la-vida/skills/algoritmos-para-la-vida
```

Dentro de una sesión de Hermes también puedes usar:

```text
/skills install oddradiocircle/algoritmos-para-la-vida/skills/algoritmos-para-la-vida
```

Consulta la [guía de skills de Hermes Agent](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills/).

### Marketplace de Claude Code

Este repositorio también incluye un marketplace para Claude Code.

Añádelo:

```text
/plugin marketplace add oddradiocircle/algoritmos-para-la-vida
```

Después instala el plugin:

```text
/plugin install algoritmos-para-la-vida@algoritmos-para-la-vida
```

---

## Compatibilidad

El skill usa el formato `SKILL.md` del ecosistema Agent Skills y evita depender
de herramientas exclusivas de un solo proveedor.

| Entorno | Instalación recomendada |
|---|---|
| ChatGPT | ZIP |
| Claude | ZIP |
| Claude Code | `npx skills` o marketplace |
| Codex | `npx skills` |
| Cursor | `npx skills` |
| Cline | `npx skills` |
| Roo Code | `npx skills` |
| Windsurf | `npx skills` |
| OpenCode | `npx skills` |
| Hermes Agent | `npx skills` o `hermes skills install` |
| Otros agentes compatibles con Agent Skills | `npx skills` o instalación manual |

La compatibilidad básica no significa que todos los agentes implementen
exactamente las mismas funciones alrededor de un skill. Este proyecto procura
que su comportamiento central dependa de instrucciones y referencias portables,
no de extensiones exclusivas de una plataforma.

---

## Qué puede ayudarte a pensar

El catálogo está organizado alrededor de cuatro territorios.

### Elegir y parar

¿Cuándo vale la pena seguir buscando y cuándo una opción ya es suficientemente
buena?

Incluye ideas como:

- calibración y umbrales de parada;
- regla del 37 % y sus límites;
- satisficing;
- búsqueda con información;
- reglas de parada especializadas.

### Tiempo y atención

¿Cómo ordenar trabajo cuando tiempo, atención o capacidad son limitados?

Incluye:

- WSPT;
- Earliest Due Date;
- algoritmo de Moore;
- batching;
- cambio de contexto;
- caché LRU;
- manejo de backlog.

### Aprendizaje y exploración

¿Cuánto conviene seguir usando lo conocido y cuánto probar algo nuevo?

Incluye:

- exploración frente a explotación;
- epsilon-greedy;
- UCB cualitativo;
- actualización bayesiana;
- regularización;
- hill climbing;
- Monte Carlo;
- recocido simulado.

### Relaciones y recursos

¿Cómo pensar cooperación, incentivos, métricas y recursos compartidos?

Incluye:

- cooperación repetida;
- reciprocidad;
- diseño de mecanismos;
- subastas de Vickrey;
- ley de Goodhart;
- backoff y AIMD.

---

## Cómo trabaja

El skill no empieza buscando un algoritmo para aplicarlo a la fuerza.

Primero intenta entender:

- qué decisión o problema estás resolviendo;
- qué resultado sería suficientemente bueno;
- qué alternativas existen;
- qué restricciones no pueden ignorarse;
- cuánto tiempo tienes;
- qué sabes y qué estás suponiendo;
- qué cuesta esperar;
- qué cuesta equivocarse;
- si puedes volver atrás;
- qué otras personas reciben las consecuencias.

Después escoge la heurística mínima que pueda ayudar.

Cuando faltan datos, no los inventa. Cuando una fórmula exige condiciones que el
caso no cumple, debería decirlo. Y cuando una decisión es reversible y de bajo
riesgo, procura proponer una prueba pequeña en lugar de convertirla en una
optimización complicada.

---

## Ejemplos de uso

### Dejar de buscar

> Estoy buscando apartamento desde hace dos semanas y cada nueva opción me hace
dudar de las anteriores. Tengo un mes para decidir. ¿Cómo estructuro la búsqueda?

### Priorizar tareas

> Tengo cinco tareas, distintas duraciones y fechas límite. ¿Debería hacer
primero la más corta, la más urgente o la más importante?

### Experimentar

> Tengo una rutina que funciona razonablemente bien, pero quiero probar otra.
¿Cuánto debería explorar antes de cambiar?

### Actualizar una creencia

> Pensaba que esta forma de estudiar me funcionaba, pero llevo tres sesiones
malas. ¿Cómo separo una mala racha de evidencia suficiente para cambiar?

### Revisar una métrica

> Mi equipo mide productividad por número de tareas cerradas. La cifra mejora,
pero no estoy seguro de que el trabajo sea mejor.

### Entender un concepto

> ¿Qué es la ley de Goodhart?

> ¿Qué significa satisficing?

> ¿Cuál es la diferencia entre EDD, Moore y WSPT?

---

## Qué no hace

**Algoritmos para la vida** no convierte decisiones humanas en problemas
matemáticos por defecto.

En particular:

- no decide por ti;
- no ejecuta por ti acciones irreversibles;
- no inventa datos, precios, disponibilidad, normas o probabilidades;
- no trata una heurística como garantía de un resultado óptimo;
- no aplica el 37 % automáticamente a cualquier búsqueda;
- no confunde una analogía computacional con evidencia;
- no sustituye la verificación de hechos actuales;
- no sustituye asesoría médica, jurídica, financiera u otra asesoría profesional.

En decisiones de alto impacto, el skill sirve principalmente para organizar
preguntas, restricciones, evidencia y puntos de revisión.

---

## Seguridad y privacidad

La versión actual del skill está compuesta por instrucciones, referencias,
plantillas y metadatos de configuración.

**No incluye scripts ejecutables.**

Puedes revisar su contenido completo antes de instalarlo:

- [`SKILL.md`](skills/algoritmos-para-la-vida/SKILL.md)
- [`catalog.md`](skills/algoritmos-para-la-vida/references/catalog.md)
- [`foundation.md`](skills/algoritmos-para-la-vida/references/foundation.md)
- [`sources.md`](skills/algoritmos-para-la-vida/references/sources.md)
- [`evals.md`](skills/algoritmos-para-la-vida/references/evals.md)

El skill puede pedir al agente que consulte información externa cuando una
decisión depende de precios, disponibilidad, normas, evidencia u otros hechos
actuales. La capacidad de hacerlo depende de las herramientas y permisos
disponibles en el agente donde esté instalado.

---

## Qué contiene el repositorio

```text
.
├── .claude-plugin/
│   └── marketplace.json
├── skills/
│   └── algoritmos-para-la-vida/
│       ├── SKILL.md
│       ├── agents/
│       │   └── openai.yaml
│       ├── references/
│       │   ├── catalog.md
│       │   ├── evals.md
│       │   ├── foundation.md
│       │   └── sources.md
│       └── templates/
│           └── analisis-caso.md
├── CHANGELOG.md
├── LICENSE
└── README.md
```

### `SKILL.md`

Es el punto de entrada del skill. Define cuándo debe activarse, cómo analizar
una situación, cómo elegir una heurística y qué límites debe respetar.

### `catalog.md`

Contiene las fichas de las heurísticas: problema, idea, procedimiento,
información necesaria, supuestos, límites y riesgos.

### `foundation.md`

Reúne el fundamento conceptual que sostiene el catálogo.

### `sources.md`

Contiene la trazabilidad bibliográfica de las referencias utilizadas.

### `evals.md`

Incluye casos de evaluación manual para comprobar activación, selección de
heurística, factualidad, lenguaje claro y límites de seguridad.

### `analisis-caso.md`

Es una plantilla estructurada para analizar casos de manera reproducible.

---

## Inspiración

Este skill parte de las ideas de *Algorithms to Live By: The Computer Science of
Human Decisions*, de Brian Christian y Tom Griffiths, publicado en español como
*Algoritmos para la vida*.

El libro fue un punto de partida para explorar cómo conceptos de ciencias de la
computación pueden ayudar a pensar decisiones bajo tiempo, información y
capacidad limitados.

Este repositorio desarrolla una interpretación independiente, con:

- un catálogo propio;
- procedimientos de aplicación;
- referencias públicas;
- supuestos explícitos;
- límites de transferencia;
- evaluaciones del comportamiento del skill.

No es una traducción ni una adaptación oficial del libro y no está afiliado con
sus autores o su editorial.

---

## Principio de diseño

El objetivo del proyecto no es encontrar una fórmula para cada problema.

Una heurística es útil cuando hace visible un intercambio que antes estaba
escondido: buscar mejor frente a buscar más, explorar frente a explotar, ordenar
frente a ejecutar, medir frente a distorsionar una métrica.

Por eso el skill procura conservar cuatro cosas:

1. **Agencia humana:** la decisión sigue siendo de la persona.
2. **Supuestos visibles:** una regla solo tiene sentido bajo determinadas condiciones.
3. **Incertidumbre explícita:** no toda decisión admite una cifra precisa.
4. **Revisión:** una buena decisión provisional puede cambiar cuando aparece nueva información.

---

## Desarrollo y evaluación

El comportamiento esperado está documentado en
[`references/evals.md`](skills/algoritmos-para-la-vida/references/evals.md).

Entre otras cosas, los casos comprueban que el skill:

- explique conceptos sin iniciar interrogatorios innecesarios;
- no aplique automáticamente la regla del 37 %;
- separe datos verificables de preferencias;
- distinga entre WSPT, EDD y Moore según el objetivo;
- no convierta reciprocidad en represalia;
- no prescriba decisiones médicas;
- reconozca cuando ninguna heurística del catálogo es apropiada;
- prefiera experimentos pequeños en decisiones reversibles;
- rechace falsas precisiones;
- detecte problemas de Goodhart;
- no se active innecesariamente para tareas fuera de alcance.

Las evaluaciones son actualmente una guía de revisión humana, no una suite
automatizada.

---

## Versiones

Consulta el [historial de cambios](CHANGELOG.md) para ver las novedades de cada
versión.

El paquete listo para instalar se publica en [Releases](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases).

Para obtener siempre la versión más reciente:

[**Descargar el último ZIP**](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/latest/download/algoritmos-para-la-vida-skill.zip)

---

## Contribuciones

Las sugerencias son bienvenidas, especialmente cuando ayudan a:

- corregir una aplicación incorrecta de una heurística;
- identificar supuestos que no estén suficientemente explícitos;
- añadir mejores referencias;
- mejorar los casos de evaluación;
- documentar compatibilidad con otros agentes;
- encontrar ejemplos cotidianos donde una heurística funcione —o falle— de manera instructiva.

Puedes abrir un issue para proponer una mejora o reportar un problema.

---

## Licencia

MIT. Consulta [`LICENSE`](LICENSE).
