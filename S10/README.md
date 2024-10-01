# Sesión 10: Creación y uso de `.gitignore` en Git

El archivo `.gitignore` es una herramienta fundamental en Git que permite **evitar que ciertos archivos sean incluidos en el repositorio**. Este archivo define qué archivos o carpetas no deben ser rastreados ni subidos al repositorio, lo cual es útil para:

  * Evitar que archivos grandes o innecesarios se suban al repositorio.
  * Proteger archivos sensibles, como contraseñas o configuraciones locales.
  * Ignorar archivos generados automáticamente que no deben compartirse con otros colaboradores.

En esta sesión, aprenderás cómo crear y usar un archivo `.gitignore`, además de ver un ejemplo práctico para entender su utilidad.

---

## 1.- Crear un archivo `.gitignore`

El archivo `.gitignore` es un archivo de texto que debe estar ubicado en la raíz de tu repositorio Git. Puedes crearlo fácilmente desde la terminal:

```bash
$ touch .gitignore
```

Una vez creado, puedes abrirlo con cualquier editor de texto (por ejemplo, nano, vim o un editor gráfico) y empezar a agregar patrones de archivos o directorios que quieres que Git ignore.

---

## 2.- Añadir patrones de archivos y carpetas

Dentro del archivo `.gitignore`, puedes especificar los archivos o carpetas que deseas que Git ignore usando patrones simples. Aquí tienes algunos ejemplos comunes:

  * **Ignorar un archivo específico**: Si quieres ignorar un archivo en particular, simplemente pon su nombre en el `.gitignore`:
     > ```plaintext
     > config.php
     > ```

  * **Ignorar todos los archivos de un tipo**: Si quieres ignorar todos los archivos de un cierto tipo, puedes usar un comodín (`*`):
     > ```plaintext
     > *.log   # Ignora todos los archivos .log
     > *.tmp   # Ignora todos los archivos temporales .tmp
     > ```

  * **Ignorar una carpeta completa**: Para ignorar una carpeta completa, usa una barra (/) antes del nombre de la carpeta:
     > ```plaintext
     > /node_modules/  # Ignora la carpeta node_modules
     > ```

  * **Ignorar archivos o carpetas ocultos**: Si quieres ignorar todos los archivos o carpetas ocultos (aquellos que comienzan con un punto), usa el siguiente patrón:
     > ```plaintext
     > .*
     > ```

  * **Ignorar archivos dentro de una subcarpeta específica**: Si quieres ignorar archivos solo dentro de una carpeta específica, puedes usar la ruta relativa:
     > ```plaintext
     > /build/*.js  # Ignora todos los archivos .js dentro de la carpeta build
     > ```

---

## Importancia de usar `.gitignore`

El archivo `.gitignore` es esencial en el desarrollo colaborativo porque evita que se suban archivos que no son necesarios o que podrían causar problemas en el repositorio, como:

  * **Archivos de configuración local**: Cada desarrollador puede tener su propia configuración local, y subir estos archivos podría sobreescribir las configuraciones de otros.
  * **Archivos generados automáticamente**: Archivos como los creados en procesos de compilación o los instalados por gestores de paquetes (como node_modules/ o build/) no necesitan estar en el repositorio porque se pueden regenerar fácilmente.
  * **Archivos grandes o temporales**: Subir archivos grandes o temporales puede aumentar innecesariamente el tamaño del repositorio y hacer más lenta la clonación o descarga.

---

## Ejemplo práctico de uso de `.gitignore`

Supongamos que estás trabajando en un proyecto donde tienes algunos archivos de configuración locales que no deben ser compartidos con el equipo, y también una carpeta que contiene archivos generados automáticamente. En este ejemplo, vamos a:

  1. Ignorar el archivo `config.local.json` que contiene configuraciones locales.
  2. Ignorar la carpeta `build/` que contiene archivos generados.
  3. Ignorar todos los archivos de tipo `.log`.


### Paso 1: Crear el proyecto y agregar un `.gitignore`

Primero, crea un nuevo proyecto y añade un archivo `.gitignore`:

```bash
$ mkdir mi-proyecto-gitignore
$ cd mi-proyecto-gitignore
$ git init
$ touch .gitignore
```

### Paso 2: Configurar el archivo `.gitignore`

Edita el archivo `.gitignore` y añade las siguientes reglas:

```plaintext
# Ignorar archivo de configuración local
config.local.json

# Ignorar la carpeta build con archivos generados
/build/

# Ignorar todos los archivos .log
*.log
```

Guarda el archivo y verifica su contenido:

```bash
$ cat .gitignore
config.local.json
/build/
*.log
```

### Paso 3: Agregar archivos y carpetas al proyecto

Ahora, vamos a agregar algunos archivos al proyecto para probar nuestro `.gitignore`:

```bash
$ touch config.local.json
$ mkdir build
$ touch build/output.js
$ touch app.log
$ touch main.js
```

### Paso 4: Verificar qué archivos están siendo ignorados

Para verificar que Git está ignorando correctamente los archivos especificados en `.gitignore`, puedes usar el comando `git status`:

```bash
$ git status
# On branch main
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       .gitignore
#       main.js
#
nothing added to commit but untracked files present
```

Como puedes ver, los archivos `config.local.json`, la carpeta _build/_ y los archivos _.log_ no aparecen en el listado de git status, porque Git los está ignorando según las reglas en el archivo `.gitignore`.

### Paso 5: Agregar y confirmar los archivos rastreados

Puedes proceder a agregar y confirmar los archivos que no están siendo ignorados (como `main.js` y `.gitignore`):

```bash
$ git add .gitignore main.js
$ git commit -m "Añadir archivo .gitignore y main.js"
```

---

## Resumen de comandos útiles para `.gitignore`

  * **git status**: Verifica los archivos que están siendo rastreados y los que no, según las reglas del `.gitignore`.
  * **git add**: Añade archivos rastreados para confirmarlos.
  * **git commit -m "mensaje"**: Confirma los cambios en los archivos rastreados.
  * **cat .gitignore**: Muestra el contenido del archivo `.gitignore`.
