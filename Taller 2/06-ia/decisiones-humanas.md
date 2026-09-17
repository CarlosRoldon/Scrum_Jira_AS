# Fase 6 — Matriz "IA propone → nosotros decidimos"

---

## 1. Bloque obligatorio de uso de IA

| Elemento | Contenido |
|---|---|
| **Herramienta / modelo** | Claude (Anthropic), interfaz web. Uso los días 12, 14 y 16 de septiembre de 2026. |
| **Propósito** | Generación de alternativas de stakeholders y factores PESTEL, detección de omisiones, crítica de clasificaciones, separación síntoma/problema, contraste de formulaciones del problema y generación de preguntas de defensa. **No se usó para redactar conclusiones ni para tomar decisiones.** |
| **Prompt principal** | Ver `prompts.md` — 9 prompts completos organizados en tres ciclos (Generar → Criticar → Decidir). |
| **Salida relevante** | Ver `salidas-ia.md` — se documentan únicamente las 6 salidas que modificaron el análisis. |
| **Evaluación humana** | Ver tabla del punto 2 de este archivo: 8 propuestas aceptadas, 5 modificadas, 6 rechazadas. |
| **Evidencia** | Observación directa del proceso actual de la clínica (cuaderno de consultas, carpeta de historias, Excel de inventario), revisión del modelo de datos del sistema, y normativa verificable. Ver `02-pestel/evidencias.md`. |
| **Decisión final** | Formulación B del problema (centrada en el veterinario y la trazabilidad del paciente), con PP1 como pain point principal y PP3 como secundario. |
| **Reflexión** | Ver punto 4 de este archivo. |

---

## 2. Matriz de decisiones

