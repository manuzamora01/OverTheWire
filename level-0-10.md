## Level 0

  

### 🎯 Objetivo

Conectarse al servidor de OverTheWire usando SSH con las credenciales proporcionadas.

<img width="1005" height="262" alt="image" src="https://github.com/user-attachments/assets/243e2481-290c-4e24-8a2c-aeb8376c3162" />


---

  

### 🧠 Enfoque

En este nivel inicial el objetivo es simplemente establecer una conexión remota al servidor.

  

Para ello, hay que usar el protocolo SSH indicando:

- Usuario

- Dirección del servidor

- Puerto específico

  

---

  

### 💻 Comandos utilizados

```bash

ssh bandit0@bandit.labs.overthewire.org -p 2220
```

---

## Level 0 → Level 1

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo llamado `readme` dentro del directorio home del usuario.

<img width="1018" height="403" alt="image" src="https://github.com/user-attachments/assets/9bae4106-48fd-4e98-b4e3-21ea5a4d5303" />


---

  

### 🧠 Enfoque

Después de conectarse al servidor, el objetivo es explorar el sistema de archivos para localizar el archivo indicado.

  

El enunciado ya da pistas claras:

- El archivo se llama `readme`

- Está en el directorio home

  

Por lo tanto, basta con:

1. Listar los archivos del directorio

2. Leer el contenido del archivo

  

---

  

### 💻 Comandos utilizados

```bash
pwd
ls
cat readme
```
<img width="768" height="256" alt="image" src="https://github.com/user-attachments/assets/d924afbd-4656-4d18-a364-f9353806e41b" />


---

## Level 1 → Level 2

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo llamado `-` dentro del directorio home.

<img width="616" height="370" alt="image" src="https://github.com/user-attachments/assets/a2deabb8-7954-44ef-a164-941b566284ee" />


---

  

### 🧠 Enfoque

El objetivo parece sencillo, pero el nombre del archivo (`-`) introduce un problema.

  

En Linux, el carácter `-` tiene un significado especial y suele interpretarse como entrada estándar (stdin) en muchos comandos. 

Por eso, no se puede acceder directamente al archivo usando `cat -`.

  

La clave está en indicar explícitamente que se trata de un archivo en el directorio actual.

  

---

  

### 💻 Comandos utilizados

```bash
pwd
ls
cat ./-
```
<img width="312" height="195" alt="image" src="https://github.com/user-attachments/assets/bf238614-7c4b-49a3-a2aa-c7e9cf910b6b" />


---

## Level 2 → Level 3

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 
El password está almacenado en un archivo llamado `--spaces in this filename--` ubicado en el directorio home.

<img width="834" height="241" alt="image" src="https://github.com/user-attachments/assets/741f28b3-c969-4925-9c91-5275b59bc23c" />


---

  

### 🧠 Enfoque

El problema principal en este nivel es que el nombre del archivo contiene espacios.

  

En la terminal, los espacios se usan para separar argumentos, por lo que el nombre del archivo se interpreta como múltiples parámetros. 

Por ello, es necesario usar una técnica para tratar el nombre como un único argumento.

  

---

  

### 💻 Comandos utilizados

```bash
pwd
ls -l
cat "--spaces in this filename--"
```

<img width="676" height="172" alt="image" src="https://github.com/user-attachments/assets/138a0fe6-8486-4d3c-b783-597a5d69d449" />


---

## Level 3 → Level 4

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo oculto dentro del directorio `inhere`.

<img width="544" height="235" alt="image" src="https://github.com/user-attachments/assets/912db7cc-55ee-4f69-a10f-de73c8a2c54b" />


---

  

### 🧠 Enfoque

Primero es necesario entrar en el directorio indicado (`inhere`).

  

Una vez dentro, al listar los archivos con `ls`, no aparece ningún archivo visible. 

Esto indica que el archivo podría estar **oculto**.

  

En Linux, los archivos ocultos comienzan con un punto (`.`), por lo que es necesario usar una opción especial para poder visualizarlos.

  

---

  

### 💻 Comandos utilizados

```bash
pwd
ls -l
cd inhere/
ls -la
cat .Hiding-From-You
```

<img width="606" height="318" alt="image" src="https://github.com/user-attachments/assets/974c1b49-66b5-4377-b442-df906ade6d12" />


---

## Level 4 → Level 5

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el único archivo **legible por humanos** dentro del directorio `inhere`.

<img width="987" height="279" alt="image" src="https://github.com/user-attachments/assets/e0d27f0b-ffd5-4136-9d9d-cbbcff43b6f8" />


