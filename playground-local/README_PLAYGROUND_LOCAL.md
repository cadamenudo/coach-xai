# Playground Local – Coach Xai

Este folder contiene prototipos de interfaz para probar el comportamiento de Coach Xai **en local**, sin exponer el repositorio ni conectar a APIs externas.

## Estructura

- `ui/coach-xai-playground.html`  
  Chat de prueba con un mock de Coach Xai que:
  - detecta emociones,
  - distingue entre gastos, deudas, ahorro, ingresos y metas,
  - simula los estadios “sobreviviendo / asegurar / acumular”.

- `scenarios/SCENARIOS_XAI.md`  
  Banco de escenarios de conversación para probar tono y lógica.

- `notes/NOTES.md`  
  Bitácora de ajustes, observaciones y pendientes del Coach.

## Cómo usar el playground

1. Abrir `ui/coach-xai-playground.html` con doble clic (se abre en el navegador).
2. Escribir como si fueras el usuario:
   - ejemplos de deuda, gastos, ahorro, metas, emociones.
3. Usar `SCENARIOS_XAI.md` como guía:
   - copiar un escenario,
   - pegarlo en el chat,
   - observar la respuesta del mock.
4. Registrar ajustes o ideas en `notes/NOTES.md`.

> Nota: Este playground es **solo para diseño de tono y lógica**.  
> No hace cálculos con datos reales ni se conecta todavía al KB ni a modelos externos.
