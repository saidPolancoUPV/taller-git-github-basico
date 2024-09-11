# Sesión 03: Flujo de trabajo en Git y comandos esenciales

Git es una poderosa herramienta de control de versiones que te permite llevar un registro de los cambios en tus proyectos, facilitando la colaboración y la recuperación de versiones anteriores de tu código. En este tutorial, aprenderás sobre el flujo de trabajo básico de Git y cómo utilizar algunos de los comandos más importantes para trabajar con tus archivos y commits.

## Flujo de trabajo básico de Git

El flujo de trabajo de Git puede dividirse en tres pasos principales:

  1. **Modificación de archivos**: Trabajas en tus archivos de proyecto, creando, modificando o eliminando contenido.
  2. **Preparación de los cambios (staging)**: Usas el comando `git add` para agregar los archivos modificados al área de preparación (staging), lo que indica a Git que deseas incluir esos cambios en el próximo commit.
  3. **Commit de los cambios**: Usas el comando `git commit` para guardar los cambios en el historial de Git. Un commit es una "foto" del estado de tu proyecto en ese momento.

A lo largo de este flujo, usarás comandos como `git add`, `git commit`, `git rm --cached`, `git reset`, y `git restore --staged`. A continuación, se explica cada uno en detalle.

---

## Comando `git add`: Añadir archivos al área de preparación (staging)

Cuando modificas o creas un archivo en tu proyecto, Git no lo rastrea automáticamente para el siguiente commit. Necesitas usar `git add` para decirle a Git qué archivos quieres incluir en el próximo commit.

Una vez que hayas realizado cambios en tu área de trabajo, verificaremos el estado del repositorio:

```bash
$ git status
```

Luego, agregamos al área de preparación (staging) los archivos que queremos con seguimiento, es decir, aquellos que queremos se guarden en el historial del proyecto.

```bash
$ git add <archivo>
```

_Opcional_: puedes utilizar el comando `git add .` para agregar todos los cambios pendientes al staging.

### Ejemplo:

Imagina que has creado un archivo llamado `index.html` en tu proyecto. Para añadirlo al área de preparación, debes ejecutar:

```bash
$ git add index.html
```

Si has modificado varios archivos y quieres añadir todos al área de preparación, puedes usar:

```bash
$ git add .
```

_Nota_: El `.` significa "todos los archivos modificados o nuevos". Este comando añade todos los archivos en la carpeta actual y subcarpetas al área de preparación.

---

## Comando `git commit`: Guardar los cambios en el historial

Una vez que los archivos están en el área de preparación, necesitas "guardar" esos cambios en el historial de tu proyecto. Esto se hace con git commit. Un commit en Git es como un "punto de restauración", donde puedes registrar un estado específico de tu proyecto.

```bash
$ git commit -m "Mensaje descriptivo del cambio"
```

### Ejemplo:

Si has hecho cambios en varios archivos y los has añadido al área de preparación, puedes hacer un commit con un mensaje claro que describa esos cambios:

```bash
$ git commit -m "Añadí la página de inicio y modifiqué el archivo de estilos"
```

El mensaje debe ser descriptivo para que puedas entender fácilmente qué se ha cambiado al revisar el historial del proyecto.

_Nota_: Si olvidas añadir el `-m` y el mensaje entre comillas, Git abrirá el editor de texto predeterminado para que escribas el mensaje.

---

## Comando `git rm --cached`: Eliminar archivos del área de preparación (staging)

Si decides que no quieres que un archivo que ya has añadido al área de preparación forme parte del próximo commit, puedes eliminarlo de esa área usando `git rm --cached`. Este comando no elimina el archivo del proyecto, solo lo quita del área de preparación.

```bash
$ git rm --cached <archivo>
```

### Ejemplo:
Si has añadido por error el archivo `notas.txt` al área de preparación pero no quieres incluirlo en el commit, puedes ejecutar:

```bash
$ git rm --cached notas.txt
```

Esto eliminará el archivo del área de preparación, pero el archivo seguirá existiendo en tu carpeta de proyecto.

---

## Comando `git reset`: Deshacer cambios en el área de preparación

Si has añadido archivos al área de preparación pero te das cuenta de que no deberías haberlo hecho, puedes "resetear" o deshacer esos cambios con git reset.

```bash
$ git reset <archivo>
```

### Ejemplo:

Imagina que añadiste `style.css` al área de preparación por error. Para eliminarlo del área de preparación y revertir ese archivo a su estado anterior, puedes usar:

```bash
$ git reset style.css
```

Esto saca el archivo style.css del área de preparación y lo deja sin rastrear para el próximo commit, pero mantiene los cambios en tu directorio de trabajo.

---

## Comando `git restore --staged`: Retirar archivos del área de preparación sin perder los cambios

Si has añadido un archivo al área de preparación con git add y te das cuenta de que aún no quieres que forme parte del commit, pero tampoco quieres perder las modificaciones, puedes usar git restore --staged.

```bash
$ git restore --staged <archivo>
```

### Ejemplo:
Has añadido `app.js` al área de preparación pero decides que aún no quieres hacer commit de los cambios:

```bash
$ git restore --staged app.js
```

Esto quita el archivo del área de preparación sin borrar los cambios hechos en el archivo. Sigue existiendo en tu directorio de trabajo, con las modificaciones intactas, pero no será incluido en el commit.

---

## Resumen del glujo completo de trabajo en Git

A continuación, se resume el flujo completo de trabajo usando los comandos aprendidos:

  1. **Modificación**: Haces cambios en los archivos del proyecto.
  2. **Preparación (staging)**: Añades los archivos modificados al área de preparación usando `git add`.
  3. **Revisión del estado**: Puedes usar `git status` para ver qué archivos han sido modificados y cuáles están en el área de preparación.
  4. **Corrección**: Si cometiste un error, puedes usar git rm --cached, git reset, o git restore --staged para ajustar los archivos en el área de preparación.
  5. **Guradado del historial**: Realizas un commit con `git commit -m "Descripción del cambio"`.

---

## Resumen de los comandos

  * `git add <archivo>`: Añade un archivo al área de preparación.
  * `git commit -m "mensaje"`: Crea un commit con los cambios añadidos al área de preparación.
  * `git rm --cached <archivo>`: Quita un archivo del área de preparación sin eliminarlo del proyecto.
  * `git reset <archivo>`: Retira un archivo del área de preparación, pero mantiene los cambios en el directorio de trabajo.
  * `git restore --staged <archivo>`: Saca un archivo del área de preparación sin perder los cambios hechos en el archivo.
