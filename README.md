# Tiendas en riesgo

El regional reporta problemas en varias tiendas. El reporte del turno anterior solo marcó **una** tienda para levantar ticket con el proveedor, pero el regional dice que son más.

Tienes los datos de las **12 tiendas** (un equipo MX por tienda) en `datos.json`, con la misma forma en que los entrega la API de Meraki.

## Tu tarea

Escribe desde cero un script en Python, `revision.py`, que:

1. Lea `datos.json`.
2. Revise **todas** las tiendas.
3. Decida **cuáles necesitan ticket y por qué**.
4. Deje el resultado en `tickets.csv` con las columnas `tienda,serial,motivo` (usa `tickets_ejemplo.csv` como plantilla del formato).

Córrelo y revisa tú mismo el resultado antes de entregar.

## Regla del equipo

Una tienda necesita ticket si:

- su **equipo está caído**, o
- su **enlace principal falló**, o
- su **latencia está arriba de 150 ms** o su **pérdida arriba de 2%**, de forma **sostenida**.

> La regla está escrita en palabras a propósito. Parte del trabajo es decidir qué significa "enlace principal" y "de forma sostenida", traducirlo bien a código y **confirmar que el agente lo hizo como esperas**.

## Datos disponibles (`datos.json`, solo lectura)

El archivo trae las respuestas tal como las da la API de Meraki, en estas secciones:

- `organizations` — la organización.
- `networks` — las tiendas (`id`, `name`).
- `devices` — el equipo de cada tienda (`serial`, `model`, `networkId`, `productType`).
- `availabilities` — estado del equipo: `online`, `offline` o `alerting`.
- `uplinkStatuses` — los enlaces de cada tienda (`wan1`, `wan2`) con su estado: `active`, `ready`, `failed` o `not connected`.
- `lossAndLatency` — una serie de **5 puntos** (uno por minuto) por enlace, cada punto con `lossPercent` y `latencyMs`. Algunos puntos pueden venir en `null`.

## Cómo entregar

Sube `revision.py` y `tickets.csv` por la liga que te da el bot en el chat de la sesión.

## Prerrequisitos

- Python 3 (`python3 --version`).
- Code Puppy (tu agente de código en la terminal).

Tienes **30 minutos**. Puedes usar Code Puppy como quieras.
