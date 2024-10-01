# Sesión 08: Roles en Git y GitHub, Contribución a Proyectos de Terceros y Permisos en Repositorios de Equipo

En esta sesión, aprenderás cómo funcionan los roles en equipos de desarrollo que usan Git y GitHub. Veremos el concepto de **fork** para contribuciones en proyectos de terceros, así como cómo se gestionan los **permisos** en repositorios de equipo en GitHub.

## ¿Qué es un Rol en un Proyecto de GitHub?

En GitHub, los roles definen los permisos que tienes para interactuar con un repositorio. Aquí hay algunos roles comunes en un proyecto de equipo:

  1. **Owner (Propietario)**: Tiene control total sobre el repositorio, incluyendo permisos de administración, configuración, y la capacidad de eliminar el repositorio.
  2. **Maintainer (Mantenedor)**: Puede gestionar _issues_, _pull requests_, y fusionar cambios al repositorio. Suelen ser responsables de revisar las contribuciones de otros colaboradores.
  3. **Collaborator (Colaborador)**: Tiene permisos para contribuir directamente al repositorio. Pueden hacer _push_ a las ramas, abrir _pull requests_ y crear _issues_.
  4. **Contributor (Contribuidor)**: Cualquier persona que contribuya a un proyecto, pero sin permisos directos para modificar el repositorio. Normalmente trabajan a través de un **fork** y envían sus cambios mediante pull requests.

---

## Contribuir a Proyectos de Terceros: El Concepto de "Fork"

Cuando contribuyes a un proyecto que no es tuyo o en el que no tienes permisos directos para hacer cambios, debes crear un **fork** del repositorio. Esto te permite hacer cambios en tu propio repositorio y luego proponer esos cambios a través de un **pull request**. A continuación, te mostramos cómo funciona.

### 1.- Hacer un Fork del Repositorio

  1. Ve al repositorio de GitHub que quieres contribuir. Por ejemplo, este: `https://github.com/usuario-original/proyecto`.
  2. Haz clic en el botón **Fork** en la esquina superior derecha de la página del repositorio.

    ![Fork Button](https://user-images.githubusercontent.com/xyz/fork_button.png)

  3. GitHub creará una copia del repositorio en tu cuenta, que será tu propio **fork**. Ahora puedes modificar tu versión sin afectar el repositorio original.

---

### 2.- Clonar el Fork a Tu Computadora

Una vez que hayas hecho el fork del repositorio, necesitas clonarlo localmente para poder trabajar en él:

```bash
$ git clone https://github.com/tu-usuario/proyecto-fork.git
$ cd proyecto-fork
```

---

## 3.- Crear una Rama para Tus Cambios

Es buena práctica crear una nueva rama para cada conjunto de cambios que quieras hacer. Esto ayuda a mantener tu trabajo organizado y fácil de gestionar.

```bash
$ git checkout -b mi-rama
```

---

## 4.-  Hacer Cambios y Hacer Commit

Realiza los cambios que desees en el código del proyecto. Una vez que los hayas hecho, agrégalo al área de preparación y realiza un commit:

```bash
$ git add archivo_modificado.txt
$ git commit -m "Agregué nueva funcionalidad"
```

---

## 5.- Subir los Cambios a Tu Fork en GitHub

Ahora que has hecho los cambios y el commit, debes subir tu rama con los cambios a tu repositorio fork en GitHub:

```bash
$ git push origin mi-rama
```

---

## 6.- Crear un Pull Request

Ve a tu repositorio fork en GitHub: https://github.com/tu-usuario/proyecto-fork.

Verás un botón que dice **`Compare & pull request`**. Haz clic en él.

Llena los detalles del _pull request_. Especifica qué cambios has hecho y por qué son necesarios.

Envía el _pull request_ al repositorio original. Los mantenedores del proyecto revisarán tus cambios y, si todo está bien, los fusionarán en el repositorio original.

---

## Permisos en Repositorios de Equipo

En los repositorios de equipo, los permisos definen qué puede hacer cada persona con el código y la configuración del repositorio. Dependiendo de tu rol en el equipo, tus permisos pueden variar:

### Tipos de Permisos:

  * **Read (Lectura)**: Los usuarios con este permiso pueden ver el código, las _issues_ y los _pull requests_, pero no pueden hacer cambios.
  * **Triage**: Además de leer el código, estos usuarios pueden gestionar _issues_ y _pull requests_, pero no pueden hacer commits o fusiones de código.
  * **Write (Escritura)**: Los usuarios con permisos de escritura pueden hacer _push_ a las ramas, crear y cerrar _issues_, y gestionar _pull requests_. Sin embargo, no pueden realizar tareas administrativas como eliminar el repositorio.
  * **Maintain (Mantenimiento)**: Pueden realizar tareas de mantenimiento del repositorio, como fusionar _pull requests_, gestionar ramas, y asignar issues a otros colaboradores.
  * **Admin (Administrador)**: Tienen control total sobre el repositorio. Pueden cambiar las configuraciones del repositorio, agregar o eliminar colaboradores, y eliminar el repositorio si es necesario.

---

## Colaboración en un Proyecto de Equipo

Supongamos que estás trabajando en un equipo en GitHub. Aquí te mostramos cómo fluye el proceso:

  1. **Owner (Propietario)** del proyecto crea un repositorio y asigna a los miembros del equipo diferentes roles (_collaborators_).
  2. **Collaborators (Colaboradores)** del equipo clonan el repositorio y crean ramas para trabajar en nuevas características o resolver bugs.
  3. Una vez que un colaborador termina su trabajo, crea un _pull request_ para que el maintainer o el owner revise y fusione los cambios en la rama principal.

Si alguien fuera del equipo quiere contribuir al proyecto, hace un _fork_ del repositorio y envía un _pull request_ desde su _fork_.