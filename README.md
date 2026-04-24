# Comandos UNIX — Guía de Referencia

> Una referencia rápida y organizada de los comandos esenciales de UNIX.

---

## Gestión de archivos y directorios

| Comando | Descripción |
|---------|-------------|
| `ls` | Lista los nombres de los archivos en el directorio actual. Admite opciones como `-l` para información detallada (permisos, propietario, tamaño, fecha) o `-t` para ordenar por fecha de última modificación. |
| `cp` | Copia un archivo a otro (por ejemplo, `cp archivo1 archivo2`). Sobrescribe el archivo de destino de manera silenciosa si este ya existe. |
| `mv` | Mueve o renombra un archivo sin alterar su contenido. |
| `rm` | Elimina (borra) archivos de forma irrevocable. |
| `pwd` | Imprime en pantalla el "directorio de trabajo" (*print working directory*), indicando la ruta del directorio en el que te encuentras actualmente. |
| `cd` | Cambia tu directorio actual de trabajo al especificado en el argumento. |
| `mkdir` | Crea un nuevo directorio. |
| `rmdir` | Elimina un directorio, pero solo funciona si este se encuentra completamente vacío. |

---

## Visualización y edición de archivos

| Comando | Descripción |
|---------|-------------|
| `cat` | Imprime el contenido completo de uno o varios archivos directamente en la terminal. |
| `ed` | Editor de texto estándar utilizado para crear, escribir y modificar el contenido de los archivos. |
| `pr` | Prepara archivos para su impresión, añadiendo encabezados y paginación (típicamente de 66 líneas por página), y permite organizar la salida en columnas. |
| `tail` | Imprime la parte final de un archivo. Por defecto, muestra las últimas 10 líneas. |

---

## Procesamiento de texto y comparación

| Comando | Descripción |
|---------|-------------|
| `wc` | Cuenta y muestra el número de líneas, palabras y caracteres presentes en uno o varios archivos. |
| `grep` | Busca dentro de los archivos e imprime únicamente las líneas que coinciden con un patrón, palabra o expresión regular específica. |
| `sort` | Ordena el contenido de los archivos línea por línea. Por defecto lo hace en orden alfabético, aunque admite opciones para orden numérico o inverso. |
| `cmp` | Compara dos archivos e indica la ubicación exacta (número de carácter y de línea) de la primera diferencia que encuentra. |
| `diff` | Realiza una comparación más detallada que `cmp`, reportando todas las líneas que difieren (añadidas, cambiadas o eliminadas) entre dos archivos de texto. |

---

## Información del sistema y comunicación

| Comando | Descripción |
|---------|-------------|
| `who` | Muestra una lista de los usuarios conectados actualmente al sistema, incluyendo la terminal que usan y la hora de ingreso. |
| `date` | Muestra la fecha y la hora actuales del sistema. |
| `man` | Muestra las páginas del manual de UNIX. Permite consultar el funcionamiento, opciones y detalles de cualquier otro comando. |
| `echo` | Imprime en pantalla exactamente los argumentos que se le pasen; útil para comprobar cómo la terminal interpreta comodines o abreviaturas de archivos. |
| `mail` | Permite enviar mensajes a otros usuarios del sistema o leer los correos recibidos. |
| `write` | Establece una conexión bidireccional que imprime lo que escribes directamente en la terminal de otro usuario en tiempo real. |

---

*Referencia basada en los comandos estándar de UNIX.*
