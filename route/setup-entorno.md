---
icon: folder-tree
---

# Setup - Entorno

Esta guía te acompañará paso a paso en la creación, configuración y comprensión de la estructura base de tu proyecto dentro del Stack Soft Free. Vamos a empezar desde cero, con calma y desde los fundamentos: utilizando una herramienta que tiene Node.js y sí, es su gestor de paquetes, **npm**, para instalar **Astro**. Luego integraremos **Vue** y **Tailwind CSS**, y finalmente exploraremos cómo se organiza el proyecto internamente y qué configuraciones básicas necesitáis para comenzar a trabajar sin problemas.



### 🚀 Crear un proyecto nuevo con Astro

#### 🌟 ¿Qué es Astro?

**Astro** es un framework moderno basado en **JavaScript**. Tal vez te preguntes:

> “¿Framework de qué? ¿De HTML, CSS, JavaScript?”

La respuesta es: **Astro es un framework de JavaScript**, tal como lo son otros populares como **Next.js** o **Vite**.

Esto significa que usa JavaScript como base para ayudarte a construir sitios web de forma más organizada, eficiente y moderna, integrando también HTML y CSS, claro está. Pero su verdadero poder va más allá de solo usar JavaScript.

#### 🚀 ¿Por qué usamos Astro?

Astro está diseñado para crear sitios web rápidos y eficientes, con una experiencia de desarrollo muy cómoda. Algunas de sus características más destacadas:

* Permite **combinar múltiples tecnologías** como **Vue, React, Svelte** (e incluso HTML puro) en un mismo proyecto, según lo necesites.
* Solo **envía al navegador el código mínimo necesario**, lo que mejora mucho el rendimiento.
* Es muy flexible para construir desde **sitios estáticos** hasta proyectos más complejos conectados con bases de datos o APIs.
* Tiene un enfoque moderno, ideal para equipos que usan stacks híbridos o buscan rendimiento sin perder productividad.

En nuestro stack, Astro será el **punto de partida** y el núcleo del proyecto, y desde aquí construiremos todo lo demás: integraremos Vue, añadiremos estilos con Tailwind CSS, conectaremos con el backend y más.

> Ahora que ya sabéis un poco de Astro, continuemos con la creación de nuestro proyecto con esta tecnología, pendientes en este punto, ya que es de suma importancia.

### 📌 Creación de proyecto

{% stepper %}
{% step %}
#### 🧱 Define tu carpeta de trabajo

Esto puede parecer algo muy tonto, pero es de vital importancia, saber donde trabajaremos y tendremos nuestro proyecto FullStack.

Ahora bien, es importante tener instalador node.js y npm anteriormente, que funcionarán como nuestro motor y gestor de paquetes para nuestro entorno de desarrollo frontend.

