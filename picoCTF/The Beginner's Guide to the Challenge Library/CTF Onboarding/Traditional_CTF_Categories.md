## Categorías Tradicionales en CTFs

Los retos de Capture-The-Flag se dividen en diferentes disciplinas según el tipo de vulnerabilidad o la tecnología que se analice. A continuación se detallan las seis categorías principales ordenadas por su naturaleza y curva de aprendizaje:

| Categoría | Descripción Breve | Nivel General |
| :--- | :--- | :--- |
| **General Skills** | Uso de la terminal, comandos esenciales y bases. | Inicial / Accesible |
| **Cryptography** | Cifrados, códigos, romper implementaciones de algoritmos. | Variable (Básico a Avanzado) |
| **Forensics** | Análisis de archivos, metadatos, redes y artefactos digitales. | Variable |
| **Web Exploitation** | Vulnerabilidades en aplicaciones web y servidores. | Moderado a Avanzado |
| **Reverse Engineering**| Destripar programas compilados o scripts para ver cómo funcionan. | Moderado a Avanzado |
| **Binary Exploitation**| Explotación de fallos de memoria (pila, desbordamientos). | Avanzado / El más complejo |

---

### 🛠️ General Skills (Habilidades Generales)
* **En qué consiste:** Retos diseñados para ganar soltura con las herramientas y conceptos esenciales del día a día en ciberseguridad. 
* **Conceptos clave:** Uso de la línea de comandos de Linux (`bash`), lectura de código fuente básico, navegación por sistemas de archivos y traducción de codificaciones comunes como Base64 o Hexadecimal.
* **Recomendación:** Es el punto de partida ideal si el resto de categorías resultan abrumadoras.

### 🔐 Cryptography (Criptografía)
* **En qué consiste:** Trabajar con datos codificados o cifrados que debes romper o descodificar.
* **Conceptos clave:** Identificación de patrones sencillos (Cifrado César, ROT13, Base64) en niveles iniciales, escalando hasta algoritmos criptográficos reales (RSA, AES) en los que debes explotar debilidades en su implementación matemática.

### 🔍 Forensics (Análisis Forense)
* **En qué consiste:** Investigar archivos individuales, imágenes de discos duros, capturas de tráfico de red (`.pcap`) o cualquier artefacto digital en busca de información oculta.
* **Conceptos clave:** Esteganografía (ocultar datos en imágenes o audios), filtrado de paquetes de red y recuperación de archivos borrados. Muchos retos introductorios son muy accesibles al principio.

### 🌐 Web Exploitation (Explotación Web)
* **En qué consiste:** Buscar y explotar vulnerabilidades en aplicaciones y servidores web.
* **Conceptos clave:** Inspección del código fuente de una página (HTML/JS), manipulación de cookies o parámetros HTTP en niveles básicos, avanzando hacia técnicas como Inyección SQL (SQLi), Cross-Site Scripting (XSS) o fallos de lógica en el lado del servidor.

### 🔄 Reverse Engineering (Ingeniería Inversa)
* **En qué consiste:** Analizar un programa ya compilado (o un script complejo) sin tener la documentación para averiguar exactamente qué hace, con el fin de descubrir qué entrada específica genera la bandera.
* **Conceptos clave:** Uso de desensambladores y depuradores (debuggers) para leer código ensamblador (Assembly) o rastrear el comportamiento del programa paso a paso. Tiene una curva de aprendizaje inicial pronunciada.

### 💥 Binary Exploitation (Explotación de Binarios / Pwn)
* **En qué consiste:** Explotar vulnerabilidades de seguridad de memoria en programas compilados para tomar el control del flujo de ejecución.
* **Conceptos clave:** Desbordamientos de búfer (*Buffer Overflows*), fallos en cadenas de formato (*Format String bugs*) o problemas de gestión de memoria (*Use-After-Free*). 
* **Nota técnica:** Es considerada la categoría más difícil de todas, ya que requiere dominar primero la ingeniería inversa para luego sumarle técnicas de explotación activa.