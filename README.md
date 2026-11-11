# Portfolio Candela Merás

Portfolio de **Candela Merás**, diseñadora de indumentaria argentina y creadora de la marca **Meiri Doll**.

- Sitio: https://candelameras.vercel.app/
- Panel para editar: https://candelameras.vercel.app/admin/

## Guía para editar la página (Candela)

### Entrar

1. Abrí **candelameras.vercel.app/admin** en el celular.
2. Tocá **"Iniciar sesión con GitHub"** (la primera vez te pide autorizar; aceptá).
3. Tip: agregá la página a la pantalla de inicio (en el menú del navegador → *Agregar a pantalla de inicio*) para tenerla como una app.

> No uses "Iniciar sesión con un token de acceso": no hace falta.

### Qué hay adentro

Vas a ver **"Contenido de la página"** con dos partes:

| Parte | Qué cambia en la web |
|---|---|
| **Portada, Sobre mí y Contacto** | Todo lo que no son proyectos: la portada con el carrusel de fotos, el texto de "Sobre mí", el título de la sección de proyectos y los botones de contacto |
| **Proyectos** | La lista de proyectos, cada uno con sus secciones de fotos |

#### Portada, Sobre mí y Contacto

- **Portada**
  - *Texto chico de arriba*, *Nombre*, *Subtítulo*, *Descripción*: los textos de la primera pantalla.
  - *Fotos del carrusel*: las fotos que van rotando a la derecha (cada 4 segundos). Podés agregar, sacar y arrastrar para cambiar el orden. Tiene que haber al menos una.
- **Sobre mí**
  - *Frase debajo de la inicial*: la frase chiquita debajo de la "C" grande.
  - *Texto*: para separar párrafos dejá **una línea en blanco** entre ellos. Si ponés una palabra entre asteriscos, como `*Meiri Doll*`, se muestra en letra caligráfica.
- **Encabezado de Proyectos**: el título "Mis proyectos" y la frase de abajo.
- **Contacto**: título, subtítulo, email, usuario de Instagram (sin @) y WhatsApp. El WhatsApp va **solo con números**, con código de país: `5493415706842`. Si dejás un campo vacío, ese botón no aparece.

#### Proyectos

Es una lista: los proyectos aparecen en la web **en el mismo orden** que acá. Para cambiar el orden, arrastralos.

En la web los proyectos aparecen **cerrados**: se ve el título, la descripción, 4 fotos chiquitas de muestra (las primeras del proyecto) y "Ver proyecto". Al tocarlo se despliega. Cada proyecto abierto tiene su propio link (ej. `candelameras.vercel.app/#meiri-doll`) que podés copiar del navegador y mandar: abre directo ese proyecto.

Cada proyecto tiene:

- **Título**, **Etiqueta** (el texto chico de arriba, ej. *Colección · Facultad*) y **Descripción**.
- **Mostrar en la página**: si está apagado, el proyecto no aparece en la web. Sirve para ir armándolo tranquila y publicarlo cuando esté listo.
- **Destacado**: le pone el fondo color crema (hoy lo tiene Meiri Doll).
- **Secciones**: los bloques de fotos del proyecto (ej. *Figurines*, *Fichas técnicas*). Cada sección tiene:
  - **Título de la sección**.
  - **Fotos por fila**: 1 a 4. En el celular se ven como máximo 2 por fila.
  - **Forma de las fotos**: vertical, horizontal, cuadrada o panorámica. En la grilla las fotos se recortan a esa forma; cuando alguien toca una foto, se ve completa.
  - **Fotos**: las fotos de la sección. Se pueden reordenar arrastrando.
  - **Videos**: clips cortos. Aparecen después de las fotos, con la misma forma, y se reproducen solos, sin sonido y en bucle. Al tocarlos se abren con sonido.

Una sección **sin fotos ni videos no se muestra**, así que podés dejar secciones vacías preparadas sin que se vean.

### Subir fotos

1. En el campo de fotos, tocá el botón para agregar y elegí desde la galería o sacá una foto.
2. No hace falta achicarlas antes: el panel las comprime solo al subirlas (quedan livianas para que la web cargue rápido).
3. Las fotos subidas quedan guardadas en el panel, así que podés reutilizarlas en otra sección sin volver a subirlas.

### Subir videos

Los videos **no se comprimen solos** (las fotos sí), así que hay un límite: **30 MB por video**. Si el video pesa más, el panel no te deja subirlo.

