# Fase 2 — Evidencias, supuestos y opiniones

**Propósito:** para cada factor PESTEL seleccionado, dejar explícito qué lo
sustenta y qué sigue siendo un supuesto sin validar. Este archivo es el que
sostiene el criterio de resistencia del repositorio.

---

## Convención de etiquetas

| Etiqueta | Significado |
|---|---|
| `[EVIDENCIA-D]` | **Evidencia directa.** Observación propia del equipo sobre la operación real de la clínica o sobre el sistema construido. |
| `[EVIDENCIA-N]` | **Evidencia normativa.** Norma vigente, verificable en fuente oficial. |
| `[EVIDENCIA-S]` | **Evidencia secundaria.** Dato de fuente externa (sectorial, estadística). |
| `[SUPUESTO]` | Afirmación plausible que el equipo **aún no ha validado**. |
| `[OPINIÓN]` | Juicio del equipo. No se usa para sostener requisitos. |

---

## Tabla de trazabilidad por factor

| Factor | Afirmación | Etiqueta | Soporte / Método de validación pendiente |
|---|---|---|---|
| **P1** | Existe política pública distrital de bienestar animal con campañas gratuitas de vacunación | `[EVIDENCIA-N]` | Portal del instituto distrital de protección y bienestar animal |
| **P1** | Un porcentaje relevante de pacientes de la clínica se vacuna en campañas | `[SUPUESTO]` | Revisar 30 historias del cuaderno y contar cuántas tienen vacunas sin registro propio |
| **P2** | La obligación de facturación electrónica se ha extendido progresivamente a micronegocios | `[EVIDENCIA-N]` | Normativa DIAN vigente |
| **P2** | Esta clínica específica está obligada hoy | `[SUPUESTO]` | **Preguntar al contador (S7).** Pregunta concreta: "¿La clínica está obligada a factura electrónica y desde cuándo?" |
| **E1** | La clínica no puede asumir licencias recurrentes | `[SUPUESTO]` fuerte | Preguntar al administrador (S1) cuánto paga hoy por software y cuánto estaría dispuesto a pagar al mes |
| **E1** | El stack elegido no tiene costo de licencia | `[EVIDENCIA-D]` | Verificado por el equipo: Jakarta EE, Tomcat, MySQL Community, PrimeFaces Community |
| **E2** | El gasto de los hogares en mascotas crece sostenidamente | `[EVIDENCIA-S]` | Informes sectoriales de consumo. **Citar fuente concreta antes de la sustentación** |
| **E2** | Esa tendencia aplica al barrio de la clínica | `[SUPUESTO]` | Comparar facturación de los últimos 12 meses (si existe registro) |
| **S1** | Los propietarios esperan trato individualizado por la mascota | `[EVIDENCIA-S]` | Literatura sobre humanización de mascotas |
| **S1** | En esta clínica el registro se organiza por nombre del animal | `[EVIDENCIA-D]` | Observación del cuaderno de consultas: los encabezados son el nombre del animal |
| **S2** | El personal tiene baja alfabetización en software de gestión | `[SUPUESTO]` de alto impacto | **Prueba de usabilidad cronometrada:** pedir a la auxiliar registrar una consulta completa y medir tiempo y errores. Umbral aceptable: < 2 min |
| **T1** | La clínica opera con equipos de gama baja y conectividad doméstica | `[SUPUESTO]` | Inspección de 15 min: RAM, SO, navegador, tipo de conexión |
| **T1** | Un sistema dependiente de internet dejaría de operar en cortes | `[EVIDENCIA-D]` | Deducción verificable de la arquitectura, no de la clínica |
| **T2** | WhatsApp es el canal de contacto dominante | `[EVIDENCIA-S]` | Penetración documentada del canal en Colombia |
| **T2** | Los clientes de esta clínica aceptarían recordatorios por ese canal | `[SUPUESTO]` | Encuesta de 3 preguntas en recepción durante una semana |
| **A1** | Los residuos veterinarios son RESPEL con obligación de gestor autorizado | `[EVIDENCIA-N]` | Normativa ambiental de residuos peligrosos y biosanitarios |
| **A1** | La clínica hoy no deja traza documental de esas bajas | `[SUPUESTO]` | Preguntar si existe contrato con gestor y si llevan planilla |
| **A2** | La clínica usa papel para historia y factura | `[EVIDENCIA-D]` | Observación directa |
| **A2** | Digitalizar reducirá significativamente el consumo | `[OPINIÓN]` | **No se usa para sostener ningún requisito.** Se declara como expectativa |
| **L1** | La Ley 1581 de 2012 aplica al tratamiento de datos de los clientes | `[EVIDENCIA-N]` | Texto de la ley |
| **L1** | El sistema hoy almacena datos personales identificables | `[EVIDENCIA-D]` | Verificado en el modelo de datos: tabla de propietarios con documento, teléfono y dirección |
| **L2** | El acto médico debe ser atribuible y documentado | `[EVIDENCIA-N]` | Marco de ejercicio profesional veterinario |
| **L2** | El tiempo mínimo de conservación de la historia clínica veterinaria | `[SUPUESTO]` | **No lo sabemos.** Se debe consultar antes de definir política de purga de datos |

