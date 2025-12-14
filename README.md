# Seguridad básica en aplicaciones (JavaScript)

Este repositorio contiene una serie de **micro-píldoras prácticas** para introducir conceptos básicos de **seguridad y criptografía** aplicados a aplicaciones y APIs.

Las actividades están diseñadas para:
- ser **muy sencillas**
- poder probarse **directamente desde la consola del navegador**
- comprender conceptos clave antes de pasar a soluciones más complejas (APIs, JWT, HTTPS, etc.)

---

## Objetivos de aprendizaje
Al finalizar estas actividades, el alumnado será capaz de:

- Comprender qué es la **integridad de la información**.
- Explicar qué es un **hash criptográfico** y para qué se utiliza.
- Diferenciar claramente **hash** y **cifrado**.
- Detectar la **manipulación de datos**.
- Relacionar estos conceptos con la **seguridad en APIs**.
- Aplicar principios básicos de **programación segura**.

---

## Relación con el DBC (RA5)

Esta actividad está alineada con el **RA5**:

> *Protege las aplicaciones y los datos definiendo y aplicando criterios de seguridad en el acceso, almacenamiento y transmisión de la información.*

Se trabajan, a nivel introductorio, los siguientes aspectos:
- Uso de **técnicas criptográficas** (hash SHA-256).
- Protección de la **información transmitida**.
- Detección de **modificaciones no autorizadas**.
- Buenas prácticas de **programación segura**.
- Base conceptual para sistemas de seguridad reales (tokens, firmas, APIs seguras).

---

## Contenido del repositorio

El repositorio se organiza en **micro-píldoras**, cada una con:
- un concepto clave
- un ejemplo práctico
- una prueba sencilla

### Píldoras incluidas:
1. **Hash como detector de cambios**  
   (integridad de la información)
2. **El hash no es cifrado**  
   (diferencia entre integridad y confidencialidad)
3. **Hash + secreto**  
   (detección de manipulaciones)
4. **Verificación OK / NO OK**  
   (aceptar o rechazar datos)

---

## Requisitos
No es necesario instalar nada.

Solo se necesita:
- Un navegador moderno (Chrome, Firefox, Edge…)
- Acceso a la **consola del navegador** (F12)

---

## ▶️ Cómo usar este repositorio

1. Abre los ejemplos indicados.
2. Copia el código JavaScript.
3. Pégalo en la **consola del navegador**.
4. Ejecuta el código y observa el resultado.
5. Modifica los mensajes y analiza qué ocurre.

---

## Conexión con proyectos reales
Los conceptos trabajados aquí son la base de:
- Tokens JWT
- Firmas de mensajes
- Hash de contraseñas
- Seguridad en APIs REST
- Comunicaciones seguras

---

## 📌 Nota final
Estas actividades **no sustituyen** a sistemas de seguridad completos, pero ayudan a entender **qué problema se está resolviendo** antes de usar librerías y frameworks.

> Una aplicación segura no confía: verifica.
