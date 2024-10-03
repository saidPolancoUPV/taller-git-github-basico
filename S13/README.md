# Sesión 13: Crear una Tarea Autocalificable en GitHub Classroom

En esta sesión aprenderás cómo configurar una tarea autocalificable en GitHub Classroom usando **GitHub Actions**. Esta es una herramienta útil para que los docentes puedan realizar pruebas automáticas en los envíos de los estudiantes y proporcionar retroalimentación inmediata.

## Requisitos previos

Antes de empezar, asegúrate de tener lo siguiente:

  * Una **organización** de GitHub creada para tu aula.
  * Un aula ya configurada en [GitHub Classroom](https://classroom.github.com/).
  * Un **repositorio de plantilla** para las pruebas automatizadas que se aplicarán a los repositorios de los estudiantes.
  * Conocimiento básico de cómo funciona **GitHub Actions** para realizar pruebas automatizadas (aunque lo explicaremos aquí de manera general).

---

## Paso 1: Crear un repositorio de plantilla con pruebas automatizadas

  1. Inicia sesión en [GitHub](https://github.com/) y accede a tu organización.
  2. Crea un nuevo repositorio que funcionará como **repositorio de plantilla** para la tarea.
     * Dale un nombre descriptivo, como `tarea1-plantilla`.
     * Configura el repositorio como **público** o **privado**, según tu preferencia.
     * Marca la opción de **Initialize with a README**.
  3. Dentro del repositorio de plantilla, crea un archivo llamado `.github/workflows/test.yml`. Este archivo definirá el flujo de trabajo de GitHub Actions que realizará las pruebas.

### 1.1 Configuración de GitHub Actions en el repositorio

El archivo `test.yml` contiene las instrucciones para que GitHub Actions ejecute pruebas automatizadas en el código enviado por los estudiantes. Un ejemplo simple para probar código en Python sería:

```yaml
name: Autograding

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository content
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.x'

    - name: Install dependencies
      run: |
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest
```

Este archivo YAML está configurado para:
  
  * Ejecutarse cada vez que el código es subido al repositorio (on: push).
  * Usar un entorno Ubuntu (runs-on: ubuntu-latest).
  * Instalar las dependencias listadas en el archivo requirements.txt.
  * Ejecutar las pruebas con pytest.

---

### 1.2 Incluir las pruebas en el repositorio

Crea un archivo llamado `tests/test_example.py` en el repositorio de plantilla. Este archivo debe contener las pruebas que se aplicarán al código de los estudiantes. Un ejemplo de una prueba simple podría ser:

```python
def test_suma():
    assert suma(2, 3) == 5
```

En este ejemplo, suma es una función que los estudiantes deben implementar. La prueba verifica si la función suma correctamente dos números.

---

## Paso 2: Crear una tarea autocalificable en GitHub Classroom

  1. Dirígete a tu aula en GitHub Classroom.
  2. Haz clic en _New Assignment_ para crear una nueva tarea.
  3. Asigna un nombre a la tarea, por ejemplo, "Tarea 1: Función Suma Autocalificable".
  4. Configura la tarea como Individual o Group assignment, según sea el caso.
  5. En la sección _Template repository_, selecciona el repositorio de plantilla que creaste en el Paso 1.
  6. Haz clic en Enable autograding.

### 2.1. Configuración del autograding

Una vez que habilites autograding, verás una interfaz para definir las pruebas automatizadas que se ejecutarán sobre el código de los estudiantes. Aquí puedes configurar las mismas pruebas que definiste en el archivo `test_example.py`.

Define las pruebas que GitHub Classroom ejecutará para calificar automáticamente. Por ejemplo:

  * **Input**: suma(2, 3)
  * **Output esperado**: 5
  * **Tipo de prueba**: Custom Test (esto permite ejecutar el test automáticamente usando los archivos de GitHub Actions).

Configura las ponderaciones o puntos que cada prueba vale. Por ejemplo, la prueba de la función suma podría valer 10 puntos.

Haz clic en Save una vez que hayas configurado todas las pruebas.

---

## Paso 3: Compartir la tarea con los estudiantes

  1. Una vez que hayas configurado la tarea autocalificable, GitHub Classroom generará un enlace de invitación.
  2. Comparte este enlace con tus estudiantes. Cuando acepten la tarea, se les creará un repositorio individual con el contenido de la plantilla.
  3. Los estudiantes completarán el código y subirán sus cambios (con git push).
  4. GitHub Actions ejecutará automáticamente las pruebas que configuraste y GitHub Classroom generará una calificación automática basada en los resultados de las pruebas.

---

## Paso 4: Revisar los resultados y calificaciones

  1. En tu aula de GitHub Classroom, puedes ver el progreso de los estudiantes desde la pestaña de la tarea.
  2. Verás los resultados de las pruebas automáticas en cada repositorio de los estudiantes. Si las pruebas se ejecutaron correctamente y el código pasó todas las pruebas, la calificación automática se mostrará aquí.
  3. También puedes revisar los logs de GitHub Actions para ver detalles sobre las pruebas fallidas o exitosas.

---

## Ejemplo práctico

Supongamos que quieres que los estudiantes implementen una función llamada suma que toma dos números y retorna su suma. El flujo sería el siguiente:

  1. Creas un repositorio de plantilla con las pruebas que verifican la función suma.
  2. Configuras una tarea autocalificable en GitHub Classroom, habilitando la opción de autograding.
  3. Los estudiantes aceptan la tarea, implementan la función suma, y hacen git push.
  4. GitHub Actions ejecuta las pruebas automáticamente.
  5. GitHub Classroom asigna una calificación automática basada en si la función suma pasa las pruebas.
