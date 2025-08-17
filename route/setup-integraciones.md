---
icon: folder-tree
---

# Setup - Integraciones

{% hint style="info" %}
Estás emocionado, porque estáis más cerca de volverte un Dios en el desarrollo web moderno, espero que así sea, porque te cuento que vamos a realizar 2 integraciones bastante importantes, un framework de interfaces de usuario y un framework de estilado.
{% endhint %}

Como hemos venido mencionando desde páginas anteriores, podemos crear nuestras páginas web con Astro sin sacrificar nuestros componentes de los frameworks favoritos que tenemos. Necesitaremos crear islas con el framework de ui que queramos.

{% hint style="danger" %}
Si no sabéis que es una Isla, te invito a leer esta página, porque no podéis lanzarte a algo si no conoces sus fundamentos, te invitamos a hacerlo, sigue este enlace [Islas](setup-conceptos.md#arquitectura-de-islas).
{% endhint %}

Astro admite una variedad de frameworks populares, incluidos  incluidos [React](https://react.dev/), [Preact](https://preactjs.com/), [Svelte](https://svelte.dev/), [Vue](https://vuejs.org/), [SolidJS](https://www.solidjs.com/), [AlpineJS](https://alpinejs.dev/) y [Lit](https://lit.dev/) con integraciones oficiales.

También podemos encontrar más integraciones gracias a las [integraciones de frameworks mantenidas por la comunidad](https://astro.build/integrations/?search=\&categories%5B%5D=frameworks) (por ejemplo, Angular, Qwik, Elm) en nuestro directorio de integraciones.

### 🟢 Integrando el framework de Vue

#### 🤨 ¿Qué es Vue.js?

{% hint style="info" %}
Vue es un **framework progresivo de JavaScript** diseñado para construir interfaces de usuario (UI).
{% endhint %}

Eso significa que podéis usarlo tanto para cosas simples (como un contador) como para construir aplicaciones web completas con múltiples páginas y funcionalidades complejas.

A diferencia de otros frameworks más "todo o nada", Vue te permite **empezar de a poco**. Podéis usarlo solamente donde necesitáis interactividad sin tener que reescribir todo tu sitio.

#### 🔍 ¿Y qué lo hace especial?

* Tiene una **sintaxis muy amigable** y fácil de aprender.
* Su estructura basada en componentes hace que el código sea **más organizado y reutilizable**.
* Ofrece **reactividad automática**: si un dato cambia, la interfaz se actualiza sola.
* Es muy **ligero y rápido**.

#### ⚙️ ¿Por qué lo integramos con Astro?

<details>

<summary>Reactividad</summary>

Formularios que reaccionen al usuario.

</details>

<details>

<summary>Interactividad</summary>

Interacción en tiempo real (como likes o comentarios).

</details>

<details>

<summary>Funcionalidad</summary>

Funcionalidades como sliders, modales, pestañas, carruseles, etc.

</details>

Ahí es donde entra **Vue**. Gracias a la filosofía de **"JavaScript bajo demanda"** de Astro, podéis decirle:

> “Usa Vue **solo en este componente** que necesita interactividad, y no cargues nada más.”

Así obtenemos lo mejor de dos mundos:

* Sitios **rápidos, ligeros y optimizados** gracias a Astro.
* Componentes **interactivos y potentes** gracias a Vue.

{% hint style="info" %}
Estaremos conociendo mucho más del framework Vue.js en su respectivo momento, estamos trabajando en profundizar más en ello, mientras tanto podéis continuar con la instalación, integración y configuración con Astro.
{% endhint %}

#### 💻  Instalando e integrando Vue

Vamos a ver más a detalle cada uno de estos, así que estaos atentos, porque es de vital importancia y no cometer errores que nos cuesten tiempo, trabajo y sacrificio.

{% stepper %}
{% step %}
📁 Instalación&#x20;

Astro incluye un comando que podemos usar en nuestra terminal Warp `astro add`  para automatizar la configuración de las integraciones oficiales.

Para instalar `@astrojs/vue` , ejecuta lo siguiente desde el directorio de tu proyecto y sigue las instrucciones:

```bash
npx astro add vue
```

Vamos a desglosar la acción o comando que ejecutamos:

* `npx`  👉 Ejecuta paquetes de npm sin necesidad de instalarlos globalmente. Es decir, usa directamente el ejecutable que viene del paquete sin que tengas que instalarlo antes con `npm install`.
* `astro`  👉 Es el nombre del paquete CLI de Astro. Al usar `npx astro`, estás accediendo a los comandos que Astro CLI ofrece.
* `add`  👉 Es un subcomando de `astro`. Su función es **agregar integraciones oficiales** al proyecto, como Vue, React, Tailwind, etc.
* `vue`  👉 Especifica qué integración se desea agregar. En este caso, `vue` le indica a Astro que vas a trabajar con componentes Vue en tu proyecto.

Apenas ejecutamos este comando, nos va a salir en nuestra consola, un asistente donde tendremos que seguir esta serie de opciones a continuación:

```bash
√ Resolving packages...

Astro will run the following command:
If you skip this step, you can always run it yourself later

npm i @astrojs/vue@^5.1.0 vue@^3.5.18

? Continue? >> (Y/n)
// Simplemente ingresemos la letra Y en mayúscula, presionamos Enter
```

Luego nos mostrará lo siguiente:

<pre class="language-bash"><code class="lang-bash">| Installing dependencies..

Astro will make the following changes to your config file:
╭ astro.config.mjs ─────────────────────────────╮
│ // @ts-check                                  │
│ import { defineConfig } from 'astro/config';  │
│                                               │
│ <a data-footnote-ref href="#user-content-fn-1">import vue from '@astrojs/vue';</a>           │
│                                               │
│ // https://astro.build/config                 │
│ export default defineConfig({                 │
│   <a data-footnote-ref href="#user-content-fn-2">integrations: [vue()]</a>                    │
│ });                                           │
╰───────────────────────────────────────────────╯

? Continue? (Y/n)
// Escribi Y y presionamos Enter
</code></pre>

A continuación, nos mostrará lo siguiente:

<pre class="language-bash"><code class="lang-bash">success  Added the following integration to your project:
  - @astrojs/vue
  
Astro will make the following changes to your tsconfig.json:
╭ tsconfig.json ──────────────────────────╮
│ {                                       │
│   "extends": "astro/tsconfigs/strict",  │
│   "include": [                          │
│     ".astro/types.d.ts",                │
│     "**/*"                              │
│   ],                                    │
│   "exclude": [                          │
│     "dist"                              │
│   ],                                    │
│   <a data-footnote-ref href="#user-content-fn-3">"compilerOptions"</a>: {                │
│     <a data-footnote-ref href="#user-content-fn-4">"jsx": "preserve"</a>                 │
│   }                                     │
│ }                                       │
╰─────────────────────────────────────────╯

? Continue? » (Y/n)
// Escribimos Y y presionamos Enter
</code></pre>

Este será lo último que nos mostrará la consola y con eso, ya finalizamos la instalación, integración y configuración en nuestro proyecto:

```bash
success  Successfully updated TypeScript settings
```
{% endstep %}
{% endstepper %}

### 🔵 Integrando el framework de Tailwind

#### 🤨 ¿Qué es Tailwind CSS?

{% hint style="info" %}
Tailwind es un **framework de utilidades para CSS**.
{% endhint %}

En lugar de escribir tus propios estilos desde cero o usar clases predefinidas como en Bootstrap, Tailwind te da **pequeñas clases reutilizables (utilidades)** que representan estilos específicos: margen, padding, color, tamaño, alineación, etc.

#### 🧠 ¿Por qué lo usaremos?

Tailwind resuelve muchos de los dolores comunes que enfrentamos al escribir CSS a mano:

| Problema común                    | Cómo lo soluciona Tailwind                                                     |
| --------------------------------- | ------------------------------------------------------------------------------ |
| Repetir estilos o copiar clases   | Usa clases reutilizables                                                       |
| Estilos que se desordenan         | Todo se mantiene visual y legible desde el HTML                                |
| Tener que nombrar miles de clases | No tenéis que inventar nombres como `.boton-principal-activo-verde-hovered-v2` |
| CSS gigante y poco optimizado     | Tailwind elimina todo lo que no usas en producción (¡purga automática!)        |

#### 🧩 ¿Por qué lo integramos con Astro y Vue?

Astro y Vue son frameworks modernos, y Tailwind también. Funcionan **a la perfección juntos** porque:

* Astro y Vue permite importar y configurar Tailwind de forma directa.
* Astro genera archivos optimizados, Vue componentes que necesitan estilos y Tailwind se encarga de reducir los estilos al mínimo.
* Podéis usar Tailwind tanto en componentes (`.astro o .vue`) o donde lo necesites.

{% hint style="info" %}
Estaremos conociendo mucho más del framework Tailwind CSS en su respectivo momento, estamos trabajando en profundizar más en ello, mientras tanto podéis continuar con la instalación, integración y configuración con Astro.
{% endhint %}

{% stepper %}
{% step %}
📁 Instalación

Así cómo antes como el caso de Vue, Astro incluye un comando que podemos usar en nuestra terminal Warp `astro add`.

Para instalar `@tailwindcss/vite` , ejecuta lo siguiente desde el directorio de tu proyecto y sigue las instrucciones:

```bash
npx astro add tailwind
```

Vamos a desglosar la acción o comando que ejecutamos:

* `npx`  👉 Ejecuta paquetes de npm sin necesidad de instalarlos globalmente. Es decir, usa directamente el ejecutable que viene del paquete sin que tengas que instalarlo antes con `npm install`.
* `astro`  👉 Es el nombre del paquete CLI de Astro. Al usar `npx astro`, estás accediendo a los comandos que Astro CLI ofrece.
* `add`  👉 Es un subcomando de `astro`. Su función es **agregar integraciones oficiales** al proyecto, como Vue, React, Tailwind, etc.
* `tailwind`👉 Especifica qué integración se desea agregar. En este caso, `tailwind`le indica a Astro que vas a trabajar con el estilado de Tailwind en tu proyecto.

Apenas ejecutamos este comando, nos va a salir en nuestra consola, un asistente donde tendremos que seguir esta serie de opciones a continuación:

```bash
√ Resolving packages...

  Astro will run the following command:
  If you skip this step, you can always run it yourself later

 ╭──────────────────────────────────────────────────────╮
 │ npm i @tailwindcss/vite@^4.1.11 tailwindcss@^4.1.11  │
 ╰──────────────────────────────────────────────────────╯

? Continue? » (Y/n)
// Escribimos Y, para continuar pulsamos Enter
```

Luego nos mostrará lo siguiente:

<pre class="language-bash"><code class="lang-bash">√ Installing dependencies...

  <a data-footnote-ref href="#user-content-fn-5">Astro will scaffold ./src/styles/global.c</a>

? Continue? » (Y/n)
// Escribimos Y, presionamos Enter para continuar
</code></pre>

A continuación, nos mostrará lo siguiente:

<pre class="language-bash"><code class="lang-bash">Astro will make the following changes to your config file:

 ╭ astro.config.mjs ────────────────────────────────── ╮
 │ // @ts-check                                        │
 │ import { defineConfig } from 'astro/config';        │
 │                                                     │
 │ import vue from '@astrojs/vue';                     │
 │                                                     │
 │ <a data-footnote-ref href="#user-content-fn-1">import tailwindcss from '@tailwindcss/vite';</a>  │
 │                                                     │
 │ // https://astro.build/config                       │
 │ export default defineConfig({                       │
 │   integrations: [vue()],                            │
 │                                                     │
 │   <a data-footnote-ref href="#user-content-fn-6">vite:</a> {                                           │
 │     <a data-footnote-ref href="#user-content-fn-2">plugins: [tailwindcss()]</a>                     │
 │   }                                                 │
 │ });                                                 │
 ╰─────────────────────────────────────────────────────╯

? Continue? » (Y/n)
// Escribimos Y, presionamos Enter para continuar
</code></pre>

Este será lo último que nos mostrará la consola y con eso, ya finalizamos la instalación, integración y configuración en nuestro proyecto:

<pre class="language-bash"><code class="lang-bash"> success  Added the following integration to your project:
  - tailwind action required  You must import your Tailwind 
  stylesheet, e.g. in a shared layout:

 ╭ src/layouts/Layout.astro ──────────╮
 │ ---                                │
 │ <a data-footnote-ref href="#user-content-fn-7">import '../styles/global.css'</a>  │
 │ ---                                │
 ╰────────────────────────────────────╯
</code></pre>

Por poco se me escapa algo, en el anterior bloque de código, el asistente nos especifica que debemos buscar donde importar nuestro `global.css` , pero tenemos un pequeño problema, se desconoce si se trabajarán layouts o simplemente se insertará directamente en el `index.astro`  estamos en debate con esa situación.

Pero algo si es seguro, que se integre directamente en un layout, que ya muy pronto nos estaremos apropiando de esos conocimientos.
{% endstep %}
{% endstepper %}

> ¿Cómo te has sentido hasta ahora? Te invitamos a seguir en esta travesía.

Espero que así sea, ya cada vez que nos adentramos, nos apropiamos más, te invitamos a seguir en esta travesía y nos vemos en **Astro - Páginas**.

[^1]: Esto es lo nuevo que se agregará!

[^2]: Así cómo antes con el caso del import, esto también se agregará!

[^3]: Esto será bastante importante más adelante!

[^4]: Esto debemos dejarlo cómo está, porque es una configuración por defecto.

[^5]: Nos indica una ruta, donde&#x20;

[^6]: Estas son configuraciones para vite, que también lo veremos a su debido tiempo.

[^7]: Nos está comentando que debemos agregar esta línea de código para que se empiecen a aplicar el framework sobre todas las páginas.
