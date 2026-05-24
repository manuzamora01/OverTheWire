# Bases — General Skills

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
Este reto nos presenta una cadena de texto extraña y nos sugiere que su significado tiene algo que ver con "bases" (sistemas de codificación). El objetivo es decodificar este texto para encontrar la frase oculta.

* **Objetivo:** Decodificar la cadena `bDNhcm5fdGgzX3lwcDM1`.
* **Pistas dadas:** Nos dicen que la respuesta debe enviarse dentro del formato de la bandera (`picoCTF{...}`) y sugieren el uso de CyberChef.

---

## 2. Información Inicial e Infraestructura
* **Texto a decodificar:** `bDNhcm5fdGgzX3lwcDM1`
* **Herramientas posibles:** Terminal de Linux (`base64`), CyberChef.
* **Concepto clave:** Codificación Base64.

---

## 3. Análisis Técnico y Conceptos

### ¿Qué es Base64?
A pesar del nombre del reto, Base64 **no es un sistema de numeración o cifrado**, sino un esquema de **codificación**. 
Se utiliza para transformar datos binarios (como imágenes o archivos compilados) en una cadena de texto ASCII imprimible. Utiliza 64 caracteres comunes (letras mayúsculas y minúsculas de la A a la Z, números del 0 al 9, y los símbolos `+` y `/`). 

Es extremadamente común en ciberseguridad, desarrollo web y correos electrónicos. Un rasgo muy característico de Base64 es que las cadenas suelen terminar en uno o dos signos de igual (`=` o `==`), conocidos como *padding* o relleno, aunque no siempre están presentes si la cadena original encaja perfectamente en los bloques, como ocurre en este reto.

---

## 4. Resolución Paso a Paso

### Método 1: Usando la Terminal de Linux (El método nativo)
Linux viene con una herramienta nativa llamada `base64` que permite codificar y decodificar este tipo de cadenas directamente desde la consola. Usamos el comando `echo` para imprimir la cadena y la tubería (`|`) para pasársela al comando `base64` con el parámetro `-d` (decode).

```bash
echo "bDNhcm5fdGgzX3lwcDM1" | base64 -d
```
Al ejecutarlo, la terminal nos devuelve la frase: `l3arn_th3_r0p35`

### Método 2: Usando CyberChef
1. Abrimos CyberChef.
2. Buscamos la receta **"From Base64"** en el panel izquierdo y la arrastramos al centro.
3. Pegamos `bDNhcm5fdGgzX3lwcDM1` en el panel de *Input*.
4. El panel de *Output* revelará automáticamente el texto descodificado: `l3arn_th3_r0p35`.

---

## 5. Flag Obtenida
Siguiendo las instrucciones de la pista, envolvemos el texto descodificado en el formato estándar de las banderas:

`picoCTF{l3arn_th3_r0p35}`

---

## 6. Notas para el Futuro
* En CTFs, si ves una cadena de texto que parece aleatoria pero solo contiene letras (mayúsculas/minúsculas) y números (y a veces termina en `=`), el 99% de las veces es **Base64**.
* A diferencia del cifrado ROT13, Base64 no se usa para ocultar secretos porque es trivial de revertir. Solo se usa para transportar datos de forma segura entre sistemas.