# Warmed Up — General Skills

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
Este reto es un ejercicio fundamental sobre sistemas numéricos. Nos pide convertir un número dado en formato hexadecimal (base 16) a su equivalente en formato decimal (base 10) estándar.

* **Objetivo:** Convertir el valor `0x3D` de base 16 a base 10.
* **Pistas dadas:** Nos recuerdan que la respuesta debe ir envuelta en el formato de la bandera. Por ejemplo, si el resultado fuera 22, la flag a enviar sería `picoCTF{22}`. También sugieren que se puede usar CyberChef.

---

## 2. Información Inicial e Infraestructura
* **Valor a convertir:** `0x3D`
* **Herramientas posibles:** Matemáticas manuales, consola de Python, CyberChef o conversores web.
* **Concepto clave:** Sistemas de numeración (Hexadecimal a Decimal).

---

## 3. Análisis Técnico y Conceptos

### El sistema Hexadecimal (Base 16)
El sistema que usamos en el día a día es el decimal (base 10), que usa los dígitos del 0 al 9. El sistema hexadecimal utiliza 16 símbolos: los números del `0` al `9` y las letras de la `A` a la `F` (donde A=10, B=11, C=12, D=13, E=14, F=15).

* **El prefijo `0x`:** En programación, cuando ves un número que empieza por `0x`, es simplemente la forma estándar de decirle al ordenador: *"Oye, lo que viene a continuación está en hexadecimal"*. El valor real a convertir es solo `3D`.

---

## 4. Resolución Paso a Paso

Hay varias formas de resolver esto, desde lo más manual hasta lo automático:

### Método 1: Matemáticas Manuales
En base 16, la posición de la derecha se multiplica por $16^0$ (que es 1) y la siguiente por $16^1$ (que es 16).
Sabiendo que la letra `D` equivale a 13:
* $3 \times 16 = 48$
* $13 \times 1 = 13$
* Sumamos ambas partes: $48 + 13 = 61$

### Método 2: Usando Python (La forma más rápida del hacker)
Cualquier terminal de Linux suele tener Python instalado. Puedes usarlo como una calculadora inteligente. Si abres la terminal y escribes `python3`, basta con introducir el número hexadecimal directamente, o usar la función `int()` especificando la base:

```python
# Opción A: Escribir el número directamente con su prefijo
>>> 0x3D
61

# Opción B: Convertir el string diciendo que es base 16
>>> int("3D", 16)
61
```

### Método 3: Usando CyberChef
1. Entramos en CyberChef.
2. Busramos la receta **"From Hex"** (o "To Decimal").
3. Ponemos `3D` en el *Input* y el *Output* nos dará automáticamente el `61`.

---

## 5. Flag Obtenida
Siguiendo las instrucciones de la pista, envolvemos nuestro resultado numérico en el formato estándar de las banderas de la plataforma:

`picoCTF{61}`

---

## 6. Notas para el Futuro
* Memorizar que el prefijo `0x` significa "Hexadecimal" es crucial para los retos de Ingeniería Inversa y Explotación Binaria.
* Las letras en hexadecimal no distinguen entre mayúsculas y minúsculas (`0x3D` es lo mismo que `0x3d`).
* Python es la calculadora definitiva para los CTFs. Ante cualquier conversión numérica, la consola interactiva de Python te dará la respuesta en segundos.