| # | Elemento analizado | Propuesta de la IA | Qué verificamos | Decisión del equipo | Razón / evidencia |
|---|---|---|---|---|---|
| 1 | Stakeholder: DIAN | Incluir como externo, poder alto, interés bajo | Revisamos el módulo de facturación: emite consecutivo interno sin numeración autorizada ni campos fiscales | **ACEPTADA** | La brecha es real y verificable en nuestro propio modelo de datos |
| 2 | Stakeholder: autoridad sanitaria | Incluir "ICA / autoridad de sanidad animal" | El ICA regula producción pecuaria; para pequeñas especies en Bogotá el interlocutor es la Secretaría Distrital de Salud / IDPYBA | **ACEPTADA CON CORRECCIÓN DE ENTIDAD** | La categoría era correcta; el nombre concreto, no. Aceptarlo tal cual habría dejado una afirmación no verificable |
| 3 | Stakeholder: mascotas | Incluir a los pacientes como stakeholder primario | Contrastamos con nuestra definición operativa: debe poder generar una estrategia de gestión | **RECHAZADA** | No admite estrategia de gestión posible. Su interés lo representan S5 y S2. Se modela como entidad del dominio |
| 4 | Stakeholder: aseguradoras de mascotas | Incluir como externo por facturación a terceros | Revisamos la facturación real de la clínica: 100 % a particular, sin convenios | **RECHAZADA** | Stakeholder de un negocio hipotético. Habría metido un canal y un ingreso inexistentes en el Canvas |
| 5 | Poder del peluquero | Poder medio ("define el precio del servicio") | El precio lo fija el administrador; el peluquero solo clasifica el tamaño | **MODIFICADA → poder bajo** | Ejecutar una regla no es definirla. Surgió un requisito nuevo: rango de peso objetivo |
| 6 | Poder del cliente final | Poder bajo (no decide nada) | Discutimos el costo de cambio: nulo, la competencia está en la cuadra siguiente | **MODIFICADA → poder medio** | La IA evaluó poder individual; el poder relevante es el agregado y de salida |
| 7 | Estrategia para DIAN | "Gestionar de cerca" | No es ejecutable: no se co-diseña con un regulador | **MODIFICADA** → "restricción no negociable" | Una estrategia que no se puede ejecutar no es una estrategia |
| 8 | Factor PESTEL: habeas data | Incluir Ley 1581 de 2012 como factor legal de alto impacto | Verificamos el modelo de datos: guardamos documento, teléfono y dirección de los propietarios | **ACEPTADA — impacto máximo** | Cambió tres decisiones de diseño: autorización de tratamiento, hash de contraseñas y justificación de los roles como medida de seguridad |
| 9 | Factor PESTEL: RESPEL | Incluir gestión de residuos peligrosos | Revisamos el módulo de inventario: la baja es genérica, sin tipo de movimiento | **ACEPTADA** | Generó el requisito de "baja por vencimiento" con traza de lote |
| 10 | Factores macroeconómicos (TRM, reforma tributaria, inestabilidad política) | Incluir como factores PESTEL | Preguntamos qué decisión del sistema cambia con cada uno | **RECHAZADOS (19 factores)** | Ninguno cambiaba una decisión concreta. Criterio: factor sin decisión asociada es contexto decorativo |
| 11 | IVA en servicios veterinarios | Incluir como factor legal | Un valor que puede cambiar por norma y debe ser editable | **RECONVERTIDO** en parámetro configurable del sistema | Una restricción parametrizable no es un factor de contexto |
| 12 | "Los clientes no vuelven" | Clasificado como **problema**, causa: falta de recordatorios | Buscamos evidencia de la causa del abandono: no tenemos ninguna | **RECHAZADA LA CLASIFICACIÓN** → síntoma sin causa identificada | **Decisión más importante del equipo.** Aceptarla habría llevado a elegir la Formulación A del problema |
| 13 | Prueba síntoma/problema | Método: "si al resolver X desaparecen Y y Z, X es el problema" | Lo aplicamos a los 18 pain points | **ACEPTADA como método** | Es una herramienta de razonamiento, no una afirmación sobre la clínica. Estructura el árbol de causalidad |
| 14 | Early adopter del Canvas | Debe ser el veterinario, no el administrador | Coherencia con la clasificación de S2 (poder de veto de hecho) | **ACEPTADA** | Quien decide comprar no es quien adopta. Cambió el diseño de la capacitación |
| 15 | Propuesta de valor del Canvas | Es una lista de módulos, no un valor | Comparamos con el bloque de ventaja especial: contradicción interna | **ACEPTADA** | Reescrita en términos verificables y con el afectado central nombrado |
| 16 | Fuentes de ingreso del Canvas | Añadir suscripción SaaS y venta a otras veterinarias | No existe ningún stakeholder identificado que corresponda a ese segmento | **RECHAZADA** | Habría roto la trazabilidad con el bloque 2. Reformulamos el bloque como ahorro y riesgo evitado |
| 17 | Recordatorios por WhatsApp a todos los clientes | Incluir como canal | Contradice el factor legal L1 | **ACEPTADA CON CONDICIÓN** | El canal se mantiene condicionado a la autorización de tratamiento de datos |
| 18 | Equipo de desarrollo como stakeholder | Excluirlo por ser ejecutor | Discutimos el sesgo de diseñar para la rúbrica | **RECHAZADA** | Toma decisiones de diseño reales; declararlo evita ocultar el sesgo |
| 19 | Formulación del problema | Recomienda B | Aplicamos la prueba de desaparición a las tres formulaciones | **ACEPTADA, con criterio propio añadido** | Añadimos el criterio de *poder explicativo*, que la IA no usó y que es el que más diferencia produce |
| 20 | Acortar la formulación B | Eliminar la mención a la ventana de 15–20 minutos | Sin esa ventana, B se vuelve un enunciado abstracto aplicable a cualquier organización | **RECHAZADA** | Lo que la IA veía como exceso de longitud es lo que hace el problema operativo y medible |

