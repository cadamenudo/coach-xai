📘 Coach Xai – Budget AI Engine
Sistema de conocimiento y lógica del Coach Financiero de Cada Menudo

Moneta Fintech LLC

🧠 ¿Qué es Coach Xai?

Coach Xai es el motor de razonamiento, conocimiento y comportamiento que impulsa al coach financiero dentro de la app Cada Menudo.
Su propósito es ofrecer orientación clara, humana y educativa sobre:

manejo del presupuesto

hábitos de gasto

reserva de emergencia

metas financieras

superávit / déficit

deudas

estado financiero general

Todo basado en datos reales del usuario, lógica de coaching definida y reglas internas estrictas.

Coach Xai no recomienda productos financieros, no proyecta inversiones ni sustituye asesoría profesional.
Es un sistema educativo y de acompañamiento conductual.

🏗️ Arquitectura del Repositorio

La estructura completa del proyecto:

coach-xai/
├─ README.md
├─ .gitignore
│
├─ docs/
│  ├─ INDEX.md
│  ├─ COACH_XAI_MASTER_DOCUMENT.md
│  ├─ INTERFACE_LAYER_XAI.md
│  ├─ DATA_CONTRACT_XAI.md
│  ├─ FLOWS_XAI.md
│  ├─ MEMORY_LAYER_XAI.md
│  ├─ OPERATIONS_LAYER_XAI.md
│  ├─ EVALUATION_SUITE_XAI.md
│  └─ ARCHITECTURE_OVERVIEW.md
│
├─ core/
│  ├─ CORE_PROMPT_XAI.md
│  ├─ LOGIC_LAYER_XAI.md
│  └─ STAGES_MODEL_XAI.md
│
├─ modules/
│  ├─ RESERVA_EMERGENCIA_XAI.md
│  ├─ METAS_FINANCIERAS_XAI.md
│  ├─ GASTOS_DESVIACIONES_XAI.md
│  ├─ SUPERAVIT_DEFICIT_XAI.md
│  ├─ DEUDAS_XAI.md
│  └─ ESTADO_FINANCIERO_XAI.md
│
├─ support-docs/
│  ├─ GLOSARIO_FINANCIERO_XAI.md
│  ├─ BENCHMARKS_EDUCATIVOS_XAI.md
│  ├─ GUIA_TONO_ESTILO_XAI.md
│  └─ PREGUNTAS_FRECUENTES_XAI.md
│
├─ backend/
│  ├─ xai_dev.py
│  ├─ config.example.json
│  └─ README_BACKEND.md
│
├─ tests/
│  ├─ TEST_PLAN_XAI.md
│  ├─ cases/
│  │  ├─ case_sobreviviendo.json
│  │  ├─ case_asegurando.json
│  │  ├─ case_acumulando.json
│  │  ├─ case_deuda_alta.json
│  │  └─ case_reserva_baja.json
│  └─ scripts/
│     └─ run_manual_tests.md
│
└─ .github/
   └─ workflows/
      └─ test-xai.yml

🎯 Objetivo del Proyecto

El propósito de este repositorio es definir:

La lógica interna del coach

El conocimiento que puede usar

Los límites operacionales

Los cálculos autorizados

El tono y estilo de comunicación

El comportamiento educativo y conductual

La interacción con la app Cada Menudo

Los escenarios y pruebas que aseguran consistencia

Esta base es la “mente” del coach, totalmente independiente del UI y del backend de producción.

🧩 Componentes Principales
### 1. Core

Define la identidad del coach:

quién es

cómo habla

qué puede hacer

cómo piensa

etapas financieras del usuario

2. Modules

Cada módulo es un “sub-cerebro” especializado: reservas, metas, desviaciones de gastos, deudas, etc.

3. Docs

Toda la arquitectura conceptual, flujos, contratos de datos, memoria y evaluación del sistema.

4. Support-Docs

Glosarios, benchmarks educativos, tono de voz y FAQ.

5. Backend

Scripts para pruebas locales, prototipos y validaciones.

6. Tests

Casos, scripts y lineamientos para garantizar resultados consistentes.

🚦 Regla Central del Sistema

Xai sí puede hacer cálculos simples internos
(sumas, porcentajes, ratios, brechas, comparaciones, meses, etc.)
siempre y cuando:

✔ Los datos provienen de la app Cada Menudo
✔ La fórmula está documentada en el Knowledge Base
✔ No impliquen recomendaciones de productos, inversiones o asesoría profesional

💬 Tono del Coach

Humano

Empático

Claro

Directo sin juzgar

Estilo Xavier Serbia (“mi gente”, “vamos paso a paso”) sin exagerar

Siempre educativo y práctico

La guía completa está en:
support-docs/GUIA_TONO_ESTILO_XAI.md

🚀 Roadmap

Integración con backend-producto

Pruebas automatizadas sobre casos reales

Expansión a módulos avanzados (hábitos, coaching conductual)

Versión bilingüe (ES / EN)

Evaluación continua con métricas de calidad

📄 Licencia

© 2025 Moneta Fintech LLC — Todos los derechos reservados.
Este repositorio contiene propiedad intelectual interna.
No público. No redistribuir.