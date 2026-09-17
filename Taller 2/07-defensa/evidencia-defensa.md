# Fase 7 — Evidencia de defensa

**Fecha de la defensa:** _[completar el día de la sustentación]_
**Integrantes presentes:** Julián David Oviedo · Leonardo Fonseca Palma · Juan Sebastian Pineda
**Duración:** 5 minutos de pitch + preguntas del docente

---

## 1. Guion del pitch (5 minutos)

> Formato de viñetas para uso en sustentación. **No leer palabra por palabra.**

### Minuto 1 — El problema

- Veterinaria Sandoval opera hoy con tres soportes que no se hablan: cuaderno de
  consultas, carpeta de historias en papel y un Excel de inventario.
- El afectado central **no es el cliente**: es el veterinario en consulta.
- Tiene entre 15 y 20 minutos para decidir, y no puede reconstruir el historial
  del paciente de forma confiable.
- Consecuencia triple: riesgo clínico, riesgo legal y pérdida económica.

### Minuto 2 — Dos decisiones que cambiaron después de usar IA

**Decisión 1 — Incorporamos reguladores que habíamos omitido.**
- Nuestro mapa inicial tenía 6 stakeholders, todos internos o comerciales.
- La IA señaló la ausencia de entes reguladores.
- **Lo verificamos en nuestro propio sistema:** la factura era un consecutivo
  interno sin campos fiscales, y la tabla de vacunación no tenía campo de lote.
- Corregimos la entidad que la IA nombró mal (no es el ICA para pequeñas
  especies) y entraron dos requisitos legales al alcance.

**Decisión 2 — Cambiamos el problema central.**
- Nuestra intuición inicial apuntaba al cliente que no recibe recordatorios.
- La IA lo clasificó como problema y le asignó una causa.
- **Lo rechazamos:** no tenemos ninguna evidencia de la causa del abandono.
- Aplicamos la prueba de desaparición y quedó claro que los recordatorios son un
  efecto de la fragmentación, no una causa.

### Minuto 3 — El stakeholder que clasificamos mal

- El peluquero canino: la IA le dio poder medio porque "define el precio".
- Falso en esta clínica: el precio lo fija el administrador; él solo clasifica el
  tamaño del paciente **a ojo**.
- Bajamos su poder a bajo, y de paso apareció un requisito que no teníamos:
  definir el tamaño por rango de peso en kilogramos, no por etiqueta subjetiva.
- Aprendizaje: **ejecutar una regla no es definirla**.

### Minuto 4 — El pain point y su evidencia

- **PP1:** el historial no se puede reconstruir en la consulta.
- **Evidencia directa, no opinión:** el cuaderno está organizado
  cronológicamente por fecha de atención, no agrupado por paciente. Reconstruir
  el historial de un animal exige hojear hacia atrás.
- Impacto: ocurre en **cada consulta**, no ocasionalmente.
- Es la raíz de otros cuatro pain points: esquema de vacunación, facturación a
  mano, recordatorios imposibles y falta de trazabilidad de lote.

### Minuto 5 — La incoherencia del Canvas y el cierre

- **Incoherencia detectada:** el Canvas prometía recordatorios automáticos por
  WhatsApp a todos los clientes. Eso contradice el factor legal de habeas data:
  no se puede contactar a un titular de datos sin autorización previa.
- **Corrección:** el canal se mantiene, pero condicionado a una casilla de
  autorización en el registro del cliente. Apareció un campo obligatorio nuevo.
- **Cierre:** el valor del sistema no es digitalizar el cuaderno. Es que el
  mismo registro que hace el veterinario en la consulta alimente el inventario,
  la factura y la trazabilidad legal **sin que nadie lo transcriba dos veces**.

---

## 2. Banco de preguntas — respuestas preparadas

### 1. ¿Por qué este stakeholder tiene ese nivel de poder y no otro?

- Aplicamos dos preguntas: **¿puede detener el proyecto?** y **¿puede vaciarlo
  de contenido?**
- **S1 Administrador — poder alto:** paga, autoriza el cambio de proceso y puede
  devolver todo al papel. Es el único con poder formal de cancelación.
