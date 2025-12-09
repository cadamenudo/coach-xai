📁 COACH_XAI_MASTER_DOCUMENT.md
Documento Maestro del Coach Xai

Cada Menudo / Moneta Fintech LLC
Versión 1.0

1. PROPÓSITO DEL DOCUMENTO

Este documento reúne toda la arquitectura conceptual, técnica y operativa del Coach Xai.
Es la referencia central para:

desarrollo

UX

IA conversacional

QA

integraciones

mantenimiento

versionamiento

El objetivo es que cualquier miembro del equipo pueda entender cómo funciona el Coach Xai de principio a fin.

2. MISIÓN DEL COACH XAI

El Coach Xai tiene una misión clara:

“Ayudar al usuario a entender cómo se mueve su dinero y avanzar hacia sus metas mediante pasos pequeños, claros y consistentes”.

No toma decisiones por el usuario.
No recomienda productos financieros.
No juzga.
No regaña.
Solo educa, acompaña y da claridad.

3. TONO Y ESTILO

El tono del Coach Xai debe ser:

claro

sencillo

empático

directo

educativo

basado en hábitos pequeños

estilo Xavier Serbia, sin exageraciones

Nunca usa:

juicios

lenguaje imperativo duro

recomendaciones de productos

promesas irreales

La experiencia debe sentirse humana, profesional y accesible.

4. COMPONENTES DEL SISTEMA

El Coach Xai está formado por siete capas principales:

Core Prompt

Logic Layer (orquestador de intenciones y reglas internas)

Modules Layer (módulos financieros)

Support Documents (referencias educativas y operativas)

Interface Layer

Memory Layer

Operations Layer

Este documento describe cómo se integran.

5. CORE PROMPT (Identidad del Coach)

El Core Prompt define:

quién es el Coach

cómo debe hablar

cuáles son sus límites

qué es lo más importante para el usuario

cómo se manejan las intenciones

Incluye:

Misión

Tono

Guardrails

Estilo educativo

Palabras prohibidas

Palabras recomendadas

Manejo de incertidumbre

6. LOGIC LAYER (Orquestador Principal)

La Logic Layer determina cómo el Coach decide qué módulo usar en cada momento.

Incluye:

6.1. Intenciones admitidas

METAS

RESERVA

GASTOS

DESVIACION

DESEQUILIBRIO

DEUDAS

ESTADO_FINANCIERO

ORIENTACION_GENERAL

ACLARACION

6.2. Reglas de selección

El Coach analiza:

texto del usuario

datos financieros enviados por la app

historial no sensible (de la Memory Layer)

Luego activa el módulo adecuado.

7. MODULES LAYER (Módulos Financieros)

Cada módulo interpreta datos y produce una respuesta clara.

7.1. Módulos actuales:

Reserva de Emergencia

Metas Financieras

Gastos y Desviaciones

Superávit / Déficit

Deudas

Estado Financiero (Stages)

Cada módulo tiene su propio documento .md con:

objetivo

inputs

lógica

interpretación

frases base

acciones sugeridas

límites específicos

8. SUPPORT DOCUMENTS

Referencia operativa para el Coach Xai:

glosario financiero

rangos educativos

benchmarks conductuales

explicaciones simples por tema

parámetros educativos (6–36 meses reserva, etc.)

guía de interpretación

Estos documentos alimentan respuestas coherentes.

9. INTERFACE LAYER (Interacción con el Usuario)

Define:

plantillas de respuesta

estructura de mensajes

tono

cómo iniciar flujos

cómo cerrar conversaciones

Incluye:

formato JSON obligatorio

estructura del mensaje final

manejo de aclaraciones

mensajes cortos vs largos

10. MEMORY LAYER (Memoria Controlada)

La app controla qué recuerda Xai, nunca el modelo.

Puede recordar:

stage financiero

metas activas

desviaciones frecuentes

historial mensual resumido

hitos logrados

preferencias del usuario

última intención detectada

Nunca recuerda:

datos personales

números de cuenta

textos emocionales profundos

direcciones

información sensible de ninguna clase

La memoria es siempre estructurada.

11. OPERATIONS LAYER (Ejecución en Producción)

Define:

control de errores

límites de longitud

fallback messages

seguridad

logging permitido

rendimiento

versionamiento

modos operativos (estándar, baja información, meta activa, educativo)

La app y el backend garantizan que:

no se registren datos sensibles

el modelo no desborde límites

la respuesta siempre incluya JSON estructurado

12. DATA CONTRACT (Contrato de Datos)

Define:

Qué recibe el Coach:

ingreso

gastos

superávit/déficit

desviaciones

metas

estado financiero

preferencias

mensaje del usuario

Qué devuelve:
{
  "intencion_detectada": "",
  "estado_financiero": "",
  "mensaje_coach": "",
  "puntos_clave": [],
  "acciones_sugeridas": []
}


Formato consistente → la app siempre sabe cómo renderizar.

13. FLOWS (Flujos Conversacionales)

Guían al Coach en:

bienvenida

diagnóstico

metas

déficit

superávit

gastos

reserva

deudas

etapas

celebraciones

falta de datos

aclaración

Cada flujo especifica:

disparadores

estructura

puntos clave

acciones conductuales

14. EVALUATION SUITE (Sistema de Pruebas)

Incluye:

casos simulados

stress tests

pruebas de guardrails

pruebas de intención

pruebas de variación de datos

continuidad conversacional

observabilidad

Su objetivo: evitar errores antes del lanzamiento.

15. CICLO DE VIDA DEL COACH XAI

Input de la app

Evaluación de intención

Activación del módulo correspondiente

Consulta a documentos de soporte

Construcción de respuesta con Interface Layer

Aplicación de guardrails y tono

Devolución del JSON estructurado

App procesa y actualiza memoria

16. VERSIONAMIENTO

Toda actualización requiere:

número de versión

fecha

módulos afectados

motivo del cambio

evidencia de pruebas

validación de guardrails

17. FUTURAS EXPANSIONES

Módulo de hábitos

Módulo educativo de ahorro

Módulo de proyección mensual

Integración con insights automáticos

Ajustes personalizados según etapa
