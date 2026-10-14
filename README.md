# SINAPSIS · Marketing con IA real · Código abierto (MIT)

> **SINAPSIS** — *"Marketing que piensa como tu cliente"*
> Analiza cualquier sitio web, genera estrategias con Gemini/Claude y crea videos promo con Higgsfield.
> **Gratis, sin planes, sin cuentas de pago, sin rastreadores.** 1 archivo, 0 dependencias.

## 📁 Contenido

| Archivo | Qué es |
|---|---|
| `index.html` | **Todo el sitio**: landing + acceso + panel (analizador, IA real, video) + privacidad |
| `LICENSE` | Licencia MIT: úsalo, modifícalo y publícalo libremente |
| `robots.txt` / `sitemap.xml` | SEO básico |
| `_headers` | Cabeceras de seguridad para Cloudflare Pages / Netlify |
| `og-image.svg` | Imagen para compartir (~2 KB) |

## 🤖 IA real: tus llaves (BYOK)

SINAPSIS no cobra ni intermedia: tú pones tus llaves y pagas directo a cada proveedor por lo que uses.

| Proveedor | Para qué | Dónde está la llave | Costo aprox. |
|---|---|---|---|
| **Gemini** (`gemini-3.8-flash`) | Estrategias, titulares, textos | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) | Nivel gratuito generoso |
| **Claude** (`claude-sonnet-5-5`) | Análisis profundo, copy premium | [console.anthropic.com](https://console.anthropic.com/) | Pago por uso (centavos/estrategia) |
| **Higgsfield** (`seedance-2.0`) | Video promo 5s con audio | [console.higgsfield.ai](https://console.higgsfield.ai/) | Saldo prepago (centavos/video) |

**Cómo activarlo:** entra al panel → sección *IA real con tus llaves* → elige Gemini o Claude → pega tu llave → *Guardar* → *Probar conexión* → usa el botón **IA real** en el generador. Para video: pega tu Key ID + Secret de Higgsfield, describe el clip y pulsa **Generar video**.

**Seguridad:** las llaves viven solo en tu navegador (`localStorage`) y viajan directo a cada proveedor. Nunca pasan por servidores nuestros (no tenemos). Bórralas del panel cuando quieras y no las uses en computadoras ajenas.

> ⚠️ Nota sobre Higgsfield: su API está diseñada para llamarse desde servidor y podría bloquear peticiones de navegador (CORS) en el futuro. Si el panel muestra bloqueo, genera con `curl`:
> ```
> curl -X POST https://api.higgsfield.ai/bytedance/seedance-2.0/text-to-video \
>  -H "Authorization: Key $HF_API_KEY_ID:$HF_API_KEY_SECRET" \
>  -H "Content-Type: application/json" \
>  -d '{"prompt":"Cinematic promo of my business","resolution":"720p","generate_audio":true,"duration":5,"aspect_ratio":"16:9"}'
> ```
> y consulta el `status_url` devuelto hasta `status: completed` → `video.url`.

## 🔍 Analizador de sitios (funciona sin llaves)

Pega cualquier link → descarga el HTML → extrae título, H1, CTAs, WhatsApp, formularios, prueba social, tecnología → califica /100 en Mensaje · Confianza · Conversión · SEO → recomendaciones priorizadas → estrategia personalizada.

> ⚠️ La **vista previa dentro del chat no tiene internet**: ahí usa **"Ver ejemplo"**. Para links reales e IA real, **descarga `index.html` y ábrelo en tu navegador** o publícalo (abajo).

## 🚀 Publícalo gratis

### GitHub Pages (recomendado para open source)
1. Crea un repo **público** en GitHub (ej: `sinapsis`)
2. Sube todos los archivos de esta carpeta (`index.html`, `LICENSE`, `README.md`, `robots.txt`, `sitemap.xml`, `og-image.svg`, `.nojekyll`)
3. Ve a **Settings → Pages** → *Deploy from a branch* → rama `main` → carpeta `/ (root)` → **Save**
4. En 1-2 minutos estará en `https://TU-USUARIO.github.io/sinapsis/`
5. Actualiza `https://sinapsis.mx/` por tu URL real en `index.html` (canonical + OG) y `sitemap.xml`

> Nota: GitHub Pages ignora el archivo `_headers` (no soporta cabeceras personalizadas),
> pero el CSP dentro del `<meta>` de `index.html` sí se aplica y protege igual al navegador.

### Otras opciones
- **Cloudflare Pages**: arrastra la carpeta → `*.pages.dev` (+ `_headers` automático)
- **Netlify Drop**: [app.netlify.com/drop](https://app.netlify.com/drop) → arrastra → listo
- **Vercel**: traduce `_headers` a `vercel.json` (incluye el `connect-src` tal cual)

Cambia `https://github.com/tu-usuario/sinapsis` por tu repo real y `https://sinapsis.mx/` por tu dominio (canonical, OG, sitemap).

## 🎨 Marca

- **Nombre**: SINAPSIS · **Eslogan**: "Marketing que piensa como tu cliente"
- **Colores**: fondo `#05080F` · violeta `#7C5CFF` · turquesa `#3EE6C4`
- **Tipografía**: stack del sistema (0 peticiones)

## 🤝 Contribuir

1. Haz fork del repo
2. Crea tu rama (`git checkout -b mejora-analizador`)
3. Haz commit y push, abre un Pull Request
4. Ideas bienvenidas: más chequeos, streaming de IA, más modelos de video, PWA offline

---
*Última actualización: 2026-10-14. Textos legales/testimonios de ejemplo: valídalos antes de lanzar.*
