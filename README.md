# Portfolio Candela Merás

Portfolio de **Candela Merás**, diseñadora de indumentaria argentina y creadora de la marca **Meiri Doll**.

- Sitio: https://veraenzo.github.io/Portfolio-Candela/
- Panel para editar: https://veraenzo.github.io/Portfolio-Candela/admin/

## Cómo funciona

Sitio estático de una sola página (HTML + CSS + JS vanilla, sin build). El contenido **no está en el HTML**: `index.html` lee dos archivos JSON y arma la página.

| Archivo | Qué contiene |
|---|---|
| `content/general.json` | Portada (textos + fotos del carrusel), Sobre mí, encabezado de proyectos, contacto |
| `content/proyectos.json` | Lista de proyectos → secciones → fotos |
| `images/` | Fotos (WebP). Las que sube Candela desde el CMS van a `images/subidas/` |
| `admin/` | Panel de edición [Sveltia CMS](https://sveltiacms.app) |

Candela edita desde el celular en `/admin/`: inicia sesión con GitHub, cambia textos, sube fotos y publica. Cada cambio es un commit en `main` y GitHub Pages actualiza el sitio en ~1 minuto. Las fotos se convierten a WebP (máx. 2048 px) en el navegador antes de subirse.

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

1. **GitHub Pages**: Settings → Pages → Source: *Deploy from a branch* → `main` / `(root)`.
2. **Autenticación**: en `admin/config.yml`, poner en `backend.base_url` la URL del Worker de [sveltia-cms-auth](https://github.com/sveltia/sveltia-cms-auth). Si el Worker tiene la variable `ALLOWED_DOMAINS`, agregar `veraenzo.github.io`.
3. **Acceso de Candela**: invitarla como colaboradora del repo (Settings → Collaborators) con su cuenta de GitHub.

Si el sitio pasa a un dominio propio, actualizar `site_url`/`display_url` en `admin/config.yml`, las etiquetas `og:` de `index.html` y `ALLOWED_DOMAINS` del Worker.

## Contacto

- Email: candela@meiridoll.com
- Instagram: [@meiridoll](https://instagram.com/meiridoll)
