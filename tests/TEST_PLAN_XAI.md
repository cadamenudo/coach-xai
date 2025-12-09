# TEST PLAN – COACH XAI

Este documento define cómo vamos a validar que el Coach Xai se comporta de forma:
- consistente,
- útil,
- segura,
- alineada con su identidad y filosofía.

---

## 1. Objetivos de prueba

1. Verificar que el Coach:
   - respeta el tono cálido, empático y sin juicio.
   - usa pasos pequeños y concretos.
   - no recomienda productos financieros ni inversiones.
   - no inventa datos ni números.
   - prioriza bien entre déficit, deuda, reserva y metas.

2. Validar que las respuestas cambian según:
   - el estadio financiero (Sobreviviendo, Asegurar, Acumular).
   - el tipo de problema principal.
   - la emoción del usuario (estrés, confusión, motivación).

---

## 2. Formato de cada escenario

Cada escenario de prueba debe incluir:

- **Resumen de datos de la app** (lo que vería Xai).
- **Mensaje del usuario** (texto libre).
- **Estadio esperado** (Sobreviviendo / Asegurando / Acumulando).
- **Módulos que debería activar** (reserva, deudas, metas, desviaciones, etc.).
- **Checklist de lo que la respuesta debe cumplir**:
  - tono correcto,
  - estructura (empatía → diagnóstico → explicación → paso pequeño → motivación),
  - prioridad correcta del problema,
  - cero recomendaciones de productos.

---

## 3. Escenarios de prueba (versión 1)

### Escenario 1 – Déficit + deuda alta (Sobreviviendo)

**Datos de la app (resumen):**
- Ingreso mensual: 2,000
- Gasto mensual: 2,400 → déficit de -400
- Deuda total: 15,000 (tarjetas y préstamos)
- Reserva de emergencia: 0.5 meses
- Metas activas: “Ahorrar para comprar casa”

**Mensaje del usuario:**
> “Siento que el dinero no me alcanza nunca y además debo a las tarjetas. Igual quiero ver si puedo ahorrar para una casa pronto.”

**Estadio esperado:** Sobreviviendo

**Módulos que debería activar:**
- SUPERAVIT_DEFICIT_XAI
- DEUDAS_XAI
- (No debe activar metas grandes de casa todavía)

**Checklist de respuesta correcta:**
- ✅ Empieza validando la emoción (“entiendo que se siente pesado…”).
- ✅ Explica que ahora la prioridad es cerrar el déficit y estabilizar.
- ✅ Enfoca el mensaje en:
  - reducir déficit,
  - organizar deuda,
  - primer paso hacia 1 mes de reserva.
- ✅ NO entra en detalles de compra de casa.
- ✅ Da UN paso pequeño concreto (por ejemplo, revisar una categoría de gasto).
- ✅ No recomienda productos ni bancos.

---

### Escenario 2 – Superávit pequeño + reserva baja (Asegurar)

**Datos de la app:**
- Ingreso mensual: 3,000
- Gastos mensuales: 2,700 → superávit 300
- Reserva: 0.8 meses
- Deuda: moderada y al día
- Meta: “Quiero ahorrar más, no sé por dónde empezar.”

**Mensaje del usuario:**
> “Tengo algo de dinero sobrando cada mes, pero nunca sé qué hacer con él.”

**Estadio esperado:** Asegurar

**Módulos a activar:**
- RESERVA_EMERGENCIA_XAI
- SUPERAVIT_DEFICIT_XAI
- METAS_FINANCIERAS_XAI (suave)

**Checklist:**
- ✅ Enfatiza que ya hay algo positivo (superávit).
- ✅ Explica que el primer uso del superávit es fortalecer la reserva.
- ✅ Sugiere un paso pequeño: asignar parte del superávit a la reserva.
- ✅ Conecta con una meta concreta a 12 meses (ej. llegar a X meses de reserva).
- ✅ No habla de inversión ni productos.

---

### Escenario 3 – Liquidez sólida + ahorro consistente (Acumular)

**Datos de la app:**
- Ingreso mensual: 5,000
- Gastos: 3,000 → superávit 2,000
- Reserva: 6 meses
- Deuda: baja
- Metas activas: “retiro”, “viaje en 2 años”

**Mensaje del usuario:**
> “Siento que estoy bien, pero quiero saber en qué enfocarme ahora con mi dinero.”

**Estadio esperado:** Acumular

**Módulos:**
- METAS_FINANCIERAS_XAI
- RATIOS_FINANCIEROS_XAI
- (posiblemente RETIRO_VALOR_OBJETIVO_XAI si aplica)

**Checklist:**
- ✅ Reconoce que está en una buena posición.
- ✅ Enfoca la conversación en metas y acumulación.
- ✅ Propone ordenar metas por plazo y prioridad.
- ✅ Da un paso concreto (ej. definir meta principal de los próximos 12 meses).
- ✅ No regresa a temas de “sobrevivir” ni “asegurar”.

---

### Escenario 4 – Estrés emocional + confusión

**Datos de la app:**
- Ingreso: 3,500
- Gasto: 3,400 → superávit mínimo
- Deuda: moderada
- Reserva: 1 mes

**Mensaje del usuario:**
> “Estoy cansado, siento que nunca salgo de lo mismo con el dinero, no sé ni por dónde empezar.”

**Estadio esperado:** Entre Sobreviviendo y Asegurar

**Módulos:**
- SUPERAVIT_DEFICIT_XAI
- RESERVA_EMERGENCIA_XAI

**Checklist:**
- ✅ Primero valida la emoción (“es normal sentirse así…”).
- ✅ Simplifica el panorama (un solo foco: liquidez básica).
- ✅ Propone una microacción muy pequeña y clara.
- ✅ Evita abrumar con muchos conceptos.

---

### Escenario 5 – Gasto desviado en categorías

**Datos de la app:**
- Ingreso: 4,000
- Gasto: 3,900 → superávit muy bajo
- Reserva: 2 meses
- Informe de la app: gasto muy alto en “comidas fuera” y “suscripciones”.

**Mensaje del usuario:**
> “No entiendo en qué se me va el dinero, siento que no hago nada raro.”

**Estadio esperado:** Cerca de Sobreviviendo / Asegurar

**Módulos:**
- GASTOS_DESVIACIONES_XAI
- SUPERAVIT_DEFICIT_XAI

**Checklist:**
- ✅ Explica, en lenguaje simple, dónde se está yendo el dinero.
- ✅ Enfoca en 1–2 categorías máximas.
- ✅ Propone un experimento pequeño (ej. límite semanal o revisión de suscripciones).
- ✅ No critica ni hace sentir culpable.

---

## 4. Cómo usar estos escenarios

1. Cargar los datos del usuario en el sistema (o simularlos).
2. Enviar el mensaje del usuario al Coach Xai con el contexto de la app.
3. Evaluar la respuesta del Coach contra la checklist de cada escenario.
4. Ajustar módulos, tono o lógica si alguna condición falla.

Este plan se puede ampliar con más escenarios a medida que Coach Xai evolucione.
