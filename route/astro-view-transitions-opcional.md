---
hidden: true
icon: planet-ringed
---

# Astro - View Transitions (opcional)

{% hint style="info" %}
Actualización del contenido de nuestra página sin tener que recargar la navegación completa normal del navegador, lo que nos proporciona animaciones fluidas entre páginas.
{% endhint %}

Astro nos ofrece un componente de enrutamiento `<ViewTransitions />` que se puede agregar dentro del `<head>` de una sola página para controlar las transiciones de página mientras navegamos hacia otra página.

{% hint style="danger" %}
Esto es opcional, pero se hace con tan pocas líneas de código.
{% endhint %}

Para integrar este componente dentro de otro componente .astro reutilizable, como un encabezado común o un diseño, así como también podemos lograr integrarlo no solo a una página, sino a todo un sitio (modo SPA).

El soporte de las view transitions en Astro está impulsado por la nueva API del navegador [View Transitions](https://developer.chrome.com/docs/web-platform/view-transitions/) y también nos incluye:

* Algunas opciones de animación integrada, como `fade`, `slide` y `none`.
* Soporte para animaciones de navegación hacia adelante y hacia atrás.
* La capacidad de personalizar todos los aspectos de la animación de transición y crear tus propias animaciones.
* La opción de impedir la navegación del lado del cliente para enlaces que no sean de página.
* Control sobre el movimiento de respaldo para navegador que aún no admiten la API de View Transitions.
* Soporte automático para refers-reduced-motion.

### 🎬 Agregando las View Transitions a una página

Opta por utilizar view transitions en páginas individuales importando y añadiendo el componente de enrutamiento `<ViewTransitions />` dentro del `<head>` en cada página deseada.

Veamos como aplicar este componente a continuación:

```javascript
---
import { ViewTransitions } from 'astro:transitions';
---
```

```html
<html lang="es">
  <head>
    <title>Mi página de inicio</title>
    <ViewTransitions />
  </head>
  <body>
    <h1>¡Bienvenido a mi sitio web!</h1>
  </body>
</html>
```

### 🌐 View Transitions completas en todo el sitio (modo SPA)

Importamos y agregamos nuestro componente dentro del head común o de diseño compartido. Astro se encargará de crear animaciones de página predeterminadas basadas en las similitudes entre la antigua y la nueva, y también proporcionará un comportamiento de respaldo para los navegadores que no la admitan.

Veamos mejor este caso a continuación:

```javascript
---
import { ViewTransitions } from 'astro:transitions';
---
```

```html
<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
<meta name="generator" content={Astro.generator} />

<!-- Etiquetas Meta Primarias -->
<title>{title}</title>
<meta name="title" content={title} />
<meta name="description" content={description} />

<ViewTransitions />
```

### 💫 Directivas de animación integradas

Astro viene con algunas animaciones para anular la transición fade predeterminada. Se necesita agregar la directiva de transition:animate a elementos individuales para personalizar el comportamiento de transiciones específicas.

* `fade` (por defecto): Una animación de fundido cruzado, es decir, el contenido antiguo se desvanece y el nuevo contenido se desvanece al aparecer.
* `initial`: Optar por no usar la animación de fundido cruzado y en su lugar utilizar el estilo predeterminado del navegador.
* `slide`: Una animación donde el contenido antiguo se desliza hacia la izquierda y el nuevo contenido se desliza desde la derecha. En la navegación atrás, la animación actúa de forma opuesta.
* `none`: Desactiva las animaciones predeterminadas del navegador. Úsalo en el elemento `<html>` de una página para desactivar el fade predeterminado para cada elemento en la página.

```javascript
---
import CommonHead from '../components/CommonHead.astro';
---
```

```html
<html transition:animate="none">
  <head>
    <CommonHead />
  </head>
  <body>
    <header>
      ...
    </header>
    <!-- Anula la configuración predeterminada de tu página en un solo elemento -->
    <main transition:animate="slide">
      ...
    </main>
  </body>
</html>
```

> Continuando con los principios de Astro, en este caso desde el aspecto visual para el usuario, este componente tiene muchas cosas, así que si deseas saber más te invito a este [enlace](https://docs.astro.build/es/guides/view-transitions/).

Te invito a que visites la siguiente página de **Astro - Precarga**.
