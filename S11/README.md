# Sesión 11: Historial de Commits y Cambio de Rama HEAD en Git

En esta sesión aprenderás a revisar el historial de cambios de un proyecto utilizando comandos básicos de Git, como `git log` y `git log --oneline`, así como a entender y utilizar la referencia `HEAD` para moverte entre ramas o commits.

---

## 1. Revisar el historial de commits

### ¿Qué es el historial de commits?

El historial de commits en Git es una lista cronológica de todas las confirmaciones (commits) realizadas en el repositorio. Cada commit tiene un identificador único (hash) y contiene información sobre los cambios, el autor, la fecha y un mensaje descriptivo.

### Comando `git log`

El comando `git log` te permite revisar el historial de commits en detalle. Para ejecutarlo, abre una terminal en tu proyecto y escribe:

```bash
$ git log
```

Este comando te mostrará algo como lo siguiente:

```sql
Copiar código
commit 9bfb1b2a3d8a4bd9dd112cdbb2d7b7987e49d1c2
Author: Juan Pérez <juanperez@example.com>
Date:   Tue Sep 10 14:32:05 2024 -0500

    Añadir archivo README.md

commit a9d8a7f2c9bb2398b67e73fb235198a8bc8e5f2d
Author: María López <marialopez@example.com>
Date:   Mon Sep 9 10:10:25 2024 -0500

    Corregir errores en la lógica de la función principal
```

Elementos del historial:

  * **commit**: Identificador único (hash) del commit.
  * **Author**: El nombre y correo electrónico del autor que hizo el commit.
  * **Date**: La fecha y hora en que se realizó el commit.
  * **Mensaje**: El mensaje descriptivo del commit.

### Comando `git log --oneline`

Si quieres ver el historial de commits de manera más compacta, puedes usar la opción `--oneline`, que mostrará cada commit en una sola línea:

```bash
$ git log --oneline
```

El resultado será algo como esto:

```css
9bfb1b2 Añadir archivo README.md
a9d8a7f Corregir errores en la lógica de la función principal
```

Este formato es útil cuando deseas tener una visión general rápida del historial de commits, mostrando solo el hash corto y el mensaje del commit.

---

## 2. Cambio de rama HEAD

### ¿Qué es la rama HEAD?
En Git, `HEAD` es un puntero que señala al commit actual en el que estás trabajando. Por defecto, HEAD suele apuntar a la última confirmación de la rama actual (generalmente la rama main o master).

### Mover HEAD a un commit anterior

Para "moverte" a un commit específico del historial, puedes usar el comando git checkout seguido del hash del commit. Esto es útil si deseas revisar cómo estaba el proyecto en un punto anterior en el tiempo.

Por ejemplo, si quieres moverte al commit con el hash `a9d8a7f`:

```bash
$ git checkout a9d8a7f
```
Ahora, Git moverá `HEAD` al commit correspondiente y cambiará el estado de tu proyecto a ese punto del historial. Ten en cuenta que estarás en un estado de "`detached HEAD`" (cabeza separada), lo que significa que no estás en una rama, sino directamente en un commit específico.

Para volver a la rama principal (por ejemplo, main), simplemente ejecuta:

```bash
$ git checkout main
```

### Crear una nueva rama desde un commit específico

Si quieres hacer cambios en ese commit específico sin perder tu trabajo en la rama principal, puedes crear una nueva rama a partir de ese commit:

```bash
$ git checkout -b nueva-rama a9d8a7f
```

Esto crea y cambia automáticamente a una nueva rama llamada nueva-rama, que empieza desde el commit `a9d8a7f`.

---

## Ejemplo práctico

Vamos a ver un ejemplo práctico de cómo revisar el historial y mover HEAD.

### 1. Crear un proyecto de ejemplo

Primero, creamos un nuevo proyecto y hacemos algunos commits:

```bash
$ mkdir mi-proyecto
$ cd mi-proyecto
$ git init
$ echo "Hola Mundo" > archivo.txt
$ git add archivo.txt
$ git commit -m "Añadir archivo.txt"
$ echo "Hola Git" >> archivo.txt
$ git add archivo.txt
$ git commit -m "Actualizar archivo.txt con Hola Git"
```

### 2. Revisar el historial de commits

Ahora que tenemos dos commits, revisemos el historial:

```bash
$ git log --oneline
```

Resultado:

```css
d5f8c4b Actualizar archivo.txt con Hola Git
a6b7d3c Añadir archivo.txt
```

### 3. Mover HEAD al primer commit

Supongamos que queremos ver cómo estaba el proyecto en el primer commit. Usamos el hash del commit `a6b7d3c`:

```bash
$ git checkout a6b7d3c
```

Tu proyecto ahora estará en el estado del primer commit.

### 4. Volver a la rama principal

Para regresar a la rama principal (`main`), ejecuta:

```bash
$ git checkout main
```

---

## Resumen de comandos

  * **git log**: Muestra el historial de commits de manera detallada.
  * **git log --oneline**: Muestra el historial de commits en formato simplificado.
  * **git checkout `<commit>`**: Mueve HEAD a un commit específico (estado detached).
  * **git checkout `<branch>`**: Mueve HEAD a una rama específica.
  * **git checkout -b `<branch> <commit>`**: Crea y cambia a una nueva rama a partir de un commit específico.