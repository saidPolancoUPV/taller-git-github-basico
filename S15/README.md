# Sesión 15: Crear una Tarea Autocalificable en GitHub Classroom con C++ sin Pruebas Unitarias

En esta sesión, aprenderás a configurar una tarea autocalificable en **GitHub Classroom** utilizando **C++**. A diferencia de las tareas con pruebas unitarias, aquí evaluaremos los programas de los estudiantes mediante la ejecución directa de sus programas y la comparación de la salida con los resultados esperados.

## Requisitos previos

Antes de comenzar, asegúrate de tener:
  * Una **organización** en GitHub para tu aula.
  * Un aula creada en [GitHub Classroom](https://classroom.github.com/).
  * Un **repositorio de plantilla** con un archivo de código base en C++.
  * GitHub Actions configurado para ejecutar compilaciones y pruebas automáticas.

---

## 1. Crear un Repositorio de Plantilla para la Tarea

  1. Inicia sesión en [GitHub](https://github.com/) y accede a la organización de tu aula.
  2. Crea un nuevo repositorio que funcionará como **repositorio de plantilla** para la tarea.
    - Asigna un nombre descriptivo, por ejemplo, `tarea1-plantilla-cpp`.
    - Configúralo como **público** o **privado**, según tus necesidades.
    - Inicializa el repositorio con un **README.md**.

### 1.1 Estructura del Repositorio

Dentro del repositorio de plantilla, crea los siguientes archivos y directorios:
```
area1-plantilla-cpp/
├── src/
│ └── main.cpp
├── tests/
│ └── test_input.txt
│ └── expected_output.txt 
├── .github/
│ └── workflows/
│ └── autograding.yml
└── README.md
```


### 1.2 Código Base (main.cpp)

En el archivo `src/main.cpp`, agrega el siguiente código base:

```cpp
#include <iostream>

int main() {
    int a, b;
    std::cin >> a >> b;
    std::cout << "La suma es: " << (a + b) << std::endl;
    return 0;
}
```

Este es un ejemplo simple de un programa que toma dos números como entrada y devuelve su suma.

### 1.3 Archivos de Prueba

Crea dos archivos dentro del directorio `tests/`:

  * `test_input.txt`: Contiene los valores de entrada para el programa.
  ```
  3 5
  ```
  * `expected_output.txt`: Contiene la salida esperada del programa para la entrada proporcionada.
  ```
  La suma es: 8
  ```

---

##  2. Configurar GitHub Actions para la Autocalificación

  1. En la carpeta `.github/workflows/`, crea el archivo `autograding.yml`. Este archivo configurará GitHub Actions para compilar y ejecutar el programa de los estudiantes.
```yaml
name: Autograding

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Set up C++ environment
      run: sudo apt-get install g++

    - name: Compile program
      run: g++ src/main.cpp -o main

    - name: Run tests
      run: ./main < tests/test_input.txt > output.txt

    - name: Compare output
      run: diff output.txt tests/expected_output.txt
```

Explicación del archivo `autograding.yml`

  * **Checkout repository**: Este paso obtiene el código del repositorio del estudiante.
  * **Set up C++ environment**: Instala el compilador g++ en la máquina de ejecución.
  * **Compile program**: Compila el código del archivo `main.cpp` en un ejecutable llamado main.
  * **Run tests**: Ejecuta el programa del estudiante con la entrada del archivo `test_input.txt` y guarda la salida en `output.txt`.
  * `Compare output`: Compara la salida generada por el programa del estudiante con el archivo `expected_output.txt`. Si las salidas coinciden, la prueba se considera exitosa.

---

## 3. Crear la Tarea en GitHub Classroom

  1. Ve a GitHub Classroom y selecciona tu aula.
  2. Haz clic en **New Assignment** para crear una nueva tarea.
  3. Asigna un nombre a la tarea, como "Tarea 1: Suma de dos números en C++".
  4. Configura la tarea como **Individual o Group assignment**, según lo desees.
  5. En la sección **Template repository**, selecciona el repositorio de plantilla que creaste anteriormente (`tarea1-plantilla-cpp`).
  6. Haz clic en Enable autograding para habilitar la calificación automática.
  7. No es necesario agregar pruebas personalizadas en esta etapa, ya que el sistema autocalificará en función de los resultados de GitHub Actions.

---

## 4. Compartir la Tarea con los Estudiantes

  1. Una vez que la tarea esté lista, GitHub Classroom generará un enlace de invitación.
  2. Comparte el enlace con tus estudiantes para que acepten la tarea.
  3. Cuando los estudiantes acepten la tarea, se les creará un repositorio basado en la plantilla que configuraste.
  4. Los estudiantes deberán implementar su código en el archivo `main.cpp` y hacer **commit** y **push** a su repositorio.

---

## 5. Proceso de Calificación Automática

  1. Cada vez que un estudiante realice un **push** de su código al repositorio, GitHub Actions compilará y ejecutará el programa.
  2. Si la salida generada por el programa del estudiante coincide con el archivo `expected_output.txt`, el test pasará.
  3. Puedes ver los resultados de la ejecución en la pestaña Actions del repositorio del estudiante, donde se mostrará si las pruebas pasaron o fallaron.

---

## Ejemplo Práctico

Supongamos que el objetivo de la tarea es que los estudiantes implementen un programa en C++ que sume dos números y muestre el resultado. El flujo sería el siguiente:

  1. El estudiante clona el repositorio generado a partir de la plantilla.
  2. Implementa el código en `main.cpp`:
```cpp
#include <iostream>

int main() {
    int a, b;
    std::cin >> a >> b;
    std::cout << "La suma es: " << (a + b) << std::endl;
    return 0;
}
```

  3. Realiza un **commit** y **push** de su código:
  ```bash
git add .
git commit -m "Implementación de la función suma"
git push
```

  4. GitHub Actions compila el código y ejecuta las pruebas.
  5. Si el programa genera la salida correcta, la prueba pasa y la tarea se marca como aprobada.

