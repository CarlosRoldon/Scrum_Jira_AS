# Fase 3 — Pain Points

**Regla de distinción que aplicó el equipo:**

> Un **síntoma** es lo que la gente reporta cuando le preguntas qué le molesta.
> Un **problema** es la causa que, si se elimina, hace desaparecer varios
> síntomas a la vez.
> **Prueba operativa:** si al resolver X desaparecen también Y y Z, entonces X
> es problema y Y, Z eran síntomas.

---

## 1. Tabla principal: Stakeholder → Pain point → Impacto → Evidencia → Decisión

| ID | Stakeholder | Pain point (formulado como problema) | Impacto | Evidencia | Decisión del equipo |
|---|---|---|---|---|---|
| **PP1** | S2 Veterinarios | En la consulta no se puede reconstruir el historial del paciente: los antecedentes están en cuadernos distintos y algunos episodios no quedaron escritos | **Clínico y legal.** Riesgo de repetir un tratamiento, de aplicar un biológico duplicado o de omitir una alergia registrada | `[EVIDENCIA-D]` Observación del cuaderno: los registros son cronológicos por fecha de atención, no agrupados por paciente. Reconstruir un historial exige hojear hacia atrás | **CONSERVADO — pain point principal.** Es el único cuya solución arrastra a PP2, PP4 y PP6 |
| **PP2** | S2 Veterinarios | El esquema de vacunación de un paciente no es consultable de un vistazo: hay que deducirlo de fechas sueltas | Se aplican refuerzos fuera de ventana o no se aplican. Pérdida de eficacia del biológico y de ingreso recurrente | `[EVIDENCIA-D]` No existe ninguna vista consolidada del esquema en el soporte actual | **CONSERVADO** — es **consecuencia de PP1**, pero se conserva porque genera un requisito propio y medible (vista de esquema) |
| **PP3** | S1 Administrador | El inventario físico no coincide con el registrado: no hay registro del consumo en consulta | Pérdida económica silenciosa; quiebres de stock de biológicos; medicamentos vencidos no detectados | `[EVIDENCIA-D]` El Excel de inventario solo registra compras, no salidas por consulta. La salida ocurre en el consultorio y nadie la anota | **CONSERVADO** — segundo pain point en prioridad |
| **PP4** | S1 Administrador | No se puede saber qué servicio es rentable ni cuánto factura cada línea (consulta, peluquería, venta) | Decisiones de precio y de compra tomadas por intuición | `[SUPUESTO]` fuerte. Validación: pedir al administrador que responda "¿cuánto facturó peluquería el mes pasado?" y cronometrar cuánto tarda | **CONSERVADO CON MARCA DE SUPUESTO** |
| **PP5** | S3 Auxiliar de recepción | La agenda de citas en papel no detecta choques de horario ni disponibilidad del veterinario | Sobreagendamiento, esperas del cliente, fricción en recepción | `[EVIDENCIA-D]` Agenda física de una sola columna sin distinción por profesional | **CONSERVADO** |
| **PP6** | S3 Auxiliar de recepción | Facturar exige recopilar a mano lo que se hizo en la consulta preguntando al veterinario | Demora en caja, errores de cobro, servicios no facturados | `[EVIDENCIA-D]` La factura se arma después de la atención, con memoria del veterinario como fuente | **CONSERVADO** — es **el mismo problema que PP1 visto desde caja** |
| **PP7** | S4 Peluquero | La clasificación de tamaño del paciente es subjetiva y no queda registrada | Cobros inconsistentes por el mismo servicio al mismo paciente | `[EVIDENCIA-D]` No existe tabla de rangos escrita | **CONSERVADO** — pain point menor, pero genera un requisito barato y de alto retorno |
| **PP8** | S5 Propietarios | El propietario no sabe cuándo le toca el siguiente refuerzo o desparasitación de su mascota | Incumplimiento del esquema preventivo; el cliente percibe descuido | `[SUPUESTO]` Validación: encuesta de 3 preguntas en recepción | **CONSERVADO CON MARCA DE SUPUESTO** |
| **PP9** | S7 Contador | Recibe información de ventas desordenada y a destiempo | Retrabajo contable, riesgo de inconsistencia en declaraciones | `[SUPUESTO]` Validación: preguntarle en qué formato recibe hoy la información | **CONSERVADO** |
| **PP10** | S8/S9 Reguladores | No hay trazabilidad de lote de biológico aplicado ni numeración fiscal de factura | Riesgo de sanción; imposibilidad de responder ante un evento adverso post-vacunal | `[EVIDENCIA-D]` Verificado en el modelo de datos actual: la tabla de vacunación no tiene campo de lote | **CONSERVADO** — no lo reporta ningún humano, pero es real |

---

## 2. Pain points DESCARTADOS por ser síntomas

Esta sección es la que demuestra que el equipo distingue síntoma de problema.