- **S2 Veterinarios — poder medio-alto:** no pueden cancelarlo, pero si
  registrar toma más tiempo que escribir en el cuaderno, vuelven al papel y el
  sistema queda vacío. Es **poder de veto de hecho**, no formal.
- **S3 Auxiliar — poder bajo:** ejecuta, no decide, no controla presupuesto.
- La distinción clave es entre **poder formal** y **poder de no-uso**.

### 2. ¿Qué evidencia tienen para afirmar que este pain point es real?

- Para **PP1**: observación directa del soporte actual. El cuaderno está
  ordenado por fecha de atención, no por paciente.
- Para **PP3**: el Excel de inventario registra compras pero no salidas; la
  salida ocurre físicamente en el consultorio y no hay ningún registro de ella.
- Para **PP10**: verificado en nuestro propio modelo de datos — la tabla de
  vacunación no tiene campo de lote.
- **Y donde no tenemos evidencia lo decimos:** PP4, PP8 y PP9 están marcados
  como supuestos, con el método de validación escrito en `evidencias.md`.

### 3. ¿Cuál de sus stakeholders podría bloquear el proyecto?

- Dos, por vías distintas.
- **S1 Administrador**, por vía formal: retira el presupuesto y se acabó.
- **S2 Veterinarios**, por vía práctica: no lo usan y el sistema muere lleno de
  pantallas vacías. Es el bloqueo más probable y el más difícil de revertir.
- Hay un tercero latente: **S8/S9 reguladores**, que no bloquean el desarrollo
  pero sí pueden invalidar el módulo de facturación ya construido.

### 4. ¿Qué propuesta de la IA rechazaron y por qué?

- La más importante: la IA clasificó *"los clientes no vuelven"* como problema y
  le asignó como causa la falta de recordatorios.
- La rechazamos porque **no teníamos evidencia de la causa**. Puede ser precio,
  ubicación o competencia.
- Si la hubiéramos aceptado, habríamos elegido la Formulación A del problema y
  diseñado un sistema de avisos sobre datos que no existen.
- Segunda: incluir a las mascotas como stakeholder. Rechazada porque no admite
  ninguna estrategia de gestión — y una fila del mapa que no genera acción es
  relleno, no análisis.

### 5. ¿Qué parte de su análisis es un supuesto todavía no validado?

- Tenemos cinco fisuras declaradas en `evidencias.md`.
- **La más riesgosa:** el factor E1, que asume que la clínica no puede pagar
  licencias de software. Es el supuesto que **más recortó el espacio de
  soluciones** y no está validado.
- Si fuera falso, se abriría la opción de comprar software comercial y el
  proyecto entero cambiaría de justificación.
- Se valida con una sola pregunta al administrador: cuánto paga hoy por software
  y cuánto pagaría al mes.

### 6. ¿Qué factor PESTEL podría cambiar la viabilidad de su sistema?

- **L1, habeas data.** Es el que más cambió nuestro análisis.
- En la primera versión, los roles `ADMINISTRADOR` / `VETERINARIO` / `EMPLEADO`
  estaban justificados solo por comodidad operativa.
- Con la Ley 1581 de 2012 dejan de ser comodidad y pasan a ser **medida de
  seguridad exigible**, junto con el hash de contraseñas y la autorización de
  tratamiento de datos.
- Es un factor que puede **invalidar una función ya construida**: sin la casilla
  de autorización, el módulo de recordatorios sería ilegal aunque funcione.

### 7. ¿Cuál es la diferencia entre el síntoma y el problema que identificaron?

- **Definición operativa:** el síntoma es lo que la gente reporta cuando le
  preguntas qué le molesta; el problema es la causa que, al eliminarse, hace
  desaparecer varios síntomas a la vez.
- **Síntomas:** "se pierden historias", "el veterinario tiene mala letra",
  "tardan en recepción", "faltan vacunas justo cuando se necesitan".
- **Problema:** no existe una fuente única de verdad del paciente y del insumo.
- **Prueba que aplicamos:** si al resolver X desaparecen también Y y Z, X es el
  problema. La aplicamos a las tres formulaciones y solo B la pasó.

### 8. ¿Qué bloque del Lean Canvas depende más directamente del stakeholder primario?

- El bloque 4, **Solución** — en concreto la historia clínica única y el
  descuento automático de insumos.
