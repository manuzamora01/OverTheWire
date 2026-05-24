# 🚩 The Beginner's Guide to the Challenge Library

Bienvenido a la sección introductoria de **picoCTF**. 

Este directorio contiene la documentación completa, la teoría base y los *write-ups* (resoluciones paso a paso) de los retos iniciales de la plataforma. El objetivo de esta sección es asentar las bases teóricas, familiarizarse con la infraestructura del laboratorio y aprender a usar las herramientas fundamentales de ciberseguridad.

---

## 🗂️ Índice de Contenidos

A continuación se muestra la estructura de esta guía, organizada en módulos de aprendizaje tal y como están en el repositorio:

### 📖 CTF Onboarding
Conceptos teóricos y metodologías fundamentales antes de empezar a resolver retos.
* [Approach](./CTF_Onboarding/Approach.md): Metodología y protocolo paso a paso para afrontar cualquier reto sin frustrarse.
* [Traditional CTF Categories](./CTF_Onboarding/Traditional_CTF_Categories.md): Explicación de las distintas disciplinas (Web, Forense, Criptografía, etc.).
* [What is a flag](./CTF_Onboarding/What_is_a_flag.md): Entendiendo qué es una bandera, su formato estándar y el "Leet Speak".

### 🛠️ Section 1 (Sanity)
Retos iniciales para comprobar la conexión con la infraestructura y comandos básicos de terminal.
* [Obedient Cat](./Section_1_Sanity/Obedient_Cat.md): Uso del comando `wget` para descargas y `cat` para lectura de archivos.
* [Super SSH](./Section_1_Sanity/Super_SSH.md): Conexión segura a contenedores remotos utilizando el protocolo `ssh`.
* [What's a net cat?](./Section_1_Sanity/Whats_a_net_cat.md): Interacción directa con puertos de red usando `nc` (netcat).

### 🔢 Section 2 (CyberChef)
Introducción a las conversiones numéricas y cifrados clásicos utilizando la terminal y herramientas web.
* [2warm](./Section_2_CyberChef/2warm.md): Conversión de valores Decimales (base 10) a formato Binario (base 2).
* [Bases](./Section_2_CyberChef/Bases.md): Identificación y decodificación de cadenas ofuscadas mediante Base64.
* [Mod 26](./Section_2_CyberChef/Mod_26.md): Introducción a la criptografía y descifrado del algoritmo de sustitución ROT13.
* [Warmed Up](./Section_2_CyberChef/Warmed_Up.md): Conversión de valores en sistema Hexadecimal (base 16) a formato Decimal (base 10).

---

## 💻 Herramientas Clave Utilizadas
Para completar esta sección introductoria, nos apoyamos principalmente en el siguiente *stack*:
1. **Terminal de Linux (Bash):** Comandos clave como `cat`, `wget`, `ssh`, `nc` y `base64`.
2. **CyberChef:** La "navaja suiza cibernética" web, indispensable para automatizar conversiones y descifrados.
3. **Python 3:** Utilizado en su modo de consola interactiva como calculadora rápida para conversiones de bases (`bin()`, `int()`).

> **Nota:** Todos los *write-ups* están diseñados como material de consulta rápida. Si en futuros retos te encuentras texto en Base64 o necesitas hacer un túnel con netcat, puedes volver a estos documentos para revisar los comandos exactos.