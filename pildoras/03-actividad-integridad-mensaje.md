
## Práctica – Integridad de mensajes con HASH (SHA-256)

### Objetivo
Comprobar que un **hash permite detectar cambios** en un mensaje.

> Si el mensaje cambia, el hash cambia.

---

## Qué tienes que hacer
Crear una **pequeña página web en HTML y JavaScript** que permita comprobar si un mensaje ha sido modificado.

La página debe:
- Tener **dos cajas de texto** (mensaje original y mensaje modificado).
- Calcular el **hash SHA-256** de cada mensaje.
- Comparar ambos hashes.
- Indicar claramente si el mensaje **ha sido modificado o no**.

---

## Requisitos mínimos

El archivo HTML debe incluir:
- Estructura HTML básica.
- Dos `textarea`.
- Botón para calcular el hash del Mensaje 1.
- Botón para calcular el hash del Mensaje 2.
- Botón para comparar hashes.
- Zona donde se muestren:
  - Hash del Mensaje 1.
  - Hash del Mensaje 2.
  - Resultado de la comparación.

---

## Funcionamiento esperado
- Si los hashes son iguales → **el mensaje NO se ha modificado**.
- Si los hashes son distintos → **el mensaje SÍ se ha modificado**.

---

## Pruebas obligatorias
Debes comprobar al menos estos casos:
1. Mensajes exactamente iguales.
2. Cambiar una sola letra.
3. Añadir un espacio.
4. Añadir un emoji o símbolo.

---

## Preguntas a responder
1. ¿Para qué sirve un hash?
2. ¿El hash cifra el mensaje? ¿Por qué?
3. ¿Qué significa comprobar la integridad de un mensaje?

---

## Entrega
Debes entregar:
- El archivo `05_integridad_hash_sha256.html`.
- Capturas donde se vean:
  - Los mensajes.
  - Sus hashes.
  - El resultado de la comparación.
- Un breve documento con las respuestas y una conclusión.

---

### Idea clave
El hash **no protege el contenido**,  
protege la **integridad**.

