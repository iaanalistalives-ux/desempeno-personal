# CLAUDE.md — Desempeño de Personal (desempeno-personal)

Las reglas generales de trabajo están en el repo privado `lives-instrucciones` (CLAUDE.md). Este archivo solo describe esta herramienta.

## Qué hace
`index.html` es un **tablero de solo lectura** del desempeño individual, con ranking entre compañeros. No guarda nada; los datos llegan en vivo, uno por persona y día (en Potenciales, por persona y semana).

Cinco pestañas:
- **Auditoras**: prendas auditadas (predeterminado), auditorías, auditorías por día, % rechazo = rechazadas ÷ auditorías, % prendas defectuosas = defectuosas ÷ auditadas.
- **Inspectoras auditadas**: el trabajo de cada inspectora según cómo salió auditado: % rechazo de su trabajo (menor es mejor), % prendas defectuosas, auditorías a su trabajo.
- **Insp. Final Costura**: % eficiencia = minutos ganados ÷ minutos asistidos (minutos ganados = (prendas + reinspeccionadas) × T. STD, solo si hubo minutos asistidos), prendas por día, % primeras, prendas inspeccionadas, defectos.
- **Eficiencia**: Acabados (Doblado, Plancha, Vapor, Encajado y Apoyo), Costura y Corte. % eficiencia = minutos producidos ÷ minutos asistidos, ponderado por día (puede diferir hasta 2 puntos de la semanal de pago), incentivo (S/) y horas asistidas.
- **Potenciales**: potencial promedio = suma de potenciales ÷ mediciones.

Cómo se calcula:
- Todo ponderado: suma de numeradores ÷ suma de denominadores del período.
- Mínimo de datos para entrar al ranking (3 / 8 / 8 auditorías o días por semana, mes o año; en Potenciales 1 / 2 / 4 mediciones).
- Puntaje 0–100 = percentil entre compañeros (mínimo 3 personas con datos suficientes; en Eficiencia y Potenciales, dentro de cada área).
- Referencia del grupo = media ± 1 desviación estándar ("Sobre / Como / Bajo sus compañeras"). Comparación con su propio promedio de hasta 3 períodos anteriores.
- Alertas: baja o sube N períodos seguidos, su mejor y peor marca, tercio más bajo N seguidos; en IFC, "Faltan horas en N días".

Vistas: Semana/Mes/Año con ‹ ›, área, indicador, Tarjetas/Tabla, búsqueda por persona; KPIs con mini-gráficos, ranking, tendencia, "Quién más cambió", mapa por período y ficha por persona ("Día por día", hasta 500 filas). Excel LIVES con Resumen (indicadores y ranking) y Detalle.

## Base de datos (Supabase lives-datos)
- Una sola función: `desempeno_personal` (`p_accion:'datos'`, `p.grupo`: auditoras, inspectoras, ifc, acabados, potenciales).
- Lee: `auditorias`, `auditoria_auditoras`, `ifc_registros`, `ifc_horas_jornada`, `acabados_hist_persona_dia`, `potenciales`. Los datos se registran en sus propias herramientas (Registro de Auditorías, Auditoría Final, Inspección Final de Costura, Acabados, Potenciales).
- No usa Storage.

## Quién la usa
Según las entradas por el portal de los últimos 30 días al 21/10/2026: 2 personas (incluye Datos e IA).

## Quién puede ver
Solo lectura; no tiene permisos propios.
