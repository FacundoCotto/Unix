# Comandos UNIX — Guía de Referencia

> Una referencia rápida y organizada de los comandos esenciales de UNIX, con ejemplos cotidianos y explicaciones paso a paso.

---

## Gestión de archivos y directorios

---

### `ls` — Listar archivos

Lista los nombres de los archivos en el directorio actual. Admite opciones como `-l` para información detallada (permisos, propietario, tamaño, fecha) o `-t` para ordenar por fecha de última modificación.

**Ejemplo:**

```
ls -l
```

**Paso a paso:**

1. `ls` recorre el directorio actual.
2. `-l` le indica que muestre el resultado en formato largo.
3. Para cada archivo verás: permisos, propietario, tamaño en bytes y fecha de última modificación.

```
-rw-r--r-- 1 facundo 1024 Apr 24 10:00 notas.txt
-rwxr-xr-x 1 facundo 4096 Apr 23 09:15 script.sh
```

---

### `cp` — Copiar archivos

Copia un archivo a otro. Sobrescribe el archivo de destino de manera silenciosa si este ya existe.

**Ejemplo:**

```
cp notas.txt notas_backup.txt
```

**Paso a paso:**

1. `cp` toma el primer argumento (`notas.txt`) como origen.
2. El segundo argumento (`notas_backup.txt`) es el destino.
3. Si `notas_backup.txt` ya existía, lo sobreescribe sin avisar.
4. El archivo original `notas.txt` queda intacto.

---

### `mv` — Mover o renombrar archivos

Mueve o renombra un archivo sin alterar su contenido.

**Ejemplo — Renombrar:**

```
mv notas.txt apuntes.txt
```

**Ejemplo — Mover a otro directorio:**

```
mv apuntes.txt documentos/apuntes.txt
```

**Paso a paso:**

1. `mv` toma el primer argumento como origen.
2. Si el destino es un nombre distinto en el mismo directorio, lo renombra.
3. Si el destino es otro directorio, lo mueve allí.
4. El archivo original desaparece de su ubicación anterior.

---

### `rm` — Eliminar archivos

Elimina archivos de forma irrevocable (no van a la papelera).

**Ejemplo:**

```
rm borrador.txt
```

**Paso a paso:**

1. `rm` busca el archivo `borrador.txt` en el directorio actual.
2. Lo elimina permanentemente del sistema de archivos.
3. No hay confirmación ni papelera de reciclaje: el archivo se pierde para siempre.

> **Precaución:** Usar con cuidado. No hay forma de recuperar el archivo eliminado.

---

### `pwd` — Directorio actual

Imprime en pantalla el "directorio de trabajo" (_print working directory_), indicando la ruta completa donde te encontrás.

**Ejemplo:**

```
pwd
```

**Paso a paso:**

1. `pwd` consulta al sistema en qué directorio está posicionado el shell.
2. Imprime la ruta absoluta completa.

```
/home/facundo/documentos
```

---

### `cd` — Cambiar de directorio

Cambia tu directorio actual de trabajo al especificado en el argumento.

**Ejemplo:**

```
cd documentos
```

**Paso a paso:**

1. `cd` recibe el nombre del directorio al que querés ir.
2. El shell se posiciona dentro de ese directorio.
3. Podés verificar el cambio con `pwd`.

**Variantes útiles:**

```
cd ..        # Sube un nivel al directorio padre
cd ~         # Va al directorio home del usuario
cd /         # Va a la raíz del sistema
```

---

### `mkdir` — Crear un directorio

Crea un nuevo directorio vacío.

**Ejemplo:**

```
mkdir proyectos
```

**Paso a paso:**

1. `mkdir` recibe el nombre del directorio a crear.
2. Crea la carpeta `proyectos` en el directorio actual.
3. Podés verificarlo con `ls`.

---

### `rmdir` — Eliminar un directorio vacío

Elimina un directorio, pero solo si está completamente vacío.

**Ejemplo:**

```
rmdir proyectos
```

**Paso a paso:**

1. `rmdir` intenta eliminar el directorio `proyectos`.
2. Si el directorio tiene archivos adentro, el comando falla con un error.
3. Si está vacío, lo elimina sin confirmación.

---

## Visualización y edición de archivos

---

### `cat` — Ver contenido de un archivo

Imprime el contenido completo de uno o varios archivos directamente en la terminal.

**Ejemplo:**

```
cat notas.txt
```

**Paso a paso:**

