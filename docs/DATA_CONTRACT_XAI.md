📁 DATA_CONTRACT_XAI.md
Contrato de Datos entre la App Cada Menudo y el Coach Xai

Moneta Fintech LLC – Versión 1.0

1. OBJETIVO

Este documento define qué datos recibe el Coach Xai, en qué formato, y qué devuelve.
Es el puente entre:

la app móvil/web

el modelo de lenguaje

El objetivo es asegurar que Xai siempre reciba datos limpios, coherentes y estructurados, y responda con mensajes consistentes y utilizables por la app.

2. PRINCIPIOS DEL DATA CONTRACT

La app controla la data.
Xai NO accede por sí mismo a bases de datos ni APIs.

El modelo nunca almacena información sensible.
Solo procesa lo que la app le envía en cada llamada.

Formato estándar JSON para TODAS las llamadas.

Todos los mensajes del usuario y datos actualizados viajan juntos en una misma llamada.

Xai responde con estructura fija, para que la app pueda renderizar sin errores.

3. INPUT: LO QUE LA APP LE ENVÍA AL COACH

La app enviará SIEMPRE un objeto JSON con esta estructura:

{
  "usuario": {
    "nombre": "string | null",
    "pais": "string | null",
    "moneda": "string (USD, MXN, etc)",
    "idioma": "es" 
  },
  "finanzas": {
    "ingreso_mensual": 0,
    "gasto_mensual": 0,
    "superavit_mensual": 0,
    "porcentaje_superavit": 0,
    "top_desviaciones": [
      {
        "categoria": "string",
        "desviacion_mensual": 0,
        "porcentaje": 0
      }
    ],
    "gastos_por_categoria": [
      { "categoria": "Vivienda", "monto": 0 },
      { "categoria": "Alimentación", "monto": 0 },
      { "categoria": "Transporte", "monto": 0 },
      { "categoria": "Deudas", "monto": 0 },
      { "categoria": "Otros", "monto": 0 }
    ],
    "estado_financiero": "sobreviviendo | asegurando | acumulando"
  },
  "metas": [
    {
      "id": "string",
      "nombre": "string",
      "monto_meta": 0,
      "monto_actual": 0,
      "fecha_meta": "YYYY-MM-DD",
      "categoria": "Ahorro | Deuda | Patrimonio",
      "progreso": 0
    }
  ],
  "mensaje_usuario": "texto completo del usuario"
}

4. CAMPOS MÍNIMOS REQUERIDOS

Para asegurar funcionamiento:

Obligatorios:

ingreso_mensual

gasto_mensual

superavit_mensual

mensaje_usuario

Opcionales pero recomendados:

top_desviaciones

gastos_por_categoria

metas

Siempre válido que vengan vacíos (Xai debe saber manejarlo):

nombre

pais

metas: []

gastos_por_categoria: []

5. DETECCIÓN DE INTENCIÓN (INTENT)

A partir de mensaje_usuario, el modelo debe identificar uno de estos intents estándar:

RESERVA_EMERGENCIA
METAS
GASTOS
DESEQUILIBRIO (déficit / superávit)
DEUDAS
ESTADO_FINANCIERO
ORIENTACION_GENERAL
CLARIFICACION


Esto determina qué módulo interno usa Xai.

6. OUTPUT: LO QUE EL COACH DEVUELVE A LA APP

La respuesta SIEMPRE tiene estructura JSON fija, seguida del campo mensaje_usuario listo para mostrar en chat.

{
  "intencion_detectada": "string",
  "estado_financiero": "sobreviviendo | asegurando | acumulando | null",
  "mensaje_coach": "string (respuesta final lista para mostrar)",
  "puntos_clave": [
    "string",
    "string"
  ],
  "acciones_sugeridas": [
    "string",
    "string"
  ]
}

7. REGLAS PARA EL MENSAJE DEL COACH

El texto que genere:

7.1 Debe cumplir:

tono Xavier Serbia

lenguaje claro, simple

frases cortas

guías conductuales paso a paso

límites del coach (no recomendar productos)

7.2 Nunca debe incluir:

montos específicos obligatorios

instrucciones absolutas (“tienes que…”)

opiniones médicas, legales o fiscales

juicios o regaños

información que no vino en el input

8. CÓMO LLAMA LA APP AL COACH (EJEMPLO)
{
  "usuario": {
    "nombre": "Ana",
    "moneda": "USD",
    "idioma": "es"
  },
  "finanzas": {
    "ingreso_mensual": 3800,
    "gasto_mensual": 4200,
    "superavit_mensual": -400,
    "porcentaje_superavit": -10.5,
    "top_desviaciones": [
      {
        "categoria": "Comidas fuera",
        "desviacion_mensual": 180,
        "porcentaje": 32
      }
    ],
    "estado_financiero": "sobreviviendo"
  },
  "metas": [
    {
      "id": "1",
      "nombre": "Fondo de mudanza",
      "monto_meta": 3000,
      "monto_actual": 200,
      "fecha_meta": "2025-07-01",
      "categoria": "Ahorro",
      "progreso": 7
    }
  ],
  "mensaje_usuario": "Por qué no me da el dinero este mes?"
}

9. RESPUESTA ESPERADA DEL COACH (EJEMPLO)
{
  "intencion_detectada": "DESEQUILIBRIO",
  "estado_financiero": "sobreviviendo",
  "mensaje_coach": "OK, vamos por partes. Este mes tu ingreso bajó respecto a tus gastos y eso te dejó con un déficit de $400. La desviación más grande viene de comidas fuera. Nada está perdido — esto solo nos dice por dónde empezar a ajustar.",
  "puntos_clave": [
    "Déficit mensual: -$400",
    "Principal desviación: comidas fuera (+32%)"
  ],
  "acciones_sugeridas": [
    "Revisar si esta desviación es puntual o repetida",
    "Definir un monto máximo semanal para esta categoría"
  ]
}

10. ERRORES CONTROLADOS (FALLBACKS)

Si falta un dato crítico:

OK, necesito un dato más para ayudarte bien.  
¿Cuál es tu ingreso mensual aproximado?


Si el mensaje es ambiguo:

Déjame entenderte mejor.  
¿Estás hablando de tus gastos, una meta o tu reserva?


Si pide algo fuera del alcance del coach:

Esa parte no puedo decidirla yo, pero sí puedo ayudarte 
a entender los factores que normalmente se consideran.

FIN DEL DOCUMENTO
