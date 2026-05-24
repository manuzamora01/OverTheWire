# Mod 26 — Cryptography

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
El reto nos introduce a los conceptos más básicos de la criptografía clásica haciéndonos una pregunta directa: *"¿Sabes qué es ROT13?"*. Además, la plataforma nos sugiere usar una herramienta online llamada **CyberChef**.

* **Objetivo:** Descifrar el contenido del archivo `values.txt` (o el texto cifrado proporcionado) utilizando el algoritmo de sustitución ROT13.
* **Pistas dadas:** Nos indican que no hace falta hacerlo a mano y nos recomiendan usar CyberChef.

---

## 2. Información Inicial e Infraestructura
* **Archivo del reto:** `values.txt` (contiene la bandera cifrada, que normalmente empieza por `cvpbPGS{...}`).
* **Herramienta principal:** [CyberChef](https://gchq.github.io/CyberChef/) o la terminal de Linux.
* **Concepto clave:** Algoritmo ROT13.

---

## 3. Análisis Técnico y Conceptos

### ¿Qué es ROT13 y la aritmética Mod 26?
**ROT13** ("Rotar 13 posiciones") es un cifrado de sustitución simple (una variante del Cifrado César) que reemplaza cada letra por la decimotercera letra que le sigue en el alfabeto. 

Dado que el alfabeto inglés básico tiene exactamente 26 letras, la aritmética modular ("Mod 26") entra en juego: desplazar una letra 13 posiciones hacia adelante, y luego otras 13 posiciones, la devuelve exactamente a su punto de origen (13 + 13 = 26). Esto significa que **ROT13 es su propio inverso**: el mismo proceso se usa tanto para cifrar como para descifrar.

### ¿Qué es CyberChef?
Desarrollado por el GCHQ (la agencia de inteligencia británica), CyberChef es una aplicación web conocida como "la navaja suiza cibernética". Permite crear "recetas" arrastrando bloques para aplicar múltiples operaciones de cifrado, descifrado y formateo a cualquier texto de forma instantánea.

---

## 4. Resolución Paso a Paso

Tienes dos formas de resolver este reto. Es recomendable documentar ambas:

### Método 1: Usando CyberChef (El método web sugerido)
1. Abrimos el archivo `values.txt` y copiamos el texto cifrado. Veremos que empieza por `cvpbPGS{`, que es el equivalente a `picoCTF{` desplazado 13 posiciones.
2. Entramos en la web de [CyberChef](https://gchq.github.io/CyberChef/).
3. En el panel izquierdo (*Operations*), buscamos **ROT13** y arrastramos el bloque a la columna central (*Recipe*).
4. Pegamos el texto cifrado en el panel superior derecho (*Input*).
5. Automáticamente, en el panel inferior derecho (*Output*), aparecerá el texto descifrado en texto claro.

### Método 2: Usando la Terminal de Linux (El método rápido)
Si no queremos salir de la terminal, podemos usar el comando `tr` (translate) para mapear el alfabeto desplazado. Simplemente leemos el archivo y lo pasamos por la tubería (`|`):

```bash
cat values.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

## 5. Flag Obtenida
Al pasar el texto cifrado por el algoritmo ROT13, obtenemos nuestra bandera en el formato estándar:

`picoCTF{...}` *(Nota: Rellena esta línea con el contenido exacto que te arrojó CyberChef o la terminal).*

---

## 6. Notas para el Futuro
* El patrón `cvpbPGS{` siempre, **siempre** significa que estamos ante un texto cifrado con ROT13. Es un patrón visual que debes memorizar en los CTFs.
* CyberChef es una herramienta indispensable; cuando encuentres texto sin sentido aparente (Base64, Hexadecimal, binario), usa el bloque "Magic" de CyberChef, ya que a menudo adivina y resuelve el cifrado automáticamente.