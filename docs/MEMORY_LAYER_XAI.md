📁 MEMORY_LAYER_XAI.md
Capa de Memoria – Coach Xai (Cada Menudo / Moneta Fintech LLC)

Versión 1.0

1. OBJETIVO

La Memory Layer define qué puede recordar el Coach Xai entre interacciones y qué nunca debe recordar.
No es memoria del modelo en sí, sino memoria gestionada por la app, completamente bajo control del backend.

Su propósito es:

Mantener continuidad útil en conversaciones.

Facilitar seguimiento de metas y hábitos.

Recordar señales relevantes sin almacenar datos sensibles.

Cumplir con prácticas de privacidad y protección del usuario.

2. PRINCIPIOS CLAVE

La app es quien guarda y administra la memoria.
El modelo nunca almacena información por sí mismo.

Solo se guarda información no sensible y útil para guiar al usuario.

Toda memoria debe ser opcional, actualizable y borrable.

El modelo solo recibe lo que la app decide enviarle en cada llamada.

La memoria tiene estructura: nada se almacena en texto libre.

3. LO QUE XAI PUEDE RECORDAR (A TRAVÉS DE LA APP)

La app puede almacenar estos elementos para enviarlos en cada llamada:

3.1. Estado Financiero (Stage)

sobreviviendo

asegurando

acumulando

Sirve para continuidad en flujos.

3.2. Metas activas del usuario

Por cada meta:

nombre

monto objetivo

monto acumulado

fecha objetivo

progreso (%)

categoría

Esto permite que Xai dé seguimiento natural:

“Veo que tu meta de viaje avanza al 40%. Buen ritmo.”

3.3. Historial resumido de superávit / déficit

Ejemplo:

mes_actual: -180
mes_anterior: +20
mes_2: -75


Usado para frases tipo:

“En los últimos 3 meses tu presupuesto ha variado bastante.”

3.4. Desviaciones frecuentes

La app puede guardar las 3 categorías con más variaciones:

[
  { categoria: "Comidas fuera", repeticiones: 4 },
  { categoria: "Transporte", repeticiones: 2 }
]


No son datos sensibles y ayudan al Coach a entender patrones.

3.5. Hitos logrados

pago completo de una deuda

completar una meta

alcanzar un superávit notable

mejorar una categoría de gasto

Se usa para reconocimiento positivo.

3.6. Preferencias del usuario

Ejemplos:

idioma

moneda

tono corto/largo de respuestas

si prefiere pasos semanales o mensuales

No se almacena nada personal.

3.7. Última intención detectada

Sirve para continuar conversaciones sin perder el hilo:

"ultima_intencion": "METAS"

4. LO QUE XAI NO DEBE RECORDAR NUNCA

Esto es crítico para seguridad, privacidad y cumplimiento.

La memoria jamás debe incluir:

4.1. Datos personales

nombre legal

dirección

email

teléfono

foto

nombres de dependientes

ubicación exacta

contactos o relaciones

4.2. Datos financieros sensibles

números de cuenta

saldos bancarios exactos

historial completo de transacciones

fotos de recibos

números de tarjeta

login o credenciales financieras

4.3. Información emocional profunda o sensible

Salud mental

Diagnósticos

Situaciones legales

Problemas familiares

4.4. Opiniones políticas, religiosas o ideológicas

Nunca deben almacenarse ni usarse para personalizar el Coach.

5. ESTRUCTURA QUE LA APP USA PARA GUARDAR MEMORIA

La app puede mantener un objeto como este:

{
  "stage": "asegurando",
  "metas": [...],
  "historial_superavit_deficit": [...],
  "desviaciones_frecuentes": [...],
  "hitos": [...],
  "preferencias": {
    "idioma": "es",
    "respuesta_corta": false
  },
  "ultima_intencion": "METAS"
}


Esto se envía junto con los datos mensuales.

6. CÓMO XAI INTERPRETA LA MEMORIA

El modelo no “recuerda”.
La app le manda un resumen en cada consulta.

Ejemplo:

Si ultima_intencion = METAS, Xai puede continuar ese diálogo.

Si hay “hitos”, Xai puede resaltarlos.

Si detecta repeticiones de déficit, puede hacer un comentario educativo.

Pero nunca almacena nada por su cuenta.

7. FEEDBACK LOOP

La app debe decidir:

qué eventos se agregan a memoria

cuándo eliminar memoria (ej: reset del usuario)

cuándo actualizarla (al cerrar un mes, por ejemplo)

Xai solo accede a lo que la app envía en el JSON de entrada.

8. CICLO DE VIDA DE LA MEMORIA

Crear memoria: instalación o primer uso

Actualizar: cada mes o evento

Limpiar: cuando el usuario lo solicita

Destruir: al desinstalar o borrar datos desde la app

FIN DEL DOCUMENTO
