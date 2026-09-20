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
conversación o desde un agente que cargue skills. Elige la ruta que se parezca
más a la forma en que ya trabajas:

- **Aplicaciones conversacionales:** Claude Desktop o ChatGPT.
- **Agentes con instalación de skills:** Claude Code, Hermes Agent, Codex o
  Gemini CLI.
- **Otros agentes compatibles:** herramientas como Cursor, Windsurf, Cline,
  Roo Code, Goose u OpenCode.

## Instalación

### Claude Desktop

Claude Desktop recibe los skills como un paquete `.zip`.

1. Descarga o clona este repositorio.
2. Comprime la carpeta `skills/algoritmos-para-la-vida/` como un ZIP,
   conservando `SKILL.md` dentro de la carpeta del skill.
3. En Claude Desktop abre **Customize → Skills → + → Create skill → Upload a
   skill** y selecciona el ZIP.

Por ejemplo, desde una terminal macOS o Linux:

```bash
git clone --depth 1 https://github.com/oddradiocircle/algoritmos-para-la-vida.git /tmp/algoritmos-para-la-vida
cd /tmp/algoritmos-para-la-vida/skills
zip -r ~/Desktop/algoritmos-para-la-vida.zip algoritmos-para-la-vida
```

Consulta la [guía oficial para usar skills en Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

### ChatGPT

ChatGPT también permite cargar un paquete ZIP desde su interfaz:

1. Abre la sección **Skills** desde la barra lateral —en algunas cuentas
   aparece dentro de **Plugins**—.
2. Selecciona **Create → Upload from your computer**.
3. Sube el ZIP de `skills/algoritmos-para-la-vida/` preparado en la sección
   anterior.

La disponibilidad depende del plan y de la configuración del espacio de
trabajo. Consulta la [guía oficial de Skills en ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).

### Gemini

Para este formato, la ruta documentada es **Gemini CLI**. Instálalo para tu
usuario así:

```bash
gemini skills install \
  https://github.com/oddradiocircle/algoritmos-para-la-vida.git \
  --path skills/algoritmos-para-la-vida \
  --scope user \
  --consent
```

Para instalarlo solo en el proyecto actual, cambia `--scope user` por
`--scope workspace`. Comprueba el resultado con:

```bash
gemini skills list --all
```

También puedes escribir `/skills list all` dentro de una sesión de Gemini CLI.
Consulta la [documentación de skills de Gemini CLI](https://geminicli.com/docs/cli/skills/).

### Agentes con instalación de skills

La forma común de instalarlo es con [`skills.sh`](https://skills.sh/):

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida --skill algoritmos-para-la-vida
```

Este comando lo instala en el proyecto actual. Para una instalación global —que
quede disponible en tus proyectos— añade `--global` y elige el agente con
`--agent`.

#### Claude Code

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --agent claude-code \
  --global
```

Para instalarlo solo en el proyecto actual, omite `--global`. Claude Code carga
los skills personales desde `~/.claude/skills/` y los del proyecto desde
`.claude/skills/`.

Consulta la [documentación de skills de Claude Code](https://code.claude.com/docs/en/skills).

#### Hermes Agent

En Hermes, el comando sin `-p` usa el perfil activo. Para instalarlo en el
perfil predeterminado:

```bash
hermes profile use default
hermes skills install oddradiocircle/algoritmos-para-la-vida/skills/algoritmos-para-la-vida
```

Comprueba la instalación así:

```bash
hermes skills list --source hub
hermes skills check
```

Para un perfil específico, créalo si todavía no existe y antepón `-p` a los
comandos:

```bash
hermes profile create mi-perfil
hermes -p mi-perfil skills install oddradiocircle/algoritmos-para-la-vida/skills/algoritmos-para-la-vida
hermes -p mi-perfil skills list --source hub
```

Si quieres que ese perfil quede seleccionado como el predeterminado para las
siguientes sesiones:

```bash
hermes profile use mi-perfil
```

Consulta la [guía de skills de Hermes Agent](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills/)
y la [guía de perfiles](https://hermes-agent.nousresearch.com/docs/user-guide/profiles/).

#### Codex

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --agent codex \
  --global
```

Codex también reconoce skills personales en `~/.agents/skills/` y skills del
proyecto en `.agents/skills/`. Si no aparece de inmediato, reinicia Codex.

## Otras herramientas compatibles

`skills.sh` permite dirigir la instalación a otros agentes. Usa un identificador
por vez:

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida \
  --skill algoritmos-para-la-vida \
  --agent cursor \
  --global
```

Algunos identificadores habituales son:

| Herramienta | Identificador para `--agent` |
|---|---|
| Cursor | `cursor` |
| Windsurf | `windsurf` |
| Cline | `cline` |
| Roo Code | `roo` |
| Goose | `goose` |
| OpenCode | `opencode` |
| GitHub Copilot | `github-copilot` |

Sustituye `cursor` por el identificador de la herramienta que uses. Revisa la
[lista actual de agentes de skills.sh](https://www.skills.sh/docs/cli), porque
los nombres y destinos pueden cambiar. Si una herramienta no aparece en esa
lista, consulta su documentación para saber si admite el formato Agent Skills.

Puedes consultar el [historial de cambios](CHANGELOG.md) para ver qué trae cada
versión.

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

## Licencia

MIT. Consulta [`LICENSE`](LICENSE).
