🗒️ NOTES – Coach Xai Playground
Registro de decisiones, pruebas, bugs y pendientes

(Uso interno – Moneta Fintech LLC)

📌 Propósito del archivo

Este archivo sirve como bitácora rápida para documentar:

Ajustes que hacemos al tono, lógica y respuestas del mock.

Cosas que probamos en el playground HTML.

Bugs encontrados.

Ideas futuras para el Coach.

Cosas que deben trasladarse luego al KB oficial, módulos, o logic layer.

El objetivo es no perder nada mientras iteramos rápido.

📚 1. Log de pruebas recientes
[FECHA] – Interacción básica

Input del usuario:

“Hola”

Respuesta del mock:
(pegar aquí la respuesta)

Observación:

✔️ Saludo adecuado

❌ Evitar repetir frases largas

🔧 Ajustar apertura más cálida y menos repetitiva

[FECHA] – Caso: gastos + deuda + poco ahorro

Input del usuario:

“gastos, mucha deuda y poco ahorro”

Respuesta del mock:
(pegar respuesta aquí)

Observación:

✔️ Detecta combinación triple

✔️ Tono calmado

🔧 Podría hacer pregunta final más concreta

[FECHA] – Caso: emoción detectada

Input del usuario:

“estoy estresado por mis cuentas”

Respuesta:
(pegar respuesta)

Observación:

✔️ Buena validación emocional

🔧 Ajustar frase “gracias por compartir” → hacerlo más natural

🧠 2. Ajustes de tono pendientes

Evitar expresiones repetitivas como “vamos paso a paso” (máx 1 vez cada 3 respuestas).

Quitar completamente “mi gente”.

Usar más variedad en: “Gracias por compartirlo”, “Aprecio que lo digas”, etc.

Reducir densidad de párrafos → respuestas más cortas y directas.

⚙️ 3. Ajustes lógicos pendientes

Afinar detección de combinaciones (gasto + deuda + meta).

Añadir detección de metas tipo: “quiero ahorrar para X”.

Añadir detección de ingreso inestable (“trabajo cambia”, “comisiones”, “ingreso irregular”).

Preparar capa de escenarios según estadio (borrador en Logic Layer).

🐞 4. Bugs detectados
1. Reacción desajustada en frases no financieras

Ejemplo:
“Estoy cansado hoy” → activa modo financiero cuando debería pedir claridad.

Solución pendiente:
Añadir una rama inicial: “¿Esto tiene que ver con tu dinero o es otra cosa?”

2. Caso: “no sé qué hacer”

El mock devuelve genérico → mejorar con orientación más cálida.

💡 5. Ideas futuras para el playground

Botón “generar respuesta aleatoria con mismo input”.

Modo “comparar tono” entre Xai y un asistente genérico.

Simular estadios: toggle entre Sobreviviendo, Asegurar, Acumular.

Usar JSON de input para simular datos reales de usuario.

Exportar conversaciones de prueba como .MD.

📦 6. Cosas que deben integrarse al repositorio principal

Cualquier ajuste de tono → support-docs/GUIA_TONO_ESTILO_XAI.md

Nuevas ramas lógicas → core/LOGIC_LAYER_XAI.md

Nuevas detecciones o reglas → Módulos específicos.

Mejoras en estrategia de interacción → docs/INTERFACE_LAYER_XAI.md

✔️ 7. To-Do List rápida

 Afinar las respuestas cuando el usuario menciona “todo”, “todo mal”.

 Crear módulo “Ingresos inestables”.

 Añadir ejemplos en KB sobre “microacciones semanales”.

 Añadir más variedad en cierres de mensaje.

🏁 Final

Este archivo se actualizará continuamente mientras iteramos el Coach Xai.
Sirve como puente entre la experimentación del playground y la arquitectura real del sistema.
