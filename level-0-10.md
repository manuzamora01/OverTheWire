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

  ![[Pasted image 20260521104105.png]]

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
![[Pasted image 20260521104125.png|439]]

---

## Level 1 → Level 2

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo llamado `-` dentro del directorio home.

  ![[Pasted image 20260521104600.png]]

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
![[Pasted image 20260521104622.png]]

---

## Level 2 → Level 3

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 
El password está almacenado en un archivo llamado `--spaces in this filename--` ubicado en el directorio home.

  ![[Pasted image 20260521111917.png]]

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

![[Pasted image 20260521111922.png]]

---

## Level 3 → Level 4

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo oculto dentro del directorio `inhere`.

  ![[Pasted image 20260521112022.png]]

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

![[Pasted image 20260521112044.png]]

---

## Level 4 → Level 5

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el único archivo **legible por humanos** dentro del directorio `inhere`.

  ![[Pasted image 20260521112710.png]]

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

![[Pasted image 20260521112717.png]]

---

## Bandit Level 5 → Level 6

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en un archivo dentro del directorio `inhere` que cumple las siguientes condiciones:

  

- Legible por humanos 

- Tamaño de 1033 bytes 

- No ejecutable 

  ![[Pasted image 20260521113305.png]]

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

![[Pasted image 20260521113327.png]]

---

## Level 7 → Level 8

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt`, junto a la palabra clave `millionth`.

  ![[Pasted image 20260521114006.png]]

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

![[Pasted image 20260521114018.png]]

---

## Level 8 → Level 9

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt` y es la única línea que aparece una sola vez.

  ![[Pasted image 20260521114406.png]]

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

![[Pasted image 20260521114359.png]]

---

## Level 9 → Level 10

  

### 🎯 Objetivo

Encontrar el password del siguiente nivel. 

El password está almacenado en el archivo `data.txt`, dentro de una de las pocas cadenas legibles, precedida por varios caracteres `=`.

  ![[Pasted image 20260521114953.png]]

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

![[Pasted image 20260521115023.png]]
