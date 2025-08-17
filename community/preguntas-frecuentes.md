---
icon: question
---

# Preguntas frecuentes

<details>

<summary>¿No es mejor desarrollar toda la aplicación (frontend y backend) desde un solo lugar en lugar de separarlos?</summary>

Ese comentario viene de una idea bastante común en entornos más **monolíticos**:

> _"Si ya tenés un backend, que desde ahí salga todo, incluyendo el HTML, CSS y JS"_ — algo típico de frameworks como Laravel, Django o Ruby on Rails.

Pero en la práctica actual, **esa decisión depende de tu objetivo y de la complejidad del proyecto**.\
Te lo desgloso para que lo veas claro:

### 🏗 **Frontend desde el backend (monolítico)**

{% hint style="info" %}
**Ejemplo:** usar Laravel Blade, Django Templates, ASP.NET Razor, etc.
{% endhint %}

#### Ventajas

* Todo en un mismo proyecto/repositorio.
* Menos configuraciones de integración.
* Despliegue más sencillo (subes una sola aplicación).
* Menos dependencias entre equipos (si es un equipo pequeño).

#### Desventajas

* Menos flexibilidad para usar frameworks modernos de UI (Vue, React, Svelte).
* El frontend suele estar más "acoplado" a la lógica del backend.
  * Problemas:
    * Si cambias algo en el backend, debes cambiar el frontend
    * Es difícil reutilizar el frontend con otros backends
    * Los equipos no pueden trabajar independientemente
    * Las pruebas son más complejas
  * Ventajas:
    * Desarrollo más rápido inicialmente
    * Menos abstracción = código más directo
    * Mejor rendimiento (menos capas intermedias)
* Menos control sobre optimización y performance del lado del cliente.
* No aprovechas arquitectura moderna tipo **Astro Islands** o render híbrido.

### 🚀 **Frontend separado del backend (arquitectura desacoplada)**

{% hint style="info" %}
**Ejemplo:** un proyecto Astro + Vue que consume una API de Node, Laravel, etc.
{% endhint %}

#### Ventajas

* Frontend libre para evolucionar sin tocar el backend.
* Puedes usar lo último en performance y UX (SSG, ISR, SPA parcial, etc.).
* Backend más limpio, centrado solo en datos y lógica de negocio.
* Escala mejor si después quieres cambiar el backend sin rehacer la UI.

#### Desventajas

* Necesita configurar comunicación entre frontend y backend (CORS, API, auth).
* Despliegues dobles (frontend y backend por separado).
* Un poco más de curva de aprendizaje al inicio.

💡 Entonces... ¿Por qué influye Astro?

1. Porque Astro está hecho justo para **UI desacoplada y optimizada**.
2. Así entendemos bien cada capa: primero la presentación (UI), después la lógica (backend).
3. Nos deja libertad de conectar a cualquier backend (Node, Laravel, Go, Python, etc).

</details>

