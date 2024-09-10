# Curso Git y Github básico y para docentes.

## ¿Qué es Git y qué no es Git?

### ¿Qué es Git?

**Git** es un sistema de control de versiones distribuido (DVCS) diseñado para rastrear cambios en archivos, coordinar el trabajo entre múltiples personas y gestionar proyectos de desarrollo de software de manera eficiente. Algunas de sus características clave incluyen:

1. **Control de versiones**: Git rastrea y registra los cambios realizados en un proyecto a lo largo del tiempo, permitiendo a los usuarios acceder a versiones anteriores, fusionar cambios y revertir errores.
   
2. **Distribuido**: Cada clon de un repositorio es una copia completa, con todo el historial del proyecto. Esto permite trabajar sin una conexión continua a un servidor central, proporcionando flexibilidad y resiliencia.
   
3. **Ramas y fusiones**: Git facilita la creación de ramas para el desarrollo aislado de nuevas características o soluciones, lo que permite trabajar de manera independiente y luego fusionar los cambios en la rama principal.
   
4. **Snapshots, no diferencias**: A diferencia de otros sistemas, Git almacena el estado completo del proyecto (snapshot) en cada confirmación (commit), en lugar de solo los cambios realizados. Esto mejora la eficiencia y la integridad del historial.

5. **Alto rendimiento**: Git está diseñado para ser rápido y eficiente incluso en grandes proyectos, manejando miles de archivos con facilidad.

### ¿Qué no es Git?

1. **No es un sistema de respaldo**: Aunque Git mantiene un historial completo de los cambios, su propósito no es actuar como un sistema de respaldo. No gestiona la integridad física de tus archivos o la disponibilidad a largo plazo, como lo haría un servicio de respaldo.

2. **No es un gestor de proyectos**: Git rastrea cambios en el código y facilita la colaboración, pero no proporciona herramientas específicas para la gestión de proyectos (planificación, asignación de tareas, etc.).

3. **No es un entorno de desarrollo**: Git es una herramienta de control de versiones. No ofrece funcionalidades como un editor de código, depurador, compilador o integración de herramientas de desarrollo.

4. **No es una herramienta para archivos binarios grandes**: Aunque Git puede manejar archivos binarios, no está optimizado para trabajar con ellos, especialmente si son grandes. Los repositorios de Git crecen rápidamente con archivos binarios, lo que puede afectar su rendimiento.

5. **No es centralizado**: A diferencia de los sistemas de control de versiones centralizados (como Subversion o CVS), Git es distribuido. Esto significa que no hay un solo servidor que mantenga una copia "oficial" del repositorio.

6. **No es una plataforma de hosting**: Git no proporciona por sí solo un entorno para compartir proyectos en línea o colaborar a través de la web. Esto lo hacen servicios externos que integran Git, como GitHub o GitLab.

---

## Principales diferencias entre Git y GitHub

### Git

**Git** es un sistema de control de versiones distribuido diseñado para gestionar el seguimiento de cambios en archivos, coordinar el trabajo en proyectos y garantizar la integridad del historial del código. Algunas características clave de Git son:

- **Sistema de control de versiones distribuido**: Git se utiliza para gestionar y registrar los cambios en un proyecto a lo largo del tiempo, almacenando un historial completo de versiones.
- **Repositorio local**: Git permite a los desarrolladores trabajar de manera local, sin necesidad de estar conectados a Internet o a un servidor central. Cada clon de un repositorio es una copia completa del proyecto, incluyendo su historial.
- **Control sobre el historial**: Git ofrece poderosas herramientas para realizar commits, crear ramas, fusionar cambios y revertir a versiones anteriores del código.
- **Independencia de la plataforma**: Git se puede usar en cualquier sistema y no requiere necesariamente de servicios externos para funcionar.

