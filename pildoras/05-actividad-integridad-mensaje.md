
---

## Objetivo
Comprender el concepto de **integridad de la información** mediante el uso de **hashes**.  
Se deberá comprobar que **si un mensaje cambia, su hash cambia**, aunque la modificación sea mínima.

---

## Contexto
Debes crear una **pequeña aplicación web en HTML y JavaScript** que permita comprobar si un mensaje ha sido modificado.

La aplicación deberá:
- Permitir introducir **dos mensajes de texto**.
- Calcular el **hash SHA-256** de cada mensaje.
- Comparar ambos hashes para decidir si el mensaje ha sido modificado.

## Parte A – Estructura del archivo HTML

Crea un archivo HTML que contenga:

- Estructura HTML básica (`<!doctype html>`, `<html>`, `<head>`, `<body>`).
- Un título visible en la página.
- Dos cajas de texto (`textarea`):
  - **Mensaje 1 (original)**.
  - **Mensaje 2 (posible modificado)**.
- Un botón para calcular el hash del Mensaje 1.
- Un botón para calcular el hash del Mensaje 2.
- Un botón para **comparar** ambos hashes.
- Un área donde se muestre:
  - Hash del Mensaje 1.
  - Hash del Mensaje 2.
  - Resultado de la comparación.

---

## Parte B – Cálculo del hash SHA-256

Implementa en **JavaScript** una función que:

1. Reciba un texto como parámetro.
2. Calcule su **hash SHA-256** utilizando la API `crypto.subtle`.
3. Devuelva el hash en formato **hexadecimal**.

---

## Parte C – Lógica de la aplicación

### 1. Calcular hash del Mensaje 1
- Leer el contenido del primer `textarea`.
- Calcular su hash.
- Mostrar el resultado en la página.

### 2. Calcular hash del Mensaje 2
- Leer el contenido del segundo `textarea`.
- Calcular su hash.
- Mostrar el resultado en la página.

### 3. Comparar mensajes
- Comparar los hashes obtenidos.
- Si los hashes son iguales → **el mensaje NO se ha modificado**.
- Si los hashes son distintos → **el mensaje SÍ se ha modificado**.
- Mostrar el resultado de forma clara al usuario.

---

## Parte D – Pruebas obligatorias

Realiza, como mínimo, las siguientes pruebas:

1. Mensaje 1 y Mensaje 2 exactamente iguales.
2. Cambiar una sola letra en el Mensaje 2.
3. Añadir un espacio al final del Mensaje 2.
4. Añadir un emoji o símbolo especial al Mensaje 2.

Observa cómo cambia el hash en cada caso.

---

## Parte E – Preguntas a responder

Responde brevemente en el documento de entrega:

1. ¿Por qué el hash cambia completamente aunque el mensaje cambie muy poco?
2. ¿Sirve el hash para ocultar el mensaje? Explica por qué.
3. ¿En qué situaciones reales es útil comprobar la integridad de un mensaje?
4. ¿Qué información deberías guardar para comprobar la integridad de un mensaje en el futuro?

---

## Parte F – Entrega

Se derá entregar:

- El archivo `05_integridad_hash_sha256.html`.
- Capturas de pantalla donde se vea:
  - Mensaje 1 y su hash.
  - Mensaje 2 modificado y su hash.
  - Resultado de la comparación.
- Un documento con las respuestas a las preguntas y una breve conclusión.

---


