# Sesión 04: Clonar un repositorio de GitHub y trabajar con Git

En este tutorial, aprenderás a clonar un repositorio de GitHub a tu máquina local y a trabajar con él usando Git. Cubriremos los comandos básicos como `git clone`, `git add`, `git commit`, y explicaremos detalladamente los comandos `git push` y `git pull`.

## Requisitos previos

  * Tener **Git** instalado en tu computadora.
  * Contar con una cuenta en **GitHub**.
  * Tener el enlace del repositorio que quieres clonar.

---

## 1.- Clonar el repositorio desde GitHub

El primer paso es clonar (copiar) un repositorio de GitHub a tu máquina local. Esto creará una copia completa del proyecto que podrás modificar y luego enviar de vuelta a GitHub.

```bash
$ git clone <URL-del-repositorio>
```

### Ejemplo

Imagina que el enlace del repositorio de GitHub es https://github.com/usuario/proyecto.git. Para clonar el repositorio, usarías el siguiente comando:

```bash
$ git clone https://github.com/usuario/proyecto.git
```

  > **Nota**: Cambia <URL-del-repositorio> por la URL del repositorio que deseas clonar. Al ejecutar este comando, se descargará una copia del repositorio en tu computadora.

### Resultado

Este comando creará una carpeta en tu máquina con el nombre del repositorio y copiará todo el contenido dentro de ella. Luego de clonar el repositorio, navega dentro de la carpeta recién creada:

```bash
$ cd proyecto
```

---

## 2.- Añadir archivos modificados al área de preparación

Después de clonar el repositorio, puedes hacer cambios en los archivos o añadir nuevos archivos al proyecto. Cuando estés listo para guardar esos cambios, primero necesitas agregar los archivos al área de preparación (staging area) usando el comando git add.

```bash
$ git add <archivo>
```

### Ejemplo

Si has creado o modificado un archivo llamado `index.html`, lo añadirías al área de preparación de la siguiente manera:

```bash
$ git add index.html
```

Si quieres añadir todos los archivos modificados y nuevos a la vez, puedes usar:

```bash
$ git add .
```

  > **Nota**: El . significa "todos los archivos nuevos o modificados". Este comando agrega todos los archivos a la vez al área de preparación.

---

## 3.- Hacer un commit de los cambios

Una vez que los archivos están en el área de preparación, necesitas hacer un commit. Un commit en Git es como una "foto" de los cambios que has realizado hasta ese momento.

```bash
$ git commit -m "Descripción del cambio"
```

### Ejemplo

Si has hecho cambios en varios archivos y los has añadido al área de preparación, puedes hacer un **commit** con un mensaje que describa esos cambios, como por ejemplo:

```bash
$ git commit -m "Modifiqué la página de inicio y añadí el archivo de estilos"
```

  > **Nota**: El mensaje entre comillas debe ser descriptivo para que puedas identificar fácilmente lo que has cambiado al revisar el historial del proyecto más adelante.

---

## 4.- Enviar los cambios a GitHub con git push

Una vez que has hecho un commit localmente, necesitas enviar esos cambios de vuelta al repositorio en GitHub para que otros puedan verlos o para tener una copia de seguridad de tu trabajo. Esto se hace con el comando git push.

```bash
$ git push origin main
```

### Explicación

  * **git push**: Envía los commits locales al repositorio remoto (en este caso, GitHub).
  * **origin**: Es el nombre predeterminado que Git le da al repositorio remoto cuando lo clonas.
  * **main**: Es el nombre de la rama principal en la que estás trabajando. Puede ser diferente (por ejemplo, master), dependiendo de cómo esté configurado el repositorio.

Cuando ejecutas este comando, Git enviará todos tus cambios al repositorio de GitHub, y esos cambios estarán disponibles para ti y para cualquier otra persona que tenga acceso a ese repositorio.

  > Nota: Si es la primera vez que estás haciendo git push, Git puede pedirte que ingreses tus credenciales de GitHub (nombre de usuario y contraseña o token personal de acceso).

---

## 5.- Actualizar tu repositorio local con git pull

Si estás trabajando en equipo o desde diferentes computadoras, es posible que alguien más haya hecho cambios en el repositorio de GitHub. Para asegurarte de tener la versión más reciente del proyecto, debes usar el comando git pull.

```bash
$ git pull origin main
```

### Explicación

  * **git pull**: Descarga y aplica los cambios del repositorio remoto a tu copia local.
  * **origin**: Es el nombre del repositorio remoto.
  * **main**: Es la rama principal del repositorio.

Al ejecutar `git pull`, Git descargará cualquier cambio que se haya hecho en el repositorio en GitHub y los fusionará con los cambios que tengas en tu copia local. Esto te ayuda a mantenerte sincronizado con el trabajo de otros miembros del equipo.