#### Ejemplos de comandos de Git:
- `git init`: Inicializa un repositorio Git en un directorio.
- `git clone`: Crea una copia local de un repositorio.
- `git commit`: Guarda los cambios en el repositorio local.
- `git merge`: Fusiona cambios de diferentes ramas.

### GitHub

**GitHub** es una plataforma de alojamiento y colaboración basada en la web que utiliza Git como sistema de control de versiones. Ofrece servicios adicionales para facilitar la gestión de proyectos y la colaboración entre desarrolladores. Algunas características de GitHub son:

- **Almacenamiento en la nube**: GitHub permite a los desarrolladores alojar sus repositorios Git de forma remota en la nube, lo que facilita compartir proyectos con otros.
- **Interfaz web**: GitHub proporciona una interfaz web donde los usuarios pueden ver el código, realizar revisiones (code reviews), hacer comentarios, y gestionar problemas (issues) o solicitudes de extracción (pull requests).
- **Colaboración**: GitHub está diseñado para facilitar el trabajo en equipo. Ofrece herramientas para gestionar el flujo de trabajo colaborativo, como los pull requests, el seguimiento de problemas (issues) y la integración continua (CI).
- **Visibilidad pública o privada**: GitHub permite que los repositorios sean públicos (accesibles para cualquier persona) o privados (solo para colaboradores seleccionados).
- **Integración con otros servicios**: GitHub se integra con muchas otras herramientas, como plataformas de CI/CD, gestores de proyectos y editores de código.

#### Funciones adicionales de GitHub:
- **Pull requests**: Solicitudes para fusionar cambios entre ramas, con la posibilidad de revisiones y comentarios antes de aceptar la fusión.
- **Issues**: Herramienta para gestionar y seguir el progreso de problemas o tareas relacionadas con el proyecto.
- **GitHub Actions**: Plataforma de automatización para crear flujos de trabajo CI/CD dentro de GitHub.
- **GitHub Pages**: Permite alojar páginas web estáticas directamente desde un repositorio.

### Diferencias clave

| Característica       | Git                                      | GitHub                                              |
|----------------------|------------------------------------------|-----------------------------------------------------|
| **Función principal** | Sistema de control de versiones distribuido. | Plataforma de hosting y colaboración para proyectos Git. |
| **Repositorio**       | Local, en la máquina del usuario.        | Remoto, en la nube (disponible a través de la web).  |
| **Conectividad**      | Funciona sin conexión a Internet.        | Requiere conexión para acceder a repositorios remotos. |
| **Interfaz**          | Basado en la línea de comandos.          | Interfaz web y línea de comandos.                   |
| **Colaboración**      | Requiere intercambio manual de repositorios (por ejemplo, con `git push` y `git pull`). | Facilita la colaboración a través de pull requests y revisiones de código. |
| **Herramientas adicionales** | No incluye herramientas de gestión de proyectos. | Ofrece gestión de proyectos, seguimiento de problemas, automatización y más. |

---

## Diferencias entre Git y otros sistemas de gestión de versiones

Git es uno de los sistemas de control de versiones distribuidos (DVCS) más populares. Sin embargo, existen otros sistemas de gestión de versiones, tanto centralizados como distribuidos, que tienen diferencias clave en cuanto a funcionamiento, estructura y características. A continuación, se describen las diferencias principales entre Git y otros sistemas de control de versiones como **Subversion (SVN)**, **Mercurial**, y **Perforce**.

### Git vs. Subversion (SVN)

**Subversion (SVN)** es un sistema de control de versiones centralizado (CVCS) y uno de los predecesores más populares de Git.

