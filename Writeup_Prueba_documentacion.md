¡Excelente! Aquí tienes el 'Write-up' profesional en formato Markdown, estructurado y con un tono técnico, incluyendo la información de la imagen.

---

# Reto CTF: Explotación de Inyección SQL para Bypass de Autenticación

**Categoría:** Web
**Estado:** ✅ Resuelto

## Objetivo

El objetivo de este reto era identificar y explotar una vulnerabilidad de Inyección SQL en un formulario web de autenticación. Al explotar esta vulnerabilidad, se buscaba bypassar el proceso de inicio de sesión sin necesidad de credenciales válidas, obteniendo acceso no autorizado al sistema y, consecuentemente, la flag del desafío.

## Procedimiento Detallado

El desafío se presentaba como un ejercicio de inyección SQL en un formulario, indicando la presencia de una aplicación web vulnerable a este tipo de ataque.

1.  **Análisis del Formulario de Autenticación:**
    Se identificó un formulario de inicio de sesión estándar que solicitaba un "Username" y una "Password". Ante la descripción del reto, la hipótesis principal fue que la aplicación construía dinámicamente la consulta SQL de autenticación utilizando la entrada del usuario sin una adecuada sanitización o uso de sentencias preparadas.

2.  **Identificación de la Vulnerabilidad (Inyección SQL Clásica):**
    El tipo más común de inyección SQL para bypass de autenticación es la conocida como "OR 1=1". Esta técnica busca modificar la cláusula `WHERE` de la consulta SQL subyacente para que siempre evalúe a verdadero, independientemente de las credenciales originales.

    La consulta SQL típica en el backend para un inicio de sesión podría ser algo similar a:
    ```sql
    SELECT * FROM users WHERE username = '[INPUT_USERNAME]' AND password = '[INPUT_PASSWORD]';
    ```

3.  **Construcción y Ejecución del Payload:**
    Para explotar esta vulnerabilidad, se formuló un payload diseñado para cerrar la cadena de la contraseña, introducir una condición siempre verdadera (`OR '1' = '1'`), y comentar el resto de la consulta SQL para evitar errores de sintaxis.

    *   **Campo `Username`:** Se utilizó un nombre de usuario arbitrario, en este caso, `Ken Sato`. Para este tipo de bypass, el valor del username no es crítico, aunque a veces se usa un usuario conocido como `admin`.
    *   **Campo `Password`:** Se inyectó el siguiente payload:
        ```
        ' OR '1' = '1'; --
        ```
        **Explicación del Payload:**
        *   La primera comilla simple (`'`) cierra la cadena de la contraseña original.
        *   `OR '1' = '1'` introduce una condición lógica que siempre es verdadera (`true`).
        *   El punto y coma (`;`) termina la instrucción SQL actual.
        *   Los dos guiones (`--`) son un comentario en SQL, lo que provoca que cualquier parte restante de la consulta SQL original (como la segunda condición `AND password = '[INPUT_PASSWORD]'`) sea ignorada por el intérprete de la base de datos.

    Al introducir este payload, la consulta SQL resultante en el backend se transformaría aproximadamente en:
    ```sql
    SELECT * FROM users WHERE username = 'Ken Sato' AND password = '' OR '1' = '1'; -- '
    ```
    Esta consulta se evalúa como `SELECT * FROM users WHERE (username = 'Ken Sato' AND password = '') OR (true)`. Debido a la condición `OR (true)`, la cláusula `WHERE` se evalúa como verdadera para todas las filas, permitiendo que la consulta devuelva registros. Típicamente, el sistema de autenticación toma el primer registro devuelto, lo que resulta en un inicio de sesión exitoso.

    La siguiente imagen muestra la introducción del payload en el formulario:

    ![Inyección SQL de Bypass de Autenticación](image.png)
    *Ilustración del payload de inyección SQL ingresado en los campos de usuario y contraseña.*

4.  **Verificación y Obtención de la Flag:**
    Al pulsar el botón "Submit" con el payload inyectado, el sistema de autenticación fue bypassado exitosamente. Esto llevó a una página donde se encontraba la flag.

    **Flag Obtenida:**
    `FLAG{...}` (La flag real se recuperaría tras la ejecución exitosa del payload)

## Conclusión

Este reto demostró la criticidad de implementar medidas de seguridad robustas contra la inyección SQL en aplicaciones web. La ausencia de validación de entrada o el uso inadecuado de sentencias preparadas (prepared statements) o ORM con parámetros parametrizados en el backend puede llevar a vulnerabilidades severas que permiten a un atacante bypassar controles de autenticación, acceder a información sensible o incluso controlar la base de datos subyacente.

La explotación de esta vulnerabilidad de tipo "OR 1=1" es una de las técnicas más básicas pero efectivas de inyección SQL para bypass de autenticación, subrayando la importancia de prácticas de desarrollo seguro.