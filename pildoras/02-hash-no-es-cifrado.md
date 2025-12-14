# El hash y la integridad del mensaje

## Idea clave

El **hash sirve para comprobar la integridad del mensaje**, es decir, **detectar cambios**.

Es importante entender que:

> El hash **no impide** que cambien un mensaje.  
> Sirve para **detectar si el mensaje ha sido modificado**.

El mensaje puede cambiar, pero si cambia, el hash ya no coincidirá.

---

## Qué significa comprobar la integridad

Comprobar la integridad de un mensaje significa:
- Verificar que el mensaje recibido es **exactamente el mismo** que el original.
- Detectar si alguien ha modificado el contenido durante el envío o almacenamiento.

El hash actúa como una **huella digital del mensaje**.

---

##  Ejemplo sencillo: detectar cambios en un mensaje

Vamos a simular dos situaciones:
1. El mensaje original.
2. El mismo mensaje con un pequeño cambio.

Si el mensaje cambia, el hash cambia.

---

## Ejemplo práctico (consola del navegador)

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
