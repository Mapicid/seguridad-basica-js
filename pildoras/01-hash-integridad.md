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
# Ejemplo sencillo: Emisor y receptor usando hash  
## Comprobación de integridad de un mensaje

Este ejemplo muestra cómo se utiliza un **hash** para comprobar si un mensaje ha sido modificado durante su envío. No se usa cifrado, solo **integridad de la información**.

---

## Emisor (quien envía el mensaje)

El emisor tiene el siguiente mensaje:

"Nota=10"

Calcula el hash del mensaje:

hash("Nota=10") → d4c5e1...

Envía al receptor **dos cosas**:
- El mensaje
- El hash del mensaje

Mensaje: "Nota=10"  
Hash:    d4c5e1...

---

## Receptor (quien recibe el mensaje)

El receptor recibe:

Mensaje: "Nota=10"  
Hash recibido: d4c5e1...

Para comprobar si el mensaje ha sido modificado, el receptor:

1. Vuelve a calcular el hash del mensaje recibido.
2. Compara el hash calculado con el hash recibido.

hash("Nota=10") → d4c5e1...

---

##  Resultado de la verificación

- Si los hashes **coinciden** → el mensaje **NO ha sido modificado**
- Si los hashes **no coinciden** → el mensaje **ha sido manipulado**

---

## Ejemplo de manipulación

Durante el envío, alguien modifica el mensaje:

"Nota=10" → "Nota=9"

El hash recibido sigue siendo el original:

d4c5e1...

El receptor calcula el hash del mensaje modificado:

hash("Nota=9") → 33c1df...

Resultado:
- Los hashes **no coinciden**
- Se detecta la manipulación del mensaje

---

## ¿Qué algoritmo usar según el objetivo de seguridad?
Integridad de datos → SHA-256
Contraseñas         → bcrypt / argon2
Hash con secreto    → HMAC-SHA-256

## Idea clave para recordar

Un hash **no se descifra**.  
Para comprobar un mensaje, **se vuelve a calcular el hash y se compara**.

Este mecanismo se utiliza para garantizar la **integridad de la información** en aplicaciones y APIs.
