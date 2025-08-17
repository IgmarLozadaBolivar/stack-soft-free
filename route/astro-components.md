---
icon: planet-ringed
---

# Astro - Components

{% hint style="info" %}
Pequeñas piezas modulare que construyen grandes interfaces.
{% endhint %}

Los components o componentes de Astro son los elementos básicos de cualquier proyecto de Astro. Son componentes de plantillas de HTML sin tiempo de ejecución del lado del cliente y utilizan la extensión de archivo `.astro`.

{% hint style="success" %}
Si ya sabéis de HTML, es suficiente para escribir tu primer componente de Astro
{% endhint %}

Los componentes de Astro son extremadamente flexibles, puede ser tan pequeño como un fragmento de HTML, como una colección de etiquetas comunes de `<p>`  que facilita el trabajo con SEO. Los componentes pueden elementos de interfaz de usuario reutilizables, como una cabecera o una tarjeta de perfil, pueden incluso contener un diseño completo o, cuando se encuentran en la carpeta especial `src/pages/` , ser una página completa.

Algo que cabe recalcar, estos componentes no se renderizan en el lado del cliente, se renderizan en el momento de la compilación o bajo demanda. Podemos incluir código JavaScript en el frontmatter de nuestro componente, y todo será eliminado de la página final enviada a los navegadores de nuestros usuarios. El resultado de esta locura es un sitio más rápido, sin ninguna huella de JavaScript añadida por defecto.

