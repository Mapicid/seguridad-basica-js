# Píldora 1 — Hash: detector de cambios
## Integridad de la información

---

## Idea clave
Un **hash** sirve para comprobar la **integridad de un mensaje**.

> Nos permite saber si un mensaje **ha cambiado** o **sigue siendo el mismo**.

---

## ¿Qué hace un hash?
- A partir de un mensaje genera una cadena de letras y números.
- El mismo mensaje → el mismo hash.
- Si el mensaje cambia, **el hash cambia**.
- No se puede recuperar el mensaje original a partir del hash.

👉 Un hash **no oculta** información, solo **detecta cambios**.

---

## Metáfora útil
> Un hash no es un candado, es una alarma.

Si alguien modifica el mensaje, la alarma salta porque el hash ya no coincide.

---

## Ejemplo práctico (Consola del navegador)

1. Abre el navegador.
2. Pulsa **F12**.
3. Ve a la pestaña **Console**.
4. Copia y pega este código:

```js
async function hash(texto) {
  const datos = new TextEncoder().encode(texto);
  const buffer = await crypto.subtle.digest("SHA-256", datos);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  const mensajeA = "Nota=10";
  const mensajeB = "Nota=9";

  console.log("Mensaje A:", mensajeA);
  console.log("Hash A:", await hash(mensajeA));

  console.log("Mensaje B:", mensajeB);
  console.log("Hash B:", await hash(mensajeB));
})();
