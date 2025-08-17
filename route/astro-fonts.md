---
hidden: true
icon: planet-ringed
---

# Astro - Fonts

{% hint style="info" %}
En esta página te mostraremos como añadir fuentes web a tu proyecto y usarlas en tus componentes.
{% endhint %}

Escribe tu propio CSS directamente dentro de un componente de Astro o importa tu biblioteca de CSS favorita como [Tailwind](setup-integraciones.md#integrando-el-framework-de-tailwind). También es compatible con lenguajes de estilo avanzados como [Sass](../pagina-en-construccion.md) y [Less](../pagina-en-construccion.md).

### 🖼 Usando un archivo local

Cuando hablamos de archivos locales, hablamos de archivos `.woff2`, `.ttf`, `.woff` o cualquier otro, como hacemos para añadirlo, sería de la siguiente manera, tenemos una fuente de `DistantGalaxy.woff`:

{% stepper %}
{% step %}
#### Añadimos nuestro archivo a la carpeta de `public/fonts/`.
{% endstep %}

{% step %}
#### Agregamos la siguiente declaración `@fontface`  a nuestro CSS.

Esto puede ser un `.css`  global que importes, un bloque de `<style is:global>` o en un bloque `<style>`  en un diseño o componente específico donde quieras usar esa fuente.

```css
/* Registra tu font family personalizada y le 
indicamos al navegador dónde encontrarla. */
@font-face {
  font-family: 'DistantGalaxy';
  src: url('/fonts/DistantGalaxy.woff') format('woff');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}
```
{% endstep %}

{% step %}
#### Usamos el valor de `font-family`  de la declaración `@fontface`  para dar estilos a nuestro componente o diseño.

{% code title="src/pages/example.astro" %}
```javascript
---
---
```
{% endcode %}

{% code title="src/pages/example.astro" %}
```html
<h1>En una galaxia muy, muy lejana...</h1>

<p>¡Las fuentes personalizadas hacen que mis títulos se vean mucho mejor!</p>

<style>
h1 {
  font-family: 'DistantGalaxy', sans-serif;
}
</style>
```
{% endcode %}
{% endstep %}
{% endstepper %}

### 🔤 Usando Fontsource

El proyecto [Fontsource](https://fontsource.org/) simplifica el uso de [Google Fonts](https://fonts.google.com/) y otras fuentes de código abierto. Esta comunidad nos provee módulos `npm` que puedes instalar para las fuentes que quieras utilizar.

{% stepper %}
{% step %}
#### Busca la fuente de tu necesidad, para este ejemplo usaremos [Twinkle Star](https://fontsource.org/fonts/twinkle-star).&#x20;
{% endstep %}

{% step %}
#### Instala el paquete fuente que hayas elegido.

```bash
npm install @fontsource/twinkle-star
```
{% endstep %}

{% step %}
#### Importamos el paquete de fuente en el componente donde quieras usar la fuente, por lo general queréis tener tu fuente de forma global.

```javascript
---
import '@fontsource/twinkle-star';
---
```
{% endstep %}

{% step %}
#### Usamos el nombre de la fuente como se muestra `body`  en la página de Fontsource para el valor de `font-family`.

```css
h1 {
  font-family: "Twinkle Star", cursive;
}
```
{% endstep %}
{% endstepper %}

### 📝 Registrando fuentes personalizadas con Tailwind

Estaremos trabajando muy pronto en esta sección.

> Ya nos fuimos apropiando de la UI tanto con Astro y Tailwind, se nos viene encima Vue, no?

Te invito a que visites la siguiente página de **Astro - Images**.
