# Algorithms for Life

Un skill de agente para usar heurísticas y conceptos de ciencias de la
computación al tomar decisiones cotidianas.

No decide por la persona. Ayuda a comparar opciones, priorizar, buscar,
experimentar y coordinar con lenguaje claro, supuestos explícitos, incertidumbre
visible y puntos de revisión.

## Instalación

Con [`skills.sh`](https://skills.sh/):

```bash
npx skills add oddradiocircle/algoritmos-para-la-vida --skill algoritmos-para-la-vida
```

El skill también puede instalarse desde el repositorio con la herramienta de
agentes que soporte el formato Agent Skills.

## Contenido

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

El catálogo incluye elección y parada, tiempo y atención, aprendizaje y
exploración, y relaciones y recursos. Las referencias avanzadas no se usan
como fórmulas universales. Las decisiones médicas, jurídicas, financieras, de
vivienda, empleo y otras decisiones de alto impacto requieren verificación y
apoyo profesional apropiados.

## Ejemplos de uso

- «Tengo varias opciones de vivienda y un plazo corto. ¿Cómo dejo de comparar?»
- «Tengo cinco tareas con fechas distintas. ¿Qué criterio uso para ordenarlas?»
- «Quiero probar dos hábitos sin abandonar lo que ya funciona. ¿Cómo diseño un
  experimento pequeño?»

## Qué no hace

- No decide por la persona ni ejecuta acciones irreversibles.
- No inventa precios, disponibilidad, normas, evidencia ni probabilidades.
- No sustituye asesoría médica, jurídica, financiera u otra asesoría profesional.
- No convierte una heurística en una garantía de resultado óptimo.

## Licencia

MIT. Consulta [`LICENSE`](LICENSE).
