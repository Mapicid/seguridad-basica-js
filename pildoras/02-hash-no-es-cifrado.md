## Idea clave
El **hash sirve para comprobar la integridad de un mensaje**.

> Permite detectar si un mensaje **ha sido modificado**.

Es importante entender que cuando usamos un hash:

- El mensaje no se oculta.

- El mensaje se envía en texto plano.

- Cualquiera que lo intercepte puede leerlo.

- Pero si lo modifica, lo sabremos porque el hash ya no coincide.

---

## Ejemplo práctico (consola del navegador)

```js
async function hash(text) {
  const data = new TextEncoder().encode(text);
  const buffer = await crypto.subtle.digest("SHA-256", data);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  const mensajeOriginal = "Pedido=123;Total=21.50";
  const mensajeModificado = "Pedido=123;Total=0";

  const hashOriginal = await hash(mensajeOriginal);
  const hashModificado = await hash(mensajeModificado);

  console.log("Mensaje original:", mensajeOriginal);
  console.log("Hash original:", hashOriginal);

  console.log("Mensaje modificado:", mensajeModificado);
  console.log("Hash modificado:", hashModificado);

  console.log("¿El mensaje es el mismo?", hashOriginal === hashModificado);
})();

```
## ¿Qué hace este programa?

Este programa calcula el **hash SHA-256** de dos mensajes:

- Un mensaje original.
- El mismo mensaje con una pequeña modificación.

Después, **compara ambos hashes**.

Los hashes **no coinciden**, el programa devuelve `false`, lo que indica que:
- El mensaje **ha sido modificado**.
- La **integridad del mensaje no se mantiene**.

Esto demuestra que el hash permite **detectar cambios en la información**, aunque el mensaje siga siendo legible.

