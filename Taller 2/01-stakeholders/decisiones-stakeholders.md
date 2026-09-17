# Fase 1 — Decisiones del equipo sobre las propuestas de IA

**Requisito de la actividad:** al menos 2 propuestas de IA rechazadas o
modificadas, con justificación. **Documentamos 5.**

---

## Caso 1 — ACEPTADA CON MODIFICACIÓN: el peluquero canino

**Propuesta de la IA:** incluir "personal de servicios estéticos (grooming)"
como stakeholder primario con poder medio e interés alto.

**Qué verificamos:** revisamos el módulo de peluquería del sistema. La tarifa se
calcula a partir del tamaño del paciente (pequeño / mediano / grande), y esa
clasificación hoy la hace el peluquero **a ojo**, sin criterio escrito.

**Decisión del equipo:** lo incluimos como **S4**, pero **bajamos su poder de
MEDIO a BAJO**.

**Razón:** la IA le asignó poder medio porque "define el precio del servicio".
Es falso en esta clínica: el precio lo fija el administrador; el peluquero
únicamente clasifica el tamaño. Confundir *ejecutar una regla* con *definir una
regla* infla el poder del actor. Lo que sí es alto es su interés, porque la
tabla de tamaños afecta su trabajo diario.

**Consecuencia en el análisis:** apareció un requisito que no teníamos: definir
un criterio objetivo de tamaño (rango de peso en kg) en lugar de una etiqueta
subjetiva.

---

## Caso 2 — ACEPTADA: DIAN y autoridad sanitaria distrital

**Propuesta de la IA:** agregar entes reguladores (DIAN por facturación
electrónica, autoridad sanitaria por vacunación antirrábica) como stakeholders
externos de poder alto e interés bajo.

**Qué verificamos:** contrastamos contra el módulo de facturación que ya
teníamos modelado. Nuestra factura era un consecutivo interno sin resolución de
facturación ni campos fiscales. El módulo de vacunación registraba fecha y
producto, pero **no lote ni laboratorio**.

**Decisión del equipo:** aceptada sin cambios en la clasificación, pero
**precisamos la entidad**: la IA mencionó genéricamente "ICA / autoridad
sanitaria". Verificamos que el ICA regula sanidad animal de producción
pecuaria; para una clínica de pequeñas especies en Bogotá el interlocutor
pertinente es la **Secretaría Distrital de Salud / IDPYBA**. Corregimos el
nombre.

**Razón:** aceptar el nombre genérico habría dejado una afirmación no
verificable en el informe. La categoría era correcta; la entidad concreta, no.

**Consecuencia en el análisis:** dos requisitos legales entraron al alcance
(campos fiscales en factura, lote de biológico obligatorio) y aparecieron dos
factores PESTEL de la dimensión Legal.

---

## Caso 3 — RECHAZADA: "las mascotas como stakeholder"

**Propuesta de la IA:** incluir a los pacientes (las mascotas) como
stakeholders primarios, argumentando que son "los beneficiarios finales del
sistema y los afectados directos por un error clínico".

**Qué verificamos:** contrastamos contra nuestra definición operativa de
stakeholder. Un stakeholder debe poder tener interés, influir o expresar
afectación de forma que altere alguna decisión del proyecto. La mascota no
puede hacer ninguna de las tres cosas; su afectación es real, pero **la
representa íntegramente el propietario (S5) y el veterinario (S2)**.

**Decisión del equipo:** **rechazada.** La mascota se modela como *entidad del
dominio* (`Paciente`), no como stakeholder.

**Razón:** incluirla habría producido una fila del mapa sin estrategia de
gestión posible (¿cómo se "mantiene informada" a una mascota?). Una fila que no
genera ninguna acción de gestión no es análisis, es relleno. Además habría
duplicado el interés de S5 y creado la ilusión de un stakeholder más.

**Matiz que sí conservamos:** el argumento de la IA nos hizo explicitar que el
*bienestar animal* es un criterio de decisión del sistema, y lo trasladamos a
la Propuesta Única de Valor del Lean Canvas y al factor Legal-2 del PESTEL
(Ley 84 de 1989). La propuesta era mala como stakeholder y útil como criterio.

---

## Caso 4 — RECHAZADA: "aseguradoras de mascotas y planes de medicina prepagada"

**Propuesta de la IA:** incluir aseguradoras/planes prepagados veterinarios como
stakeholder externo de poder medio, por la eventual necesidad de facturar a
terceros.

**Qué verificamos:** en Veterinaria Sandoval **no existe ningún convenio** con
aseguradoras ni con planes prepagados. El 100 % de la facturación actual es a
particular.

**Decisión del equipo:** **rechazada** para el alcance actual. Se registra como
*riesgo de evolución*, no como stakeholder.

**Razón:** es un stakeholder **potencial de un negocio distinto**, no del
sistema que analizamos. Incluirlo habría metido en el Lean Canvas un canal y
una fuente de ingreso que hoy no existen, rompiendo la trazabilidad entre
hallazgos y Canvas. Es el error típico de diseñar para el caso hipotético en
lugar del caso real.

**Cómo lo detectamos:** la IA no tenía forma de saberlo. Es información que solo
se obtiene mirando las facturas reales de la clínica.

---

## Caso 5 — MODIFICADA: clasificación del cliente final

**Propuesta de la IA:** propietarios de mascotas con **poder BAJO**, cuadrante
"mantener informado".

**Qué verificamos:** discutimos qué pasa si el cliente se molesta. En una
clínica de barrio sin contratos, el cliente se va a la competencia de la cuadra
siguiente sin ningún costo de cambio, y la rotación es inmediata.

**Decisión del equipo:** subimos su poder a **MEDIO** y lo movimos a "mantener
satisfecho".

**Razón:** la IA evaluó el poder **individual** (un cliente no decide nada, es
cierto). Nosotros evaluamos el poder **agregado y de salida**: la capacidad de
abandono colectivo sí condiciona la viabilidad del negocio que el sistema
soporta. El poder no solo se ejerce decidiendo; también se ejerce yéndose.

**Consecuencia en el análisis:** obligó a incluir en el Canvas una métrica clave
de retención (% de pacientes que regresan a refuerzo de vacuna), que no
teníamos.

---

## Síntesis

| # | Propuesta IA | Resultado | Criterio que aplicó el equipo |
|---|---|---|---|
| 1 | Groomer con poder medio | Modificada (poder → bajo) | Ejecutar una regla ≠ definirla |
| 2 | Reguladores (ICA genérico) | Aceptada con corrección de entidad | Verificación de competencia real del ente |
| 3 | Mascotas como stakeholder | Rechazada | Si no genera estrategia de gestión, no es stakeholder |
| 4 | Aseguradoras de mascotas | Rechazada | No existe en el negocio real (revisión de facturas) |
| 5 | Cliente con poder bajo | Modificada (poder → medio) | Poder agregado y de salida, no individual |

**Reflexión del equipo:** la IA fue buena detectando **categorías olvidadas**
(reguladores, actores de soporte) y mala **calibrando el poder relativo**,
porque el poder depende de hechos locales que no están en el prompt: quién
firma, quién paga, quién puede irse. Eso solo lo resuelve el equipo mirando la
clínica.