**Resumen:** 8 aceptadas · 5 modificadas o condicionadas · 7 rechazadas (una de
ellas agrupa 19 factores PESTEL).

---

## 3. Métricas de la interacción

| Indicador | Valor |
|---|---|
| Ciclos completos Generar → Criticar → Decidir | 3 |
| Prompts registrados | 9 |
| Propuestas de stakeholders evaluadas | 5 |
| Factores PESTEL propuestos / conservados | 31 / 12 |
| Pain points propuestos / conservados como problema | 18 / 10 |
| Formulaciones del problema evaluadas | 3 |
| Tasa de aceptación sin modificación | **40 %** |

---

## 4. Reflexión del equipo

### ¿En qué se equivocó o quedó corta la IA?

1. **Calibró mal el poder relativo, de forma sistemática.** Falló en dos de los
   diez stakeholders (peluquero y cliente), y en ambos casos por la misma razón:
   el poder depende de hechos locales que no están en el prompt (quién firma,
   quién paga, quién puede irse sin costo). La IA razonó sobre la descripción
   del rol; nosotros razonamos sobre la clínica.

2. **Completó huecos con plausibilidad en lugar de declarar ignorancia.** El
   caso de *"los clientes no vuelven porque no reciben recordatorios"* es el más
   claro: construyó una relación causal que suena razonable y que no teníamos
   cómo sostener. Es el riesgo real de esta herramienta: **no produce
   afirmaciones absurdas, produce afirmaciones verosímiles sin respaldo**, que
   son mucho más difíciles de detectar.

3. **Propuso stakeholders y modelos de negocio que no existen** (aseguradoras,
   suscripción SaaS). Le faltaba el dato que solo se obtiene mirando las
   facturas reales.

4. **No jerarquiza espontáneamente.** Entregó 31 factores PESTEL sin distinguir
   los tres bloqueantes del resto. Generar es barato; priorizar es la parte
   cara, y esa no la hizo.

5. **Confundió extensión con falta de claridad** al evaluar la Formulación B, y
   propuso recortar justo el elemento que la hacía operativa.

### ¿Qué aportó el equipo que la IA no podía decidir por sí sola?

1. **El contexto real de la clínica.** Que no hay convenios con aseguradoras,
   que el cuaderno se organiza por nombre del animal, que el precio de
   peluquería lo fija el administrador, que la salida de insumo ocurre en el
   consultorio y nadie la anota. Nada de eso estaba en ningún prompt: se obtiene
   mirando.

2. **El criterio de admisión de factores.** *"Si no cambia una decisión concreta
   del sistema, no entra."* Ese filtro eliminó 19 de 31 factores. La IA no lo
   habría aplicado sola porque cada factor, tomado aisladamente, era verdadero.

3. **La distinción entre poder individual y poder agregado**, que reubicó al
   cliente en la matriz.

4. **La decisión de no usar "los clientes no vuelven"** como justificación de
   nada. Renunciar a un argumento cómodo porque no está sostenido es una
   decisión de integridad, no de análisis, y no se delega.

5. **El criterio de poder explicativo** para elegir la formulación del problema,
   y la prueba de desaparición aplicada a las tres alternativas.

6. **La declaración explícita de nuestras cinco fisuras** (`evidencias.md`). Una
   IA optimiza por dar una respuesta completa; un equipo que va a sustentar
   necesita saber exactamente dónde está parado en falso.

### Conclusión sobre el método

La IA fue más útil como **revisor de consistencia** que como generador de
contenido. Su mejor momento de toda la actividad fue detectar una contradicción
interna de nuestro propio documento (el peluquero tenía poder medio en la tabla
y ningún poder en la descripción del proceso). Su peor momento fue inventar una
causa para un fenómeno del que no teníamos datos.

**La regla práctica que sacamos:** usar la IA para preguntar *"¿qué me falta?"* y
*"¿en qué me contradigo?"*, nunca para preguntar *"¿qué debo concluir?"*.
