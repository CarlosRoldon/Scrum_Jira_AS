# Fase 1 — Mapa de Stakeholders

**Sistema:** Sistema de Gestión Integral para Veterinaria Sandoval (SGV)
**Squad:** 06 · **Fecha:** 16 de septiembre de 2026

---

## 1. Definición operativa adoptada

Para esta actividad entendemos por **stakeholder** toda persona, grupo u
organización que (a) tiene interés en el sistema, (b) tiene capacidad de
influir sobre su adopción o continuidad, o (c) se ve afectada por su
funcionamiento, aunque no lo use directamente.

**Criterio de exclusión que aplicamos:** un actor que no puede tomar ninguna
decisión, expresar ninguna preferencia ni ejercer ninguna presión sobre el
sistema **no es stakeholder**, aunque aparezca en la base de datos. Por eso las
mascotas se modelan como *entidad del dominio* (paciente), no como stakeholder;
su interés lo representa el propietario. Esta distinción la discutimos a raíz
de una propuesta de la IA (ver `decisiones-stakeholders.md`, caso 3).

---

## 2. Tipología usada

| Tipo | Definición aplicada al SGV |
|---|---|
| **Primario** | Usa el sistema directamente en su trabajo diario. |
| **Clave / decisor** | Autoriza, financia o puede cancelar el proyecto. |
| **Secundario** | No lo usa a diario, pero consume sus salidas o lo soporta. |
| **Externo** | No lo usa, pero impone restricciones o se ve afectado por sus resultados. |

---

## 3. Registro de stakeholders

> 10 stakeholders identificados (mínimo exigido: 6).

### S1 — Propietario-administrador de la clínica (Dr. Sandoval)

- **Tipo:** Clave / decisor
- **Poder:** ALTO · **Interés:** ALTO · **Cuadrante:** Gestionar de cerca
- **Estrategia de gestión:** Involucrarlo en cada validación de requisitos;
  demos quincenales; decisiones de alcance se cierran con su firma.
- **Justificación del poder:** es quien paga el hosting, autoriza el cambio de
  proceso y puede devolver la operación al papel en cualquier momento. Ningún
  otro actor puede revertir el proyecto por sí solo.
- **Justificación del interés:** el descuadre de inventario y la pérdida de
  ingresos lo afectan directamente en su margen.

### S2 — Médicos veterinarios (2)

- **Tipo:** Primario
- **Poder:** MEDIO-ALTO · **Interés:** ALTO · **Cuadrante:** Gestionar de cerca
- **Estrategia de gestión:** co-diseño de la pantalla de historia clínica;
  validación de campos obligatorios con ellos antes de codificar; medir tiempo
  de registro por consulta.
- **Justificación del poder:** no pueden cancelar el proyecto, pero **su no-uso
  lo mata**. Si registrar la consulta les toma más tiempo que escribir en el
  cuaderno, vuelven al papel y el sistema queda vacío. Es poder de veto de
  hecho, no formal — por eso MEDIO-ALTO y no ALTO.
- **Justificación del interés:** son los que hoy asumen el riesgo clínico de
  decidir sin historia completa.

### S3 — Auxiliar de recepción / empleado

- **Tipo:** Primario
- **Poder:** BAJO · **Interés:** ALTO · **Cuadrante:** Mantener informado
- **Estrategia de gestión:** capacitación práctica sobre agenda y facturación;
  canal directo para reportar fricciones de uso; es la fuente principal de
  requisitos de usabilidad.
- **Justificación del poder:** ejecuta, no decide. No controla presupuesto ni
  proceso.
- **Justificación del interés:** es quien más horas pasa en el sistema (agenda,
  registro de clientes, facturación) y quien recibe los reclamos del cliente
  cuando algo falla.

### S4 — Peluquero canino / groomer

- **Tipo:** Primario
- **Poder:** BAJO · **Interés:** MEDIO-ALTO · **Cuadrante:** Mantener informado
- **Estrategia de gestión:** validar con él la tabla de tarifas por tamaño del
  paciente y el flujo de agendamiento del servicio estético.
- **Justificación:** el módulo de peluquería tarifa por tamaño del paciente; si
  la clasificación de tamaños no coincide con la que él usa en la práctica, el
  precio facturado será incorrecto de forma sistemática. Lo incorporamos
  después de la crítica de la IA (ver `decisiones-stakeholders.md`, caso 1).

### S5 — Propietarios de mascotas (clientes)

- **Tipo:** Primario externo
- **Poder:** MEDIO · **Interés:** ALTO · **Cuadrante:** Mantener informado (franja superior, en el límite con «gestionar de cerca»)
- **Estrategia de gestión:** no se les da acceso al sistema en la primera
  versión; se les consulta mediante encuesta corta en recepción sobre
  recordatorios y entrega de factura.
- **Justificación del poder:** individualmente no deciden nada, pero
  **colectivamente pueden migrar a otra clínica**. Es poder de mercado, difuso
  pero real. Por eso MEDIO.
- **Justificación del interés:** su mascota y su dinero están en juego.

### S6 — Proveedores de medicamentos, biológicos e insumos

- **Tipo:** Externo
- **Poder:** MEDIO · **Interés:** BAJO · **Cuadrante:** Mantener satisfecho
- **Estrategia de gestión:** acordar formato de remisión/lote para que el
  ingreso a inventario sea trazable; no participan en el diseño.