| Característica             | Git                                       | Subversion (SVN)                             |
|----------------------------|-------------------------------------------|----------------------------------------------|
| **Modelo de almacenamiento**| Distribuido: cada clon es un repositorio completo con su historial. | Centralizado: el historial completo está en un servidor central. |
| **Repositorios locales**    | Repositorio completo en cada máquina.     | Solo el servidor central contiene el historial completo. |
| **Conectividad**            | Funciona sin conexión a Internet.         | Requiere conexión constante para la mayoría de operaciones (commits, merges). |
| **Velocidad**               | Mayor velocidad al realizar operaciones locales. | Más lento, ya que las operaciones requieren acceso al servidor. |
| **Manejo de ramas**         | Ramas ligeras y rápidas de crear, fusionar y eliminar. | Las ramas son más pesadas y pueden ser complicadas de gestionar. |
| **Snapshot vs. diferencias**| Git almacena snapshots completos de los archivos en cada commit. | SVN almacena diferencias entre archivos (deltas). |
| **Popularidad**             | Popular en proyectos de código abierto y equipos distribuidos. | Usado principalmente en empresas que necesitan un sistema centralizado. |

### Git vs. Mercurial

**Mercurial** es otro sistema de control de versiones distribuido, similar a Git, pero con algunas diferencias clave en diseño y usabilidad.

| Característica             | Git                                       | Mercurial                                   |
|----------------------------|-------------------------------------------|---------------------------------------------|
| **Interfaz**                | Requiere una curva de aprendizaje más pronunciada, con comandos más complejos. | Más fácil de usar, con una curva de aprendizaje más suave. |
| **Modelo de almacenamiento**| Distribuido: cada clon es un repositorio completo. | También distribuido, con un modelo similar a Git. |
| **Rendimiento**             | Optimizado para grandes proyectos y repositorios con miles de archivos. | Similar a Git, pero puede ser más lento en grandes proyectos. |
| **Extensibilidad**          | Muy flexible y altamente personalizable a través de scripts y plugins. | Menos extensible que Git, pero más consistente en su diseño. |
| **Ramas**                  | Las ramas en Git son más ligeras y fáciles de gestionar. | Las ramas en Mercurial son un poco más pesadas pero más fáciles de visualizar. |
| **Integridad de datos**     | Usa SHA-1 para asegurar la integridad del historial. | También usa técnicas de hashing para proteger la integridad del historial. |
| **Comunidad**               | Git tiene una comunidad mucho más grande y activa. | Mercurial tiene una comunidad más pequeña, pero estable. |

### Git vs. Perforce

**Perforce (Helix Core)** es un sistema de control de versiones centralizado, diseñado principalmente para grandes empresas con necesidades específicas de rendimiento y escalabilidad.

| Característica             | Git                                       | Perforce                                    |
|----------------------------|-------------------------------------------|---------------------------------------------|
| **Modelo de almacenamiento**| Distribuido: cada clon tiene una copia completa del repositorio. | Centralizado: el servidor central gestiona todos los archivos y metadatos. |
| **Conectividad**            | Funciona sin conexión, permitiendo commits locales. | Requiere una conexión continua con el servidor para la mayoría de operaciones. |
| **Escalabilidad**           | Escalable, pero los repositorios muy grandes pueden volverse lentos. | Altamente escalable para proyectos grandes con enormes cantidades de datos. |
| **Manejo de archivos grandes** | Git no maneja bien archivos binarios grandes sin herramientas adicionales como Git LFS. | Perforce está optimizado para manejar archivos binarios y grandes volúmenes de datos. |
| **Seguridad**               | Cada desarrollador tiene su propio repositorio local, lo que puede complicar la seguridad de los datos. | Seguridad centralizada y control de acceso detallado desde el servidor. |
| **Ramas**                  | Las ramas en Git son ligeras y fáciles de manejar. | Las ramas en Perforce son más pesadas, pero el sistema maneja bien las fusiones en proyectos grandes. |

### Git vs. Otros Sistemas (CVS, ClearCase)

Otros sistemas como **CVS** y **ClearCase** son más antiguos y menos populares en la actualidad, pero siguen siendo utilizados en algunos entornos empresariales.