1. `cat` abre el archivo `notas.txt`.
2. Imprime cada línea en la terminal de arriba hacia abajo.
3. Al terminar, devuelve el control al shell.

**Ejemplo con varios archivos:**

```
cat parte1.txt parte2.txt
```

Imprime primero el contenido de `parte1.txt` y luego el de `parte2.txt`, uno tras otro.

---

### `ed` — Editor de texto estándar

Editor de texto de línea de comandos para crear, escribir y modificar archivos.

**Ejemplo completo — Crear y escribir un archivo:**

```
ed hola.txt
```

**Paso a paso:**

1. `ed hola.txt` abre (o crea) el archivo `hola.txt`. El editor no muestra nada visible.
2. Escribís `a` y presionás Enter → activa el modo **append** (agregar texto al final).
3. Escribís el texto que quieras, línea por línea:
   ```
   Hola mundo
   Esta es la segunda linea
   ```
4. Escribís `.` (un punto solo) y presionás Enter → salís del modo append.
5. Escribís `w` y presionás Enter → **guarda** el archivo.
6. Escribís `q` y presionás Enter → **salís** del editor.

**Otros comandos útiles dentro de `ed`:**
| Comando | Acción |
|---------|--------|
| `a` | Append: agregar texto después de la línea actual |
| `i` | Insert: insertar texto antes de la línea actual |
| `d` | Delete: eliminar la línea actual |
| `p` | Print: imprimir la línea actual |
| `1,$ p` | Imprimir todo el archivo |
| `w` | Guardar el archivo |
| `q` | Salir del editor |

---

### `pr` — Preparar archivos para imprimir

Prepara archivos para su impresión, añadiendo encabezados y paginación (típicamente de 66 líneas por página), y permite organizar la salida en columnas.

**Ejemplo:**

```
pr notas.txt
```

**Paso a paso:**

1. `pr` lee el archivo `notas.txt`.
2. Agrega un encabezado automático con el nombre del archivo, fecha y número de página.
3. Divide el contenido en páginas de 66 líneas.
4. Imprime el resultado formateado en la terminal (listo para enviar a una impresora).

---

### `tail` — Ver el final de un archivo

Imprime la parte final de un archivo. Por defecto, muestra las últimas 10 líneas.

**Ejemplo:**

```
tail errores.log
```

**Paso a paso:**

1. `tail` abre el archivo `errores.log`.
2. Cuenta las líneas desde el final.
3. Muestra las últimas 10 líneas en la terminal.

**Ver más líneas:**

```
tail -n 20 errores.log
```

Muestra las últimas 20 líneas en lugar de 10.

---

## Procesamiento de texto y comparación

---

### `wc` — Contar palabras, líneas y caracteres

Cuenta y muestra el número de líneas, palabras y caracteres presentes en uno o varios archivos.

**Ejemplo:**

```
wc notas.txt
```

**Paso a paso:**

1. `wc` lee el archivo `notas.txt` completo.
2. Cuenta cuántas líneas tiene (cada salto de línea es una línea).
3. Cuenta cuántas palabras hay (separadas por espacios).
4. Cuenta cuántos caracteres en total.
5. Muestra los tres valores juntos:

```
  12   48  312 notas.txt
```

Significa: 12 líneas, 48 palabras, 312 caracteres.

---

### `grep` — Buscar texto en archivos

Busca dentro de los archivos e imprime únicamente las líneas que coinciden con un patrón o palabra específica.

**Ejemplo:**

```
grep "error" sistema.log
```

**Paso a paso:**

1. `grep` abre el archivo `sistema.log`.
2. Recorre el archivo línea por línea.
3. Compara cada línea con el patrón `"error"`.
4. Imprime solo las líneas que contienen esa palabra.

```
Apr 24 08:12: error al conectar con la base de datos
Apr 24 09:45: error de autenticación en usuario juan
```

---

### `sort` — Ordenar líneas de un archivo

Ordena el contenido de los archivos línea por línea. Por defecto en orden alfabético.

**Ejemplo:**

```
sort nombres.txt
```

**Paso a paso:**

1. `sort` lee todas las líneas del archivo `nombres.txt`.
2. Las ordena alfabéticamente de la A a la Z.
3. Imprime el resultado en la terminal (no modifica el archivo original).

**Variantes útiles:**

```
sort -r nombres.txt    # Orden inverso (Z a A)
sort -n numeros.txt    # Orden numérico
```

---