- **Justificación:** controlan disponibilidad, precios, lotes y fechas de
  vencimiento — datos que el sistema debe registrar. Pero les es indiferente
  qué software use la clínica.

### S7 — Contador externo de la clínica

- **Tipo:** Secundario
- **Poder:** MEDIO · **Interés:** MEDIO · **Cuadrante:** Mantener satisfecho
- **Estrategia de gestión:** definir con él el reporte de ventas y el formato de
  exportación antes de cerrar el módulo de facturación.
- **Justificación:** no usa el sistema a diario, pero **consume sus salidas**.
  Si el reporte no le sirve, el administrador seguirá llevando la contabilidad
  aparte y el sistema pierde su razón de ser en el módulo de facturación.

### S8 — DIAN (facturación electrónica)

- **Tipo:** Externo regulador
- **Poder:** ALTO · **Interés:** BAJO · **Cuadrante:** Mantener satisfecho
- **Estrategia de gestión:** monitorear normativa vigente; tratar la
  numeración, la resolución de facturación y el formato electrónico como
  restricción no negociable del diseño.
- **Justificación del poder:** puede sancionar y obligar a rehacer el módulo de
  facturación completo. Ninguna decisión del equipo puede sobreponerse a su
  norma.
- **Justificación del interés BAJO:** no tiene ningún interés en este proyecto
  en particular; su relación con el sistema es puramente normativa. **Poder alto
  + interés bajo no significa "ignorable": significa que si se despierta, se
  vuelve bloqueante.**

### S9 — Autoridad sanitaria distrital (Secretaría Distrital de Salud / IDPYBA)

- **Tipo:** Externo regulador
- **Poder:** ALTO · **Interés:** BAJO · **Cuadrante:** Mantener satisfecho
- **Estrategia de gestión:** verificar qué reporte de vacunación antirrábica se
  exige y en qué formato; dejar el campo de lote de biológico como obligatorio
  desde el inicio.
- **Justificación:** la vacunación antirrábica tiene control sanitario; el
  registro de lote y fecha no es un "campo más", es un requisito de
  trazabilidad ante la autoridad.

### S10 — Equipo de desarrollo (Squad 04) y docente evaluador

- **Tipo:** Secundario
- **Poder:** MEDIO · **Interés:** ALTO · **Cuadrante:** Mantener informado
- **Estrategia de gestión:** entregas semanales, sustentación y registro de
  decisiones en el repositorio.
- **Justificación:** el equipo decide el "cómo" técnico (poder de diseño), pero
  no el "qué" del negocio. El docente condiciona el alcance vía rúbrica.
  Reconocerlo explícitamente evita el sesgo de diseñar para la nota y no para
  la clínica.

---

## 4. Tabla resumen — Matriz Poder/Interés

| ID | Stakeholder | Tipo | Poder | Interés | Cuadrante | Estrategia |
|---|---|---|---|---|---|---|
| S1 | Propietario-administrador | Clave/decisor | Alto | Alto | Gestionar de cerca | Validación y firma de alcance |
| S2 | Médicos veterinarios | Primario | Medio-Alto | Alto | Gestionar de cerca | Co-diseño de historia clínica |
| S3 | Auxiliar de recepción | Primario | Bajo | Alto | Mantener informado | Capacitación y canal de fricciones |
| S4 | Peluquero canino | Primario | Bajo | Medio-Alto | Mantener informado | Validar tarifas por tamaño |
| S5 | Propietarios de mascotas | Primario externo | Medio | Alto | Mantener informado (franja superior) | Encuesta en recepción |
| S6 | Proveedores de insumos | Externo | Medio | Bajo | Mantener satisfecho | Acordar formato de lote |
| S7 | Contador externo | Secundario | Medio | Medio | Mantener satisfecho | Definir reporte de ventas |
| S8 | DIAN | Externo regulador | Alto | Bajo | Mantener satisfecho | Restricción no negociable |
| S9 | Autoridad sanitaria distrital | Externo regulador | Alto | Bajo | Mantener satisfecho | Trazabilidad de biológicos |
| S10 | Squad 04 + docente | Secundario | Medio | Alto | Mantener informado | Entregas y sustentación |

**Distribución por cuadrante**

```
                    INTERÉS BAJO              INTERÉS ALTO
                ┌──────────────────────┬──────────────────────┐
   PODER ALTO   │  Mantener satisfecho │  Gestionar de cerca  │
                │  S8 DIAN             │  S1 Administrador    │
                │  S9 Autoridad sanit. │  S2 Veterinarios     │
                ├──────────────────────┼──────────────────────┤
   PODER BAJO   │  Monitorear          │  Mantener informado  │
                │  S6 Proveedores*     │  S3 Auxiliar         │
                │  S7 Contador*        │  S4 Peluquero        │
                │                      │  S5 Clientes*        │
                │                      │  S10 Squad + docente │
                └──────────────────────┴──────────────────────┘
   * poder medio: se ubican en la franja intermedia de la matriz gráfica.
```

Ver `matriz-poder-interes.png` para la ubicación exacta en el plano.

---

## 5. Observación crítica sobre la matriz

El cuadrante más peligroso de este proyecto **no es** "gestionar de cerca", sino
**"poder alto / interés bajo"** (S8 y S9). Son actores que nadie consulta
durante el desarrollo porque no piden nada, pero cuyo incumplimiento se
descubre tarde y obliga a rehacer trabajo. Documentamos esto porque en la
primera versión de nuestro mapa ninguno de los dos aparecía.
