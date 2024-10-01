# Sesión 07: Cómo hacer un Pull Request en GitHub

Un **Pull Request** (PR) es una solicitud para que los administradores de un proyecto revisen y, eventualmente, fusionen tus cambios en la rama principal del proyecto. Los PR son fundamentales para el desarrollo colaborativo, ya que permiten la revisión de código antes de integrar cambios.

En esta sesión, aprenderás cómo crear un Pull Request en GitHub, lo que incluye los pasos desde la creación de una rama, la realización de cambios y la solicitud de fusión en GitHub.

## Requisitos Previos

Antes de comenzar, asegúrate de tener:

  1. Un repositorio en GitHub o acceso a uno donde tengas permisos para colaborar.
  2. Git instalado en tu computadora.
  3. Un repositorio clonado en tu equipo o la capacidad de crear uno nuevo.

## 1.- Clonar un repositorio o crear uno nuevo

### Opción 1: Clonar un repositorio desde GitHub
Si ya tienes un repositorio en GitHub o te han invitado a colaborar en uno, clónalo en tu computadora con el siguiente comando:

```bash
$ git clone https://github.com/tu-usuario/tu-repositorio.git
$ cd tu-repositorio
```

### Opción 2: Crear un nuevo repositorio
Si prefieres crear un repositorio nuevo, sigue estos pasos:

Crea una nueva carpeta:

```bash
$ mkdir mi_proyecto
$ cd mi_proyecto
```

Inicializa Git en la carpeta:

```bash
$ git init
```

Crea un archivo de ejemplo:

```bash
$ echo "Hello, GitHub!" > archivo.txt
```

Haz un commit inicial:

```bash
$ git add archivo.txt
$ git commit -m "Primer commit"
```

Sube el repositorio a GitHub (si es un nuevo proyecto):

```bash
$ git remote add origin https://github.com/tu-usuario/mi-proyecto.git
$ git push -u origin main
```

## 2.- Crear una nueva rama

Es buena práctica crear una nueva rama para trabajar en cambios o nuevas funcionalidades sin afectar la rama principal (main).

Crea una nueva rama y cámbiate a ella:

```bash
$ git checkout -b nombre_de_rama
```

Por ejemplo:

```bash
$ git checkout -b feature/nueva-funcionalidad
```

Verifica en qué rama estás:

```bash
$ git branch
```

La rama en la que estás activo se mostrará con un `*` junto a su nombre.

---

## 3.- Hacer cambios en la nueva rama

Realiza los cambios que deseas. Por ejemplo, edita el archivo `archivo.txt`:

```bash
$ echo "Agregando una nueva funcionalidad" >> archivo.txt
```

Luego, añade estos cambios al área de preparación y haz un commit:

```bash
$ git add archivo.txt
$ git commit -m "Agregada nueva funcionalidad"
```

---

## 4.- Subir la rama a GitHub
Una vez que hayas hecho los cambios y el commit, necesitas subir la rama a GitHub para poder crear el Pull Request.

Sube la rama:

```bash
$ git push origin nombre_de_rama
```

Ejemplo:

```bash
$ git push origin feature/nueva-funcionalidad
```

Esto subirá la rama `feature/nueva-funcionalidad` a tu repositorio en GitHub.

---

## 5.- Crear un Pull Request en GitHub

Ahora que tu rama está en GitHub, puedes solicitar que tus cambios sean revisados y fusionados en la rama principal (`main`). Para hacer esto:

  1. Ve a GitHub y abre tu repositorio.
  2. Haz clic en el botón _"Compare & pull request"_ que aparece cuando subes una nueva rama.
  3. Rellena la información del _Pull Request_:
   
     * **Título del PR**: Debe ser descriptivo y conciso.
     * **Descripción**: Explica qué cambios hiciste, por qué los hiciste y si hay algún detalle que los revisores deben conocer.
  4. Selecciona la rama de destino:
     * Por defecto, la rama de destino suele ser main, pero puedes cambiarla si es necesario.
  5. Haz clic en _"Create pull request"_.

---

## 6.  Revisión y fusión del Pull Request

Una vez que hayas creado el **Pull Request**, los colaboradores del proyecto pueden revisarlo. Ellos pueden:

  * Revisar el código y hacer comentarios.
  * Solicitar cambios si algo necesita mejorarse.
  * Aprobar y fusionar el Pull Request.

Si todo está correcto y no hay conflictos, el Pull Request puede ser fusionado en la rama principal del proyecto.

---

## 7.- Diferencia entre `git fetch` y `git pull`

Cuando otros colaboradores hacen cambios en el repositorio, es importante mantener tu rama actualizada. Para ello, usa los siguientes comandos:

  * **git fetch**: Descarga los cambios del repositorio remoto, pero no los fusiona automáticamente en tu rama local.
  
    > ```bash
    > $ git fetch origin

    Después de hacer fetch, puedes revisar los cambios y decidir cuándo fusionarlos.

  * **git pull**: Descarga y fusiona los cambios remotos directamente en tu rama local.

    > ```bash
    > $ git pull origin main

    Este comando es útil cuando quieres asegurarte de que tienes la versión más reciente antes de trabajar en una nueva característica o hacer un Pull Request.
