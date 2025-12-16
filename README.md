# Seguridad básica – Integridad y Hash (JavaScript)

Este repositorio introduce **conceptos básicos de seguridad** a través de ejemplos muy sencillos en **JavaScript**, pensados para entender **qué problema resuelve un hash** antes de utilizar soluciones más avanzadas.

No se busca memorizar algoritmos, sino **comprender ideas clave**.

---

## ¿Qué problema resolvemos?
Cuando enviamos un mensaje, archivo o dato:

- ¿Cómo sabemos que **no ha cambiado** por el camino?
- ¿Cómo detectamos si alguien lo ha modificado?

En informática no se confía: **se comprueba**.

---

## Concepto clave: Integridad
La **integridad** consiste en poder asegurar que:

> Un mensaje recibido es **exactamente el mismo** que el mensaje enviado.

Si el mensaje cambia, debemos poder detectarlo.

---

## ¿Qué es un hash?
Un **hash** es una especie de **huella digital** de un mensaje.

- Entra un mensaje → sale un hash (una cadena de letras y números).
- El **mismo mensaje** siempre genera el **mismo hash**.
- Si el mensaje cambia, **el hash cambia completamente**, aunque el cambio sea mínimo.
- El hash permite **comprobar la integridad de los datos**.

---

## Lo que un hash NO es
Un hash **no es cifrado**.

- Con un hash **no se puede recuperar el mensaje original**.
- El hash solo sirve para **comprobar si el mensaje es el mismo o ha sido modificado**.

---

## Algoritmo utilizado
En los ejemplos se utiliza **SHA-256**, un algoritmo de hash muy común y seguro.

---

## Relación con aplicaciones reales
Estos conceptos son la base de:
- Verificación de mensajes.
- Almacenamiento seguro de contraseñas.
- Tokens y firmas digitales.
- Seguridad en APIs.

---

## Idea clave para llevarse
Si el mensaje cambia → el hash cambia.

> Una aplicación segura no confía: **verifica**.

---

## Relación con el DCB (RA5)
Esta actividad está alineada con el **RA5**:

> *Protege las aplicaciones y los datos definiendo y aplicando criterios de seguridad en el acceso, almacenamiento y transmisión de la información.*

Se trabajan, a nivel introductorio, los siguientes aspectos:
- Uso de **técnicas criptográficas** (hash SHA-256).
- Protección de la **información transmitida**.
- Base conceptual para sistemas de seguridad reales (tokens, firmas, APIs seguras).

---

## Requisitos
No es necesario instalar nada.

Solo se necesita:
- Un navegador moderno (Chrome, Firefox, Edge…)
- Acceso a la **consola del navegador** (F12)

