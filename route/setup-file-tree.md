---
icon: folder-tree
---

# Setup - File Tree

Vimos varios conceptos en la anterior página, ahora nos vamos adentrar un poco más, cómo ya tenemos nuestro proyecto anteriormente creado en la página de [**Setup - Entorno**](setup-entorno.md#crear-un-proyecto-nuevo-con-astro).

### 🗂️ Estructura de archivos de Astro

#### 🤔 ¿Qué es una estructura de archivos?

> El _file tree_ o árbol de archivos representa la estructura de carpetas y archivos de tu proyecto. Es la forma en que todo está organizado: desde el código fuente hasta las configuraciones y assets.

Astro propone una estructura de carpetas y archivos organizada para cualquier proyecto, la raíz de ese proyecto deberá incluir los siguientes archivos y carpetas:

| Archivo/Carpeta     | Descripción breve                                                                          | Contenido                                     |
| ------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------- |
| 📁 src/\*           | Contiene todo el código fuente del proyecto.                                               | Páginas, componentes, estilos, imágenes, etc. |
| 🌐 public/\*        | Archivos públicos que no son procesados por Astro.                                         | Fuentes, íconos, imágenes sueltas, etc.       |
| 📦 package.json     | El manifiesto del proyecto.                                                                | Dependencias, scripts, metadatos.             |
| ⚙️ astro.config.mjs | Archivo de configuración de Astro.                                                         | Rutas, integraciones, adaptadores.            |
| 📘 tsconfig.json    | Configuración de TypeScript (aunque uses JavaScript, este archivo es útil para el editor). | Rutas, compilaciones, todo solo para el IDE.  |

Vamos a ver más a detalle cada uno de estos, así que estaos atentos, porque es de vital importancia y no cometer errores que nos cuesten tiempo, trabajo y sacrificio.

{% stepper %}
{% step %}
📁 **`src/*`**

Aquí es donde encontramos todo nuestro código fuente del proyecto, que puede incluir muchas cosas cómo:

* Páginas
* Plantillas
* Componentes de Astro
* Componentes de Frameworks (Vue, etc)
* Estilos (CSS, Sass)
* Markdown
* Imágenes optimizadas y procesadas por Astro

Astro procesa, optimiza y empaqueta los archivos en `src/` para crear la página web final que será desplegada al navegador. A diferencia de la carpeta estática `public/`, los archivos en `src/` serán procesados por Astro.

{% hint style="info" %}
Algunos archivos (como los componentes de Astro) no serán enviados al navegador como fueron escritos, sino que serán renderizados a HTML estático.
{% endhint %}

{% hint style="info" %}
Otros archivos (como CSS) serán enviados directamente al navegador, pero antes serán optimizados o empaquetados con otros archivos para un mejor rendimiento.
{% endhint %}

Ahora veremos cada una de las cosas que incluye astro, que ya mencionamos anteriormente, pero vamos a profundizar un poco más.

{% tabs %}
{% tab title="src/pages" %}
Las rutas de páginas se crean para tu sitio añadiendo tipos de archivos compatibles a este directorio:

* `.astro`
* `.html`
* `.mdx`&#x20;

{% hint style="warning" %}
`src/pages` es un subdirectorio **requerido** en tu proyecto de Astro. Sin él, tu sitio no tendrá páginas ni rutas.
{% endhint %}
{% endtab %}

{% tab title="src/components" %}
Los **componentes** son unidades o bloques reutilizables de código para tus páginas HTML. Estos componentes pueden ser **componentes de Astro** o **componentes de framework** como React o Vue. Es común agrupar y organizar todos tus componentes en una sola carpeta.

Esta es la convención común en proyectos de Astro, pero no es necesaria. ¡Siéntete libre de organizar tus componentes a gusto!
{% endtab %}

{% tab title="src/layouts" %}
Las **plantillas** son componentes de Astro que definen la estructura de la UI compartida por una o más **páginas**.

Así como `src/components`, esta carpeta es una convención común pero no es necesaria.
{% endtab %}

{% tab title="src/styles" %}
Es una convención común para guardar todos tus archivos CSS o Sass en una sola carpeta `src/styles` pero no es necesaria. Siempre y cuando tus estilos se encuentren dentro de la carpeta `src/` y sean importados correctamente, Astro se encargará de optimizarlos.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
**🌐 `public/*`**

La carpeta `public/` es para archivos en tu proyecto que no necesiten ser procesados durante la compilación final de tu proyecto. Los archivos en esta carpeta serán copiados dentro de la carpeta build sin ser modificados y luego tu sitio será construido.

Este comportamiento hace que `public/` sea ideal para archivos comunes que no requieren ningún procesamiento, como imágenes y fuentes.

{% hint style="success" %}
Como regla general, cualquier archivo CSS o JavaScript que escribas debe estar en tu carpeta `src/`.
{% endhint %}
{% endstep %}

{% step %}
**📦 `package.json`**

Es un archivo utilizado por los gestores de paquetes de JavaScript para administrar tus dependencias. También define los scripts que se usan comúnmente para ejecutar Astro, por ejemplo:

```bash
npm run dev
npm run build
npm run preview
```

Hay [dos tipos de dependencias](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file) que puedes especificar en `package.json`: `dependencies` (dependencias) y `devDependencies` (dependencias de desarrollo).&#x20;

En la mayoría de los casos, estas funcionan de la misma manera: Astro necesita todas las dependencias al hacer _build_, y tu gestor de paquetes instalará ambos.&#x20;

{% hint style="info" %}
Recomendamos poner todas tus dependencias en `dependencies` para comenzar, y solo usar `devDependencies` si encuentras la necesidad de hacerlo.
{% endhint %}
{% endstep %}

{% step %}
**⚙️ `astro.config.mjs`**

Este archivo es generado al crear tu proyecto en Astro e incluye la configuración de tu proyecto. Aquí puedes especificar las integraciones que desees utilizar, las opciones de compilación final, la configuración del servidor, y más.
{% endstep %}

{% step %}
**📘 `tsconfig.json`**

Este archivo es generado en cada plantilla de inicio de Astro e incluye la configuración de las opciones de TypeScript para tu proyecto de Astro. Algunas características (como importaciones de paquetes de npm) no están soportadas completamente en tu editor sin un archivo `tsconfig.json`.
{% endstep %}
{% endstepper %}

> ¿Estás feliz, porque hemos retomado nuevamente nuestro camino?

Espero que así sea, ya cada vez nos adentramos más al terreno de los dioses y convivir con ellos, te invitamos a seguir en esta travesía y nos vemos en **Setup - Integraciones**.
