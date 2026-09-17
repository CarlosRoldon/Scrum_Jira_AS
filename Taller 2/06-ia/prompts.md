# Fase 6 — Prompts utilizados

**Herramienta / modelo:** Claude (Anthropic) — interfaz web
**Fechas de uso:** 12, 14 y 16 de septiembre de 2026
**Propósito general:** generación de alternativas, detección de omisiones,
crítica de clasificaciones y contraste de formulaciones. **En ningún caso se
utilizó para producir la decisión final.**

---

## CICLO 1 — GENERAR *(12 de septiembre)*

### Prompt 1.1 — Stakeholders omitidos

```
Actúa como analista de sistemas crítico.

CONTEXTO DEL SISTEMA:
Veterinaria Sandoval es una clínica veterinaria pequeña de barrio en Bogotá.
Atiende consulta general, vacunación, desparasitación, cirugía menor, peluquería
canina tarifada por tamaño del paciente, y vende medicamentos y alimento.
Trabajan el propietario-administrador, dos médicos veterinarios, una auxiliar de
recepción y un peluquero. Hoy operan con cuadernos físicos, historias clínicas
en papel y un Excel de inventario. Estamos analizando un sistema web (Jakarta
EE, JSF/PrimeFaces, JPA/Hibernate, MySQL) con roles ADMINISTRADOR, VETERINARIO y
EMPLEADO, y módulos de historia clínica, citas, vacunación, desparasitación,
inventario y facturación.

NUESTROS STAKEHOLDERS ACTUALES:
1. Propietario-administrador
2. Médicos veterinarios
3. Auxiliar de recepción
4. Propietarios de mascotas (clientes)
5. Proveedores de medicamentos e insumos
6. Equipo de desarrollo

Genera 5 stakeholders que podríamos estar omitiendo. Para cada uno indica tipo
(primario, secundario, clave/decisor o externo), poder, interés y por qué podría
afectar o ser afectado. No decidas por nosotros; plantea alternativas y separa
claramente qué es hecho, qué es supuesto y qué es recomendación.
```

### Prompt 1.2 — Factores PESTEL

```
A partir del contexto anterior, genera posibles factores PESTEL para este
sistema. Cubre las seis dimensiones. Para cada factor explica (a) qué decisión
concreta del sistema podría condicionar y (b) qué evidencia sería necesaria para
afirmar que es relevante en ESTA clínica.

No inventes datos, cifras ni estadísticas. Si no puedes sostener un dato, dilo
explícitamente en lugar de estimarlo.
```

### Prompt 1.3 — Pain points

```
Con base en el contexto y en los stakeholders, propón posibles pain points para
cada uno. Para cada pain point indica el impacto (clínico, económico, legal u
operativo) y qué evidencia haría falta para confirmarlo. No los priorices
todavía.
```

---

## CICLO 2 — CRITICAR *(14 de septiembre)*

### Prompt 2.1 — Revisión del mapa de stakeholders

```
Actúa como revisor crítico de nuestro mapa de stakeholders (te adjunto la
versión con 10 actores y su clasificación Poder/Interés).

Busca inconsistencias en la clasificación Poder/Interés y posibles errores en la
estrategia de gestión asignada. Propón cambios, pero separa claramente hechos,
supuestos y recomendaciones.

Preguntas concretas que quiero que respondas:
- ¿Algún actor está sobrevalorado en poder?
- ¿Algún actor está en el cuadrante equivocado?
- ¿Hay alguna estrategia de gestión que no sea ejecutable en la práctica?
```

### Prompt 2.2 — Síntoma vs. problema

```
Estos son nuestros pain points [lista de 18 ítems recogidos en el ciclo 1].

Diferencia cuáles parecen síntomas, cuáles son problemas y cuáles son
oportunidades. Para cada uno explica qué evidencia necesitaríamos para
validarlo. Si dos ítems son manifestaciones de la misma causa, dilo y señala
cuál es la causa.
```

### Prompt 2.3 — Crítica de coherencia del Lean Canvas

```
Te paso nuestro Lean Canvas en 9 bloques [contenido]. Contrástalo contra
nuestro mapa de stakeholders y nuestra lista de pain points [adjuntos].

Señala incoherencias: bloques que afirmen algo que ningún stakeholder sostiene,
elementos del Canvas sin origen en un pain point, métricas que no se puedan
medir con los datos del sistema, y contradicciones con nuestros factores PESTEL
legales. No reescribas el Canvas; señala los conflictos.
```

---

## CICLO 3 — DECIDIR *(16 de septiembre)*

### Prompt 3.1 — Formulaciones alternativas del problema

```
Con base en nuestro análisis completo [stakeholders, PESTEL, pain points],
produce 3 formulaciones alternativas del problema central de Veterinaria
Sandoval. Que sean genuinamente distintas entre sí en cuanto al stakeholder
afectado y al tipo de impacto, no tres versiones redactadas del mismo enunciado.
```

### Prompt 3.2 — Comparación de formulaciones

```
Compara estas tres formulaciones del problema [A, B, C]. Evalúalas usando:
stakeholder afectado, evidencia disponible, impacto, claridad y relación con el
sistema.

Recomienda una, pero deja explícito qué debería verificar el equipo antes de
adoptarla y qué se pierde al descartar las otras dos.
```

### Prompt 3.3 — Preguntas difíciles de defensa

```
Somos un squad que va a sustentar este análisis ante un docente que evalúa
pensamiento crítico y penaliza las respuestas genéricas.

Genera las 10 preguntas más incómodas que nos podrían hacer sobre este análisis:
las que apunten a supuestos no validados, a clasificaciones discutibles y a
contradicciones internas. No respondas las preguntas.
```

---

## Prompts que NO usamos y por qué

| Prompt descartado | Razón |
|---|---|
| "Escribe el informe completo de la actividad" | Habría producido Nivel 1. El informe es el resultado del análisis, no su insumo. |
| "Dame las cifras del mercado veterinario en Colombia con fuentes" | Riesgo de datos fabricados. Preferimos marcar `[SUPUESTO]` antes que citar una cifra que no pudimos verificar. |
| "Decide cuál es el problema principal" | Es exactamente la decisión que la actividad exige que tome el equipo. |
| "Inventa las entrevistas con los stakeholders" | Sería fabricar evidencia. Preferimos declarar la fisura (`evidencias.md`, punto 1). |

---

## Nota sobre el estilo de los prompts

Los tres prompts de los ciclos 1 y 2 incluyen deliberadamente la instrucción
**"separa hechos, supuestos y recomendaciones"** y **"no inventes datos"**. Esa
formulación es la que permitió después construir `evidencias.md`: si el prompt
no exige la separación, la salida llega mezclada y el equipo pierde la
trazabilidad de qué estaba sostenido y qué no.
