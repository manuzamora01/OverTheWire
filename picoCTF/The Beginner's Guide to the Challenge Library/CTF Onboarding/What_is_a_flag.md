# Introducción a los retos CTF (Capture The Flag)

## ¿Qué es una Flag (Bandera)?
Una **Flag** es una cadena de texto (*string*) oculta dentro de un reto que sirve como **prueba absoluta** de que lo has resuelto correctamente. Al introducir esta cadena en la interfaz del reto, la plataforma valida tu respuesta y te otorga los puntos correspondientes.

---

## Formato Estándar de las Flags
Para evitar confusiones y saber exactamente cuándo has encontrado la solución real, las banderas siguen un formato común y predecible:

> ### `picoCTF{...}`

### Características principales:
* **Estructura:** Comienzan siempre con la palabra clave `picoCTF` seguida de la solución encerrada entre llaves `{}`.
* **Contenido Interno:** Casi todas las banderas tienen un aspecto similar a:  
  `picoCTF{l33tsp34k_phr4s3_1234abcd}`
* **Uso de Leet Speak:** El texto de dentro suele utilizar *"Leet Speak"* (un "lenguaje" clásico en informática que sustituye determinadas letras por números, como la `e` por el `3`, la `a` por el `4`, o la `o` por el `0`).
* **Temática:** A menudo, la frase oculta hace alusión a la vulnerabilidad explotada o a la temática del propio ejercicio.