---

  

### 🧠 Enfoque

Dentro del directorio `inhere` hay múltiples archivos con nombres similares (`-file00`, `-file01`, etc.).

  

El problema es doble:

1. Los archivos comienzan con `-`, lo que puede causar problemas al usar comandos como `cat`.

2. La mayoría de archivos contienen datos binarios, por lo que no son legibles.

  

La estrategia consiste en:

- Acceder correctamente a cada archivo

- Identificar cuál contiene texto legible

  

---

  

### 💻 Comandos utilizados

```bash
cd inhere/
ls -la
cat ./-file00
cat ./-file01
cat ./-file02
```

<img width="690" height="717" alt="image" src="https://github.com/user-attachments/assets/21dd99ae-2a2c-46fe-bde0-d7c9eb305fbd" />


---

## Bandit Level 5 → Level 6

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo dentro del directorio `inhere` que cumple las siguientes condiciones:

  

- Legible por humanos 

- Tamaño de 1033 bytes 

- No ejecutable 

<img width="856" height="330" alt="image" src="https://github.com/user-attachments/assets/c095ae5d-8292-44a6-b099-7d22f035e550" />


---

  

### 🧠 Enfoque

En este nivel hay muchos archivos distribuidos en diferentes subdirectorios dentro de `inhere`.

  

Buscar manualmente sería ineficiente, por lo que la mejor estrategia es usar el comando `find` para localizar archivos que cumplan ciertas condiciones.

  

Se utilizan filtros para:

- Tamaño exacto del archivo

- Tipo de archivo (archivo normal)

- Permisos (no ejecutable)

  

---

  

### 💻 Comandos utilizados

```bash
cd inhere/
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
```

<img width="450" height="48" alt="image" src="https://github.com/user-attachments/assets/6c2aa8a3-cb5c-465c-931d-a4c41d150fff" />


---

## Level 7 → Level 8

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt`, junto a la palabra clave `millionth`.

<img width="595" height="252" alt="image" src="https://github.com/user-attachments/assets/17fb6a22-7513-430b-8676-24287737c1d7" />


---

  

### 🧠 Enfoque

Dado que el archivo `data.txt` es bastante grande, no es eficiente buscar manualmente.

  

La clave del ejercicio es identificar una palabra específica (`millionth`) dentro del archivo y mostrar la línea que la contiene.

  

Para ello, se utiliza el comando `grep`, que permite buscar patrones dentro de archivos de texto.

  

---

  

### 💻 Comandos utilizados

```bash
pwd
ls -l
cat data.txt | grep millionth
```

<img width="555" height="175" alt="image" src="https://github.com/user-attachments/assets/903f4198-5aed-40cc-851a-10b8c3f27923" />


---

## Level 8 → Level 9

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt` y es la única línea que aparece una sola vez.

<img width="745" height="342" alt="image" src="https://github.com/user-attachments/assets/b4b6ba81-c3bd-4dd4-b1d0-f068dc626c23" />


---

  

### 🧠 Enfoque

El archivo contiene múltiples líneas, muchas de ellas repetidas.

  

El objetivo es encontrar la única línea que no tiene duplicados.

  

Para ello, es necesario:

1. Agrupar líneas iguales

2. Identificar cuáles aparecen solo una vez

  

Esto se consigue combinando los comandos `sort` y `uniq`.

  

---

  

### 💻 Comandos utilizados

```bash
sort data.txt | uniq -u
```

<img width="391" height="81" alt="image" src="https://github.com/user-attachments/assets/64cc8157-53cb-40b9-bfee-54dbe229f343" />


---

## Level 9 → Level 10

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt`, dentro de una de las pocas cadenas legibles, precedida por varios caracteres `=`.

<img width="928" height="247" alt="image" src="https://github.com/user-attachments/assets/6b3211e8-43dd-4c4e-9ae8-82074ec8e33f" />


---

  

### 🧠 Enfoque

El archivo contiene principalmente datos binarios, por lo que no es posible leerlo directamente con `cat`.

  

La estrategia consiste en:

1. Extraer únicamente las cadenas legibles del archivo.

2. Filtrar aquellas que contengan el patrón `=` indicado en el enunciado.

  

Para ello, se combinan los comandos `strings` y `grep`.

  

---

  

### 💻 Comandos utilizados

```bash
strings data.txt | grep "="
```

<img width="430" height="256" alt="image" src="https://github.com/user-attachments/assets/c31f7244-d6ed-4690-aa38-660d354b0056" />


