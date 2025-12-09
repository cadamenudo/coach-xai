📁 ARCHITECTURE_OVERVIEW_XAI.md
Overview de Arquitectura – Coach Xai

Cada Menudo / Moneta Fintech LLC
Versión 1.0

1. OBJETIVO DEL DOCUMENTO

Este archivo ofrece una vista general de alto nivel del Coach Xai:

cómo está organizado

cómo fluye la información

cómo interactúan las capas

cómo se estructuran los módulos

cómo se integra con la app Cada Menudo

Es el documento que sirve de mapa para cualquier persona que revise o mantenga el sistema.

2. COMPONENTES PRINCIPALES DE LA ARQUITECTURA

El Coach Xai está compuesto por 7 capas, cada una con responsabilidades claras.

1. Core Prompt

Define la identidad del Coach:

misión

tono

estilo

límites

reglas de comunicación

visión educativa

Todo comportamiento parte desde el core.

2. Logic Layer (Orquestador de Intenciones)

Es el cerebro lógico del sistema.

Funciones:

detectar intención

seleccionar módulo

interpretar contexto

decidir el flujo adecuado

activar fallback si falta información

Intenciones principales:

METAS

RESERVA

GASTOS

DESVIACIÓN

SUPERÁVIT / DÉFICIT

DEUDAS

ESTADO FINANCIERO

ACLARACIÓN

3. Modules Layer (Módulos Financieros)

Cada módulo resuelve un tema financiero específico:

Reserva de emergencia

Metas financieras

Gastos y desviaciones

Superávit / déficit

Deudas

Estado financiero (stages)

Cada módulo incluye:

objetivo

lógica interna

interpretación

acciones conductuales

límites y advertencias

4. Support Documents

Conocimiento que el Coach usa para educar:

glosario financiero

benchmarks educativos

guía de tono y estilo

preguntas frecuentes

conceptos explicados de forma simple

No son reglas, sino referencias educativas.

5. Interface Layer

Define cómo el Coach se comunica:

estructura del mensaje

plantillas de respuesta

formato JSON

aperturas y cierres

tono conversacional

gestión de aclaraciones

mensajes cortos o largos

La Interface Layer produce la respuesta final para la app.

6. Memory Layer

Memoria controlada por la app (no por el modelo).

Debe almacenar solo:

etapa financiera

metas activas

desviaciones frecuentes

historial mensual resumido

hitos logrados

preferencias del usuario

última intención

Nunca almacena datos personales ni sensibles.

7. Operations Layer

Controla la ejecución en producción:

manejo de errores

seguridad

guardrails

rendimiento

observabilidad (logs sin datos sensibles)

límites de longitud

versionamiento

modos operativos

Es fundamental para evitar fallas o respuestas incorrectas.

3. FLUJO COMPLETO DE UNA INTERACCIÓN

La app envía JSON con datos financieros + mensaje del usuario.

Logic Layer detecta intención.

Selecciona el módulo correspondiente.

El módulo interpreta la data.

La Interface Layer construye la respuesta final.

La Operations Layer valida seguridad, longitud y formato.

Se genera un JSON estructurado.

La app lo muestra y actualiza memoria.

4. RELACIÓN DE ARCHIVOS
Carpeta	Propósito
/core	Identidad del Coach, lógica central, reglas base.
/modules	Módulos financieros independientes.
/support-docs	Conocimiento educativo y referencias.
/docs	Documentación, arquitectura, procesos y overview.
/backend	Scripts de prueba e integración con la API.
/tests	Pruebas, casos simulados y validación automática.
5. PRINCIPIOS DE DISEÑO

Modularidad
Cada módulo funciona de forma independiente.

Interpretación, no cálculo
Xai interpreta datos, no hace matemáticas complejas.

Pasos pequeños
Toda acción sugerida es realista y sostenible.

Privacidad máxima
No guarda información sensible; la app controla todo.

Consistencia
El tono, estructura y formato son siempre iguales.

Explicación clara
Siempre explica el “por qué”, no solo el “qué”.

6. FUTURAS EXTENSIONES (ROADMAP)

módulo de hábitos financieros

módulo educativo interactivo

sección de insights automáticos

personalización según etapa del usuario

capa de evaluación mensual automatizada

integración con analítica basada en patrones

FIN DEL DOCUMENTO
