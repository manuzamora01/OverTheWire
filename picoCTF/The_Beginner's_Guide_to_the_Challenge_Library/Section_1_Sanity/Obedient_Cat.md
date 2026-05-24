# Obedient Cat — General Skills

**Dificultad:** Fácil (Sanity Check)  
**Plataforma:** picoCTF  
**Puntuación:** Variable  

---

## 1. Enunciado y Objetivos
El reto nos indica que hay una bandera escondida en texto claro (*in plain sight* / *in-the-clear*) dentro de un archivo descargable. Este tipo de retos sirve como "sanity check" para asegurar que el entorno de red funciona y que sabemos interactuar con los archivos del laboratorio.

* **Objetivo:** Descargar el archivo proporcionado y leer su contenido directamente en la terminal para extraer la bandera.
* **Pistas dadas:** Nos enseñan a descargar archivos usando comandos web y a visualizarlos dentro de la webshell.

---

## 2. Información Inicial e Infraestructura
* **Archivo del reto:** `flag` (sin extensión).
* **Herramienta principal:** Terminal de Linux (`bash`).
* **Comandos clave:** `wget`, `cat`.

---

## 3. Análisis Técnico y Conceptos

### El comando `cat` (*Concatenate*)
En sistemas Unix/Linux, `cat` es uno de los comandos fundamentales más utilizados. Su función principal es leer el contenido de uno o varios archivos y volcarlo directamente en la salida estándar (la pantalla de la terminal). 

A diferencia de los editores de texto como `nano` o `vim`, `cat` no abre una interfaz interactiva; simplemente imprime el texto de golpe, lo que lo hace ideal para scripts de automatización o lecturas rápidas de banderas.

---

## 4. Resolución Paso a Paso (Bitácora de la Terminal)

### Paso 1: Descarga del archivo
Primero, utilizamos el comando `wget` seguido de la URL del enlace que proporciona la plataforma para descargar el archivo directamente a nuestro directorio de trabajo:

```bash
wget [https://artifacts.picoctf.net/c/XXXXX/flag](https://artifacts.picoctf.net/c/XXXXX/flag)
```

### Paso 2: Verificación
Listamos el contenido del directorio actual para confirmar que el archivo `flag` se ha descargado correctamente:

```bash
ls -l
```

*Salida esperada:* Un archivo llamado `flag` con permisos de lectura.

### Paso 3: Lectura del contenido
Ejecutamos el comando `cat` apuntando al archivo que acabamos de descargar para revelar el secreto guardado en su interior:

```bash
cat flag
```

---

## 5. Flag Obtenida
Al ejecutar el comando anterior, el servidor imprime directamente la bandera en texto claro en la pantalla:

`picoCTF{g00d_c47_b3v1_XXXXXX}` *(Nota: Los caracteres del final varían por instancia).*

---

## 6. Notas para el Futuro
* Siempre que un reto mencione que la información está en *"plain sight"*, el uso de `cat` o `strings` es la primera línea de acción.
* No es necesario que un archivo tenga la extensión `.txt` para que contenga texto legible por el sistema.