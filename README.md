# Algoritmos para la vida

[![skills.sh](https://img.shields.io/badge/skills.sh-compatible-2563EB?style=flat-square)](https://skills.sh/)
[![Licencia MIT](https://img.shields.io/badge/licencia-MIT-2563EB?style=flat-square)](LICENSE)

Hay decisiones que no necesitan una fórmula perfecta, sino una forma más clara
de mirarlas.

**Algoritmos para la vida** es un skill para usar con agentes de IA. Lleva
heurísticas y conceptos de ciencias de la computación a decisiones cotidianas:
elegir entre varias opciones, dejar de buscar, ordenar tareas, probar un
hábito, cuidar la atención o revisar una regla que no está dando el resultado
esperado.

No decide por ti. Te ayuda a ver qué estás tratando de lograr, qué información
tienes, qué estás suponiendo y qué paso pequeño podrías dar ahora. También hace
visibles la incertidumbre, los límites y el momento en que conviene volver a
revisar la decisión.

## Inspiración

Este skill parte de las ideas de *Algorithms to Live By: The Computer Science of
Human Decisions*, de Brian Christian y Tom Griffiths, publicado en español como
*Algoritmos para la vida*.

El libro fue un punto de partida para conectar conceptos de ciencias de la
computación con decisiones cotidianas. Este repositorio desarrolla una
interpretación independiente, con un catálogo propio, referencias públicas y
límites explícitos. No es una traducción, adaptación oficial ni un proyecto
afiliado con sus autores o su editorial.

## Dónde usarlo

No necesitas saber programar. Puedes usarlo desde una aplicación de
conversación o desde un agente que cargue skills:

- **Aplicaciones conversacionales:** Claude Desktop, ChatGPT o Hermes Desktop.
- **Agentes con instalación de skills:** Claude Code, Hermes Agent (CLI) o
  Codex.
- **Otros agentes compatibles:** Cursor, Windsurf, Cline, Roo Code, Goose u
  OpenCode.

## Instalación sencilla

### Claude Desktop — Mac o Windows

Claude Desktop permite cargar un skill como un archivo `.zip`:

1. Descarga el [ZIP del release v0.2.0](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/download/v0.2.0/algoritmos-para-la-vida-skill.zip).
2. En Claude Desktop abre **Customize → Skills → + → Create skill → Upload a
   skill** y selecciona el ZIP.

Si no ves la sección **Skills**, puede que la función todavía no esté disponible
para tu cuenta o espacio de trabajo.

### ChatGPT — Mac o Windows

En la aplicación de ChatGPT para macOS o Windows, el procedimiento es el mismo
si tu cuenta o espacio de trabajo tiene disponible la función **Skills**:

1. Abre **Skills** desde la barra lateral —en algunas cuentas aparece dentro de
   **Plugins**—.
2. Selecciona **Create → Upload from your computer**.
3. Descarga el [ZIP del release v0.2.0](https://github.com/oddradiocircle/algoritmos-para-la-vida/releases/download/v0.2.0/algoritmos-para-la-vida-skill.zip) y súbelo.

La documentación oficial no describe una instalación directa desde la URL de
GitHub escribiendo una instrucción en el chat. Si no aparece **Skills**, la
función puede depender de tu plan o de la configuración del espacio de trabajo.
Consulta la [guía oficial de Skills en ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).

### Hermes Desktop

Hermes Desktop tiene una sección **Skills** para explorar e instalar skills del
catálogo disponible:

1. Abre **Skills**.
2. Busca el skill.
3. Selecciona **Install**.

Consulta la [documentación de Hermes Desktop](https://hermes-agent.nousresearch.com/docs/user-guide/desktop/).

## Instalación estándar

Para agentes de terminal, la ruta recomendada es [`npx skills`](https://www.skills.sh/):

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --global
```

Esto instala el skill para tus proyectos. Para instalarlo solo en el proyecto
actual, omite `--global`. Si necesitas elegir un agente compatible, añade
`--agent <identificador>`.

### Hermes Agent CLI

Hermes Agent todavía no figura entre los destinos publicados por `skills.sh`.
Si usas su CLI, instala el skill con su comando nativo:

```bash
hermes skills install oddradiocircle/algoritmos-para-la-vida/skills/algoritmos-para-la-vida
```

Consulta la [guía de skills de Hermes Agent](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills/).

### Alternativa: marketplace de Claude

En Claude Code, puedes instalar el marketplace con:

```text
/plugin marketplace add oddradiocircle/algoritmos-para-la-vida
/plugin install algoritmos-para-la-vida@algoritmos-para-la-vida
```

## Qué encontrarás

```text
skills/algoritmos-para-la-vida/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── catalog.md
│   ├── evals.md
│   ├── foundation.md
│   └── sources.md
└── templates/analisis-caso.md
```

El catálogo recorre cuatro territorios que suelen mezclarse en la vida real:

- **Elegir y parar:** cuándo seguir buscando y cuándo una opción ya es suficiente.
- **Tiempo y atención:** cómo ordenar tareas, proteger la concentración y soltar
  carga que ya no sirve.
- **Aprendizaje y exploración:** cuánto conviene probar algo nuevo y cuánto
  confiar en lo que ya funciona.
- **Relaciones y recursos:** cómo cooperar, repartir recursos y revisar las
  reglas que producen ciertos comportamientos.

Las referencias más técnicas aparecen con sus condiciones y límites. No son
fórmulas universales. En decisiones médicas, jurídicas, financieras, de
vivienda, empleo, seguridad u otros asuntos de alto impacto, hace falta
verificar la información vigente y buscar el apoyo profesional adecuado.

## Algunos ejemplos

- «Tengo varias opciones de vivienda y un plazo corto. ¿Cómo dejo de comparar?»
- «Tengo cinco tareas con duraciones y fechas distintas. ¿Qué criterio uso para
  ordenarlas?»
- «Quiero probar dos hábitos sin abandonar lo que ya funciona. ¿Cómo diseño un
  experimento pequeño?»

## Qué no hace

- No decide por ti ni ejecuta acciones irreversibles.
- No inventa precios, disponibilidad, normas, evidencia ni probabilidades.
- No sustituye asesoría médica, jurídica, financiera u otra asesoría profesional.
- No convierte una heurística en una garantía de resultado óptimo.

Puedes consultar el [historial de cambios](CHANGELOG.md) para ver qué trae cada
versión.

## Licencia

MIT. Consulta [`LICENSE`](LICENSE).
