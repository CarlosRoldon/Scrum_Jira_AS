# Fase 5 — Decisiones y correcciones del Lean Canvas

**Archivo del Canvas:** `lean-canvas.png`
**Método:** construimos una primera versión del Canvas, le pedimos a la IA que
buscara incoherencias contra `stakeholders.md` y `pain-points.md`, evaluamos
cada crítica y corregimos.

---

## 1. Los 9 bloques y su trazabilidad

| # | Bloque | Contenido | Trazabilidad |
|---|---|---|---|
| 1 | Problema | PP1, PP2, PP3, PP6, PP10 | `pain-points.md` |
| 2 | Segmentos de clientes | S1, S2, S3, S4 (usuarios) / S5, S7 (beneficiarios) | `stakeholders.md` |
| 3 | Propuesta única de valor | "Sin transcribir nada dos veces" | `problem-solution-fit.md` §4.4 |
| 4 | Solución | Historia única, esquema de vacunación, descuento de insumos, factura automática, roles | Una línea por pain point del bloque 1 |
| 5 | Canales | Presencial + WhatsApp | Factor PESTEL T2 |
| 6 | Fuentes de ingreso / beneficio | Ahorro y riesgo evitado | PP3, PP6, PP2, PP10 |
| 7 | Estructura de costos | Licencias $0, infraestructura existente | Factor PESTEL E1 |
| 8 | Métricas clave | 5 métricas medibles | `problem-solution-fit.md` §4.3 |
| 9 | Ventaja especial | Ajuste al proceso real + costo cero + opera sin internet | E1, T1 |

**Regla que nos impusimos:** ningún elemento del Canvas puede existir si no
apunta a una celda concreta de los archivos anteriores. Si no tiene origen, se
borra.

---

## 2. Incoherencias detectadas y corregidas

### Corrección 1 — "Early adopter" estaba mal elegido *(crítica de la IA, aceptada)*

- **Versión inicial:** el early adopter era **el administrador (S1)**, porque es
  quien decide.
- **Incoherencia señalada:** quien decide comprar no es necesariamente quien
  adopta primero. Si el administrador adopta y los veterinarios no registran,
  el sistema queda vacío y el Canvas pierde coherencia con la clasificación de
  poder de S2 ("poder de veto de hecho").
- **Corrección:** el early adopter pasó a ser **el veterinario que hoy asume el
  riesgo de decidir sin historial completo**. El administrador es el
  **comprador/decisor**, no el adoptante.
- **Consecuencia:** cambió el bloque de canales — la capacitación se diseña
  primero para el consultorio, no para la caja.

### Corrección 2 — La propuesta de valor describía la solución, no el valor *(crítica de la IA, aceptada)*

- **Versión inicial:** *"Sistema web para gestión integral de clínicas
  veterinarias con historia clínica, inventario y facturación."*
- **Incoherencia señalada:** eso es una lista de módulos. No dice qué cambia
  para nadie, y sería idéntica para cualquier software del mercado. Además
  contradecía el bloque 9 (ventaja especial), donde afirmábamos ser distintos
  de un producto genérico.
- **Corrección:** *"Todo lo que el veterinario necesita saber del paciente, en
  pantalla y en menos de diez segundos — y ese mismo registro alimenta el
  inventario, la factura y la trazabilidad legal sin transcribir nada dos
  veces."*
- **Razón:** la nueva versión es verificable (hay una métrica detrás) y nombra
  al afectado central del problema elegido.

### Corrección 3 — Métricas que no se podían medir *(detectada por el equipo)*

- **Versión inicial:** "satisfacción del cliente", "eficiencia operativa",
  "calidad de la atención".
- **Problema:** ninguna es medible con los datos del sistema. Son deseos, no
  métricas.
- **Corrección:** las cinco métricas actuales, todas obtenibles de la base de
  datos o de un cronómetro: tiempo de consulta del historial, tiempo de registro
  de la consulta, desviación de inventario, % de aplicaciones con lote, % de
  retorno a refuerzo.
- **Nota:** esta corrección **no la propuso la IA**. Salió de preguntarnos
  "¿quién mediría esto y con qué?".

### Corrección 4 — Fuentes de ingreso inventadas *(crítica de la IA, RECHAZADA parcialmente)*

- **Propuesta de la IA:** incluir en el bloque 6 un modelo de suscripción
  mensual (SaaS) y la venta del sistema a otras veterinarias.
- **Decisión:** **rechazada** para este Canvas.
- **Razón:** el sistema es un desarrollo a la medida para una clínica concreta,
  en un contexto académico. Declarar ingresos por suscripción sería inventar un
  modelo de negocio que ningún stakeholder identificado sostiene: no existe S
  alguno que sea "otras veterinarias". Habría roto la trazabilidad con el bloque
  2. Reformulamos el bloque como **"Fuentes de ingreso / beneficio"**, midiendo
  retorno en ahorro y riesgo evitado.
- **Lo que sí aceptamos:** la crítica nos obligó a declarar explícitamente que
  el sistema **no se vende**, cosa que antes quedaba ambigua.

### Corrección 5 — Canales contradecían el marco legal *(crítica de la IA, aceptada)*

- **Versión inicial:** "recordatorios automáticos por WhatsApp a todos los
  clientes".
- **Incoherencia señalada:** contradice el factor PESTEL **L1** (habeas data).
  No se puede contactar a un titular de datos sin autorización previa para esa
  finalidad.
- **Corrección:** el canal se mantiene, pero condicionado a la casilla de
  autorización de tratamiento de datos en el registro del cliente. Sin
  autorización, no hay recordatorio.
- **Consecuencia:** apareció un campo obligatorio nuevo y un caso de uso que no
  teníamos.

### Corrección 6 — El bloque "Problema" mezclaba síntomas *(detectada por el equipo)*

- **Versión inicial:** incluía "se pierden las historias en papel" y "los
  clientes no vuelven".
- **Corrección:** ambos salieron. El primero es síntoma de PP1; el segundo es un
  síntoma sin causa identificada (ver `pain-points.md` §2) y no puede sostener
  ningún bloque del Canvas.

---

## 3. Bloque más dependiente del stakeholder primario

**Respuesta a la pregunta 8 del banco de defensa.**

El bloque más dependiente de S2 (veterinarios) es la **Solución (bloque 4)**,
específicamente la historia clínica única y el descuento automático de insumos.

Toda la cadena de valor del Canvas arranca en un solo acto: **que el veterinario
registre la atención en el sistema en el momento en que ocurre**. Si ese acto no
sucede:

- el bloque 1 (problema) sigue vigente,
- el bloque 3 (propuesta de valor) es falso,
- el bloque 6 (beneficio) no se materializa,
- el bloque 8 (métricas) no tiene datos que medir.

El Canvas completo cuelga de un stakeholder con **poder formal medio**. Esa es
la fragilidad estructural del proyecto y la reconocemos explícitamente.

---

## 4. Riesgo declarado

El Canvas asume que registrar en el sistema toma **menos tiempo** que escribir
en el cuaderno. Ese supuesto no está validado (ver `evidencias.md`, factor S2 y
"fisura 5"). Si es falso, la ventaja especial se convierte en desventaja y hay
que rediseñar el bloque 4 alrededor de la velocidad de captura, no de la
completitud del dato.
