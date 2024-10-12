# Sesión 14: Crear una Tarea Autocalificable en GitHub Classroom con JUnit y Maven

Esta sesión te guiará en la creación de una tarea autocalificable en GitHub Classroom utilizando **JUnit** para realizar pruebas en proyectos de Java y **Maven** como sistema de construcción y gestión de dependencias.

## Requisitos previos

Antes de comenzar, asegúrate de tener:
- Una **organización** en GitHub para tu aula.
- Un aula creada en [GitHub Classroom](https://classroom.github.com/).
- Un **repositorio de plantilla** con un proyecto Java y pruebas escritas en **JUnit**.
- Maven instalado y configurado en tu entorno de desarrollo.

---

## 1.- Crear un repositorio de plantilla con JUnit y Maven

  1. Inicia sesión en [GitHub](https://github.com/) y accede a la organización de tu aula.
  2. Crea un nuevo repositorio que funcionará como **repositorio de plantilla** para la tarea.
      * Asigna un nombre descriptivo, por ejemplo, `tarea1-plantilla-java`.
      * Configúralo como **público** o **privado**, según tus necesidades.
      * Inicializa el repositorio con un **README.md**.
  3. Dentro del repositorio, crea una estructura básica de proyecto para Java utilizando **Maven**.

### 1.1 Configurar el proyecto Maven

  1. Dentro de tu repositorio de plantilla, crea la siguiente estructura de carpetas:
```
tarea1-plantilla-java/
├── src/
│ ├── main/
│ │ └── java/
│ │ └── App.java
│ └── test/
│ └── java/
│ └── AppTest.java
└── pom.xml
```

---

### 1.2.- Crea el archivo `App.java` en la carpeta `src/main/java` con el siguiente contenido:

```java
public class App {
 public static void main(String[] args) {
     System.out.println("Hello, GitHub Classroom!");
 }

 public static int suma(int a, int b) {
     return a + b;
 }
}
```

---

### 1.3.- Este es un ejemplo de una clase sencilla con un método suma que los estudiantes deberán completar.

Crea el archivo `AppTest.java` en la carpeta `src/test/java` con el siguiente contenido:

```Java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class AppTest {

    @Test
    public void testSuma() {
        assertEquals(5, App.suma(2, 3));
    }
}
```

Este archivo contiene una prueba de JUnit que verifica si el método suma suma correctamente dos números.

---

### 1.4.- Crea el archivo `pom.xml` en el directorio raíz del proyecto. Este archivo configura el proyecto Maven y sus dependencias, incluyendo JUnit:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>tarea1-plantilla-java</artifactId>
    <version>1.0-SNAPSHOT</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.1</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>

```

Este archivo agrega JUnit como dependencia de prueba.

---


## 2.- Crear la tarea en GitHub Classroom

  1. Accede a GitHub Classroom y selecciona tu aula.
  2. Haz clic en **New Assignment** para crear una nueva tarea.
  3. Asigna un nombre a la tarea, como "Tarea 1: Implementación de la función suma en Java".
  4. Configura la tarea como **Individual o Group assignment**, dependiendo de cómo deseas organizar a tus estudiantes.
  5. En la sección **Template repository**, selecciona el repositorio de plantilla que creaste en el paso anterior.
  6. Haz clic en **Enable autograding** para habilitar la calificación automática.


### 2.1.- Configuración del autograding con Maven

Cuando habilitas autograding, deberás configurar las pruebas que se ejecutarán en el código de los estudiantes:

  1. En la sección **Custom Test**, selecciona la opción para ejecutar pruebas automatizadas con Maven.
     * Configura el comando para ejecutar las pruebas: `mvn test`. Este comando ejecutará todas las pruebas definidas en el archivo `AppTest.java`.
  2. Define las pruebas basadas en los resultados esperados. Por ejemplo:
     * Input: `App.suma(2, 3)`
     * Output esperado: `5`
  3. Asigna puntos a cada prueba, según la complejidad o importancia de la tarea.
  4. Haz clic en **Save** para guardar la configuración de las pruebas.

---

## 3.- Compartir la tarea con los estudiantes

  1. Una vez que la tarea esté lista, GitHub Classroom generará un enlace de invitación.
  2. Comparte este enlace con tus estudiantes para que acepten la tarea.
  3. Cuando los estudiantes acepten la tarea, se les creará un repositorio basado en la plantilla que configuraste.
  4. Los estudiantes podrán escribir su código en el método suma y luego hacer push de sus cambios al repositorio.

---

### 4.- Ejecución de las pruebas y calificación automática

  1. Cada vez que un estudiante realice un `git push`, el código se probará automáticamente usando las pruebas definidas con JUnit.
  2. GitHub Actions ejecutará el comando `mvn test` en el repositorio del estudiante, y los resultados de las pruebas serán visibles en GitHub Classroom.
  3. Si las pruebas pasan, se asignará una calificación automática basada en las pruebas configuradas en el autograding.

---

## Ejemplo práctico

Supongamos que quieres que los estudiantes implementen el método suma correctamente. El flujo sería el siguiente:

  1. Los estudiantes aceptan la tarea y clonan el repositorio.
  2. Implementan el método suma en `App.java`:
```Java
public static int suma(int a, int b) {
    return a + b;
}
```
  3. Hacen commit y push de su solución:
```Java
git add .
git commit -m "Implementación de la función suma"
git push
```
  4. GitHub Actions ejecuta el comando `mvn test` para verificar la implementación.
  5. Si el método `suma` pasa las pruebas, GitHub Classroom califica automáticamente la tarea.

---

## 5. Revisar los resultados y retroalimentación

  1. En GitHub Classroom, puedes revisar los resultados de las pruebas de cada estudiante.
  2. Podrás ver qué pruebas han fallado o pasado, y GitHub Classroom asignará una calificación automática basada en las pruebas configuradas.
  3. Si lo deseas, puedes proporcionar retroalimentación adicional a los estudiantes, revisando los logs de las pruebas.






