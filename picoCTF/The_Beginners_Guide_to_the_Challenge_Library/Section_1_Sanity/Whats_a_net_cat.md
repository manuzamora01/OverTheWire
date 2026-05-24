# what's a net cat? — General Skills

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
El reto nos introduce a una de las herramientas de terminal más importantes en ciberseguridad: **netcat** (`nc`). El objetivo es utilizar esta herramienta para conectarnos a un servidor remoto a través de un puerto específico. Al establecer la conexión TCP, el servidor nos enviará la bandera automáticamente por pantalla.

* **Objetivo:** Conectarse al servidor `fickle-tempest.picoctf.net` en el puerto `53925` utilizando el comando `nc`.
* **Pistas dadas:** El propio nombre del reto y la descripción nos apuntan directamente al uso de `nc`.

---

## 2. Información Inicial e Infraestructura
* **Servidor (Host):** `fickle-tempest.picoctf.net`
* **Puerto:** `53925`
* **Comando clave:** `nc` (netcat)

---

## 3. Análisis Técnico y Conceptos

### ¿Qué es Netcat (`nc`)?
Netcat es conocida mundialmente como la "navaja suiza" de las redes en sistemas TCP/IP. Es una utilidad de consola que permite leer y escribir datos a través de conexiones de red de forma extremadamente sencilla. 

En el contexto de los CTFs, se usa constantemente para:
1. Interactuar con servicios remotos y leer banderas.
2. Enviar *payloads* (cargas útiles) en retos de explotación de binarios.
3. Abrir puertos a la escucha en tu propia máquina para recibir conexiones inversas (*Reverse Shells*).

---

## 4. Resolución Paso a Paso (Bitácora de la Terminal)

### Paso 1: Estructurar la sintaxis del comando
Para conectarnos a un servidor remoto usando netcat como cliente, la sintaxis básica es sumamente directa. No requiere "flags" (parámetros con guiones) para una conexión estándar, solo el nombre del servidor seguido del puerto, separados por un espacio:

```bash
nc servidor puerto
```

### Paso 2: Ejecución de la conexión
Lanzamos el comando exacto con los datos proporcionados por la plataforma en nuestra terminal:

```bash
nc fickle-tempest.picoctf.net 53925
```

Al ejecutar este comando y pulsar Enter, netcat resolverá la dirección web, establecerá un túnel directo con el puerto 53925 del servidor y mostrará en nuestra terminal cualquier texto que la máquina remota nos envíe.

---

## 5. Flag Obtenida
Tras establecer la conexión con éxito, el servidor remoto escupe directamente la bandera en formato de texto plano y cierra la conexión:

`picoCTF{n3tcat_m4st3r_XXXXXX}` *(Nota: Actualiza esta línea con los caracteres finales de tu instancia).*

---

## 6. Notas para el Futuro
* A diferencia de `ssh`, netcat (`nc`) no proporciona una conexión cifrada, no pide usuario ni contraseña; actúa simplemente como una tubería de texto puro entre dos máquinas.
* El puerto en netcat se pone **sin** usar el parámetro `-p` cuando actúas como cliente (el `-p` se usa cuando quieres poner a netcat a escuchar/abrir un puerto local usando `nc -lvnp`).