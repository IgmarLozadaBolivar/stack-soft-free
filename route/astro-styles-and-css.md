---
icon: planet-ringed
---

# Astro - Styles and CSS

{% hint style="info" %}
Astro fue diseñado para que estilar y escribir CSS sea pan comido.
{% endhint %}

Escribe tu propio CSS directamente dentro de un componente de Astro o importa tu biblioteca de CSS favorita como [Tailwind](setup-integraciones.md#integrando-el-framework-de-tailwind). También es compatible con lenguajes de estilo avanzados como [Sass](../pagina-en-construccion.md) y [Less](../pagina-en-construccion.md).

### 🎨 Estilando en Astro

Estilar un componente de Astro es tan fácil como agregar una etiqueta `<style>` a tu componente o plantilla de página. Cuando colocas una etiqueta `<style>` dentro de un componente de Astro, Astro detectará el CSS e incluirá tus estilos automáticamente.

```html
<style>
  h1 { color: red; }
</style>
```

#### 📍 Estilos locales

Las reglas de CSS en Astro `<style>` tienen **un alcance local de forma predeterminada**. Los estilos con alcance local se compilan para que sólo se apliquen al HTML escrito dentro de ese mismo componente. El CSS escrito dentro de un componente de Astro se encapsula automáticamente dentro del mismo.

```html
<style>
  h1 {
    color: red;
  }

  .text {
    color: blue;
  }
</style>
```

Se compila en esto:

```html
<style>
  h1[data-astro-cid-hhnqfkh6] {
     color: red;
  }
  .text[data-astro-cid-hhnqfkh6] {
    color: blue;
  }
</style>
```

Los estilos locales no se filtran y no afectarán al resto de tu sitio web.

{% hint style="danger" %}
Los estilos locales tampoco se aplicarán a otros componentes de Astro contenidos dentro del maquetado. Si necesitas estilar un componente hijo, considera envolver ese componente en un `<div>` (u otro elemento) que luego puedas estilar.
{% endhint %}

#### 🌍 Estilos globales

Si bien recomendamos estilos locales para la mayoría de los componentes, eventualmente puedes encontrar una razón válida para escribir CSS global. Puedes desactivar el CSS con alcance local predeterminado con el atributo `<style is:global>`.

```html
<style is:global>
  /* Global, entregada tal como está al navegador.
     Se aplica a todas las etiquetas <h1> de tu sitio web. */
  h1 { color: red; }
</style>
```

#### 🎛️ Variables de CSS

La etiqueta `<style>` de Astro puede hacer referencia a cualquier variable CSS disponible en la página. También puedes pasar variables CSS directamente desde el frontmatter de tu componente usando la directiva `define:vars`.

```javascript
---
const foregroundColor = "rgb(221 243 228)";
const backgroundColor = "rgb(24 121 78)";
---
```

```html
<style define:vars={{ foregroundColor, backgroundColor }}>
  h1 {
    background-color: var(--backgroundColor);
    color: var(--foregroundColor);
  }
</style>
<h1>Hola</h1>
```

#### 📝 Estilos en línea

Puedes estilar elementos HTML en línea utilizando el atributo `style`. Esto puede ser un string CSS o un objeto de propiedades CSS.

```html
<p style={{ color: "brown", textDecoration: "underline" }}>My text</p>
<p style="color: brown; text-decoration: underline;">My text</p>
```

### 🔌 Integraciones de CSS

#### 🌬️ Tailwind

De esto ya hablamos en su momento, te invito a seguir esta página 👉 [Setup - Integraciones - Tailwind](setup-integraciones.md#integrando-el-framework-de-tailwind).

> Cada vez más cerca de finalizar la travesía con Astro y adentrarnos con Vue.

Te invito a que visites la siguiente página de **Astro - Alias**.
