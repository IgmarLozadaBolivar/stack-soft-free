---
hidden: true
icon: planet-ringed
---

# Astro - Precarga (opcional)

{% hint style="info" %}
Los tiempos de carga de las páginas juegan un papel importante en la usabilidad y el disfrute general de un sitio.
{% endhint %}

La **precarga opcional** de Astro aporta los beneficios de las navegaciones de páginas casi instantáneas a su aplicación multipágina (MPA) a medida que sus visitantes interactúan con el sitio.

### 🛠 Habilitar la precarga

Puedes habilitar la precarga con la configuración `prefetch`, dentro de nuestro archivo de configuración:

```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  prefetch: true
});
```

Un script de precarga se agregará a todas las páginas de tu sitio. Luego puedes agregar el atributo `data-astro-prefetch` a cualquier enlace `<a />` en tu sitio para optar por la precarga. Cuando pasa el cursor sobre el enlace, el script buscará la página en segundo plano.

```html
<a href="/about" data-astro-prefetch>
```

{% hint style="danger" %}
Toma en cuenta que la precarga solo funciona para los enlaces dentro de tu sitio, y no para los enlaces externos.
{% endhint %}

### ⚙ Configuración de precarga

#### 📈 Estrategias de precarga

Astro admite 4 estrategias de precarga para varios casos de uso:

* `hover` (por defecto): Precarga cuando pasas el cursor o te enfocas en el enlace.
* `tap`: Precarga justo antes de hacer clic en el enlace.
* `viewport`: Precarga cuando los enlaces entran en el viewport.
* `load`: Precarga todos los enlaces en la página después de que la página se ha cargado.

Puedes especificar una estrategia para un enlace individual pasándola al atributo `data-astro-prefetch`:

```html
<a href="/about" data-astro-prefetch="tap">Acerca</a>
```

Cada estrategia está ajustada para precargar solo cuando sea necesario y ahorrar el ancho de banda de tus usuarios. Por ejemplo:

* Si un visitante está usando el [modo ahorro de datos](https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/saveData) o tiene una [conexión lenta](https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/effectiveType), la precarga volverá a la estrategia `tap`.
* Desplazarse rápidamente sobre los enlaces no los precargará.
* Los enlaces que usan la estrategia `viewport` o `load` se precargan con una prioridad más baja para evitar obstruir la red.

#### 🔗 Precargar todos los enlaces de forma predeterminada

Si quieres precargar todos los enlaces, incluidos los que no tienen el atributo `data-astro-prefetch`, puedes establecer `prefetch.prefetchAll` en `true`:

```javascript
 import { defineConfig } from 'astro/config';

export default defineConfig({
  prefetch: {
    prefetchAll: true
  }
});
```

Puedes optar por no precargar los enlaces individuales estableciendo `data-astro-prefetch="false"`:

```html
<a href="/about" data-astro-prefetch="false">Acerca</a>
```

> Existen muchas más estrategias de precarga, así como también usar la precarga con las transiciones visual dentro de Astro, si deseas saber más, te invito a este [enlace](https://docs.astro.build/es/guides/prefetch/#configuraci%C3%B3n-de-precarga).

Te invito a que visites la siguiente página de **Astro - Complementos**.