> Si no lo tenéis instalado aún, regresa a la sección de [<mark style="color:$primary;">Workspace -> Node.js y npm</mark>](editor.md#instalacion-de-node.js-y-npm) y sigue los pasos desde allí, cuándo estés listo, vuelve y retoma este punto.

Ya luego de que previamente hayas elegido tu carpeta de trabajo, abre tu terminal **Warp**, si no la tienes, te invito a seguir la sección de [Warp Terminal](editor.md#warp-terminal), muévete a la ruta donde deseas crear tu proyecto, por ejemplo:

```bash
// Para los usuarios que trabajan en la raíz interna
cd C:\Users\losad\projects\stack-soft-free

// Para los usuarios que trabajan en raíces alternas
cd D:\projects\stack-soft-free
```

Ahora, stack-soft-free será nuestro directorio donde podremos dejar nuestros proyectos, ejercicios y prácticas de todo lo que aprenderemos con esta guía, ahora si bien vamos a abarcar 3 casos para crear un directorio para trabajar un proyecto en específico, pongamos el ejemplo de un login, entonces yo quisiera que dentro de mi directorio padre que contiene todos mis proyectos, es decir, stack-soft-free, quiero crear un directorio hijo que viene siendo un proyecto real y se llamará form-login, entonces a continuación, te presento los 3 casos:

{% tabs %}
{% tab title="Caso 1" %}
Entonces, sabemos que queremos crear un directorio hijo que se llamará form-login, entonces el primer caso va de la siguiente manera:

```bash
// No quiero inicializar git de forma local y tampoco quiero
// clonar un repositorio remoto desde GitHub, solo quiero trabajar
// y ya está, entonces haremos lo siguiente:

// Cabe aclarar que ya estamos dentro del directorio padre
// stack-soft-free y vamos a crear el directorio hijo form-login
mkdir form-login
cd form-login

// Y de forma inmediata empezamos a trabajar dentro del directorio
// de form-login
```
{% endtab %}

{% tab title="Caso 2" %}
Cómo ya sabemos lo que queremos hacer, entonces veamos cómo es este caso:

```bash
// Estamos dentro de stack-soft-free, y necesitamos crear form-login
mkdir form-login
cd form-login
git init -- ¡Ojo aquí! Estoy inicializando un repositorio local
```
{% endtab %}

{% tab title="Caso 3" %}
Ahora veamos el caso 3, que sucede de la siguiente manera:

```bash
// Recordamos que estamos en stack-soft-free y quiero tener form-login
// pero resulta que yo tengo repositorio creado en GitHub, entonces
// quiero clonarlo y tenerlo local, pero que ya está inicializado
// git y conectado de forma remota con GitHub, entonces:

// Esta es la forma a través de HTTP
git clone https://github.com/IgmarLozadaBolivar/form-login.git

// Esta es la forma a través de SSH
git clone git@github.com:IgmarLozadaBolivar/form-login.git

// Esta es la forma a través de GitHub Cli
gh repo clone IgmarLozadaBolivar/form-login
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### ⚙️ Ejecuta el generador de Astro

Para crear nuestro proyecto vamos a utilizar **npm**, que es el gestor de paquetes que viene junto con Node.js.

El comando que vamos a ejecutar es el siguiente, pero así como tuvimos 3 casos de trabajo, lo mismo pasa con ejecutar este comando:

{% tabs %}
{% tab title="Caso 1" %}
En el caso 1, si recordamos anteriormente el caso 1 de la creación de nuestro directorio, entonces el comando que usaremos también varía, en este caso sería ejecutar lo siguiente:

```bash
npm create astro@latest
```
{% endtab %}

{% tab title="Caso 2 y 3" %}
Ahora en el caso 2, tendremos que ejecutar el comando pero agregando algo adicional para evitarnos problemas que son un dolor de cabeza y no tener que volver a hacer todo de nuevo, este comando es:

```bash
npm create astro@latest .
// El . me permite decir que ya tengo un directorio creado anteriormente
// y que solo quiero que tomes el directorio en el que estoy como
// la referencia para que crees lo que tengas que crear
```
{% endtab %}
{% endtabs %}

Vamos a desglosarlo:

* `npm`  **▶️** Es nuestro gestor de paquetes, quién se encargará de **descargar** e **instalar** herramientas.
* `create`  **▶️** Le estamos diciendo que queremos **crear** un nuevo proyecto.
* `astro`  **▶️** Es el nombre del **paquete** o **herramienta** que vamos a usar, en este caso Astro.
* `@latest`  ▶️ Le indicamos que queremos trabajar con la **última versión disponible públicamente** de Astro.
* `.`  ▶️ Esto solo aplica para el caso 2 y 3, entonces esto me permite decirle que ya tengo un directorio anteriormente creado y que solo quiero que uses ese como referencia para crear lo que tengas que crear, del caso contrario si no le pasamos esto, entonces nos pedirá que pongamos un nombre al proyecto y esto generaría otro directorio y eso no queremos.

Este comando iniciará un asistente interactivo que te guiará paso a paso para configurar tu nuevo proyecto. Podéis aceptar las opciones sugeridas o personalizar según lo que necesites, pero en este caso, ya tenemos previamente definidas las opciones sugeridas, estate atento.
{% endstep %}

{% step %}
#### 🤖 Opciones del asistente interactivo de Astro

Al ejecutar el comando anterior, nuestra consola, nos arrojará la siguiente información:

```bash
// El comando npx, es una herramienta que viene integrada de npm
// que nos permite ejecutar paquetes sin tenerlos descargados globalmente y
// es muy útil.
> npx
> create-astro

astro Launch sequence initiated.

// Nos solicitará que ingresemeos el nombre de nuestro proyecto
// para esta guía usaré el siguiente nombre: "stack-example"
dir Where should we create your new project?
stack-example
```

Luego nos pedirá que seleccionemos una plantilla base para empezar a trabajar, por recomendación de nuestra parte es mejor una plantilla vacía y totalmente limpia, para ese caso seleccionaremos `Use minimal (empty) template`, veamos lo que nos muestra la consola:

```bash
// Simplemente nos pide con que plantilla queremos trabajar
tmpl How would you like to start your new project?
    > A basic, helpful starter project (recommended)
    - Use blog template
    - Use docs (Starlight) template
    - Use minimal (empty) template

// Para seleccionar, simplemente nos desplazamos entre las opciones usando
// las flechas de navegación nuestro teclado y cuando veamos que este simbolo
// > esté seleccionando Use minimal (empty) template, presionamos Enter.
🔺⬆️🔻
⬅️⬇️➡️
```

Lo siguiente que nos preguntará es si ¿Queremos instalar las dependencias?, veamos esto mejor en lo que nos muestra en la consola:

```bash
// Nos pregunta si queremos instalar las depedencias del proyecto
deps Install dependencies (recommended)
🟢 Yes 🔘 No

// Seleccionamos que sí por defecto, pero sucede casos que debido a la
// mala conexión de nuestro internet nos sale errores, diciendo time out
// y nos indica que de forma manual debemos instalar las dependencias por
// medio de este comando.
npm install o npm i -- ¡Cualquiera de las 2 formas, funcionará sin problemas!
```

Luego nos pregunta si queremos inicializar un repositorio, veamos esto mejor en nuestra consola, pero esto puede variar dependiendo si ya estás en un repositorio **GitHub** inicializado (local o remoto) o no:

{% tabs %}
{% tab title="Caso 1" %}
Si estás siguiendo los pasos desde que iniciamos con este Setup, entonces te pasará lo siguiente dentro de tu consola Warp:

```bash
// Nos pregunta si queremos que nuestro proyecto haga git init
// esto es opcional, pero es recomendable que si lo inicialices
// para empezar a familiarizarte más con Git y GitHub
git Initialize a new git repository? (optional)
🟢 Yes 🔘 No
```
{% endtab %}

{% tab title="Caso 2" %}
En el caso de que anteriormente, tuvieras un directorio o repositorio inicializado solamente local, entonces te pasará el siguiente caso en la consola:

```bash
// Esto nos indica, que cómo anteriormente tenías el directorio
// inicializado con git y solo local, nos arrojará lo siguiente:
◻️ Nice!
 Git has already has initialized
```
{% endtab %}

{% tab title="Caso 3" %}
En el caso 3, es algo similar al caso 2, pero con la diferencia de que tienes un directorio o repositorio inicialiazado y clonado desde GitHub, es decir, de forma remota, si este es tu caso, entonces la consola, te mostrará lo siguiente:

```bash
// Esto nos indica, que cómo anteriormente tenías el directorio
// inicializado con git y de manera remota es decir desde GitHub,
// nos arrojará lo siguiente:
◻️ Nice!
 Git has already has initialized
```
{% endtab %}
{% endtabs %}

Ya con todo lo que hicimos anteriormente desde el tema de ejecución del comando de crear proyecto hasta terminar de configurar las opciones de creación, ya solo tendremos que esperar que descargue, instale y configure todo lo necesario, ya finalizado podemos continuar con el siguiente paso.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
<mark style="color:$info;">Espera con ansias la parte 2, de la configuración de nuestro setup, gracias por tu paciencia, cuándo esté disponible estaremos, actualizando este texto.</mark>
{% endhint %}
