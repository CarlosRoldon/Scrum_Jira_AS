# Fase 2 — Análisis PESTEL

**Sistema:** Sistema de Gestión Integral para Veterinaria Sandoval (SGV)
**Regla del equipo:** un factor solo entra al PESTEL si podemos decir **qué
decisión del sistema condiciona**. Un factor que no cambia ninguna decisión es
contexto decorativo y lo descartamos.

De 31 factores propuestos por la IA a lo largo de dos ciclos, **conservamos 12**
(2 por dimensión). Los descartes están en `evidencias.md`.

---

## P — POLÍTICO

### P1. Política distrital de bienestar y protección animal en Bogotá

- **Qué condiciona:** la existencia de un instituto distrital dedicado a
  protección animal y de campañas públicas de esterilización y vacunación
  antirrábica gratuitas significa que **parte de la demanda de vacunación se
  atiende fuera del canal privado**.
- **Decisión que cambia:** el módulo de vacunación no puede asumir que todas
  las dosis aplicadas a un paciente fueron aplicadas en la clínica. Debe
  permitir **registrar dosis aplicadas en otro sitio** (campaña distrital, otra
  veterinaria) para que el esquema de vacunación quede completo.
- **Estado:** `[EVIDENCIA]` para la existencia de la política pública;
  `[SUPUESTO]` para el porcentaje de pacientes afectados.

### P2. Presión regulatoria creciente sobre la formalización de micronegocios

- **Qué condiciona:** los establecimientos pequeños están siendo incorporados de
  forma progresiva a obligaciones de facturación y reporte electrónico antes
  reservadas a empresas medianas.
- **Decisión que cambia:** el módulo de facturación **no puede diseñarse como un
  consecutivo interno**. Debe nacer preparado para numeración autorizada y
  exportación a un proveedor tecnológico de facturación electrónica.
- **Estado:** `[EVIDENCIA]` para la tendencia normativa; `[SUPUESTO]` para el
  calendario exacto aplicable a esta clínica — debe confirmarlo el contador (S7).

---

## E — ECONÓMICO

### E1. Estructura de costos de un micronegocio: presupuesto de TI cercano a cero

- **Qué condiciona:** una clínica de barrio con 5 empleados no sostiene
  licencias por usuario, ni un servidor propio, ni un contrato de soporte.
- **Decisión que cambia:** descartamos cualquier alternativa con costo de
  licencia recurrente. El stack elegido (Jakarta EE, MySQL, Tomcat) es libre, y
  el despliegue debe caber en un hosting compartido o en el equipo de recepción
  de la clínica. **Esta es la restricción que más recortó el espacio de
  soluciones.**
- **Estado:** `[SUPUESTO FUERTE]` — se valida preguntando al administrador (S1)
  cuánto paga hoy por software. Método de validación en `evidencias.md`.

### E2. Crecimiento del gasto de los hogares en mascotas

- **Qué condiciona:** el gasto en salud y cuidado de animales de compañía viene
  creciendo por encima de otras categorías de consumo del hogar. Esto sostiene
  la demanda de servicios recurrentes (vacunación, peluquería, alimento).
- **Decisión que cambia:** justifica invertir en la **trazabilidad del
  recurrente** (esquema de vacunación, refuerzos, desparasitación periódica) y
  no solo en el registro de la consulta puntual. El valor del sistema está en
  la recurrencia, no en la transacción aislada.
- **Estado:** `[EVIDENCIA]` para la tendencia sectorial; `[SUPUESTO]` para que
  se cumpla en el barrio específico de la clínica.

---

## S — SOCIAL

### S1. Humanización de la mascota y expectativa de trato individualizado

- **Qué condiciona:** el propietario ya no percibe al animal como propiedad sino
  como miembro del hogar, y espera que la clínica **recuerde a su mascota por
  el nombre y conozca su historia**.
- **Decisión que cambia:** la búsqueda del paciente debe ser por nombre de la
  mascota, no solo por documento del propietario; y la pantalla de atención
  debe mostrar el historial reciente en el primer golpe de vista, sin
  navegación adicional.
- **Estado:** `[EVIDENCIA]` para el fenómeno social general; `[EVIDENCIA
  DIRECTA]` para la clínica: en el cuaderno actual los registros están
  encabezados por el nombre del animal, no por el del dueño. El proceso real ya
  refleja esa expectativa.

### S2. Brecha de alfabetización digital del personal no administrativo

- **Qué condiciona:** el personal que más usará el sistema (auxiliar, peluquero)
  tiene experiencia con WhatsApp y con Excel básico, no con software de
  gestión.
- **Decisión que cambia:** prohíbe formularios con muchos campos obligatorios y
  obliga a valores por defecto, listas desplegables en lugar de texto libre, y
  mensajes de error en lenguaje natural. **Un sistema correcto pero incómodo
  produce el mismo resultado que no tener sistema: se vuelve al cuaderno.**
- **Estado:** `[SUPUESTO]` de alto impacto. Validación: prueba de usabilidad
  cronometrada con la auxiliar sobre el registro de una consulta.

---

## T — TECNOLÓGICO

### T1. Infraestructura local limitada y conectividad no garantizada

- **Qué condiciona:** la clínica opera con uno o dos equipos de escritorio de
  gama baja y conexión de internet doméstica. Un corte de internet en horario
  de atención no es excepcional.
- **Decisión que cambia:** descartamos una arquitectura que dependa de servicios
  externos en línea para operar el núcleo (registrar consulta, facturar). El
  despliegue local con MySQL en la misma máquina mantiene la clínica operando
  sin internet. Obliga además a **definir un procedimiento de respaldo**, que
  en una instalación local es responsabilidad de la clínica y no del proveedor.