- Todo el Canvas cuelga de un solo acto: **que el veterinario registre la
  atención en el momento en que ocurre**.
- Si eso no pasa: el problema sigue vigente, la propuesta de valor es falsa, el
  beneficio no se materializa y las métricas no tienen datos que medir.
- Reconocemos que el Canvas completo depende de un stakeholder con poder formal
  medio. Es nuestra fragilidad estructural y está declarada.

### 9. Si desapareciera el stakeholder principal, ¿seguiría existiendo el problema?

- Hay que separar dos "principales".
- Si desaparece **S1 (el administrador)**: sí, el problema sigue. La
  fragmentación de la información es independiente de quién sea el dueño.
- Si desaparecen **S2 (los veterinarios)**: no. Sin acto clínico no hay historia
  clínica que reconstruir, ni insumo que descontar, ni factura que armar. El
  problema desaparece **junto con el negocio**.
- Eso confirma que el problema está bien anclado: **está en el proceso, no en
  una persona**, pero su punto de origen es el acto de la consulta.

### 10. ¿Qué decisión tomó el equipo que la IA no podía tomar por ustedes?

- Tres, y las tres por la misma razón: dependían de información que no está en
  ningún prompt.
- **Descartar 19 de 31 factores PESTEL**, aplicando el criterio "si no cambia
  una decisión concreta del sistema, no entra". Cada factor descartado era
  verdadero; ninguno era útil.
- **Rechazar el argumento de que los clientes se van por falta de
  recordatorios**, aunque era cómodo y sostenía una narrativa atractiva.
  Renunciar a un argumento que no está respaldado es una decisión de integridad,
  no de análisis.
- **Corregir el poder del peluquero y del cliente**, porque el poder real
  depende de quién firma, quién paga y quién puede irse sin costo — y eso solo
  se sabe mirando la clínica.

---

## 3. Preguntas adicionales previstas y respuesta corta

| Pregunta | Respuesta preparada |
|---|---|
| ¿Por qué 10 stakeholders y no 6? | Los 6 iniciales eran todos internos o comerciales. Los 4 añadidos son de soporte y regulatorios, y son los que introdujeron restricciones no negociables |
| ¿Por qué el contador no está en "gestionar de cerca" si es importante? | Porque su interés en el proyecto es bajo: no lo usa. Consume una salida. Se le consulta para definir el reporte y nada más |
| ¿No es el cliente el stakeholder más importante? | Es el más importante para el negocio, no para el sistema. El sistema no lo tiene como usuario en esta versión |
| ¿Cómo saben que el sistema mejorará algo? | No lo sabemos: lo declaramos como hipótesis con métricas de verificación en `problem-solution-fit.md` §4.3 |
| ¿Qué pasa si los veterinarios no lo usan? | El proyecto fracasa. Está declarado como riesgo principal y como condición de falsabilidad |
| ¿Usaron IA para escribir esto? | Sí, y está documentado: 9 prompts, 3 ciclos, 20 propuestas evaluadas, 40 % aceptadas sin modificación. La trazabilidad completa está en `06-ia/` |

---

## 4. Acta de la defensa

> **Completar el día de la sustentación.**

| Campo | Contenido |
|---|---|
| Fecha y hora | |
| Docente evaluador | |
| Integrantes presentes | |
| Integrante que expuso cada sección | |
| Preguntas efectivamente formuladas | |
| Respuestas dadas | |
| Observaciones del docente | |
| Compromisos de ajuste derivados de la defensa | |

---

## 5. Reparto sugerido de la exposición

| Sección | Responsable | Tiempo |
|---|---|---|
| Problema y contexto | Integrante 1 | 1 min |
| Stakeholders y matriz | Integrante 2 | 1 min |
| PESTEL y pain points | Integrante 3 | 1.5 min |
| Canvas, uso de IA y cierre | Integrante 4 | 1.5 min |
| Preguntas | Todos — responde quien expuso la sección | — |

**Regla del equipo para la defensa:** ningún integrante responde leyendo. Si no
sabe la respuesta, dice qué archivo del repositorio la contiene y por qué el
equipo decidió así. Reconocer un supuesto no validado suma; inventar evidencia
resta.
