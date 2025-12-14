# Actividad 05 — Verificación de integridad de un mensaje

En esta actividad vas a realizar una **simulación sencilla** del funcionamiento de la seguridad en aplicaciones y APIs.

El objetivo es comprobar cómo se puede **detectar si un mensaje ha sido modificado**, utilizando un **hash con una clave privada**.

No es necesario usar servidores ni red real.  
Todo se probará desde la **consola del navegador**.

---

## Objetivo de la actividad

- Comprender cómo se verifica la **integridad de un mensaje**
- Usar un **hash + clave privada**
- Simular el funcionamiento básico de un **token**
- Detectar cuándo un mensaje es válido y cuándo ha sido manipulado

---

## Idea clave

El hash **no impide** que cambien un mensaje.  
Sirve para **detectar si el mensaje ha sido modificado**.

Cuando se añade una **clave privada**, solo quien la conoce puede generar un hash válido.

---

## Qué vas a hacer

Cada alumno debe:

1. Crear **su propio mensaje**
2. Definir **su propia clave privada**
3. Generar un “token” (hash del mensaje + clave privada)
4. Verificar el mensaje
5. Simular una manipulación y comprobar qué ocurre

---

## Código base (consola del navegador)

Copia y pega este código en la consola del navegador (F12):

```js
async function hash(text) {
  const data = new TextEncoder().encode(text);
  const buffer = await crypto.subtle.digest("SHA-256", data);
  return [...new Uint8Array(buffer)]
    .map(b => b.toString(16).padStart(2, "0"))
    .join("");
}

(async () => {
  // 1. MENSAJE (elige uno propio)
  const mensaje = "Alumno=TuNombre;Nota=8";

  // 2. CLAVE PRIVADA (elige una propia)
  const clavePrivada = "mi_clave_super_secreta";

  // 3. EL SERVIDOR CREA EL TOKEN
  const token = await hash(clavePrivada + mensaje);

  // 4. VERIFICACIÓN DEL MENSAJE
  const mensajeRecibido = mensaje; // prueba a cambiarlo
  const tokenCalculado = await hash(clavePrivada + mensajeRecibido);

  console.log("Mensaje recibido:", mensajeRecibido);
  console.log("Token recibido:", token);
  console.log("¿Mensaje válido?", token === tokenCalculado);
})();

