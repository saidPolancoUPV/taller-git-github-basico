# Sesión 05: Uso del comando `git diff` en Git

En esta sesión, aprenderás a usar el comando `git diff` para comparar cambios en los archivos de un repositorio Git. Explicaremos qué hace este comando, cómo interpretarlo y proporcionaremos un ejemplo práctico para que puedas verlo en acción.

## ¿Qué es `git diff`?

El comando `git diff` es una herramienta en Git que te permite ver las diferencias entre las versiones de tus archivos. Es especialmente útil para:

  * Comparar los cambios no guardados (no "commiteados").
  * Ver las diferencias entre commits específicos.
  * Revisar las diferencias antes de preparar y hacer commit de tus cambios.

## 1. Preparativos iniciales

Antes de poder usar `git diff`, asegúrate de tener Git instalado en tu computadora y de estar dentro de un repositorio de Git. Si no tienes uno, puedes crear uno con los siguientes comandos:

  1. **Crea una carpeta para el proyecto**:
```bash
$ mkdir mi_proyecto
$ cd mi_proyecto
```

  2. **Inicializa Git en la carpeta**:
```bash
$ git init
```

  3. **Crea un archivo inicial**:
```bash
$ echo "Hello, Git!" > archivo.txt
```

  4. **Haz un commit inicial**:
```bash
$ git add archivo.txt
$ git commit -m "Primer commit"
```

Con esto, ya tienes un repositorio de Git listo para trabajar.

---

## 2. Realiza algunos cambios

Para usar el comando `git diff`, primero necesitas realizar cambios en los archivos de tu proyecto. Vamos a modificar el archivo `archivo.txt` que creaste anteriormente:

  1. Abre el archivo `archivo.txt` y cambia su contenido. Por ejemplo, reemplaza el texto con lo siguiente:
```bash
echo "Hello, Git!" > archivo.txt
echo "Este es un cambio en el archivo" >> archivo.txt
```

Ahora, `archivo.txt` contiene una línea adicional.

---

## 3. Usa el comando `git diff`

Una vez que hayas hecho cambios en tus archivos, puedes usar `git diff` para ver cuáles son esas modificaciones antes de hacer un commit.


```bash
$ git diff
```

Este comando te mostrará las diferencias entre el archivo que has modificado y la versión más reciente que fue guardada (commit previo). En nuestro caso, te mostrará que has agregado una línea nueva.

  > _salida_:
  >
  > ```bash
  > diff --git a/archivo.txt b/archivo.txt
  > index e69de29..7d77a84 100644
  > --- a/archivo.txt
  > +++ b/archivo.txt
  > @@ -1 +1,2 @@
  > Hello, Git!
  > +Este es un cambio en el archivo```

### ¿Cómo leer la salida de git diff?

  * `--- a/archivo.txt`: Indica el archivo en su versión anterior.
  * `+++ b/archivo.txt`: Indica el archivo en su versión actual, después de los cambios.
  * `+` Este es un cambio en el archivo: Las líneas que empiezan con un signo + representan las líneas que has agregado.

  ## 4. Comparar archivos que han sido preparados para commit

Si ya has añadido los archivos al área de preparación con git add, pero aún no has hecho un commit, puedes usar `git diff --staged` para ver los cambios preparados.

```bash
$ git add archivo.txt
$ git diff --staged
```

`git diff --staged`: Te muestra las diferencias entre la versión del archivo que ha sido añadido al área de preparación (staging area) y la última versión committeada.

Este comando es útil para verificar los cambios antes de hacer el commit final.

## 5. Comparar cambios entre dos commits

También puedes usar `git diff` para comparar dos versiones anteriores de tu proyecto, conocidas como commits.

```bash
$ git diff <commit1> <commit2>
```

## Ejemplo

```bash
$ git log
commit 2c1d4e0ae1c5 (HEAD -> main) Add line to archivo.txt
commit d1b5c5ef9b78 Initial commit

$ git diff d1b5c5ef9b78 2c1d4e0ae1c5
```

Este comando muestra las diferencias entre el commit inicial (`d1b5c5ef9b78`) y el commit donde agregaste la línea nueva (`2c1d4e0ae1c5`). Esto es útil para revisar el historial de cambios entre dos puntos específicos.

## 6. Otros usos de `git diff`

  * **Comparar un archivo específico**: Si solo quieres ver las diferencias en un archivo en particular, puedes especificar el nombre del archivo al final del comando:

```bash
$ git diff archivo.txt
```

Ver diferencias en palabras (no líneas): Si prefieres ver diferencias a nivel de palabras individuales en lugar de líneas completas, usa la opción `--word-diff`:

```bash
$ git diff --word-diff
```

---

## Ejemplo práctico completo
  1. Crea un archivo:
```bash
$ echo "Hello, Git!" > archivo.txt
```

  2. Haz el primer commit:
```bash
$ git add archivo.txt
$ git commit -m "Primer commit"
```

  3. Modifica el archivo:
```bash
$ echo "Este es un cambio en el archivo" >> archivo.txt
```

  4. Usa git diff para ver los cambios:
```bash
$ git diff
```

  5. Añade el archivo al área de preparación:
```bash
$ git add archivo.txt
```

  6. Usa git diff --staged para ver los cambios preparados:
```bash
$ git diff --staged
```

  7. Haz un commit de los cambios:
```bash
$ git commit -m "Añadí una línea al archivo.txt"
```


  ## Resumen

El comando `git diff` es una herramienta poderosa que te permite ver las diferencias entre versiones de archivos en tu repositorio Git. Con este comando, puedes:

  * Revisar los cambios antes de hacer un commit.
  * Ver qué cambios se han añadido al área de preparación.
  * Comparar versiones anteriores del proyecto.

Este flujo de trabajo te ayuda a controlar y entender exactamente qué ha cambiado en tu proyecto en cualquier momento.

