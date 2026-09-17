# Fase 4 — Problem / Solution Fit

---

## 1. Las tres formulaciones alternativas

La IA produjo tres formulaciones del problema a partir de nuestro mapa de
stakeholders y nuestra lista de pain points. Las transcribimos, las evaluamos
con criterios explícitos y elegimos una.

### Formulación A — centrada en el cliente

> *"Los propietarios de mascotas de Veterinaria Sandoval no reciben
> recordatorios oportunos de los refuerzos de vacunación y desparasitación de
> sus animales, lo que provoca esquemas preventivos incompletos y pérdida de
> ingresos recurrentes para la clínica."*

### Formulación B — centrada en el veterinario *(ELEGIDA)*

> *"El médico veterinario de Veterinaria Sandoval debe tomar decisiones clínicas
> en una ventana de 15 a 20 minutos sin poder reconstruir de forma confiable el
> historial del paciente, porque la información clínica, de vacunación y de
> insumos está fragmentada en cuadernos, carpetas de papel y una hoja de cálculo
> que no se comunican entre sí. Esto genera riesgo clínico para el paciente,
> riesgo legal para el profesional y pérdida económica para la clínica."*

### Formulación C — centrada en el inventario

> *"Veterinaria Sandoval pierde dinero de forma continua porque el inventario de
> medicamentos e insumos no refleja el consumo real: no existe registro de las
> salidas que ocurren en el consultorio, lo que produce descuadres, quiebres de
> stock y medicamentos vencidos no detectados."*

---

## 2. Matriz de evaluación

Criterios exigidos por la actividad: stakeholder afectado, evidencia, impacto,
claridad y relación con el sistema. Escala 1–5.

| Criterio | A (cliente) | B (veterinario) | C (inventario) |
|---|:---:|:---:|:---:|
| **Stakeholder afectado identificado con precisión** | 3 — el afectado es difuso ("los propietarios") | **5** — un actor concreto, en un momento concreto (la consulta) | 4 — afecta al administrador, pero el que provoca el descuadre es el veterinario |
| **Evidencia disponible** | 2 — sostenido sobre `[SUPUESTO]` PP8, sin validar | **4** — `[EVIDENCIA-D]` directa sobre el cuaderno y el modelo de datos | 4 — `[EVIDENCIA-D]` sobre el Excel de inventario |
| **Impacto (magnitud × frecuencia)** | 3 — impacto económico, en cada refuerzo perdido | **5** — riesgo clínico y legal, en **cada consulta** | 4 — impacto económico continuo pero silencioso |
| **Claridad de la formulación** | 4 — clara y fácil de comunicar | 4 — precisa, pero larga | **5** — la más concreta y medible |
| **Relación con el sistema analizado** | 2 — se resuelve con un canal de avisos; no exige el sistema completo | **5** — exige exactamente el núcleo del sistema (paciente, historia, vacunación, insumo) | 3 — se resolvería con un Excel mejor diseñado |
| **Poder explicativo** (¿cuántos otros pain points explica?) | 1 — explica PP8 | **5** — explica PP1, PP2, PP6, PP8 y parcialmente PP4 y PP10 | 2 — explica PP3 y parte de PP4 |
| **TOTAL** | **15/30** | **28/30** | **22/30** |

---

## 3. Decisión y argumento

**Formulación elegida: B.**

### Por qué B es superior a A

A describe un **síntoma con envoltorio de problema**. El propietario no recibe
recordatorios porque *nadie puede saber cuándo le toca el refuerzo*, y nadie
puede saberlo porque el esquema de vacunación no está consolidado en ninguna
parte. Es decir: **A es un efecto de B**.

La consecuencia práctica de elegir A es grave: habría llevado al equipo a
diseñar un módulo de notificaciones sobre datos que no existen. Un sistema de
recordatorios alimentado por un cuaderno sigue siendo un cuaderno. Además, A
depende del supuesto PP8, que es justamente uno de los que **no hemos
validado**. Construir el problema central sobre un supuesto no verificado es el
error que la actividad pide evitar.

### Por qué B es superior a C

C es real, está bien evidenciado y tiene impacto económico medible. Es la
alternativa más seria de las dos descartadas. Pero tiene dos debilidades:

1. **Se resuelve sin el sistema.** Un Excel con dos hojas y una columna de
   salidas ya mitigaría buena parte de C. Un problema que se resuelve con la
   herramienta que ya tienen no justifica un sistema de información. B no tiene
   esa salida: consolidar historia clínica, vacunación y facturación con control
   de acceso por rol **no cabe en una hoja de cálculo**.
2. **Invierte la causalidad.** El inventario se descuadra porque la salida se
   produce en el consultorio y no queda registrada. El punto donde se pierde el
   dato es el mismo punto donde se pierde el dato clínico: **la consulta**. Si
   se resuelve el registro de la consulta (B), el registro de la salida de
   insumo viene incluido. Al revés no funciona: resolver el inventario no
   produce ninguna historia clínica.

