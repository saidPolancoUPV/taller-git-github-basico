# Sesión 06: Manejo de Ramas en Git y Subir Cambios a GitHub

En esta sesión, aprenderás cómo gestionar ramas en Git, que es una herramienta esencial para trabajar en paralelo en diferentes características o correcciones de tu proyecto. Además, verás cómo subir tus cambios a GitHub desde una rama en particular.

## ¿Qué son las ramas en Git?

Una **rama** (o _branch_ en inglés) en Git es un puntero móvil que apunta a un commit específico. Por defecto, Git crea una rama principal llamada `main` o `master`, pero puedes crear múltiples ramas para desarrollar nuevas características o arreglar errores sin afectar el código principal.

Trabajar con ramas te permite:

  * **Desarrollar nuevas características** sin afectar el código principal.
  * **Experimentar** con cambios sin romper el proyecto.
  * **Colaborar** de manera más eficiente con otros desarrolladores.

---

## 1. Crear un nuevo repositorio o clonar uno existente

### Opción 1: Crear un nuevo repositorio

  1. **Crea una nueva carpeta para tu proyecto**:
```bash
$ mkdir mi_proyecto
$ cd mi_proyecto
```

  2. **Inicializa Git**:
```bash
$ git init
```

### Opción 2: Clonar un repositorio existente desde GitHub

Si ya tienes un repositorio en GitHub, puedes clonarlo con:
```bash
$ git clone https://github.com/tu-usuario/tu-repositorio.git
$ cd tu-repositorio
```

---

## 1. Crear una nueva rama

Para crear una nueva rama y cambiarte a ella, usa el siguiente comando:

```bash
$ git checkout -b nombre_de_rama
```

### Ejemplo:

```bash
$ git checkout -b feature/nueva-funcionalidad
```

`git checkout -b nombre_de_rama`: Crea una nueva rama llamada nombre_de_rama y cambia a esa rama. En este caso, hemos creado una rama llamada `feature/nueva-funcionalidad`.

Verifica en qué rama estás:
```bash
$ git branch
```

Esto te mostrará una lista de todas las ramas y marcará con un `*` la rama en la que estás trabajando.

---

## 3. Hacer cambios en la nueva rama

Haz cambios en tu archivo: Abre un archivo existente o crea uno nuevo y realiza algunos cambios. Por ejemplo:

```bash
$ echo "Esta es una nueva funcionalidad" > nueva-funcionalidad.txt
```

Añade los cambios al área de preparación:

```bash
$ git add nueva-funcionalidad.txt
```

Haz un commit de los cambios:

```bash
$ git commit -m "Añadí una nueva funcionalidad"
```

---

## 4. Fusionar cambios entre ramas (opcional)

Después de realizar cambios en tu nueva rama, es posible que quieras fusionar estos cambios de vuelta a la rama principal (main o master).

Cambia a la rama principal:

```bash
$ git checkout main
```

Fusiona la rama:

```bash
$ git merge feature/nueva-funcionalidad
```

Este comando fusionará los cambios de la rama feature/nueva-funcionalidad en main.

## 6. Recuperar cambios de GitHub a tu repositorio local (pull)

Si otros colaboradores han hecho cambios en la rama remota y quieres obtener esos cambios, puedes usar el comando `git pull`.

```bash
$ git pull origin feature/nueva-funcionalidad
```

`git pull origin nombre_de_rama`: Este comando descarga los cambios de la rama nombre_de_rama del repositorio remoto y los fusiona con tu rama local.

---

## 7. Diferencia entre `git pull` y `git fetch`

  * `git pull`: Descarga los cambios y los fusiona inmediatamente con tu rama local.
  * `git fetch`: Solo descarga los cambios, pero no los fusiona. Te permite revisarlos antes de fusionar.

Comando para `git fetch`:

```bash
$ git fetch origin
```

Después de ejecutar `git fetch`, puedes ver qué cambios han llegado y decidir si los quieres fusionar.

---

## Ejemplo práctico completo

Crea una nueva rama:

```bash
$ git checkout -b feature/nueva-funcionalidad
```

Haz cambios en tu archivo:

```bash
$ echo "Esta es una nueva funcionalidad" > nueva-funcionalidad.txt
```

Añade los cambios al área de preparación:

```bash
$ git add nueva-funcionalidad.txt
```

Haz un commit de los cambios:

```bash
$ git commit -m "Añadí una nueva funcionalidad"
```

Sube la rama a GitHub:

```bash
$ git push origin feature/nueva-funcionalidad
```

Si hay cambios en GitHub, obtén los cambios:

```bash
$ git pull origin feature/nueva-funcionalidad
```

## Resumen
El manejo de ramas en Git es una de las mejores formas de trabajar en nuevas funcionalidades o correcciones sin afectar el código principal. Además, subir tus ramas a GitHub te permite colaborar con otros de manera eficiente. Con el tiempo, manejarás múltiples ramas y serás capaz de fusionarlas, resolver conflictos y mantener un flujo de trabajo organizado.

