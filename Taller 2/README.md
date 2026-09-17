# Actividad IA Resistente — Nivel 3
## Del stakeholder al problema validado

**Programa:** Tecnología en Sistematización de Datos
**Universidad:** Distrital Francisco José de Caldas
**Asignatura:** Ingeniería de Software
**Fecha de entrega:** 16 de septiembre de 2026

---

## 1. Identificación del squad

| Campo | Dato |
|---|---|
| **Equipo / Squad** | Squad 06 |
| **Integrantes** | Julián David Oviedo . Leonardo Fonseca Palma · Juan Sebastian Pineda
| **Sistema analizado** | Sistema de Gestión Integral para Veterinaria Sandoval (SGV) |
| **Repositorio GitHub** | `https://github.com/CarlosRoldon/Scrum_Jira_AS_G6/tree/main/Taller%202` |

---

## 2. Contexto del sistema analizado

**Veterinaria Sandoval** es una clínica veterinaria pequeña de barrio ubicada en
Bogotá. Atiende consulta general, vacunación, desparasitación, cirugía menor,
peluquería canina (tarifada por tamaño del paciente) y venta de medicamentos y
alimento. Trabajan allí el propietario-administrador, dos médicos veterinarios,
una auxiliar de recepción y un peluquero canino.

Hoy la operación se soporta en **cuadernos físicos, una carpeta de historias
clínicas en papel y un archivo de Excel para el inventario**. No existe un
registro unificado que relacione paciente, propietario, historia clínica,
esquema de vacunación y facturación.

El sistema analizado (SGV) es una **aplicación web Jakarta EE** (JSF +
PrimeFaces, JPA/Hibernate, MySQL) con control de acceso por roles
(`ADMINISTRADOR`, `VETERINARIO`, `EMPLEADO`) y módulos de historia clínica,
citas, vacunación, desparasitación, inventario y facturación.

> **Alcance de esta actividad:** NO se diseña la solución técnica. Se demuestra
> comprensión del ecosistema humano, del entorno y del problema real.

---

## 3. Problema analizado (síntesis)

> **La información clínica, comercial y sanitaria de Veterinaria Sandoval está
> fragmentada en soportes que no se comunican entre sí (papel, cuadernos y
> Excel), lo que impide reconstruir de forma confiable la historia de un
> paciente en el momento de la atención y expone a la clínica a errores
> clínicos, pérdida de ingresos por inventario descuadrado y a incumplimientos
> legales en materia de facturación electrónica y protección de datos.**

El afectado central no es el cliente final: es el **médico veterinario en
consulta**, que debe decidir con información incompleta en un tiempo de
atención de entre 15 y 20 minutos.

---

## 4. Decisión final del equipo (síntesis)

De tres formulaciones alternativas del problema generadas con apoyo de IA, el
equipo adoptó la **Formulación B (centrada en el veterinario y la trazabilidad
del paciente)** y descartó la Formulación A (centrada en el cliente y los
recordatorios) y la Formulación C (centrada en el descuadre de inventario).

**Criterio de decisión:** la Formulación B es la única cuya desaparición haría
desaparecer también a las otras dos. Los recordatorios al cliente (A) y el
descuadre de inventario (C) son **síntomas** de la misma causa raíz: no existe
una fuente única de verdad del paciente y del movimiento de insumos. Elegir A o
C habría llevado al equipo a diseñar una solución periférica (una app de avisos
o un Excel mejorado) sin resolver la fragmentación.

El detalle del contraste está en
[`04-problem-solution-fit/problem-solution-fit.md`](04-problem-solution-fit/problem-solution-fit.md).

---

## 5. Índice de evidencias

| Fase | Archivo | Qué demuestra |
|---|---|---|
| 1. Stakeholders | [`01-stakeholders/stakeholders.md`](01-stakeholders/stakeholders.md) | 10 stakeholders clasificados por tipo, poder, interés y estrategia |
| 1. Stakeholders | [`01-stakeholders/matriz-poder-interes.png`](01-stakeholders/matriz-poder-interes.png) | Matriz Poder/Interés del sistema |
| 1. Stakeholders | [`01-stakeholders/decisiones-stakeholders.md`](01-stakeholders/decisiones-stakeholders.md) | 5 propuestas de IA rechazadas o modificadas, con razón |
| 2. PESTEL | [`02-pestel/pestel.md`](02-pestel/pestel.md) | 6 dimensiones, 2 factores argumentados por dimensión |
| 2. PESTEL | [`02-pestel/evidencias.md`](02-pestel/evidencias.md) | Separación explícita entre evidencia, supuesto y opinión |
| 3. Pain Points | [`03-pain-points/pain-points.md`](03-pain-points/pain-points.md) | Stakeholder → pain point → impacto → evidencia → decisión |
| 4. Problem/Solution Fit | [`04-problem-solution-fit/problem-solution-fit.md`](04-problem-solution-fit/problem-solution-fit.md) | 3 formulaciones comparadas, 1 elegida y argumentada |
| 5. Lean Canvas | [`05-lean-canvas/lean-canvas.png`](05-lean-canvas/lean-canvas.png) | Canvas de 9 bloques |
| 5. Lean Canvas | [`05-lean-canvas/decisiones-canvas.md`](05-lean-canvas/decisiones-canvas.md) | Incoherencias detectadas y correcciones |
| 6. IA | [`06-ia/prompts.md`](06-ia/prompts.md) | Prompts completos de los 3 ciclos |
| 6. IA | [`06-ia/salidas-ia.md`](06-ia/salidas-ia.md) | Síntesis de las salidas que influyeron |
| 6. IA | [`06-ia/decisiones-humanas.md`](06-ia/decisiones-humanas.md) | Matriz "IA propone → nosotros decidimos" |
| 7. Defensa | [`07-defensa/evidencia-defensa.md`](07-defensa/evidencia-defensa.md) | Pitch, banco de preguntas y acta |

---

## 6. Criterio de resistencia

Si se eliminara por completo la conversación con la IA, este repositorio
seguiría demostrando el análisis: cada afirmación de los archivos `pestel.md`,
`pain-points.md` y `problem-solution-fit.md` está etiquetada como
`[EVIDENCIA]`, `[SUPUESTO]` u `[OPINIÓN]`, con la fuente o el método de
validación pendiente indicado. **Ninguna afirmación tiene como único soporte
"lo dijo la IA".**

---

## 7. Checklist final del equipo

- [x] Tenemos mínimo 6 stakeholders y los clasificamos (tenemos 10).
- [x] Aplicamos la matriz Poder/Interés.
- [x] Tenemos mínimo 2 factores PESTEL relevantes y argumentados por dimensión.
- [x] Cada pain point está relacionado con un stakeholder.
- [x] Distinguimos evidencia, supuesto y opinión.
- [x] El Problem/Solution Fit responde qué problema, a quién afecta y cómo mejora.
- [x] El Lean Canvas tiene los 9 bloques y es coherente.
- [x] Documentamos prompts y salidas relevantes de IA.
- [x] Registramos qué aceptamos, rechazamos o modificamos de la IA.
- [x] El repositorio GitHub contiene las evidencias.
- [x] Todos los integrantes pueden defender las decisiones.

---

> *"Entender antes de solucionar."*