### `cmp` — Comparar dos archivos (primera diferencia)

Compara dos archivos e indica la ubicación exacta de la primera diferencia encontrada.

**Ejemplo:**

```
cmp version1.txt version2.txt
```

**Paso a paso:**

1. `cmp` lee ambos archivos al mismo tiempo, byte a byte.
2. En cuanto encuentra la primera diferencia, la reporta indicando el número de byte y de línea.
3. Si los archivos son idénticos, no imprime nada y termina.

```
version1.txt version2.txt differ: char 45, line 3
```

---

### `diff` — Comparar dos archivos (todas las diferencias)

Realiza una comparación más detallada que `cmp`, reportando todas las líneas que difieren entre dos archivos.

**Ejemplo:**

```
diff original.txt modificado.txt
```

**Paso a paso:**

1. `diff` compara ambos archivos línea por línea.
2. Para cada diferencia encontrada, indica:
   - Las líneas eliminadas con `<`
   - Las líneas agregadas con `>`
3. Muestra el resultado completo, no solo la primera diferencia.

```
3c3
< Hola mundo
---
> Hola UNIX
```

Significa: en la línea 3, `"Hola mundo"` fue reemplazado por `"Hola UNIX"`.

---

## Información del sistema y comunicación

---

### `who` — Ver usuarios conectados

Muestra una lista de los usuarios que están conectados actualmente al sistema.

**Ejemplo:**

```
who
```

**Paso a paso:**

1. `who` consulta la tabla de sesiones activas del sistema.
2. Para cada usuario conectado muestra: nombre de usuario, terminal que usa y hora de ingreso.

```
facundo  tty1   Apr 24 09:00
juan     tty2   Apr 24 09:35
```

---

### `date` — Ver fecha y hora del sistema

Muestra la fecha y la hora actuales del sistema.

**Ejemplo:**

```
date
```

**Paso a paso:**

1. `date` consulta el reloj interno del sistema operativo.
2. Imprime la fecha y hora en formato estándar.

```
Thu Apr 24 10:30:00 ART 2026
```

---

### `man` — Manual de comandos

Muestra las páginas del manual de UNIX para cualquier comando.

**Ejemplo:**

```
man ls
```

**Paso a paso:**

1. `man` recibe el nombre del comando como argumento (`ls`).
2. Busca la página del manual correspondiente.
3. La abre en un visor de texto donde podés desplazarte con las flechas.
4. Presionás `q` para salir del manual y volver al shell.

El manual muestra: descripción del comando, todas sus opciones, ejemplos y notas de uso.

---

### `echo` — Imprimir texto en la terminal

Imprime en pantalla exactamente los argumentos que se le pasen.

**Ejemplo:**

```
echo "Hola, bienvenido a UNIX"
```

**Paso a paso:**

1. `echo` recibe el texto entre comillas.
2. Lo imprime directamente en la terminal tal como está escrito.
3. Muy útil para ver cómo el shell interpreta variables o comodines:

```
echo $HOME
```

```
/home/facundo
```

---

### `mail` — Enviar y leer correos entre usuarios

Permite enviar mensajes a otros usuarios del sistema o leer los correos recibidos.

**Ejemplo — Enviar un mensaje:**

```
mail juan
```

**Paso a paso:**

1. `mail juan` inicia la redacción de un mensaje para el usuario `juan`.
2. El sistema pide el asunto (`Subject:`), lo escribís y presionás Enter.
3. Escribís el cuerpo del mensaje línea por línea.
4. Para terminar y enviar, presionás `.` (punto) o `Ctrl+D` en una línea nueva.
5. El mensaje llega al buzón del usuario `juan`.

**Ejemplo — Leer correos recibidos:**

```
mail
```

Muestra la lista de mensajes en tu buzón y te permite leerlos uno por uno.

---

### `write` — Enviar mensajes en tiempo real

Establece una conexión bidireccional que imprime lo que escribís directamente en la terminal de otro usuario.

**Ejemplo:**

```
write juan
```

**Paso a paso:**

1. `write juan` establece la conexión con la terminal del usuario `juan`.
2. En la terminal de `juan` aparece un aviso: `Message from facundo`.
3. Todo lo que escribís y confirmás con Enter aparece instantáneamente en la pantalla de `juan`.
4. Para terminar la sesión, presionás `Ctrl+D`.
5. `juan` puede responder ejecutando `write facundo` en su propia terminal.

---

_Referencia basada en los comandos estándar de UNIX._
