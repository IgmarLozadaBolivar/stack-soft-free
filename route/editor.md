---
icon: laptop-code
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Workspace

Es fundamental configurar correctamente nuestro **espacio de trabajo (workspace)** para trabajar con fluidez y eficiencia. Este entorno incluye tanto las herramientas de desarrollo como la organización de archivos, configuración del proyecto y uso de extensiones útiles.

<figure><img src="https://ik.imagekit.io/i0spoii24/workspace.png" alt="workspace"><figcaption></figcaption></figure>

### IDE

Podemos utilizar cualquier **IDE (Entorno de Desarrollo Integrado)** que sea compatible con las tecnologías de nuestro stack. Algunos ejemplos recomendados son:

{% stepper %}
{% step %}
#### Visual Studio Code

Ligero, extensible y gratuito.
{% endstep %}

{% step %}
#### PhpStorm

Ideal si trabajas profundamente en Laravel y PHP.
{% endstep %}
{% endstepper %}

> 💡 Si no sabéis qué es un IDE, te invito a leer la sección 👉 [¿Qué es un IDE?](../)

### ✅ ¿Qué debe permitir nuestro entorno?

{% stepper %}
{% step %}
### Crear, editar y navegar por archivos del proyecto fácilmente.
{% endstep %}

{% step %}
### Ejecutar y depurar el código (especialmente útil con PHP/Laravel y Vue).
{% endstep %}

{% step %}
### Integrar herramientas como Git, Docker o bases de datos.
{% endstep %}

{% step %}
### Instalar extensiones o plugins útiles para mejorar la productividad.
{% endstep %}
{% endstepper %}

También así como permiten realizar cualquiera de las cosas mencionadas anteriormente, abarcamos temas cómo **Extensiones esenciales**, **Integración con Git**, **Formateo de código y estructura de archivos**. Cada uno de estos, son esenciales para trabajar con cualquier tecnología, estaremos examinando cada una con calma.

### 🛠️ Configuración del entorno

En este bloque encontrarás una guía paso a paso para dejar listo tu entorno de trabajo con todas las herramientas necesarias del Stack Soft Free. Asegúrate de seguir cada paso según tu sistema operativo.

#### 📦 Instalación de Node.js y npm

{% tabs %}
{% tab title="What is node.js?" %}
<div align="left" data-full-width="true"><figure><img src="https://img.icons8.com/color/96/nodejs.png" alt=""><figcaption></figcaption></figure></div>

🤔 ¿Qué es node.js?

Es un entorno de ejecución para JavaScript fuera del navegador web, es decir, directamente en nuestro equipo, pero... ¿A qué se debe esto?

Pues recordemos un par de cosas, cuando trabajamos con JavaScript solo funciona en un navegador web, cualquier código que tengamos se ejecuta en el entorno web y no por fuera, pero gracias a node.js esto ya es posible, y puede ser usado para crear servidores, automatizar tareas, trabajar con herramientas de desarrollo y más.

🤑 Ejemplo

Imagina que queréis imprimir un mensaje con JavaScript, pero sin la necesidad de abrir un navegador, veamos cómo es ese código:

```javascript
// archivo hola.js
console.log("¡Hola desde Node.js!");
```

Luego, simplemente lo ejecutáis en la terminal:

```bash
// usamos la herramienta node y le especificamos
// el archivo javascript que queremos que ejecute.
node <file>.js
```

Verás el resultado en la pantalla de la consola, y no en el navegador, así de simple es.
{% endtab %}

{% tab title="What is npm?" %}
<div align="left"><figure><img src="https://img.icons8.com/color/96/npm.png" alt=""><figcaption></figcaption></figure></div>

🤔 ¿Qué es npm?

npm (Node Package Manager) es el gestor paquetes de Node.js. Es como una tienda de herramientas donde podéis descargar y gestionar librerías, frameworks o utilidades para tus proyectos (por ejemplo: Astro, Tailwind, Vite, Vue, etc).

> Cuando instalas node.js, npm ya viene incluido internamente.

🤑 Ejemplo

```bash
// utilizamos la herramienta npm, acompañado de install
// que nos permite instalar paquetes y finalmente el paquete
// que queremos instalar en nuestro proyecto
npm install <package>
```

