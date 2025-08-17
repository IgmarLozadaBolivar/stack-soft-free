---
icon: planet-ringed
---

# Astro - Layouts

{% hint style="info" %}
La base de no reinventar la rueda en cada página, ¿Recordáis este dicho?
{% endhint %}

Los layouts o plantillas, son componentes de Astro para proporcionar una estructura reutilizable, como una plantilla de página.

Convencionalmente usamos el término de `layout` , para elementos compartidos en la interfaz del usuario por medio de páginas, como encabezados, barras de navegación y pies de página.

Una plantilla debe contener:

* Una **página shell** (con etiquetas `<html>`, `<head>` y `<body>`).
* Un [**`<slot/>`**](astro-components.md#slots) para especificar dónde colocar el contenido de la página.

Pero, ¡no hay nada especial acerca de los componentes plantilla! Pueden [aceptar props](astro-components.md#props-de-componentes) e [importar y usar otros componentes](astro-components.md#estructura-de-un-componente) como cualquier otro componente de Astro. Pueden incluir [componentes de framework](https://docs.astro.build/es/guides/framework-components/) y [scripts de lado del cliente](../pagina-en-construccion.md). Ni siquiera tienen que proporcionar un plantilla entera, en su lugar se pueden utilizar como plantillas parciales.

Los componentes de plantilla se colocan comúnmente en la carpeta `src/layouts` en tu proyecto, pero esto no es un requisito; puedes elegir ubicarlos en cualquier lugar de tu proyecto.

### Plantilla de ejemplo

{% code title="src/layouts/MySiteLayout.astro" %}
```javascript
---
import BaseHead from '../components/BaseHead.astro';
import Footer from '../components/Footer.astro';
const { title } = Astro.props;
---
```
{% endcode %}

{% code title="src/layouts/MySiteLayout.astro" %}
```html
<html lang="es">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <BaseHead title={title} />
  </head>
  <body>
    <nav>
      <a href="#">Inicio</a>
      <a href="#">Publicaciones</a>
      <a href="#">Contacto</a>
    </nav>
    <h1>{title}</h1>
    <article>
      <slot /> <!-- tu contenido es inyectado aquí -->
    </article>
    <Footer />
  </body>
  <style>
    h1 {
      font-size: 2rem;
    }
  </style>
</html>
```
{% endcode %}

Este sería el resultado utilizar el layout:

{% code title="src/pages/index.astro" %}
```javascript
---
import MySiteLayout from '../layouts/MySiteLayout.astro';
---
```
{% endcode %}

{% code title="src/pages/index.astro" %}
```html
<MySiteLayout title="Página De Inicio">
  <p>¡El contenido de mi página, envuelto en una plantilla!</p>
</MySiteLayout>
```
{% endcode %}

### Plantilla de ejemplo con TypeScript

{% code title="src/pages/index.astro" %}
```javascript
---
interface Props {
  title: string;
  description: string;
  publishDate: string;
  viewCount: number;
}

const { title, description, publishDate, viewCount } = Astro.props;
---
```
{% endcode %}

{% code title="src/pages/index.astro" %}
```html
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <meta name="description" content={description}>
    <title>{title}</title>
  </head>
  <body>
    <header>
      <p>Publicado el {publishDate}</p>
      <p>Visto por {viewCount} amigos</p>
    </header>
    <main>
      <slot />
    </main>
  </body>
</html>
```
{% endcode %}

> Nos adentramos a armar una estructura o arquitectura dentro un HTML, bueno realmente Astro.

Te invito a que visites la siguiente página de **Astro - Styles y CSS**.
