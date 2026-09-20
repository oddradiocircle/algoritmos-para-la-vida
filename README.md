# Algoritmos para la vida

[![skills.sh](https://img.shields.io/badge/skills.sh-compatible-2563EB?style=flat-square)](https://skills.sh/)
[![Licencia MIT](https://img.shields.io/badge/licencia-MIT-2563EB?style=flat-square)](LICENSE)

Hay decisiones que no necesitan una fórmula perfecta, sino una forma más clara
de mirarlas.

**Algoritmos para la vida** es un skill de agente que lleva heurísticas y
conceptos de ciencias de la computación a decisiones cotidianas: elegir entre
varias opciones, dejar de buscar, ordenar tareas, probar un hábito, cuidar la
atención o revisar una regla que no está dando el resultado esperado.

No decide por ti. Te ayuda a ver qué estás tratando de lograr, qué información
tienes, qué estás suponiendo y qué paso pequeño podrías dar ahora. También hace
visibles la incertidumbre, los límites y el momento en que conviene volver a
revisar la decisión.

## Instalación

Instálalo con [`skills.sh`](https://skills.sh/):

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida --skill algoritmos-para-la-vida
```

También puedes instalarlo desde este repositorio con cualquier herramienta de
agentes compatible con el formato Agent Skills.

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
