---
hidden: true
icon: planet-ringed
---

# Astro - Images

{% hint style="info" %}
Podemos trabajar nuestras imágenes en nuestro sitio de varias formas, desde las que están almacenadas localmente, enlazadas a una URL o gestionadas en un CMS o CDN.
{% endhint %}

Astro toma nuestras imágenes y las optimiza de forma automática (WebP, tamaño adaptativo, carga diferida).

### 📂 ¿Dónde debemos guardar las imágenes?

#### `src` vs `public`&#x20;

Las imágenes que tengamos locales se mantendrán en `src/` cuando sea posible, para que Astro pueda transformar, optimizar y empaquetarlas. Los archivos del directorio `/public` siempre se sirven o copian tal cómo están, sin ningún procesamiento.

Nuestras imágenes locales puede ser totalmente utilizadas por todos nuestros archivos `.astro,` `.md`, `.mdx`, `.mdoc` y por otros frameworks de ui, como `.vue`, `.jsx`, `.tsx`, `.angular` y demás.

Si deseas almacenar imágenes dentro de public, es porque consideras evitar cualquier tipo de procesamiento o para tener un enlace público directo a ellas.

#### 🌍 Imágenes remotas

Si deseas optar por almacenar tus imágenes de forma remota, es decir, en la nube, en un servidor, en un CDN y demás, en otras palabras un sistema de gestión de contenido (CMS) o en una plataforma de gestión de assets digitales (DAM).

Podemos contar con una protección adicional de que nuestro proyecto pueda tratar con fuentes externas, las imágenes remotas solo se procesarán desde `fuentes de imágenes autorizadas`  especificadas en nuestro archivo de configuración `astro.config.mjs` , sin embargo cualquier imagen remota puede ser mostrada.

### 📄 Imágenes en archivos `.astro`&#x20;

Para utilizar nuestras imágenes guardadas localmente, dentro de un archivo `.astro` , necesitamos importarlas. Las imágenes remotas y las que se encuentran en el directorio `public/`  no requiere ser importadas.

Adicional a lo mencionado anteriormente, necesitamos importar y utilizar un componente que viene integrado con el framework de Astro, en este caso hacemos mención a `<Image />`  para optimizar nuestras imágenes usando `astro:assets` . En Astro podemos utilizar las etiquetas `<img>` de la sintaxis de HTML, pero omitimos el procesamiento de imágenes, veamos el ejemplo:

{% code title="src/pages/blog/my-images.astro" %}
```javascript
---
import { Image } from 'astro:assets';
import ImagenLocal from '../../assets/images/logo.png';
---
```
{% endcode %}

{% code title="src/pages/blog/my-images.astro" %}
```html
<Image src={ImagenLocal} alt="logotipo" /> <!-- Acceso local en src -->
<Image src="/images/logo.png" alt="logotipo" width="50" height="50" /> <!-- Acceso local en public -->
<Image src="https://s3/logo.png" alt="logotipo" width="50" height="50" /> <!-- Acceso remoto -->

<img src={ImagenLocal.src} alt="logotipo"> <!-- Acceso local en src -->
<img src="/images/logo.png" alt="logotipo"> <!-- Acceso local en public -->
<img src="https://s3-bucket/logo.png" alt="logotipo"> <!-- Acceso remoto -->
```
{% endcode %}

### `<Image />` `(astro:assets)`&#x20;

Al utilizar el componente integrado `<Image />` de Astro, lo usamos para procesar y optimizar nuestras imágenes locales y remotas.

{% hint style="danger" %}
Las imágenes en la carpeta `public/` , así como las imágenes remotas no configuradas, pueden usar el componente, pero no se procesarán ni optimizarán.
{% endhint %}

Con este componente podemos transformar las dimensiones , el tipo de archivo y la calidad de una imagen local o remota no autorizada. La etiqueta de HTML `<img>`  incluye atributos `alt`, `loading` y `decoding`, e infiere las dimensiones para evitar el **Desplazamiento Acumulativo de Diseño (CLS)**.

{% hint style="info" %}
¿Qué es el Desplazamiento Acumulativo de Diseño?

Es una métrica de Core Web Vital para medir cuánto se ha desplazado el contenido de tu página durante la carga. El componente Image se optimiza para el CLS al establecer automáticamente el `ancho` y `alto`  correctos para las imágenes locales.
{% endhint %}

Veamos mejor este caso, a través de este ejemplo:

{% code title="myComponent.astro" %}
```javascript
import { Image } from 'astro:assets';
import myImage from '../assets/my_image.png'; // La imagen es 1600x900
```
{% endcode %}

{% code title="myComponent.astro" %}
```html
<Image src={myImage} alt="Una descripción de mi imagen." />
```
{% endcode %}

{% code title="Salida en el navegador" %}
```html
<img
  src="/_astro/my_image.hash.webp"
  width="1600"
  height="900"
  decoding="async"
  loading="lazy"
  alt="Una descripción de mi imagen."
/>
```
{% endcode %}

#### 📋 Propiedades

*   src (requerido)

    El valor de `src` depende de donde esté ubicado tu archivo de imagen:

    * **Imágenes locales en** `src/` - también debes importar la ruta relativa o el alias de importación para usar esa ruta como el valor de src.
    * **Imágenes locales en** `public/` - Utiliza la ruta de archivo de la imagen.
    * **Imágenes remotas** - Tomamos la URL completa de la imagen como valor de src.
*   alt (requerido)

    Lo utilizamos para proporcionar un texto alternativo para las imágenes.
*   width y height (requerido para las imágenes en public/)

    Estas propiedades nos permiten definir las dimensiones, cuando se utilizan el aspecto original, tanto la propiedad como `width` y `height` son opcionales.

Existen muchas más propiedades, pero en este caso estas son las fundamentales, si queréis conocer las demás o ser paciente para ampliar más esta documentación, independientemente de tu elección, te proporcionamos temporalmente la documentación 👉 [Saber más](https://docs.astro.build/es/guides/images/#image--astroassets).

> Hemos visto algo muy fundamental, que sigue los principios de Astro, eficiencia y rendimiento.

Te invito a que visites la siguiente página de **Astro - View Transitions**.
