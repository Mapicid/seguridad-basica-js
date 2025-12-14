# Práctica 05 — Verificación de integridad con clave privada

En esta práctica vas a simular, de forma muy sencilla, cómo un sistema comprueba
si un mensaje ha sido modificado usando un **hash y una clave privada**.

Esta idea es la base del funcionamiento de los **tokens** usados en aplicaciones y APIs.

---

## Objetivo

- Comprobar la **integridad de un mensaje**
- Detectar si el mensaje ha sido **manipulado**
- Entender cómo funciona la verificación usada en los **tokens**

---

## Idea clave

- El hash **no impide** que cambien el mensaje.
- Sirve para **detectar cambios**.
- Cuando se usa junto a una **clave privada**, solo quien conoce esa clave puede generar un hash válido.

---

## Qué tienes que hacer

Trabaja desde la **consola del navegador (F12)**.

### 1️⃣ Toma como referencia el ejemplo de la **Píldora 03**

Usa el mismo esquema de código que en la **Píldora 03 (hash + clave privada)**.

---

### 2️⃣ Personaliza el ejemplo

Debes elegir tú:

- Un **mensaje propio**  
  (por ejemplo:  
  `Alumno=TuNombre;Nota=8`  
  `Pedido=123;Total=20`  
  `Usuario=Ana;Rol=user`)

- Una **clave privada propia**  
  (no uses la del ejemplo)

---

### 3️⃣ Genera el hash del mensaje usando la clave privada

Simula que el **servidor** crea un token a partir de: clave privada + mensaje

---

### 4️⃣ Simula la verificación

Prueba **dos casos**:

- ✔️ Mensaje recibido igual al original  
- ❌ Mensaje recibido modificado (cambia algún dato)

Comprueba en consola si el mensaje es válido o no.

---

## ✅ Resultado esperado

- Cuando el mensaje **no cambia**, el resultado debe ser: ¿Mensaje válido? true
- 
- Cuando el mensaje **ha sido modificado**, el resultado debe ser: ¿Mensaje válido? false

---

## Entrega
- Captura de la consola mostrando:
  - un mensaje válido
  - un mensaje no válido
- Breve explicación (5–6 líneas) de:
  - qué has hecho
  - por qué en un caso sale `true` y en otro `false`

---



