# Fase 6 — Salidas relevantes de la IA

**Criterio de inclusión:** solo se transcriben las salidas que **efectivamente
cambiaron** el análisis. Las salidas que confirmaron lo que ya teníamos no se
documentan porque no aportan trazabilidad.

---

## Salida 1.1 — Stakeholders omitidos *(12/09/2026 · Prompt 1.1)*

**Síntesis de lo que devolvió la IA (5 propuestas):**

| Propuesta | Clasificación sugerida | Argumento de la IA |
|---|---|---|
| Entes reguladores tributarios (DIAN) | Externo · Poder alto · Interés bajo | La facturación es una obligación fiscal con formato y numeración regulados |
| Autoridad sanitaria (mencionó "ICA / autoridades de sanidad animal") | Externo · Poder alto · Interés bajo | La vacunación antirrábica tiene control y exige trazabilidad de biológicos |
| Contador o asesor contable externo | Secundario · Poder medio · Interés medio | Consume las salidas del módulo de facturación aunque no use el sistema |
| Personal de servicios estéticos (grooming) | Primario · Poder medio · Interés alto | Opera un módulo con reglas de precio propias |
| Pacientes (las mascotas) | Primario · Poder nulo · Interés alto | Son los beneficiarios finales y los afectados directos de un error clínico |

**La IA marcó explícitamente como supuesto:** que la clínica esté obligada a
facturación electrónica y que el control sanitario aplique a esta escala.

**Qué influyó:** las tres primeras propuestas entraron al mapa (con corrección
de entidad en la segunda). La cuarta entró con el poder corregido. La quinta se
rechazó. Detalle en `01-stakeholders/decisiones-stakeholders.md`.

---

## Salida 1.2 — Factores PESTEL *(12/09/2026 · Prompt 1.2)*

**Volumen:** 31 factores a lo largo de dos iteraciones (18 en la primera
respuesta, 13 adicionales al pedir cobertura completa de las dimensiones
ambiental y política).

**Los 4 factores que el equipo no había contemplado y que sí conservó:**

1. **Habeas data (Ley 1581 de 2012)** — la IA señaló que almacenar documento,
   teléfono y dirección de los propietarios activa obligaciones de autorización,
   seguridad y supresión. *Este fue el aporte más valioso de toda la actividad.*
2. **Residuos peligrosos (RESPEL)** — vinculó la baja de medicamentos vencidos
   en inventario con una obligación documental ambiental.
3. **Campañas públicas de vacunación** — planteó que parte del esquema del
   paciente puede haberse aplicado fuera de la clínica.
4. **Trazabilidad del acto médico** — señaló que la historia clínica debería ser
   no borrable y atribuible a un profesional.

**Lo que la IA hizo mal aquí:** propuso factores macroeconómicos y políticos
genéricos (tipo de cambio, inestabilidad política, reforma tributaria) sin poder
conectarlos con ninguna decisión del sistema. Cuando se le pidió la conexión
concreta, las conexiones que produjo eran forzadas. **19 de 31 factores fueron
descartados** (ver `02-pestel/evidencias.md`).

---

## Salida 2.1 — Crítica del mapa de stakeholders *(14/09/2026 · Prompt 2.1)*

**Críticas que la IA formuló (4):**

1. *"El propietario de mascotas aparece con poder bajo; sin embargo, la
   viabilidad del negocio depende de su permanencia."* → **Aceptada**, subimos
   el poder de S5 a medio.
2. *"El peluquero aparece con poder medio, pero el documento indica que el
   precio lo fija el administrador; hay inconsistencia entre la clasificación y
   la descripción del proceso."* → **Aceptada**, bajamos su poder a bajo. La IA
   detectó una contradicción interna real de nuestro propio documento.
3. *"La estrategia 'gestionar de cerca' asignada a DIAN no es ejecutable: no se
   puede co-diseñar con un ente regulador."* → **Aceptada**, cambiamos la
   estrategia a "restricción no negociable de diseño" y lo movimos al cuadrante
   correcto.
4. *"El equipo de desarrollo no debería figurar como stakeholder por ser el
   ejecutor del proyecto."* → **Rechazada.** El squad toma decisiones de diseño
   con impacto real y el docente condiciona el alcance vía rúbrica. Omitirlos
   ocultaría el sesgo de diseñar para la nota. Lo conservamos como S10 y lo
   declaramos.

