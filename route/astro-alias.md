---
hidden: true
icon: planet-ringed
---

# Astro - Alias

{% hint style="success" %}
Atajos que nos evitan dolores de cabeza.
{% endhint %}

Los alias ayudan a mejorar la experiencia de desarrollo de repositorios con muchas carpetas o importaciones relativas.

```javascript
---
import Button from './components/controls/Button.astro';
import LogoUrl from '../../assets/logo.png?url';
---
```

En este código, un desarrollador necesitaría comprender la relación de archivos entre todos los componentes, conocer esas rutas, porque si en algún caso movemos un archivo, entonces nos toca de forma manual tener que hacerlo.

Para agregar los alias que necesitamos, necesitamos hacer uso del archivo tsconfig.json y agregar lo siguiente:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["src/components/*"],
      "@assets/*": ["src/assets/*"]
    }
  }
}
```

Si tenemos nuestro servidor en ejecución y realizamos el cambio que hicimos anteriormente, no pasa nada, el servidor se reiniciará de forma automática tras el cambio de configuración. Permitiéndonos poder importar usando los alias y no sus rutas relativas de la siguiente manera:

```javascript
---
import Button from '@components/Button';
import LogoUrl from '@assets/logo.png?url';
---
```

> Estos alias, se integran dentro de VSCode y otros IDE, para que puedan interpretar los alias y saber desde donde se están llamando, genial? Verdad!

Te invito a que visites la siguiente página de **Astro - Fonts**.
