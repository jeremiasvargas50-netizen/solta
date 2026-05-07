# Soltá — Deploy a Vercel

App de PNL · Cambio de Submodalidades en 5 minutos.

## Subir a Vercel — 3 formas

### Forma 1 (la más rápida, sin Git, 60 segundos)

1. Andá a https://vercel.com/new
2. Buscá "Deploy a Template" o "Import Project" → en mobile/desktop hay un botón **"Deploy from Local Folder"**.
   Si no lo ves, instalá la CLI:
   ```
   npm i -g vercel
   ```
   Después abrí terminal en esta carpeta `solta-deploy/` y corré:
   ```
   vercel
   ```
   Te pide login (con tu email o GitHub), respondés "Y" a las preguntas y listo: te da una URL `https://solta-xxx.vercel.app`.

### Forma 2 (con GitHub — recomendada para futuras actualizaciones)

1. Crear repo nuevo en GitHub:
   - Andá a https://github.com/new
   - Nombre: `solta`
   - Privado o público, como prefieras
   - Crear

2. En tu terminal, dentro de `solta-deploy/`:
   ```
   git init
   git add .
   git commit -m "Initial commit — Soltá v1"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/solta.git
   git push -u origin main
   ```

3. En Vercel:
   - https://vercel.com/new
   - Importá el repo `solta`
   - Framework preset: **Other** (es estático)
   - Click **Deploy**
   - 30 segundos y queda online

### Forma 3 (drag & drop a Vercel)

1. Comprimí esta carpeta `solta-deploy/` en un .zip
2. Andá a https://vercel.com → New Project
3. Algunas versiones permiten arrastrar el .zip directo. Si no aparece la opción, usá la Forma 1.

## Dominio personalizado (opcional)

En el dashboard del proyecto en Vercel:
- **Settings → Domains**
- Agregá `solta.app` o el dominio que tengas
- Vercel te dice qué CNAME poner en tu DNS

## Actualizaciones futuras

Si usaste Forma 2 (GitHub):
- Editás `index.html`, hacés commit y push
- Vercel re-deploya automáticamente en 30 segundos

Si usaste Forma 1 (CLI):
- Editás `index.html`
- Corres `vercel --prod` y se actualiza

## Estructura del deploy

```
solta-deploy/
├── index.html       ← La app completa, single-file
├── vercel.json      ← Config de Vercel (headers de seguridad)
├── package.json     ← Metadata
└── README.md        ← Este archivo
```

## Notas técnicas

- **Sin build**: la app es 100% estática, solo HTML + JS + Tailwind por CDN
- **Funciona offline después del primer load**
- **Almacenamiento local**: `localStorage` — los datos quedan solo en el dispositivo del usuario
- **Sin tracking**: no usa cookies, ni Analytics, ni nada que requiera consentimiento
- **Performance**: ~50 KB el HTML, +Tailwind del CDN (cacheable)

## Datos personales embebidos

- WhatsApp: `wa.me/5491170599871`
- Instagram: `@jeremiasvargascoach`

Si querés cambiarlos, abrí `index.html` y buscá esas constantes (líneas ~112-115).

---

**Tip de SEO si vas a campañas**: agregá `<meta property="og:image">` con una imagen de 1200×630 que muestre la home. Te lo armo en 1 minuto si querés.
