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

## Ejemplo 1 – Hash de una contraseña (versión básica)

En este primer ejemplo vamos a **calcular el hash de una contraseña**.  
No se comprueba todavía si es correcta o no.  
El objetivo es **observar qué ocurre** cuando una contraseña pasa por un hash.

---

1. Abre el navegador.
2. Pulsa **F12**.
3. Ve a la pestaña **Console**.
4. Copia y pega el siguiente código:

```js
async function hash(texto) {
  const datos = new TextEncoder().encode(texto);
  const buffer = await crypto.subtle.digest("SHA-256", datos);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  const password = "1234";

  console.log("Contraseña:", password);
  console.log("Hash:", await hash(password));
})();
```