| Característica             | Git                                       | CVS / ClearCase                              |
|----------------------------|-------------------------------------------|----------------------------------------------|
| **Modelo de almacenamiento**| Distribuido.                              | Centralizado: CVS requiere conexión a un servidor central. |
| **Desempeño**              | Rápido y eficiente, especialmente para proyectos distribuidos. | Más lento y menos eficiente que Git. |
| **Manejo de conflictos**    | Git tiene potentes herramientas para resolver conflictos en fusiones. | Las fusiones en CVS pueden ser más complicadas y propensas a errores. |
| **Facilidad de uso**        | Requiere aprendizaje, pero es flexible y muy potente. | CVS es menos flexible y ClearCase es complejo de configurar. |
| **Soporte y mantenimiento** | Git es altamente soportado, con una comunidad activa. | CVS y ClearCase son más antiguos, con menos soporte en la actualidad. |


---

# ¿Git es GitHub?

**No, Git no es GitHub.**

Aunque los términos "Git" y "GitHub" a menudo se utilizan indistintamente, **son cosas diferentes**.

  > La diferencia fundamental es que **Git es la herramienta que controla versiones**, mientras que **GitHub es un servicio que aloja repositorios Git y facilita la colaboración en línea**. Puedes usar Git sin GitHub, pero no puedes usar GitHub sin Git, ya que Git es el núcleo sobre el que se basa todo el funcionamiento de GitHub.

En resumen:

- **Git = Control de versiones (local o remoto)**.
- **GitHub = Plataforma de colaboración y alojamiento de repositorios basados en Git**.

**No cometas el error de confundirlos**: Git es la tecnología base, mientras que GitHub es una plataforma que te permite aprovechar esa tecnología de manera más accesible y colaborativa.

---

## Principales diferencias entre GitHub, GitLab y Bitbucket

Cuando hablamos de plataformas para alojar repositorios Git y colaborar en proyectos de desarrollo, **GitHub**, **GitLab** y **Bitbucket** son tres de las opciones más populares. A continuación, se presentan las principales diferencias entre estas plataformas, destacando la utilidad de GitHub para estudiantes y su integración con **GitHub Classroom**.

## 1. **GitHub**

GitHub es la plataforma más conocida para el alojamiento de repositorios Git, ampliamente utilizada en la comunidad de código abierto y por desarrolladores de todo el mundo. Para estudiantes, GitHub ofrece herramientas y recursos muy útiles, como **GitHub Classroom**.

### Ventajas para estudiantes:
- **GitHub Classroom**: GitHub ofrece esta herramienta para facilitar a los profesores la gestión de tareas y proyectos de programación en un entorno de aprendizaje. Con GitHub Classroom, los estudiantes pueden:
  - Recibir y entregar asignaciones de manera estructurada.
  - Usar GitHub Actions para automatizar la evaluación de código.
  - Gestionar proyectos colaborativos entre compañeros.
  
- **GitHub Student Developer Pack**: Los estudiantes tienen acceso gratuito a varias herramientas y servicios premium que les ayudan en su desarrollo académico y profesional.
- **Comunidad activa**: GitHub es la plataforma con mayor adopción, por lo que tiene una comunidad muy activa y una gran cantidad de recursos, repositorios públicos y ejemplos de código que los estudiantes pueden estudiar.

### Características generales de GitHub:
- **Visibilidad**: Ofrece repositorios públicos gratuitos, lo que lo hace ideal para proyectos de código abierto.
- **GitHub Actions**: Automatización de flujos de trabajo de CI/CD.
- **Interfaz web intuitiva**: Fácil de usar y con muchas herramientas visuales para la revisión y gestión de proyectos.
- **GitHub Pages**: Permite a los usuarios publicar sitios web estáticos directamente desde un repositorio.

---

## 2. **GitLab**

GitLab es una plataforma similar a GitHub, pero con un enfoque fuerte en la integración continua y la entrega continua (CI/CD). Es una opción popular en empresas y entornos privados debido a sus amplias características de integración y sus opciones de autoalojamiento.