---

## Lo que el equipo NO puede afirmar todavía

Declaración explícita para la sustentación. Estas son las **cinco fisuras
conocidas** de nuestro análisis:

1. **No hemos entrevistado formalmente al personal.** Toda la caracterización de
   S2, S3 y S4 se basa en observación y en el conocimiento del proceso, no en
   entrevista estructurada con registro.
2. **No tenemos datos cuantitativos de la operación**: número de consultas
   diarias, tasa de retorno a refuerzo de vacuna, porcentaje de descuadre de
   inventario. Todos los impactos económicos que estimamos son órdenes de
   magnitud, no mediciones.
3. **No hemos confirmado la obligación tributaria concreta** de la clínica en
   materia de facturación electrónica.
4. **No hemos verificado el requisito legal de conservación** de la historia
   clínica veterinaria.
5. **El supuesto E1 (presupuesto ≈ 0) no está validado** y, sin embargo, es el
   que más recortó el espacio de soluciones. Si fuera falso, se abriría la
   opción de software comercial y **el proyecto entero cambiaría de
   justificación**. Es nuestro supuesto más riesgoso.

---

## Factores propuestos por la IA y DESCARTADOS

| Factor propuesto | Dimensión | Razón del descarte |
|---|---|---|
| Inestabilidad cambiaria y su efecto en el precio de importados | Económico | Real, pero **no cambia ninguna decisión del sistema**. El sistema registra el precio que le den; no lo negocia. |
| Reforma tributaria y tarifa de IVA en servicios veterinarios | Económico/Legal | Se descarta como factor y se conserva como **parámetro configurable** en el módulo de facturación. Un valor que debe ser editable no es un factor de contexto. |
| Adopción de inteligencia artificial en diagnóstico veterinario por imagen | Tecnológico | Fuera de alcance por completo. La clínica no tiene equipo de imagenología. Habría inflado el Canvas con una ventaja inexistente. |
| Tensión política nacional / cambio de gobierno | Político | Demasiado general. No pudimos formular ninguna decisión concreta que cambiara. **Criterio aplicado: si no cambia una decisión, no entra.** |
| Teletrabajo y consulta veterinaria remota | Social/Tecnológico | Aplicable a cadenas grandes; la clínica atiende presencialmente por naturaleza del servicio (examen físico del paciente). |
| Escasez de talento en desarrollo de software | Económico | Afecta al equipo de desarrollo, no al sistema ni a la clínica. Confunde el contexto del proyecto con el contexto del producto. |
| Huella de carbono del hosting | Ambiental | Despreciable a esta escala; habría sido un factor "para llenar la casilla". |
| Cambio climático y enfermedades vectoriales estacionales | Ambiental | **Descarte discutido.** Es plausible que aumente la demanda de desparasitación en ciertas épocas, pero no tenemos ningún dato local. Se descarta por falta de evidencia, no por irrelevancia. Queda registrado como hipótesis futura. |

**Nota metodológica:** descartamos 19 de 31 factores propuestos. El filtro fue
siempre el mismo pregunta: *¿qué decisión concreta del sistema cambia si este
factor es cierto?* Si la respuesta era "ninguna", el factor salía, por muy
verdadero que fuera.
