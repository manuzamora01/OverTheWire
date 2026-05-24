# Super SSH — General Skills

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
El reto nos pide establecer una conexión remota segura a través del protocolo SSH utilizando las credenciales provistas por la plataforma. Al conectarnos con éxito al servidor remoto, este nos otorgará de forma automática la bandera.

* **Objetivo:** Utilizar el cliente SSH de la terminal para acceder de manera remota al contenedor del reto en el puerto indicado.
* **Pistas dadas:** Nos facilitan el usuario (`ctf-player`), el host (`titan.picoctf.net`), el puerto (`50394`) y la contraseña de acceso (`84b12bae`).

---

## 2. Información Inicial e Infraestructura
* **Servidor (Host):** `titan.picoctf.net`
* **Puerto:** `50394`
* **Usuario:** `ctf-player`
* **Contraseña:** `84b12bae`
* **Comando clave:** `ssh`

---

## 3. Análisis Técnico y Conceptos

### ¿Qué es SSH (*Secure Shell*)?
SSH es un protocolo de administración remota que permite a los usuarios controlar y modificar sus servidores a través de Internet de forma completamente cifrada. Opera de manera segura ya que toda la comunicación entre el cliente (tu terminal) y el servidor remoto viaja protegida contra intercepciones.

A diferencia de otros comandos de descarga pasiva como `wget`, al ejecutar `ssh` abres una sesión interactiva en un ordenador ajeno: tu terminal se convierte en una ventana directa al sistema operativo del servidor.

---

## 4. Resolución Paso a Paso (Bitácora de la Terminal)

### Paso 1: Estructurar la sintaxis del comando
Para conectarnos a un puerto específico que no sea el puerto estándar de SSH (22), debemos usar el parámetro `-p`. La estructura básica es:

```bash
ssh usuario@servidor -p puerto
```

### Paso 2: Ejecución e intercambio de llaves (Fingerprint)
Lanzamos el comando exacto con los datos proporcionados por la instancia:

```bash
ssh ctf-player@titan.picoctf.net -p 50394
```

Al ser la primera vez que nos conectamos a este servidor, la terminal mostrará un mensaje de alerta de seguridad solicitando confirmar la autenticidad del host (ECDSA key fingerprint):

```text
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

**Acción:** Escribimos `yes` y pulsamos Enter para almacenar el servidor en nuestra lista de hosts conocidos (`~/.ssh/known_hosts`).

### Paso 3: Autenticación
El servidor solicitará la contraseña. Introducimos la clave asignada por el reto:

```text
ctf-player@titan.picoctf.net's password: 84b12bae
```

> *(Nota: Al escribir contraseñas en la terminal de Linux, el cursor no se moverá ni mostrará asteriscos por motivos de seguridad. Se pega o escribe a ciegas y se pulsa Enter).*

---

## 5. Flag Obtenida
Tras realizar la autenticación con éxito, el servidor remoto inicia sesión, despliega un mensaje de bienvenida en la terminal y expulsa directamente la bandera antes de cerrar la conexión:

`picoCTF{s5h_4ll_7h3_w4y_XXXXXX}`

---

## 6. Notas para el Futuro
* El parámetro para especificar el puerto en el comando `ssh` es obligatoriamente `-p` minúscula (a diferencia de otros comandos como `scp` que usan `-P` mayúscula).
* Si una sesión SSH se cierra inmediatamente tras mostrar la bandera, es un comportamiento automatizado por el creador del reto para liberar recursos del contenedor.