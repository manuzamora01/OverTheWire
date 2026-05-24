# 2warm — General Skills

**Dificultad:** Fácil  
**Plataforma:** picoCTF  

---

## 1. Enunciado y Objetivos
Este reto es otro ejercicio de calentamiento sobre conversión de bases numéricas. En este caso, nos pide convertir un número decimal cotidiano a su representación en código binario (el lenguaje nativo de los ordenadores).

* **Objetivo:** Convertir el número `42` (base 10) a binario (base 2).
* **Pistas dadas:** Nos recuerdan que la respuesta debe enviarse dentro del formato estándar de la bandera (`picoCTF{...}`).

---

## 2. Información Inicial e Infraestructura
* **Valor a convertir:** `42`
* **Herramientas posibles:** Matemáticas manuales, consola de Python, CyberChef.
* **Concepto clave:** Sistemas de numeración (Decimal a Binario).

---

## 3. Análisis Técnico y Conceptos

### El sistema Binario (Base 2)
A diferencia de nuestro sistema decimal que tiene 10 dígitos (0-9), el sistema binario solo tiene dos: el `0` y el `1`. Cada posición en un número binario representa una potencia de 2, empezando desde la derecha ($2^0, 2^1, 2^2, 2^3...$ es decir: 1, 2, 4, 8, 16, 32...).

Para convertir un número decimal a binario, simplemente tenemos que ver qué potencias de 2 suman nuestro número exacto, poniendo un `1` si usamos esa potencia y un `0` si no la usamos.

---

## 4. Resolución Paso a Paso

Al igual que en el reto anterior, podemos documentar varias formas de llegar al resultado:

### Método 1: Usando Python (La forma más rápida)
En la terminal de Linux o en cualquier entorno con Python, podemos usar la función nativa `bin()` para convertir cualquier número a binario al instante.

```python
>>> bin(42)
'0b101010'
```
*(Nota: Python añade el prefijo `0b` para indicar que es un número binario, de la misma forma que usa `0x` para hexadecimal. El valor real es solo lo que va después: `101010`).*

### Método 2: Matemáticas Manuales (Por potencias de 2)
Buscamos las potencias de 2 que, sumadas, den 42:
* La potencia más grande que cabe en 42 es **32** ($2^5$). Nos sobran 10.
* La siguiente que cabe en 10 es **8** ($2^3$). Nos sobran 2.
* La siguiente que cabe en 2 es **2** ($2^1$). Nos sobra 0.

Si ordenamos las posiciones (32, 16, 8, 4, 2, 1):
* 32: `1`
* 16: `0`
* 8: `1`
* 4: `0`
* 2: `1`
* 1: `0`
Resultado: **101010**

### Método 3: Usando CyberChef
1. Entramos en CyberChef.
2. Buscamos la receta **"To Binary"**.
3. Ponemos `42` en el panel de entrada y configuramos el delimitador en "None" si hace falta. Nos devolverá `101010`.

---

## 5. Flag Obtenida
Tomamos nuestro valor binario limpio (sin el prefijo `0b`) y lo metemos dentro de la estructura de la bandera:

`picoCTF{101010}`

---

## 6. Notas para el Futuro
* La función `bin()` en Python es el equivalente a `hex()` y te salva mucho tiempo en los CTFs.
* Acuérdate siempre de limpiar los prefijos numéricos de programación (`0b` para binario, `0x` para hexadecimal, `0o` para octal) antes de enviar la flag a menos que el reto pida explícitamente lo contrario.