| Síntoma reportado / propuesto | Por qué es síntoma | Problema raíz al que pertenece |
|---|---|---|
| "Se pierden historias clínicas en papel" | La pérdida física es un **modo de falla** del soporte, no la causa. Aunque no se perdiera ninguna hoja, seguiría siendo imposible consolidar el historial rápido | **PP1** |
| "El veterinario tiene mala letra y no se entiende lo que escribió" | Es un síntoma de que el registro es manuscrito y libre. Resolver la letra (digitalizando texto libre) no resolvería la fragmentación | **PP1** |
| "Se tarda mucho en atender a un cliente en recepción" | Demora observable con al menos tres causas distintas: buscar la historia, armar la factura, verificar la agenda | **PP1 + PP5 + PP6** |
| "Los clientes se quejan de que les cobraron distinto por la peluquería" | Es la manifestación de la clasificación subjetiva | **PP7** |
| "Faltan vacunas justo cuando se necesitan" | Quiebre de stock: consecuencia de no registrar salidas | **PP3** |
| "Hay medicamentos vencidos en la estantería" | Consecuencia de no controlar lotes ni fechas en el inventario | **PP3** |
| "El administrador no confía en los números del Excel" | Es una consecuencia emocional del descuadre, no un problema en sí | **PP3** |
| "Los clientes no vuelven" | **Este era el más peligroso.** Parece un problema de negocio y en realidad no sabemos su causa. Puede ser precio, ubicación, competencia o falta de recordatorio. Lo tratamos como síntoma sin causa identificada y **NO lo usamos para justificar ningún requisito** | Sin asignar — requiere investigación |

---

## 3. Oportunidades (ni síntoma ni problema)

Se registran aparte para no inflar la lista de dolores. **Una oportunidad no
justifica un requisito de la primera versión.**

| Oportunidad | Por qué NO es un pain point |
|---|---|
| Portal web para que el cliente consulte la historia de su mascota | Nadie sufre hoy por no tenerlo. Sería deseable, no doloroso |
| Integración con laboratorio externo de análisis clínicos | La clínica deriva pocos estudios. Valor potencial, dolor inexistente |
| Reportes de inteligencia de negocio y tableros | Es una mejora sobre PP4 ya resuelto, no un dolor independiente |
| Aplicación móvil para el veterinario | Atiende en consultorio, con escritorio disponible. Deseo tecnológico del equipo, no necesidad del usuario |

---

## 4. Árbol de causalidad — de los síntomas al problema raíz

```
                      ┌─────────────────────────────────────────┐
                      │  PROBLEMA RAÍZ                          │
                      │  No existe una fuente única de verdad   │
                      │  del paciente y del insumo:             │
                      │  la información vive en soportes que    │
                      │  no se comunican entre sí               │
                      └────────────────┬────────────────────────┘
                                       │
        ┌──────────────────┬───────────┴───────────┬──────────────────┐
        │                  │                       │                  │
   ┌────▼─────┐      ┌─────▼──────┐        ┌───────▼──────┐    ┌──────▼──────┐
   │   PP1    │      │    PP3     │        │     PP5      │    │    PP10     │
   │ Historial│      │ Inventario │        │   Agenda     │    │ Trazabilidad│
   │ no recon-│      │ descuadrado│        │  sin control │    │  regulatoria│
   │ struible │      │            │        │              │    │             │
   └────┬─────┘      └─────┬──────┘        └──────┬───────┘    └─────────────┘
        │                  │                      │
   ┌────┴─────┬────────┐   ├──────────┐      ┌────┴─────┐
   │          │        │   │          │      │          │
  PP2       PP6      PP8  Quiebres  Vencidos Esperas  Sobreagenda
Esquema  Facturar  Cliente de stock           del
vacunal  a mano   sin aviso                 cliente
   │          │
   └──────────┴──► PP4 (no se sabe qué es rentable)
                   PP9 (contador recibe datos sucios)
```

---

## 5. Priorización

Criterio: **impacto × frecuencia × esfuerzo de validación**.

| Prioridad | Pain point | Razón |
|---|---|---|
| 1 | **PP1** Historial no reconstruible | Riesgo clínico y legal; ocurre en cada consulta; es la raíz de PP2, PP6, PP8 |
| 2 | **PP3** Inventario descuadrado | Pérdida económica continua y cuantificable |
| 3 | **PP10** Trazabilidad regulatoria | Bajo costo de implementación, alto costo de omisión |
| 4 | **PP5** Agenda sin control | Alta frecuencia, impacto medio |
| 5 | **PP6 / PP4 / PP7** | Se resuelven en gran parte como efecto de 1 y 2 |
| 6 | **PP8 / PP9** | Dependen de supuestos aún no validados |

---

## 6. Trazabilidad pain point → PESTEL → stakeholder

| Pain point | Stakeholder | Factores PESTEL relacionados |
|---|---|---|
| PP1 | S2 | L2 (trazabilidad del acto médico), S1 (historia individualizada) |
| PP2 | S2, S5 | P1 (dosis aplicadas fuera de la clínica), E2 (ingreso recurrente) |
| PP3 | S1, S6 | A1 (baja por vencimiento con traza), E1 (margen) |
| PP4 | S1 | E1 (decisiones de precio con presupuesto ajustado) |
| PP5 | S3, S5 | S2 (interfaz simple para agendar), T1 (operar sin internet) |
| PP6 | S3 | P2 (facturación electrónica), L1 (datos del cliente) |
| PP7 | S4 | — (requisito interno de regla de negocio) |
| PP8 | S5 | T2 (WhatsApp), L1 (autorización para contactar) |
| PP9 | S7 | P2 (obligación tributaria) |
| PP10 | S8, S9 | L1, L2, P2, A1 |
