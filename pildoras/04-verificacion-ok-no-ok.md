# Píldora 04 — Verificación OK / NO OK  
## Decidir si un mensaje es válido

---

## Idea clave

Un hash **no se calcula solo para verlo**,  
se calcula para **compararlo y tomar una decisión**.

El sistema decide:
- aceptar el mensaje  
- o rechazarlo  

En función de si el hash coincide o no.

---

## Qué hace esta píldora

Este ejemplo simula cómo un sistema:
1. Recibe un mensaje y un hash
2. Vuelve a calcular el hash del mensaje recibido
3. Compara ambos hashes
4. Devuelve **true** o **false**
5. Decide si el mensaje es válido

---

## Ejemplo práctico (consola del navegador)

1. Abre el navegador
2. Pulsa **F12**
3. Ve a **Console**
4. Copia y pega este código:

```js
async function hash(text) {
  const data = new TextEncoder().encode(text);
  const buffer = await crypto.subtle.digest("SHA-256", data);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

async function verificarMensaje(mensaje, hashRecibido) {
  const hashCalculado = await hash(mensaje);
  return hashCalculado === hashRecibido;
}

(async () => {
  // Mensaje original
  const mensaje = "Alumno=Lucia;Nota=9";
  const hashCorrecto = await hash(mensaje);

  // Verificación correcta
  const esValido = await verificarMensaje(mensaje, hashCorrecto);
  console.log("Mensaje original válido:", esValido);

  // Mensaje manipulado
  const mensajeManipulado = "Alumno=Lucia;Nota=0";
  const esValidoManipulado = await verificarMensaje(
    mensajeManipulado,
    hashCorrecto
  );
  console.log("Mensaje manipulado válido:", esValidoManipulado);
})();
```
El segundo mensaje devuelve false porque el mensaje no es el mismo que el que se usó para generar el hash.
