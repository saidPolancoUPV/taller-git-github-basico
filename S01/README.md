# Sesión 01 - Git: Configuración inicial

## Configuración inicial de Git

Ahora que tienes Git instalado en tu sistema, es importante que realices una configuración inicial para personalizar tu entorno. Estos pasos solo necesitan realizarse una vez, a menos que desees cambiar alguna configuración más adelante. Utilizaremos la herramienta `git config` para establecer estas opciones.

## 1. Configurar tu identidad

Lo primero que debes hacer es configurar tu nombre de usuario y tu correo electrónico. Esta información se utilizará para identificarte en cada "commit" que realices.

### Paso 1: Configurar tu nombre de usuario
Ejecuta el siguiente comando en la terminal, reemplazando `"John Doe"` con tu nombre:

```bash
$ git config --global user.name "John Doe"
```
---

## 2. Configurar tu correo electrónico

Ejecuta este comando, reemplazando "johndoe@example.com" con tu correo electrónico:

```bash
$ git config --global user.email johndoe@example.com
```

  > Nota: Utiliza la opción `--global` para que esta configuración se aplique a todos los repositorios de tu sistema. Si deseas configuraciones diferentes para repositorios específicos, omite el --global y ejecuta estos comandos dentro del repositorio correspondiente.

---

## 3. Configurar tu editor de texto

Git utiliza un editor de texto para que ingreses mensajes cuando haces commits o editas configuraciones. Si no configuras un editor, Git usará el editor predeterminado del sistema (generalmente Vim). Para usar un editor como Emacs, Nano, o cualquier otro, ejecuta el siguiente comando, reemplazando emacs con el editor de tu preferencia:

```bash
$ git config --global core.editor emacs
```

  > Nota: Si no estás familiarizado con Vim o Emacs, te recomiendo configurar un editor con el que estés cómodo. Algunos editores comunes en Windows como Notepad++ también pueden configurarse.

---

## 4. Comprobando tu configuración

Para verificar que tu configuración se ha aplicado correctamente, puedes listar todas las configuraciones actuales con el siguiente comando:

```bash
git config --list
```

Este comando te mostrará una lista de todas las propiedades configuradas en Git, incluyendo tu nombre de usuario, correo electrónico, y otras configuraciones adicionales.

### Comprobar una configuración específica

Si quieres revisar el valor de una configuración en particular, por ejemplo tu nombre de usuario, ejecuta lo siguiente:

```bash
$ git config user.name
```

---

## 5. Archivos de configuración

Git guarda la configuración en tres ubicaciones diferentes, cada una con diferente nivel de prioridad:

  1. **Archivo global** (`~/.gitconfig` o `~/.config/git/config`): Configuración del usuario en todo el sistema. Se configura con la opción `--global`.
  2. **Archivo local del repositorio** (`.git/config`): Configuración específica de un repositorio.
  3. **Archivo del sistema** (`/etc/gitconfig`): Configuración para todos los usuarios del sistema.

Cada nivel sobrescribe los valores del anterior, es decir, la configuración local del repositorio tiene prioridad sobre la global.

---

## 6. Cambiar configuraciones en cualquier momento

Si en algún momento deseas cambiar tu configuración (como tu nombre, correo electrónico o editor), simplemente vuelve a ejecutar los comandos git config con los nuevos valores. Por ejemplo, para cambiar el editor:

```bash
git config --global core.editor "nano"
```
