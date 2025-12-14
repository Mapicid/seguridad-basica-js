# Píldora 3 — Hash + secreto  
## Detectar manipulaciones de mensajes

---

## Idea principal

Hasta ahora hemos visto que:

- El hash sirve para **detectar cambios** en un mensaje.
- Pero **cualquiera** puede calcular el hash de un mensaje.

Esto significa que:
- Si alguien cambia el mensaje,
- también puede volver a calcular el hash,
- y hacer creer que el mensaje es válido.

Para evitar esto, se añade un **secreto**.

---

## ¿Qué es el secreto?

El **secreto** es un dato que:
- **solo conoce el emisor y el receptor**
- **no se envía**
- **no se muestra**

El secreto se usa junto con el mensaje para calcular el hash.

Ejemplo: hash(secreto + mensaje)

Así:
- quien **no conoce el secreto**
- **no puede generar un hash válido**

---

## Qué conseguimos usando un secreto

Usando hash + secreto conseguimos:
- Detectar si el mensaje ha cambiado
- Detectar si el mensaje lo ha generado alguien autorizado

El mensaje puede cambiar,
pero **sin el secreto no se puede falsificar el hash**.

---

## Ejemplo práctico (consola del navegador)

Este programa:
- calcula un hash usando un mensaje y un secreto
- simula una modificación del mensaje
- comprueba si el mensaje sigue siendo válido

---

### Código de ejemplo

Copia y pega el siguiente código en la **consola del navegador (F12)**:

```js
async function hash(text) {
  const data = new TextEncoder().encode(text);
  const buffer = await crypto.subtle.digest("SHA-256", data);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  const SECRETO = "clave_del_servidor";
  const mensajeOriginal = "Alumno=Ana;Nota=8";

  const hashEnviado = await hash(SECRETO + mensajeOriginal);

  // Simulamos que el mensaje llega modificado
  const mensajeRecibido = "Alumno=Ana;Nota=10";

  const hashCalculado = await hash(SECRETO + mensajeRecibido);

  console.log("Mensaje original:", mensajeOriginal);
  console.log("Mensaje recibido:", mensajeRecibido);

  console.log("¿Mensaje válido?", hashEnviado === hashCalculado);
})();
```