Necesitamos de esta herramienta bastante fundamental para crear proyectos, instalar dependencias, ejecutar el servidor de desarrollo y construir nuestro proyecto para producción.
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [node.js](https://nodejs.org/)
2. Descarga la versión **LTS** recomendada según tu sistema operativo.
3. Una vez instalado, procede a abrir la segunda ventana para verificar si ya tienes instalado "_node.js"_ y "_npm"._
{% endtab %}

{% tab title="Verificación" %}
1. Ejecuta el siguiente comando para comprobar si ya tenéis instalado _node.js:_

```bash
node -v
```

2. Para verificar si tienes el gestor de paquetes _npm_, ejecuta el siguiente comando:

```bash
npm -v
```

Con esto, ya estamos listos para continuar con la siguiente tecnología <mark style="color:blue;">**Git**</mark>.
{% endtab %}
{% endtabs %}

🧬 Instalación de Git

{% tabs %}
{% tab title="What is this?" %}
<div align="left"><figure><img src="https://img.icons8.com/color/96/git.png" alt=""><figcaption></figcaption></figure></div>

🤔 ¿Qué es git?

Es un sistema de control de versiones distribuido. En pocas palabras, te permite guardar el historial de tu código, trabajar en equipo, retroceder a versiones anteriores, y llevar un seguimiento ordenado de los cambios realizados en un proyecto.

🤨 ¿Para qué lo usarás?

* Clonar un repositorio base.
* Mantener sincronizado tu entorno local con el repositorio en GitHub.
* Subir tus cambios y colaborar con el equipo.
* Hacer control de versiones en conjunto con el flujo de trabajo definido.

🤑 Ejemplo

```bash
// clonación de repositorio base desde tu github
git clone <url>

// navegar al repositorio
cd <repositorio>

// ver el estado
git status

// agregar y guardar cambios
git add .
git commit -m <message>

// subir cambios a github
git push origin <branch>
```
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [git](https://git-scm.com/)
2. Descarga el instalador según tu sistema operativo.
3. Una vez instalado, ve a la pestaña de verificación.
{% endtab %}

{% tab title="Verificación" %}
Para verificar si git se ha instalado correctamente, ejecuta este comando:

```bash
git --version
```
{% endtab %}
{% endtabs %}

#### 🕹️ Warp Terminal

{% tabs %}
{% tab title="What is this?" %}
<div align="left"><figure><img src="https://user-images.githubusercontent.com/85056161/221151383-dee5374b-03d9-4548-a0fd-35dfc7ea0f5b.png" alt="" width="188"><figcaption></figcaption></figure></div>

🤔 ¿Qué es Warp?

Warp es una terminal moderna, rápida y basada en Rust, que transforma la experiencia clásica de la línea de comandos en algo mucho más visual, atractivo y productivo. A diferencia de otras terminales tradicionales como PowerShelll o Bash, Warp ofrece autocompletado inteligente, interfaz dividida por bloques, y una UX enfocada en desarrolladores.

&#x20;🤨 ¿Para qué lo usarás?

* Ejecutar scripts de desarrollo.
* Usar las diversas herramientas como Git, Docker, Composer, entre otras.
* Navegar entre carpetas y proyectos.
* Correr comandos relacionados al backend y frontend sin depender de IDEs.

🤑 Ejemplo

```bash
// cualquier cosa que necesitemos hacer, warp puede hacerlo

npm run dev

node -v

git status
```
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [warp.dev](https://www.warp.dev/)
2. Descarga el instalador según tu sistema operativo.
3. Una vez instalado, ve a la pestaña de verificación.
{% endtab %}

{% tab title="Verificación" %}
Para verificar que ya está instalado, simplemente buscar el ejecutable según tu sistema operativo y con eso bastará para empezar a trabajar con esta útil herramienta.
{% endtab %}
{% endtabs %}

#### 🐘 PHP

{% tabs %}
{% tab title="What is this?" %}
<div align="left"><figure><img src="https://img.icons8.com/external-tal-revivo-color-tal-revivo/96/external-hypertext-preprocessor-a-widely-used-open-source-general-purpose-scripting-language-logo-color-tal-revivo.png" alt=""><figcaption></figcaption></figure></div>

🤔 ¿Qué es PHP?

**PHP** es un lenguaje de programación del lado del servidor (backend) ampliamente utilizado para desarrollar aplicaciones web. Es especialmente potente cuando se combina con frameworks como **Laravel**, que forma parte clave de nuestro stack.

🤨 ¿Cómo lo vamos a usar?

* Ejecutar comandos de Laravel.
* Desarrollar lógica backend.
* Realizar pruebas con PHPUnit.
* Correr scripts o tareas programadas.

🤑 Ejemplo

```bash
php -v
```
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [php.net](https://www.php.net/)
2. Descarga el archivo comprimido según tu sistema operativo.
3. Una vez descargado, se debe buscar la ruta del php.exe, copiar la ruta para pegarla en las variables de entorno y así poder pasar a la ventana de verificación.
{% endtab %}

{% tab title="Verificación" %}
Para verificar simplemente ingresaremos este comando en cualquier terminal:

```bash
php -v
```
{% endtab %}
{% endtabs %}

#### 📦 Composer

{% tabs %}
{% tab title="What is this?" %}
<div align="left"><figure><img src="https://cdn-icons-png.flaticon.com/512/919/919840.png" alt="" width="188"><figcaption></figcaption></figure></div>

🤨 ¿Qué es composer?

**Composer** es un **gestor de dependencias para PHP**. Permite instalar, actualizar y gestionar librerías o paquetes que tu proyecto necesita para funcionar correctamente.

> Es, en pocas palabras, como el `npm` de PHP.

🚀¿Por qué vamos a usar Composer?

* Para instalar Laravel y otros paquetes necesarios de PHP.
* Gestionar librerías externas necesarias para el backend PHP.
* Ejecutar comandos que interactúan con el ecosistema de Laravel.
* Mantener un control de las dependencias del proyecto mediante archivos.

🤑 Ejemplo

```bash
// Instala todas las dependencias definidas en composer.json
composer install

// Crea un proyecto nuevo con Laravel
composer create-project laravel/laravel <nombre-proyecto>

// Actualiza las dependencias del proyecto
composer update
```
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [composer](https://getcomposer.org/)
2. Descarga el instalador según tu sistema operativo.
3. Una vez descargado, lo instalas y al final, procede a la ventana de verificación para continuar.
{% endtab %}

{% tab title="Verificación" %}
Para comprobar la instalación correcta del composer, escribe este comando:

```bash
composer -v
```
{% endtab %}
{% endtabs %}

#### 🌐Docker (opcional pero recomendado)

{% tabs %}
{% tab title="What is this?" %}
<div align="left"><figure><img src="https://img.icons8.com/color/96/docker.png" alt=""><figcaption></figcaption></figure></div>

🐳 ¿Qué es Docker?

**Docker** es una plataforma que permite crear, ejecutar y gestionar contenedores. Un contenedor es un entorno aislado que incluye todo lo necesario para ejecutar una aplicación: sistema operativo, dependencias, librerías, etc.

> Con Docker, podéis asegurarte de que tu proyecto funcione igual en cualquier máquina, sin importar el sistema operativo o la configuración del equipo.

🚀 ¿Por qué usar Docker en este stack?

* Evitar problemas de configuración local.
* Tener un entorno de desarrollo controlado y replicable.
* Levantar servicios como bases de datos, servidores PHP, Laravel, etc, todo sin la necesidad de instarlo directamente en tu equipo.
* Usar archivos cómo `Dockerfile` o `docker-compose.yml` para automatizar entornos complejos.

🤑 Ejemplo

```bash
// Levanta los contenedores definidos en el archivo docker-compose.yml
docker-compose up -d
```
{% endtab %}

{% tab title="Instalación" %}
1. Ingresa a la página de [docker](https://www.docker.com/)
2. Descarga el instalador según tu sistema operativo.
3. Una vez descargado, lo instalas y al final, procede a la ventana de verificación para continuar.
{% endtab %}

{% tab title="Verificación" %}
Desde la terminal ejecutar este comando:

```bash
docker --version
```

Y para verificar el motor de Docker Compose:

```bash
docker compose version
```
{% endtab %}
{% endtabs %}

#### 🆚 VS Code vs Cursor

| Característica                  | Visual Studio Code                       | Cursor                                              |
| ------------------------------- | ---------------------------------------- | --------------------------------------------------- |
| 🧠 **Asistente con IA**         | Opcional (requiere extensiones externas) | Integración nativa con IA y copilots de código      |
| ⚙️ **Extensiones disponibles**  | Más de 30,000 extensiones                | Compatible con la mayoría de extensiones de VS Code |
| 🚀 **Rendimiento**              | Rápido y liviano                         | Igual de rápido, con interfaz más enfocada en IA    |
| 🔧 **Uso en proyectos grandes** | Altamente personalizable                 | Más minimalista, enfoque out-of-the-box             |
| 🧩 **Personalización**          | Muy sólido                               | Excelente, especialmente con ayuda de IA            |
| 🧑‍🏫 **Curva de aprendizaje**  | Muy accesible                            | Muy accesible si ya usás VS Code                    |
| 🧪 **Integración con testing**  | Nativa o por extensiones                 | Igual, pero muchas tareas son sugeridas por IA      |
| 💻 **Soporte multiplataforma**  | Windows, macOS y Linux                   | Windows, macOS y Linux                              |

👉 [VS Code](https://code.visualstudio.com/)

👉 [Cursor](https://app.gitbook.com/o/Cv2qEXvS7qso6AXL2nYv/s/fU6HjCBjf0pWwfGA1F0i/)

Continuando con nuestra travesía y con nuestras herramientas y tecnologías ya instaladas y configuradas correctamente, podemos abarcar el tema de creación, estructuración de archivos y configuración del proyecto, sigue firme en este largo camino.