### Diferencias clave:
- **CI/CD integrado**: GitLab tiene un sistema CI/CD más avanzado que GitHub, integrado desde el principio sin necesidad de configuraciones adicionales.
- **Autoalojamiento**: GitLab ofrece una opción de instalación **on-premise**, lo que permite a las empresas tener un control total sobre la seguridad y la infraestructura.
- **Mayor privacidad**: Ideal para empresas o instituciones educativas que desean alojar sus propios servidores de GitLab, evitando depender de servicios en la nube.

### Utilidad para estudiantes:
- GitLab es una buena opción para estudiantes que quieran aprender sobre **integración continua y entrega continua**, pero no ofrece tantas herramientas educativas específicas como GitHub Classroom.
  
---

### 3. **Bitbucket**

Bitbucket es otra plataforma de gestión Git, orientada especialmente a equipos que trabajan con proyectos privados y que usan el ecosistema Atlassian (que incluye herramientas como Jira y Confluence).

#### Diferencias clave:
- **Integración con Atlassian**: Se integra perfectamente con Jira y Confluence, lo que la convierte en una opción popular para equipos que ya utilizan este ecosistema de herramientas.
- **Mercado objetivo**: Bitbucket es más popular entre desarrolladores que trabajan en entornos corporativos o con proyectos privados pequeños.
- **Repositorios privados ilimitados**: Bitbucket ofrece repositorios privados gratuitos para equipos pequeños, lo que lo hace atractivo para startups o pequeños grupos de trabajo.

#### Utilidad para estudiantes:
- Aunque útil para estudiantes interesados en el desarrollo de software en entornos empresariales, Bitbucket no ofrece tantas funcionalidades o recursos específicos para la educación como GitHub con Classroom.

---

### Comparación general

| Característica              | **GitHub**                                 | **GitLab**                                 | **Bitbucket**                            |
|-----------------------------|--------------------------------------------|--------------------------------------------|------------------------------------------|
| **Enfoque principal**        | Código abierto, comunidad, educación       | CI/CD, autoalojamiento, DevOps             | Integración Atlassian, proyectos privados |
| **Herramientas educativas**  | GitHub Classroom, Student Pack             | No tiene herramientas educativas específicas | No tiene herramientas educativas específicas |
| **Repositorios privados**    | Repositorios privados gratuitos limitados  | Repositorios privados ilimitados en la versión gratuita | Repositorios privados gratuitos (equipos pequeños) |
| **Integración CI/CD**        | GitHub Actions                            | CI/CD nativo, más avanzado                 | Integración básica con pipelines         |
| **Opciones de autoalojamiento** | No disponible                             | Sí, disponible                             | No disponible                            |
| **Popularidad en código abierto** | Amplia comunidad de código abierto       | También usado para código abierto, pero menos popular | Menos utilizado en proyectos de código abierto |

---

### **GitHub Classroom: La herramienta ideal para estudiantes**

GitHub destaca sobre GitLab y Bitbucket para estudiantes gracias a su **enfoque educativo** con herramientas como **GitHub Classroom**. Esta plataforma permite a los profesores crear tareas, distribuirlas automáticamente entre los estudiantes y revisar sus progresos en tiempo real, todo utilizando las funcionalidades de Git. Además, los estudiantes pueden aprovechar recursos exclusivos como el **GitHub Student Developer Pack**, que ofrece acceso gratuito a una amplia gama de herramientas y servicios.

#### Beneficios de GitHub Classroom:
- **Facilita la enseñanza**: Los instructores pueden crear repositorios para cada estudiante o grupo, y automatizar el proceso de corrección.
- **Promueve la colaboración**: Los estudiantes pueden aprender a trabajar en proyectos grupales utilizando flujos de trabajo reales de la industria.
- **Acceso a herramientas profesionales**: A través del GitHub Student Developer Pack, los estudiantes pueden obtener acceso a software y servicios premium que les ayudará a mejorar sus habilidades.

---


