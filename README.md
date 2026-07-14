# Agentes Curados · aitmpl.com

Selección curada de agentes pre-construidos para Claude Code, extraídos del catálogo
[claude-code-templates](https://github.com/davila7/claude-code-templates) (aitmpl.com).
No es una copia del catálogo: de 600+ componentes disponibles, estos 9 pasaron un
filtro de calidad y relevancia documentado abajo.

**Fuente:** [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) · 29.5k ★ · Licencia MIT
**Snapshot:** commit `acdb589` · extraído el 14/07/2026
**Curaduría y evaluación:** Hernán Castaño

---

## Por qué una curaduría y no el catálogo completo

La calidad del catálogo es muy despareja. En la misma categoría conviven agentes de
30 líneas genéricas (ej. `sales-automator`, 961 bytes: "lidera con valor, un CTA claro")
y agentes con ingeniería real (ej. `business-analyst`, 7.7 KB: criterios de pausa
human-in-the-loop, priorización MoSCoW, reglas anti-alucinación explícitas).

**Criterio de curaduría aplicado:**

1. **Filtro de tamaño** — se descartan archivos < 2 KB (esqueletos sin ingeniería)
2. **Auditoría del contenido** — lectura completa del prompt antes de incluirlo
3. **Relevancia** — solo agentes con cruce directo a casos de uso reales de mi operación
4. **Trazabilidad** — snapshot con SHA fijado, para que la fuente sea verificable

---

## Los 9 seleccionados

| Agente | Qué hace | Caso de uso real |
|---|---|---|
| `business-analyst` | Levantamiento de procesos con BPMN, MoSCoW y pausas human-in-the-loop | Entrevistas de agentificación (inventarios de procesos por equipo) |
| `power-bi-data-modeling-expert` | Modelado de datos en Power BI (esquema estrella, relaciones) | Proyecto Snowflake BI — capa Gold → dashboard |
| `power-bi-dax-expert` | Medidas DAX, optimización de cálculos | Proyecto Snowflake BI — KPIs del dashboard |
| `prompt-builder` | Construcción sistemática de prompts (el más completo del catálogo, 18 KB) | Benchmark contra mi propio Kit de Construcción de Agentes |
| `prompt-engineer` | Refinamiento y auditoría de prompts existentes | Complemento del anterior — ciclo de mejora de skills |
| `data-analyst` | Análisis de datos con visualizaciones ancladas a decisiones | Reportes operativos y de sprint |
| `seo-specialist` | Auditoría y estrategia SEO técnica | Equipo SEO/Web — soporte de skills existentes |
| `marketing-attribution-analyst` | Modelos de atribución multi-canal | Arquitectura SEM y reporting de campañas |
| `content-marketer` | Estrategia y producción de contenido | Skills de contenido del equipo de Marketing |

Los archivos en [`originales/`](./originales/) son los MD sin modificar, tal como
los distribuye el catálogo (inglés, formato oficial de subagentes de Claude Code).

---

## Lo más valioso no son los agentes: es el formato

Los agentes bien construidos del catálogo usan el formato oficial de **subagentes**
de Claude Code, que aporta tres cosas que un prompt plano no tiene:

```markdown
---
name: nombre-del-agente
description: Cuándo usarlo, con <example> y <commentary>  ← Claude Code delega
  automáticamente cuando la tarea coincide con esta descripción
model: sonnet                                             ← modelo por agente
tools: Read, Write, Grep                                  ← herramientas restringidas
---
Cuerpo del prompt...
```

- **Auto-delegación:** la `description` con ejemplos le enseña a Claude Code *cuándo*
  invocar el agente sin que el usuario lo pida
- **Control de herramientas:** cada agente solo accede a las tools que necesita
- **Modelo por tarea:** tareas mecánicas en modelos rápidos, análisis en modelos potentes

Este formato es el insumo para evolucionar los prompts del
[Kit de Construcción de Agentes](https://github.com/Herandres/Skills-triario/tree/master/kit-construccion-agentes).

---

## Cómo se instalan y se usan

```bash
# Instalación desde el catálogo (crea el MD en .claude/agents/ del proyecto)
npx claude-code-templates@latest --agent data-ai/prompt-builder --yes
```

Una vez en `.claude/agents/`, **Claude Code los invoca solo** cuando la tarea coincide
con la `description` del agente, o explícitamente: *"usa el agente prompt-builder para..."*.

> Nota: no se activan con "actúa como la habilidad X" — son subagentes, no personalidades.

---

## Regla de adopción

Estos archivos son **materia prima, no producto final**. Antes de usarlos en operación:

1. Traducir y adaptar al contexto (los prompts genéricos se traducen, no se adoptan)
2. Ajustar tono, dominios de datos y reglas anti-alucinación propias
3. Documentar la versión adaptada como cualquier skill propia

---

*Material de terceros bajo licencia MIT — atribución a [davila7](https://github.com/davila7)
y contribuidores de claude-code-templates. La curaduría, evaluación y criterios de
adopción son trabajo propio.*