---

## Salida 2.2 — Separación síntoma / problema *(14/09/2026 · Prompt 2.2)*

**Aporte concreto:** la IA agrupó ocho de nuestros dieciocho ítems bajo una
misma causa y propuso la formulación de causa raíz *"no existe una fuente única
de verdad del paciente"*.

**Aporte metodológico:** propuso la prueba operativa que terminamos adoptando:
*si al resolver X desaparecen también Y y Z, entonces X es el problema*. Esa
prueba es la que estructura el árbol de causalidad de `pain-points.md`.

**Dónde falló:** clasificó *"los clientes no vuelven"* como **problema** con
causa "falta de recordatorios". El equipo lo rechazó: no tenemos ninguna
evidencia de la causa del abandono; puede ser precio, ubicación o competencia.
Lo degradamos a "síntoma sin causa identificada" y **lo excluimos de toda
justificación de requisitos**. Esta fue la corrección más importante que hizo el
equipo sobre la IA, porque de haberla aceptado habríamos elegido la Formulación
A del problema.

---

## Salida 2.3 — Crítica del Lean Canvas *(14/09/2026 · Prompt 2.3)*

**Incoherencias señaladas (5), de las cuales aceptamos 4:**

| # | Incoherencia señalada | Resultado |
|---|---|---|
| 1 | Early adopter = administrador contradice el "poder de veto de hecho" de los veterinarios | Aceptada |
| 2 | La propuesta de valor es una lista de módulos, idéntica a cualquier producto genérico; contradice el bloque de ventaja especial | Aceptada |
| 3 | "Recordatorios automáticos a todos los clientes" contradice el factor legal de habeas data | Aceptada |
| 4 | El bloque "Problema" contiene síntomas ya descartados en `pain-points.md` | Aceptada |
| 5 | Faltan fuentes de ingreso; sugiere modelo de suscripción y venta a otras clínicas | **Rechazada** — inventaría un segmento inexistente |

---

## Salida 3.2 — Comparación de formulaciones *(16/09/2026 · Prompt 3.2)*

**Lo que recomendó la IA:** la Formulación **B**, con una puntuación similar a
la nuestra en cuatro de los cinco criterios.

**Dónde coincidimos:** en la elección y en el argumento de causalidad (A es
efecto de B).

**Dónde nos separamos:**

- La IA calificó la claridad de B como la más baja de las tres por su extensión,
  y sugirió acortarla eliminando la mención al tiempo de consulta. **Rechazamos
  el recorte:** la ventana de 15–20 minutos es precisamente lo que convierte el
  problema en operativo y medible. Sin ella, B se vuelve un enunciado abstracto
  sobre "información fragmentada" que serviría para cualquier organización.
- La IA no aplicó el criterio de **poder explicativo** (cuántos pain points
  explica cada formulación). Lo añadimos nosotros y es el criterio que produce
  la mayor diferencia en la matriz de evaluación (5 vs 1 vs 2).
- La IA advirtió correctamente que antes de adoptar B había que verificar que
  los veterinarios no llevaran ya un archivo propio por paciente. Incorporamos
  esa verificación como condición de falsabilidad (`problem-solution-fit.md`
  §6, punto 3).

---

## Observación transversal sobre el comportamiento de la IA

1. **Fue muy buena detectando categorías ausentes** (reguladores, actores de
   soporte, obligaciones legales). Ese es su mejor uso en análisis de contexto:
   cubrir el punto ciego del equipo.
2. **Fue poco confiable calibrando magnitudes** (poder relativo, impacto
   económico, prioridad). Esas calibraciones dependen de hechos locales que no
   están en el prompt.
3. **Tendió a completar huecos con plausibilidad en lugar de con incertidumbre.**
   Asignó causa a un fenómeno del que no teníamos datos ("los clientes no
   vuelven porque no reciben recordatorios"). Cuando se le exigió separar hecho
   de supuesto, lo hizo bien; cuando no se le exigió, no lo hizo por sí sola.
4. **Detectó contradicciones internas de nuestros propios documentos** mejor de
   lo que las detectamos nosotros (caso del peluquero). Es su uso más eficiente:
   revisor de consistencia, no generador de contenido.
