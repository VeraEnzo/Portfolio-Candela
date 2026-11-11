# Portfolio Candela Merás

Portfolio de **Candela Merás**, diseñadora de indumentaria argentina y creadora de la marca **Meiri Doll**.

- Sitio: https://candelameras.vercel.app/
- Panel para editar: https://candelameras.vercel.app/admin/

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

1. **Vercel**: Add New → Project → importar `VeraEnzo/Portfolio-Candela`. Project Name: `candelameras`. Framework Preset: *Other*, sin build command ni output directory. Cada push a `main` republica.
2. **Autenticación**: el panel usa el Worker de [sveltia-cms-auth](https://github.com/sveltia/sveltia-cms-auth) compartido con Meiri Doll (`backend.base_url` en `admin/config.yml`). En Cloudflare → Worker → Settings → Variables, `ALLOWED_DOMAINS` tiene que incluir `candelameras.vercel.app` (separado por coma de `meiridoll.vercel.app`). Redesplegar el Worker después.
3. **Acceso de Candela**: invitarla como colaboradora del repo (Settings → Collaborators) con su cuenta de GitHub.

Si el sitio pasa a un dominio propio, actualizar `site_url`/`display_url` en `admin/config.yml`, las etiquetas `og:` de `index.html` y `ALLOWED_DOMAINS` del Worker.

## Contacto

- Email: candela@meiridoll.com
- Instagram: [@meiridoll](https://instagram.com/meiridoll)