- **Estado:** `[SUPUESTO]` verificable con una inspección de 15 minutos del
  equipo de recepción (RAM, sistema operativo, navegador).

### T2. Adopción generalizada de WhatsApp como canal de contacto

- **Qué condiciona:** el canal real de comunicación con el cliente ya existe y
  no es el correo electrónico ni una app propia: es WhatsApp.
- **Decisión que cambia:** el sistema **no debe construir un canal de
  notificación propio**. Debe generar el texto del recordatorio y el número, y
  dejar el envío en el canal que el cliente ya usa. Esto elimina un módulo
  completo del alcance.
- **Estado:** `[EVIDENCIA]` para la penetración del canal; `[SUPUESTO]` para que
  los clientes acepten recordatorios por ese medio — requiere autorización
  expresa por habeas data (ver L1).

---

## E — ECOLÓGICO / AMBIENTAL

### A1. Gestión de residuos biosanitarios y peligrosos (RESPEL)

- **Qué condiciona:** agujas, envases de biológicos, medicamentos vencidos y
  material de curación son residuos peligrosos con obligación de segregación y
  entrega a gestor autorizado, con soporte documental.
- **Decisión que cambia:** el módulo de inventario **no puede tratar la salida
  de un medicamento vencido como una simple baja de stock**. Necesita un tipo de
  movimiento "baja por vencimiento / disposición" que deje traza de fecha,
  lote y cantidad, porque ese dato alimenta el soporte de entrega al gestor.
- **Estado:** `[EVIDENCIA]` para la obligación normativa general; `[SUPUESTO]`
  para la práctica actual de la clínica.

### A2. Sustitución de soporte en papel

- **Qué condiciona:** la historia clínica en papel consume archivo físico, se
  deteriora y se reimprime; la factura impresa por duplicado es el estándar
  actual de la clínica.
- **Decisión que cambia:** la factura debe poder entregarse en formato digital
  y la historia clínica debe ser consultable en pantalla con calidad suficiente
  para **no tener que imprimirla** para la consulta. Si el veterinario imprime
  igual, el beneficio ambiental y el de trazabilidad se pierden a la vez.
- **Estado:** `[OPINIÓN]` en cuanto a la magnitud del ahorro; `[EVIDENCIA
  DIRECTA]` en cuanto al uso actual de papel.

---

## L — LEGAL

### L1. Ley 1581 de 2012 — Protección de datos personales (habeas data)

- **Qué condiciona:** el sistema almacena datos personales identificables de los
  propietarios (nombre, documento, dirección, teléfono). Eso obliga a
  autorización para el tratamiento, finalidad declarada, medidas de seguridad y
  derecho de supresión.
- **Decisión que cambia:** tres consecuencias directas de diseño:
  1. campo de **autorización de tratamiento de datos** en el registro de
     cliente, con fecha — sin él, no se puede enviar el recordatorio de T2;
  2. **contraseñas almacenadas con hash**, nunca en texto plano;
  3. el control de acceso por rol (`ADMINISTRADOR`, `VETERINARIO`, `EMPLEADO`)
     deja de ser una comodidad y pasa a ser una **medida de seguridad exigible**.
- **Estado:** `[EVIDENCIA]` — norma vigente y aplicable sin ambigüedad.
- **Nota:** este es el factor PESTEL que **más cambió nuestro análisis**. En la
  primera versión, los roles estaban justificados solo por comodidad operativa.

### L2. Marco legal de ejercicio profesional y protección animal

- **Qué condiciona:** el ejercicio de la medicina veterinaria y el estatuto
  nacional de protección animal exigen que el acto médico quede documentado y
  sea atribuible a un profesional identificado.
- **Decisión que cambia:** todo registro de historia clínica debe quedar
  **firmado por el usuario que lo creó y no debe poder borrarse**. Las
  correcciones se hacen por adición (nota aclaratoria), no por sobrescritura.
  Esto cambia el modelo de datos: la historia clínica es un **registro
  append-only**, no una tabla editable.
- **Estado:** `[EVIDENCIA]` para la exigencia de trazabilidad del acto médico;
  `[SUPUESTO]` sobre el tiempo mínimo de conservación aplicable.

---

## Matriz de impacto — factores priorizados

| Factor | Dimensión | Impacto en el sistema | Urgencia | ¿Bloqueante? |
|---|---|---|---|---|
| **L1** Habeas data | Legal | Muy alto | Alta | **Sí** |
| **E1** Presupuesto TI ≈ 0 | Económico | Muy alto | Alta | **Sí** |
| **L2** Trazabilidad del acto médico | Legal | Alto | Alta | **Sí** |
| **S2** Brecha digital del personal | Social | Alto | Alta | No (pero mata la adopción) |
| **T1** Infraestructura local | Tecnológico | Alto | Media | No |
| **P2** Facturación electrónica | Político | Alto | Media | Futuro cercano |
| **T2** WhatsApp como canal | Tecnológico | Medio | Media | No |
| **S1** Humanización de la mascota | Social | Medio | Media | No |
| **A1** Residuos RESPEL | Ambiental | Medio | Baja | No |
| **E2** Gasto en mascotas | Económico | Medio | Baja | No |
| **P1** Campañas distritales | Político | Bajo-Medio | Baja | No |
| **A2** Reducción de papel | Ambiental | Bajo | Baja | No |

**Conclusión de la fase:** los tres factores bloqueantes son **legales y
económicos, no tecnológicos**. Esto contradice la intuición inicial del equipo,
que había priorizado factores tecnológicos.