- Que sean **clips cortos** (menos de 1 minuto).
- Si pesa más de 30 MB, achicalo antes con una app gratuita de comprimir video (buscá "comprimir video" en la App Store o Play Store) y exportalo en **MP4, 720p o 1080p**. Un clip de 30 segundos en 720p suele pesar entre 5 y 15 MB.
- En iPhone: Ajustes → Cámara → Formatos → **"Más compatible"**. Así el video se ve en todos los navegadores (el formato "Alta eficiencia" no se ve en algunos Android y computadoras). Grabar en 1080p en vez de 4K también ayuda mucho.
- Cuanto más liviano, más rápido carga la web para quien la visita.

### Publicar los cambios

1. Cuando termines, tocá **Guardar** (arriba).
2. La web se actualiza sola en **1 o 2 minutos**. Recargá la página para verlo.

Cada vez que guardás queda registrado, así que si algo sale mal **se puede volver atrás**: avisale a Enzo.

### Ejemplos rápidos

- **Publicar Marie's Dollhouse**: Proyectos → Marie's Dollhouse → cargá fotos en las secciones que quieras → activá *Mostrar en la página* → Guardar.
- **Agregar un proyecto nuevo**: Proyectos → botón para agregar proyecto (al final de la lista) → completá título, etiqueta, descripción → agregá secciones con fotos → Guardar. Después arrastralo a la posición que quieras.
- **Cambiar las fotos de la portada**: Portada, Sobre mí y Contacto → Portada → Fotos del carrusel → agregá/sacá/reordená → Guardar.

### Si algo no anda

- **No veo el cambio en la web**: esperá 2 minutos y recargá. En el celular a veces hay que cerrar y volver a abrir la pestaña.
- **Me pide iniciar sesión de nuevo**: es normal cada tanto; volvé a tocar "Iniciar sesión con GitHub".
- **Aparece un error al guardar**: sacale captura y mandásela a Enzo.

---

## Cómo funciona

Sitio estático de una sola página (HTML + CSS + JS vanilla, sin build). El contenido **no está en el HTML**: `index.html` lee dos archivos JSON y arma la página.

| Archivo | Qué contiene |
|---|---|
| `content/general.json` | Portada (textos + fotos del carrusel), Sobre mí, encabezado de proyectos, contacto |
| `content/proyectos.json` | Lista de proyectos → secciones → fotos |
| `images/` | Fotos (WebP). Las que sube Candela desde el CMS van a `images/subidas/` |
| `admin/` | Panel de edición [Sveltia CMS](https://sveltiacms.app) |

Candela edita desde el celular en `/admin/`: inicia sesión con GitHub, cambia textos, sube fotos y publica. Cada cambio es un commit en `main` y Vercel republica el sitio en ~1 minuto. Las fotos se convierten a WebP (máx. 2048 px) en el navegador antes de subirse.

Reglas de visualización:
- Un proyecto con **"Mostrar en la página"** desactivado no aparece.
- Una sección sin fotos no aparece.

## Correr localmente

Hace falta un servidor (el sitio usa `fetch` para leer los JSON; abriendo el archivo directo no carga):

```bash
python -m http.server 8000
# o
npx http-server
```

## Puesta en marcha (una sola vez)

1. **Vercel**: proyecto `portfolio-candela` (cuenta de Enzo) conectado a este repo, Framework Preset *Other*, sin build. Dominio `candelameras.vercel.app` asignado en Settings → Domains. Cada push a `main` republica.
2. **Autenticación**: el panel usa el Worker de [sveltia-cms-auth](https://github.com/sveltia/sveltia-cms-auth) compartido con Meiri Doll (`backend.base_url` en `admin/config.yml`). En Cloudflare → Worker → Settings → Variables, `ALLOWED_DOMAINS` tiene que incluir `candelameras.vercel.app` (separado por coma de `meiridoll.vercel.app`). Redesplegar el Worker después.
3. **Acceso de Candela**: invitarla como colaboradora del repo (Settings → Collaborators) con su cuenta de GitHub.

Si el sitio pasa a un dominio propio, actualizar `site_url`/`display_url` en `admin/config.yml`, las etiquetas `og:` de `index.html` y `ALLOWED_DOMAINS` del Worker.

## Contacto

- Email: candela@meiridoll.com
- Instagram: [@meiridoll](https://instagram.com/meiridoll)