Ahora si necesitamos interactividad en un componente, que se suele hacer en esos casos, siendo así tenemos dos alternativas usar la etiqueta estándar `<script>` o integrar componentes de frameworks mediante _**islas cliente**_ cómo vimos en la página de [Setup - Concetos - Arquitectura de Islas](setup-conceptos.md#arquitectura-de-islas).

Pero que pasaría en los casos donde no hablamos de componentes interactivos sino dinámicos o reactivos, bueno siendo ese el caso, se soluciona aplazando su presentación en el servidor, a través de una directiva y denominarlas como islas de servidor, lo recuerdas? Tranquilo te invito a seguir este enlace para saber más sobre [Server Islands](setup-conceptos.md#arquitectura-de-islas). Con esto haríamos que se renderice su contenido cuando esté disponible sin comprometer la carga completa de la página.

{% hint style="warning" %}
Sé que se estarán diciendo, es mucho texto, tranquilos, ya vamos a avanzar a otros conceptos e iremos practicando un poco.
{% endhint %}

### 🌳 Estructura de un componente

Un componente de Astro se compone de dos partes principales: el script del componente y el maquetado del componente. Cada parte cumple una función diferente, pero juntas proveen un marco de trabajo más fácil de utilizar y lo suficientemente expresivo para manejar cualquier cosa que desees construir.

```html
---
// Script del componente (JavaScript) - Frontmatter
---

<!-- Maquetado del componente (HTML + JS) --> - UI
```

### 📜 Script de un componente

Astro utiliza una valla de código `---`  para identificar el script del componente, que se conoce como frontmatter.

Podemos utilizar el script del componente para escribir cualquier código de JavaScript que necesites para renderizar el maquetado, que cosas puede incluir?

* Importar otros componentes de Astro.
* Importar componentes de otros frameworks.
* Importar datos, como un archivo JSON.
* Consultar contenido de una API o base de datos.
* Crear variables que luego podemos referenciar en el maquetado.

Veamos un ejemplo sencillo de esto:

{% code title="src/components/Header.astro" %}
```javascript
---
import TitleAstro from '../components/Title.astro'; // Importando componente .astro
import TitleVue from '../components/Title.vue'; // Importando componente .vue
import algunosDatos from '../data/pokemon.json'; // Importando archivo .json

// Podemos definir props o propiedades para nuestros componentes
// que les permitan hacer algo, ya veremos más a detalle.
const { title } = Astro.props;

// Consultar datos externos, de una API privada o base de datos
// esto es un tema complejo pero estaremos trabajando en ello también.
const datos = await fetch('http://localhost:5000/login.php').then(r => r.json());
---
```
{% endcode %}

{% code title="src/components/Header.astro" %}
```html
<!-- ¡Tu maquetado va aquí! -->
// Como podemos visualizar tenemos un componente .astro llamado Title
// dentro de este componente nos dice que tiene una propiedad o prop title
// donde podemos escribir un texto, lo mismo aplica para el componente .vue.
<TitleAstro title="Hola Mundo desde un componente de Astro" />
<TitleVue title="Hola Mundo desde un componente de Vue" />
```
{% endcode %}

La valla de código o frontmatter está diseñada para garantizar que el código de JavaScript que escribes dentro se encuentre "encapsulado". Este código no se filtrará a tu aplicación, o llegará al usuario final. Puedes escribir código que sea costoso o sensible (como una llamada a una base de datos) sin preocuparte por que estos datos sensibles lleguen al navegador del usuario.

### 📐 Maquetado del componente

El maquetado se encuentra debajo de la malla de código o frontmatter y determina la salida de HTML de tu componente.

Si escribes solo HTML en esta sección, el componente va a renderizar este HTML en cualquier página de Astro donde sea importado o utilizado.

Sin embargo, el maquetado también soporta expresiones de JavaScript, etiquetas de `<style>` y `<script>` de Astro, componentes importados, y `directivas` especiales de Astro. Estos datos o valores definidos en el script pueden ser usados en el maquetado para producir HTML creado dinámicamente.

```javascript
---
import Avatar from '../components/Avatar.astro'; // Importación de un componente
import ReactPokemonComponent from '../components/ReactPokemonComponent.jsx';
const misPokemonesFavoritos = [/* ... */]; // Definición de un Arreglo
const  { title } = Astro.props; // Definición de props o propiedades
---
```

```html
<!-- Dentro de un .astro, podemos usar HTML puro -->
<h1>¡Hola mundo!</h1>

<!-- Podemos utilizar props y otras variables 
definidas en el script del componente: -->
<p>{title}</p>

<!-- Retrasa el renderizado del componente en el lado del servidor -->
<Avatar server:defer>
  <svg slot="alternativo" class="avatar-genérico" transition:name="avatar">...</svg>
</Avatar>

<!-- Incluye otros componentes UI con la directiva de hidratación `client:`: -->
<ReactPokemonComponent client:visible />

<!-- Puedes mezclar HTML con expresiones de JavaScript -->
<ul>
  <!-- Utilizamos nuestro arreglo, lo recorremos con la función
  map, y cada dato que encuentre lo va a contener un li y solo
  accederá al name -->
  {misPokemonesFavoritos.map((data) => <li>{data.name}</li>)}
</ul>
```

### 🏗️ Diseño basado en componentes

Los componentes son diseñados para ser **reusables** y **componibles**. Puedes usar componentes dentro de otros componentes para construir UI más y más avanzada. Por ejemplo, un componente `Button` podría ser usado para crear un componente `ButtonGroup`:

{% code title="src/components/ButtonGroup.astro" %}
```javascript
---
import Button from './Button.astro';
---
```
{% endcode %}

{% code title="src/components/ButtonGroup.astro" %}
```html
<div>
  <Button title="Botón 1" />
  <Button title="Botón 2" />
  <Button title="Botón 3" />
</div>
```
{% endcode %}

### 🧩 Props de componentes

En Astro, las **props de componentes** son como “paquetes de datos” que le envías a un componente para que este se configure o se renderice de cierta forma.

#### 📦 **Piensa en esto así**:

Si un componente es como un molde para hacer galletas, las props son los ingredientes que decides poner.\
El molde es el mismo, pero según los ingredientes (props) que pongas, obtendrás un resultado diferente.

#### 🧠 ¿**Qué son?**

Las props (o “propiedades”) son valores que pasas a un componente Astro cuando lo usas.\
Sirven para que ese componente sea **reutilizable** y no tengas que escribir el mismo HTML varias veces cambiando solo un par de cosas.

🕹️ ¿Cómo se usa en Astro?

Un componente de Astro puede definir y aceptar props. Estas props estarán disponibles para ser utilizadas en el renderizado del maquetado HTML y además estarán disponibles en el script del componente de manera global dentro del objeto `Astro.props`.

Aquí vemos un ejemplo de un componente que recibe una prop `saludo` y otra `nombre`. Fíjate que las props a recibir están desestructuradas del objeto global `Astro.props`.

{% code title="src/components/GreetingHeadline.astro" %}
```javascript
---
// Definimos un prop para un saludo y un nombre
const { saludo, nombre } = Astro.props
---
```
{% endcode %}

{% code title="src/components/GreetingHeadline.astro" %}
```html
<!-- Dentro de un H2, le pasamos esos props dentro de llaves -->
<h2>{saludo}, {nombre}!</h2>
```
{% endcode %}

Este componente, cuando se importa y renderiza en otros componentes, layouts o páginas de Astro, puede pasar estas props como atributos:

{% code title="src/components/GreetingCard.astro" %}
```javascript
---
// Importamos nuestro componente GreetingHeadline.astro, que
// creamos anteriormente y que recibía 2 props (saludo y nombre)
import GreetingHeadline from './GreetingHeadline.astro';
const name = 'Astro'; // En este ejemplo definimos una variable name con un valor
---
```
{% endcode %}

{% code title="src/components/GreetingCard.astro" %}
```html
<h1>Tarjeta de saludos</h1> <!-- Tenemos un h1 puro -->

<!-- Utilizamos nuestro componente importado, le pasamos los siguientes
datos dentro de cada prop que este componente puede recibir, en greeting
le pasamos "Hola" y en name le paso la variable que habíamos definido
anteriormente que contenía el valor de "Astro" -->
<GreetingHeadline greeting="Hola" name={name} /> <!-- Al final mostrará Hola Astro -->

<p>¡Espero que tenga un día maravilloso!</p> <!-- Tenemos un p puro -->
```
{% endcode %}

También puedes definir props con TypeScript usando una interfaz de tipo `Props`. Astro recogerá automáticamente la interfaz `Props` en el frontmatter y dará advertencias/errores de tipo para tu proyecto. A estas propiedades también se les puede dar valores predeterminados cuando se desestructuran desde `Astro.props`, esto es algo que aún no veremos, por temas de complejidad, pero en su debido momento, será bastante necesario.

{% code title="src/components/GreetingHeadline.astro" %}
```javascript
---
// Tenemos una interface que se llama Props
// donde defino el nombre cada prop, es decir, nombre y saludo
// donde si visualizamos bien
interface Props {
  nombre: string; // Nombre se le define que recibirá si o si un string
  saludo?: string; // En este caso, se le define si o si un string o puede ser nulo
}

// Aquí declaramos esas variables, y ya sabemos que tienen datos previamente
// definimos, donde si o si reciben el tipo de dato que se les especificó
// durante la interface.
const { saludo = "Hola", nombre } = Astro.props;
---
```
{% endcode %}

{% code title="src/components/GreetingHeadline.astro" %}
```html
<!-- Simplemente le pasamos las props definidas -->
<h2>{saludo}, {nombre}!</h2>
```
{% endcode %}

A los props de componentes se les pueden dar valores predeterminados para usar cuando no se proporciona ninguno.

{% code title="src/components/GreetingHeadline.astro" %}
```javascript
---
// Como podemos ver, podemos definir valores por defecto en nuestros props
// esto en que sentido nos sirve, en casos donde no definimos valores
// cuando importamos este componente
const { greeting = "Hola", name = "Astronauta" } = Astro.props;
---
```
{% endcode %}

{% code title="src/components/GreetingHeadline.astro" %}
```html
<h2>¡{greeting}, {name}!</h2>
```
{% endcode %}

### 📦 Slots

El elemento `<slot />` es un espacio reservado para contenido HTML externo, permitiéndote inyectar (o ingresar en la “ranura”) elementos hijos provenientes de otros archivos en el maquetado de tu componente.

Veamos este tema, con estos dos casos:

{% tabs %}
{% tab title="Caso 1" %}
Resulta que cuando trabajamos HTML puro, cierto? Tenemos etiquetas o elementos HTML que manejan otros elementos HTML hijos, por ejemplo, piensa en esas etiquetas que contienen un elemento HTML hijo, veamos algunas etiquetas que si tienen hijos:

{% code title="li.html" %}
```html
<!-- En este caso vemos una etiqueta <li>, que nos permite listar -->
<li>
    <!-- Dentro tenemos otra etiqueta, que es <a>, si podemos ver
    el hecho de tenerla dentro de <li>, la convierte en elemento hijo
    y su padre viene siendo <li> -->
    <a href="#">
    
    </a>
</li>
```
{% endcode %}

Veamos otro ejemplo con otra etiqueta:

{% code title="input-label.html" %}
```html
<!-- Podemos observar una etiqueta <label> -->
<label for="email">
    <!-- Vemos que <input> está dentro del <label> por lo tanto
    se vuelve hijo que lo está conteniendo su padre -->
    <input type="email" name="email" id="email" required>
</label>
```
{% endcode %}

Cuándo trabajamos con **Compontes**, sucede algo similar, para eso veamos como se trabajan en la ventana de **Caso 2**.
{% endtab %}

{% tab title="Caso 2" %}
Ya sabemos como se trabajan esas etiquetas padre y etiquetas hijo, en el contexto del uso del HTML puro, ahora veremos el caso pero con componentes `.astro`:

{% code title="src/components/Li.astro" %}
```html
---
const { className } = Astro.props; 
---

<!-- En algunos casos tenemos props que se definen a una atributo
HTML puro, por ejemplo class, le asignamos className, xq daremos
estilos personalizados con TailwindCSS -->
<li class={className} >

    <slot /> <!-- Lo usamos para indicar que aquí podemos insertar
    componentes o elementos hijos y que <li>, se volverá padre del hijo
    que insertemos, que será un anchor o <a> -->
    
</li>
```
{% endcode %}

Ya tenemos nuestro componente `<li>` , pero nos hace falta crear el componente `<a>` , veamos cómo hacerlo:

{% code title="src/components/Anchor.astro" %}
```html
---
const { href, texto } = Astro.props;
---

<!-- Así como mencionamos el caso de class, también aplica con href,
le pasamos un prop, xq desconocemos cuál sera la Url que tendrá -->
<a href={href} >

 {texto} <!-- Aquí, le pasamos el prop de texto, porque
 desconocemos temporalmente, cuál puede ser -->
 
</a>
```
{% endcode %}

Ya tenemos nuestro componente `<li>` y `<a>`, ahora vamos a unirlos todo en uno, de la siguiente forma:

{% code title="src/pages/index.astro" %}
```html
---
// Importamos nuestros componentes
import Li from '../components/Li.astro';
import Anchor from '../components/Anchor.astro';
---

<html lang="en">
<head>
    <meta charset="utf-8"/>
    <link rel="icon" type="image/svg+xml" href="/favicon.svg"/>
    <meta name="viewport" content="width=device-width"/>
    <meta name="generator" content={Astro.generator}/>
    <title>Astro</title>
</head>
<body>
    <!-- Vemos una particularidad, tenemos Li y Anchor,
    donde Li necesita etiqueta de apertura y cierre, mientras que
    Anchor hace apertura y cierre en el mismo lapso -->
    
    <!-- Si analizamos, tiene sentido lo que se mencionó anteriormente
    porque Li tiene un hijo, y sabemos que para hacerlo, se necesita
    englobal o encapsular el componente hijo con etiquetas de apertura
    y cierre -->
    <Li className="text-gray-500">
    
        <!-- Mientras que Anchor, solo necesita los props o datos
        que queremos que tenga ese componente, la url y un texto -->
        <Anchor href="/login" texto="Login" />
        
    </Li>
</body>
</html>
```
{% endcode %}
{% endtab %}
{% endtabs %}

Por defecto, todos los elementos hijos que le sean enviados a un componente serán renderizados en su `<slot />`.

{% hint style="info" %}
Nota

Los slots son diferente a los _props_, los props son atributos enviados a un componente Astro y disponibles para utilizar con `Astro.props`, los _slots_ renderizan elementos HTML hijos donde se lo indique.
{% endhint %}

{% code title="src/components/Wrapper.astro" %}
```javascript
---
import Header from './Header.astro';
import Logo from './Logo.astro';
import Footer from './Footer.astro';

const { titulo } = Astro.props;
---
```
{% endcode %}

{% code title="src/components/Wrapper.astro" %}
```html
<div id="content-wrapper">
  <Header />
  <Logo />
  <h1>{titulo}</h1>
  <slot />  <!-- aquí van los hijos -->
  <Footer />
</div>
```
{% endcode %}

Ahora usemos ese componente dentro de otro y veamos como funciona

{% code title="src/pages/fred.astro" %}
```javascript
---
import Wrapper from '../components/Wrapper.astro';
---
```
{% endcode %}

{% code title="src/pages/fred.astro" %}
```html
<Wrapper titulo="Página de Fred">
  <h2>Todo sobre Fred</h2>
  <p>Aquí veremos cosas sobre Fred.</p>
</Wrapper>
```
{% endcode %}

### 🏷️  Slots con nombre

Un componente de Astro también puede tener slots con nombre. Esto te permite compartir elementos HTML únicamente con el nombre correspondiente al slot.

Los slots se nombran usando el atributo `name`:

{% code title="src/components/Wrapper.astro" %}
```javascript
---
import Header from './Header.astro';
import Logo from './Logo.astro';
import Footer from './Footer.astro';

// Recibimos la propiedad "titulo" desde el componente padre
const { titulo } = Astro.props;
---
```
{% endcode %}

{% code title="src/components/Wrapper.astro" %}
```html
<div id="content-wrapper">
  <!-- Encabezado fijo -->
  <Header />

  <!-- Slot: contenido que se insertará después del header -->
  <slot name="after-header" />

  <!-- Logo central -->
  <Logo />

  <!-- Título dinámico -->
  <h1>{titulo}</h1>

  <!-- Slot principal (contenido por defecto) -->
  <slot />

  <!-- Pie de página fijo -->
  <Footer />

  <!-- Slot: contenido que se insertará después del footer -->
  <slot name="after-footer" />
</div>
```
{% endcode %}

ara inyectar contenido HTML en un slot particular, usa el atributo `slot` en cualquier elemento hijo para especificar el nombre del slot. Todos los demás elementos hijos del componente serán inyectados en el slot por defecto (sin nombre) `<slot />`.

```javascript
---
import Wrapper from '../components/Wrapper.astro';
---
```

```html
<Wrapper titulo="Página de Fred">

  <!-- Contenido que aparecerá después del Header -->
  <img 
    src="https://my.photo/fred.jpg" 
    alt="Foto de Fred" 
    slot="after-header" 
  />

  <!-- Contenido principal -->
  <h2>Todo sobre Fred</h2>
  <p>Aquí veremos cosas sobre Fred.</p>

  <!-- Contenido que aparecerá después del Footer -->
  <p slot="after-footer">© 2025 Derechos reservados</p>

</Wrapper>
```

> Hay más casos donde podemos usar Slots, pero ya te invitaría que vayas a la documentación oficial o espera a que saquemos una actualización de esta página con los otros casos de usos de los slots.

### 🌐 Componentes HTML

Astro soporta importar y usar archivos `.html` como componentes o colocarlos dentro del subdirectorio `src/pages/`. Es posible que quieras usar componentes HTML si estás reusando código de un sitio existente construido sin usar frameworks, o si quieres asegurarte que tu componente no tiene características dinámicas.

Los componentes HTML solo deben contener HTML válido, y por lo tanto le faltarán características claves de los componentes de Astro.

* Ellos no soportan el frontmatter, importaciones del lado del servidor, o expresiones dinámicas.
* Cualquier etiqueta `<script>` quedan sin agrupar, son tratados como si tuvieran `in:inline`
* Ellos solo pueden referenciar recursos que están en la carpeta [`public/`](https://docs.astro.build/es/basics/project-structure/#public).

Te invito a que visites la siguiente página de **Astro - Layouts**.
