---
hidden: true
icon: planet-ringed
---

# Astro - Enrutamiento

{% hint style="info" %}
Anteriormente vimos lo que eran las páginas en Astro y que sabemos que necesitan del enrutamiento para funcionar y trabajar de forma correcta, por lo tanto vamos a profundizar más.
{% endhint %}

Astro utiliza enrutamiento basado en archivos, cómo mencionamos en la anterior página que te invito a echarle un vistazo más 👉 [Astro - Páginas](astro-paginas.md).

Todo esto del enrutamiento tiene como fin de generar las URLs finales según el contenido de la carpeta `src/pages/` .

### 🟢 Tipos de páginas

* .astro
* .md
* .mdx (con la integración de mdx) instalada
* .html
* .js y .ts (endpoints)

### Enrutamiento basado en archivos

Astro aprovecha una estrategia de enrutamiento llamado **enrutamiento basado en archivos**. Cada `.astro`  en la carpeta `src/pages`  se convierte en una página o un endpoint en nuestro proyecto de acuerdo a su ruta.

{% hint style="info" %}
¿Cómo así que un .astro es una ruta?

Si creamos por ejemplo **about**, dentro de `src/pages` , su ruta de acceso será `https://tusitio.com/about` .
{% endhint %}

### Link entre páginas

Cuando escribimos un HTML estándar hemos utilizado la etiqueta o elemento **anchor**, que viene siendo esta pequeña amiga 👉\<a>👈, veámoslo más detallado a continuación:

```html
<a href="#">Este es un link para enlazar hacia otra página.</a>
```

Astro, utiliza una ruta relativa en base al dominio raíz cómo enlace, no una ruta de archivo relativa, pero... ¿Cómo es eso?, veamos a continuación ambos casos:

{% tabs %}
{% tab title="Ruta de dominio relativa" %}
Resulta que cuando ejecutas tu servidor, nos entrega una url que suele ser de la siguiente manera:

`https://localhost:4321`&#x20;

Resulta que si teníamos un archivo llamado about.astro, lo recuerdas? Bueno de que manera accederíamos a ese archivo, sería de la siguiente manera:

`https//localhost:4321/about`&#x20;

Si comparas uno con el otro, la diferencia es que se le adiciona un **slash** y **el nombre del archivo** al que queremos acceder, que en este caso es **about**.

Ahora cómo sería esto dentro de la etiqueta \<a>, vamos a verlo:

```html
<a href="/about"> About Us </a>
// Si observamos, no lo estoy pasando la url
https://localhost:4321/about
```

Internamente Astro sabe que desde cualquier página que el usuario esté, el siempre conocerá siempre la ruta relativa del dominio, por lo tanto solo nos pide un _"/"_, y la ruta o nombre del archivo al que queremos que vaya el usuario, en este ejemplo sería **about**.

Ahora te invito a ver el segundo caso que viene siendo **Ruta de archivo relativa**.
{% endtab %}

{% tab title="Ruta de archivo relativa" %}
Tomaremos el mismo caso cuando ejecutas tu servidor, nos entrega una url que suele ser de la siguiente manera:

`https://localhost:4321`&#x20;

Resulta que si teníamos un archivo llamado about.astro dentro de pages, lo recuerdas? Bueno de que manera accederíamos a ese archivo, sería de la siguiente manera:

`https//localhost:4321/pages/about.astro`&#x20;

Si comparas uno con el otro, la diferencia es que se le adiciona un **slash**, la **carpeta** donde se encuentra nuestro archivo y finalmente el **nombre** **del archivo** al que queremos acceder, que en este caso es **about**.

Ahora cómo sería esto dentro de la etiqueta \<a>, vamos a verlo:

```html
// Este sería el primer caso
<a href="https//localhost:4321/pages/about.astro"> About Us </a>

// El segunda caso sería así, que vendría siendo más corto y solo aplica
// si el about.astro está al mismo nivel que index.astro
<a href="./about.astro"> About Us </a>
```

Ahora ya caes en cuenta, la diferencia entre **ruta de dominio relativa** y **ruta de archivo relativa**.
{% endtab %}
{% endtabs %}

### 🔍  Páginas de Astro

Las páginas de Astro utilizan la extensión `.astro`  y tienen las mismas funcionalidades que los componentes de Astro.

{% code title="src/pages/index.astro" overflow="wrap" %}
```html
---
---
<html lang="es">
  <head>
    <title>Mi página de inicio</title>
  </head>
  <body>
    <h1>Bienvenido a mi sitio web</h1>
  </body>
</html>
```
{% endcode %}

Para evitar repetir los mismos elementos HTML en cada página, puedo mover los elementos `<head>`  y `<body>`  a sus propios componentes de plantilla, que ya veremos muy pronto en esta página.

{% hint style="info" %}
¿Podemos usar archivos `.html`? ¿Dónde debemos `incluirlos`? ¿Debemos migrar de `.html` a `.astro`?

1. Como se mencionó anteriormente si podemos manejar, crear y usar archivos de HTML.
2. Podemos incluirlos donde los necesitemos.
3. Es lo más recomendable, ya que si no lo hacemos, perderemos muchas funcionalidades que nos ofrece Astro no serán compatibles con archivos o componentes HTML.
{% endhint %}

### Página de error 404 personalizada

Por defecto Astro, ya integra de forma interna y nativa una página 404, pero podemos agregar nuestra propia página error 404, simplemente debemos crear un archivo `404.astro`  o `404.md`  en `src/pages` .

### Página de error 500 personalizada

Hacemos lo mismo que el caso de la página de 404, simplemente creamos un archivo `500.astro`  dentro de `src/pages` .

> Ya estamos cada vez más cerca de adentrarnos a la UI.

Te invito a que visites la siguiente página de **Astro - Enrutamiento**.
