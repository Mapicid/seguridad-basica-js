# Píldora 1 — Hash: detector de cambios  
## Integridad de la información

---

## Concepto clave

Un **hash criptográfico** es un resumen de un mensaje.

Su función principal es comprobar la **integridad de la información**, es decir:
> Saber si unos datos han sido modificados o no.

Características importantes de un hash:
- A partir de un texto genera una cadena de longitud fija.
- Si el texto cambia **aunque sea un solo carácter**, el hash cambia completamente.
- No se puede obtener el texto original a partir del hash (no es reversible).

👉 Un hash **no sirve para ocultar información**, sino para **detectar cambios**.

---

## Idea importante

> Un hash no es un candado, es una alarma.

Si alguien modifica los datos, la alarma “salta” porque el hash ya no coincide.

---

## Ejemplo práctico  
### (Consola del navegador)

1. Abre el navegador.
2. Pulsa **F12**.
3. Ve a la pestaña **Console**.
4. Copia y pega el siguiente código:

```js
async function hash(text) {
  const data = new TextEncoder().encode(text);
  const buffer = await crypto.subtle.digest("SHA-256", data);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  const mensaje1 = "Nota=10";
  const mensaje2 = "Nota=9";

  console.log("Mensaje 1:", mensaje1);
  console.log("Hash 1:", await hash(mensaje1));

  console.log("Mensaje 2:", mensaje2);
  console.log("Hash 2:", await hash(mensaje2));
})();
```
