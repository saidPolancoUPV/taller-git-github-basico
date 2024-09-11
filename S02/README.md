# Sesión 02: Crear un nuevo repositorio en Git desde cero

En esta sesión, aprenderás cómo crear un repositorio Git desde cero en tu sistema, sin necesidad de servicios externos como GitHub. Todo el proceso se realiza localmente.

### 1. Crear una carpeta para el proyecto

El primer paso es crear una nueva carpeta en tu sistema que será el directorio del proyecto donde Git llevará el control de versiones.

En la terminal, usa el siguiente comando para crear una nueva carpeta y luego navega dentro de ella:

```bash
$ mkdir nombre-del-proyecto
$ cd nombre-del-proyecto
```

  > **Nota**: Cambia `Nombre-del-proyecto` por el nombre de tu proyecto. Este será el directorio donde se almacenarán todos los archivos de tu proyecto.


### 2. Inicializar el repositorio Git

Una vez dentro de la carpeta, debes inicializar un nuevo repositorio Git. Esto creará un subdirectorio oculto llamado `.git`, que contendrá todos los archivos necesarios para que Git haga un seguimiento de los cambios en tu proyecto.

Ejecuta el siguiente comando para inicializar el repositorio:

```bash
Copiar código
$ git init
```

_Salida esperada_: Verás un mensaje como `Initialized empty Git repository in /ruta/a/nombre-del-proyecto/.git/`, lo que indica que el repositorio ha sido creado correctamente.

### 3. Añadir archivos al repositorio

Ahora que Git está inicializado, puedes empezar a añadir archivos a tu proyecto. Crea uno o más archivos en tu carpeta y luego añade esos archivos al control de versiones de Git.

Para crear un archivo de prueba, puedes usar el siguiente comando:

```bash
$ echo "Este es mi proyecto" > archivo.txt
```

Esto creará un archivo llamado archivo.txt con un mensaje de prueba.

Una vez que tengas los archivos que deseas **rastrear**, añade todos los archivos al área de preparación con el comando:

```bash
$ git add .
```

Nota: El `.` después de git add indica que quieres añadir todos los archivos nuevos o modificados en la carpeta actual al área de preparación.

### 4. Hacer el primer commit

Después de añadir los archivos al área de **preparación**, es hora de confirmar los cambios en el repositorio. Un commit es como un _"snapshot"_ del estado actual de tu proyecto en ese momento.

Haz el primer commit ejecutando lo siguiente:

```bash
$ git commit -m "Primer commit: añado los archivos iniciales"
```

Nota: El argumento `-m` permite agregar un mensaje que describe el cambio realizado. Es recomendable que este mensaje sea claro y descriptivo.

### 6. Ver el historial de commits

Si deseas ver el historial de commits que has realizado, puedes usar el siguiente comando para listar todos los commits con detalles como el autor, la fecha y el mensaje de cada commit.

```bash
$ git log
```

_Salida esperada_: Verás una lista de los commits realizados hasta el momento, comenzando por el más reciente.

---

## Resumen

Has creado exitosamente un nuevo repositorio Git local siguiendo estos pasos:

  * Crear una carpeta de proyecto (`mkdir`).
  * Inicializar el repositorio Git (`git init`).
  * Añadir archivos al área de preparación (`git add`).
  * Hacer un commit inicial (`git commit`).
  * Verificar el estado del repositorio (`git status`).
  * Revisar el historial de commits (`git log`).