### La prueba que aplicamos

> *Si el problema elegido desapareciera, ¿desaparecerían también los otros dos?*

- Si desaparece **B** (el veterinario registra todo en un sistema único en la
  consulta): desaparece A (el esquema queda consolidado y el recordatorio se
  puede calcular) y desaparece la causa de C (la salida de insumo queda
  registrada en el momento en que ocurre). ✔
- Si desaparece **A**: B y C siguen intactos. ✘
- Si desaparece **C**: B y A siguen intactos. ✘

**B es el único que pasa la prueba.**

---

## 4. Problem / Solution Fit

### 4.1 ¿Cuál es el problema?

La información clínica, sanitaria y comercial de la clínica está fragmentada en
soportes que no se comunican entre sí. En el momento de la atención —el único
momento en que el dato tiene valor y en que además se genera— no existe una
fuente única de verdad del paciente.

### 4.2 ¿A quién afecta y cómo?

| Afectado | Cómo lo vive |
|---|---|
| **S2 Veterinario** (afectado central) | Decide con información incompleta y asume el riesgo profesional de esa decisión |
| **S1 Administrador** | Pierde margen por descuadre e ignora la rentabilidad por línea de servicio |
| **S3 Auxiliar** | Reconstruye a mano la información de cada atención para poder facturar |
| **S5 Propietario** | Percibe una atención que no recuerda el historial de su mascota; su esquema preventivo queda incompleto |
| **S8/S9 Reguladores** | La clínica no puede demostrar trazabilidad de lote ni cumplir requisitos de facturación |

### 4.3 ¿Cómo cambia o mejora el sistema la situación?

| Antes | Después | Evidencia de que cambió (métrica) |
|---|---|---|
| El historial se reconstruye hojeando cuadernos | Historia clínica del paciente consolidada y consultable en una pantalla | Tiempo de consulta del historial < 10 segundos |
| El esquema de vacunación se deduce de fechas sueltas | Esquema consolidado con próximo refuerzo calculado | 100 % de pacientes con esquema visible y fecha de refuerzo |
| La salida de insumo no se registra | Se descuenta del inventario al registrar la atención | Diferencia entre inventario físico y del sistema < 5 % |
| La factura se arma preguntando al veterinario | La factura se alimenta automáticamente de lo registrado en la atención | Tiempo de facturación < 1 minuto; servicios no facturados ≈ 0 |
| No hay lote de biológico ni numeración fiscal | Lote obligatorio; factura con numeración autorizada | 100 % de aplicaciones con lote registrado |
| Cualquiera ve cualquier dato | Acceso segregado por rol y contraseñas con hash | 0 accesos de rol `EMPLEADO` a historia clínica |

### 4.4 Propuesta de valor (una frase)

> **Que el veterinario tenga en la pantalla, en menos de diez segundos y sin
> salir de la consulta, todo lo que necesita saber del paciente — y que ese
> mismo registro alimente automáticamente el inventario, la factura y la
> trazabilidad legal, sin que nadie lo transcriba dos veces.**

La clave es **"sin transcribir dos veces"**: es lo que distingue este sistema de
digitalizar el cuaderno.

---

## 5. Alternativas descartadas — registro formal

| Alternativa | Estado | Razón del descarte |
|---|---|---|
| Formulación A (recordatorios al cliente) | Descartada | Es síntoma de B; depende de un supuesto no validado (PP8); se resolvería sin el sistema |
| Formulación C (inventario) | Descartada como problema central, **conservada como objetivo secundario** | Se resuelve con una hoja de cálculo mejor; invierte la causalidad respecto al punto donde se pierde el dato |
| Formulación D — "la clínica no tiene presencia digital" | Descartada antes de la evaluación | Problema de marketing, no de sistema de información. No lo sufre ningún stakeholder identificado |
| Formulación E — "el software comercial del sector es caro" | Descartada | Es una **restricción** (factor E1), no un problema. Confunde la limitación con el dolor |

---

## 6. Qué tendría que pasar para que cambiemos de decisión

Declaración de falsabilidad. Cambiaríamos de la formulación B a otra si:

1. La prueba de usabilidad con la auxiliar (S3) mostrara que registrar la
   consulta en el sistema toma **más tiempo** que escribirla en el cuaderno. En
   ese caso B sería irresoluble en la práctica y habría que reformular el
   problema alrededor de la carga de registro.
2. El administrador (S1) manifestara que el descuadre de inventario le cuesta un
   monto que supera con claridad el costo del riesgo clínico percibido. Eso
   subiría C a problema principal por criterio de decisor.
3. Se descubriera que los veterinarios **sí** llevan un archivo por paciente que
   nosotros no vimos. Eso invalidaría la evidencia base de PP1.
