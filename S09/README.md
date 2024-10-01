# Sesión 09: Cómo usar el comando `git stash` en Git

El comando `git stash` es una herramienta poderosa que te permite **guardar cambios no confirmados temporalmente sin comprometerlos o perderlos**. Esto es útil cuando estás trabajando en algo y, por alguna razón, necesitas cambiar de rama o actualizar la base de código, pero no quieres perder o comprometer los cambios actuales.

En esta sesión, te mostraremos cómo funciona `git stash`, cuándo usarlo y te daremos un ejemplo práctico paso a paso.

## ¿Cuándo usar `git stash`?

Imagina que estás trabajando en un proyecto, haciendo cambios en tu código, pero aún no los has terminado. De repente, necesitas cambiar a otra rama para solucionar un problema urgente o actualizar tu código desde el repositorio remoto. Sin embargo, no quieres perder los cambios en los que has estado trabajando, ni hacer un commit parcial de algo incompleto.

Ahí es donde entra `git stash`. Te permite guardar esos cambios temporalmente y recuperarlos cuando estés listo.

---

## Paso a Paso: Uso de `git stash`

### 1.- Crear un entorno para trabajar

Primero, vamos a crear un nuevo proyecto de Git para experimentar con `git stash`. Supongamos que estás en la rama `main` trabajando en un archivo.

```bash
$ mkdir mi-proyecto
$ cd mi-proyecto
$ git init
$ touch archivo.txt
$ echo "Línea inicial en archivo.txt" > archivo.txt
$ git add archivo.txt
$ git commit -m "Añadir archivo.txt con línea inicial"
```
---

### 2.- Hacer cambios sin confirmarlos

Ahora, vamos a hacer algunos cambios en `archivo.txt` que no queremos perder, pero aún no queremos hacer un _commit_ porque el trabajo no está completo.

```bash
$ echo "Cambios temporales en el archivo.txt" >> archivo.txt
```

Si verificas el estado de tu repositorio, verás que el archivo ha sido modificado:

```bash
$ git status
# On branch main
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   archivo.txt
```

---

### 3.- Usar `git stash` para guardar los cambios temporalmente

Ahora imagina que necesitas cambiar a otra rama, pero no quieres hacer un commit de los cambios incompletos. Para guardarlos temporalmente, usa el comando `git stash`:

```bash
$ git stash
```

Esto guarda los cambios locales en un "stash" (un lugar temporal) y limpia tu directorio de trabajo. Si verificas el estado de nuevo, verás que tu directorio está limpio:

```bash
$ git status
# On branch main
nothing to commit, working tree clean
```

Tu archivo `archivo.txt` ahora está en su estado original (sin los cambios que habías hecho).

---

### 4.- Cambiar a otra rama

Ahora que tus cambios están guardados, puedes cambiar de rama sin perder los cambios. Por ejemplo, cambias a la rama _develop_ para trabajar en algo más:

```bash
$ git checkout -b develop
Switched to a new branch 'develop'
```

---

### 5.- Recuperar los cambios guardados con `git stash apply`

Una vez que hayas terminado tu trabajo en la otra rama, puedes volver a la rama original y recuperar tus cambios guardados:

```bash
$ git checkout main
$ git stash apply
```

Esto aplicará los cambios que habías guardado en el _stash_ de vuelta a tu directorio de trabajo. Si verificas el contenido de `archivo.txt`, verás que los cambios temporales han sido restaurados:

```bash
$ cat archivo.txt
Línea inicial en archivo.txt
Cambios temporales en el archivo.txt
```

---

### 6.-Confirmar los cambios restaurados

Ahora que has restaurado tus cambios temporales, puedes seguir trabajando en ellos o hacer un commit:

```bash
$ git add archivo.txt
$ git commit -m "Añadir cambios temporales a archivo.txt"
```

---

### 7.- Limpiar el stash

Después de aplicar los cambios del _stash_, Git aún mantiene una referencia de ellos en caso de que necesites aplicarlos nuevamente. Si ya no los necesitas, puedes eliminarlos con el siguiente comando:

```bash
$ git stash drop
```

Esto eliminará el stash más reciente. Si tienes varios stashes guardados, puedes ver la lista completa con:

```bash
$ git stash list
```

---

## Resumen de Comandos Útiles de git stash

  * **git stash**: Guarda los cambios no confirmados y limpia el directorio de trabajo.
  * **git stash apply**: Recupera los cambios del stash y los aplica al directorio de trabajo.
  * **git stash list**: Muestra todos los stashes guardados.
  * **git stash drop**: Elimina el stash más reciente.
  * **git stash pop**: Aplica los cambios del stash y luego lo elimina automáticamente.
  * **git stash clear**: Elimina todos los stashes.

---

## Ejemplo Práctico Completo

Imaginemos un escenario más completo:

  1. Estás trabajando en la rama `feature-xyz`, pero necesitas cambiar rápidamente a main para arreglar un bug.
  2. Tienes cambios no confirmados que no quieres perder.
  3. Usas `git stash` para guardar los cambios.
  4. Cambias a `main`, arreglas el bug, haces un commit y vuelves a tu rama de trabajo.
  5. Usas `git stash apply` para restaurar los cambios y continuar donde lo dejaste.


```bash
# Trabajas en la rama feature-xyz
$ git checkout -b feature-xyz
$ echo "Nueva funcionalidad" >> feature.txt
$ git add feature.txt
$ git commit -m "Comenzar nueva funcionalidad"

# Realizas más cambios pero no están listos para commit
$ echo "Trabajo en progreso" >> feature.txt

# Guardas los cambios sin hacer commit
$ git stash

# Cambias a main para arreglar un bug
$ git checkout main
$ echo "Arreglo del bug crítico" >> bugfix.txt
$ git add bugfix.txt
$ git commit -m "Arreglar bug crítico"

# Vuelves a tu rama de trabajo
$ git checkout feature-xyz

# Recuperas tus cambios
$ git stash apply
```


