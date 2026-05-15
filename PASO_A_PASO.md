# Soltá — Cómo actualizar la app

**El repo ya está creado y conectado a Vercel. Solo seguí estos pasos cada vez que Claude te entregue archivos nuevos.**

---

## Cada vez que Claude te da un archivo nuevo

### Opción A — Desde GitHub.com (sin terminal, 2 minutos)

1. Andá a **https://github.com/jeremiasvargas50-netizen/solta**
2. Hacé click en el archivo que querés reemplazar (ej. `index.html`)
3. Click en el ícono del lápiz ✏️ (arriba a la derecha del archivo)
4. Borrá todo el contenido y pegá el nuevo
5. Abajo click en **"Commit changes"** → **"Commit directly to main"** → **"Commit changes"**
6. Vercel detecta el cambio y redeploya solo en ~30 segundos

**Si tenés que subir un archivo nuevo que no existe todavía:**
1. En el repo, click en **"Add file"** → **"Upload files"**
2. Arrastrá el archivo o hacé click para buscarlo
3. Click en **"Commit changes"**

---

### Opción B — Desde tu computadora con Git Bash (más rápido si son varios archivos)

1. Abrí **Git Bash**
2. Andá a tu carpeta local:
   ```
   cd "/c/Users/jerem/OneDrive/Documentos/Claude/Projects/APP Submodalidades PNL/solta-deploy"
   ```
3. Copiá los archivos nuevos que te dio Claude a esa carpeta (reemplazando los viejos)
4. Tres comandos:
   ```
   git add .
   git commit -m "describí qué cambiaste"
   git push
   ```
5. Listo — Vercel redeploya solo en 30 segundos

---

## Archivos del repo y qué hace cada uno

| Archivo | Qué es | ¿Se actualiza seguido? |
|---------|--------|----------------------|
| `index.html` | La app completa | Sí — es el que Claude modifica |
| `sw.js` | Service worker (cache offline) | Solo cuando Claude lo pide |
| `vercel.json` | Configuración de Vercel | Raro |
| `manifest.json` | Info de la PWA (nombre, íconos) | Raro |
| `package.json` | Metadata del proyecto | Nunca |
| `icon-*.png` | Íconos de la app | Nunca |
| `PASO_A_PASO.md` | Este archivo | Cuando algo cambia |

---

## URLs importantes

| Qué | URL |
|-----|-----|
| App en producción | https://solta.vercel.app |
| Repo en GitHub | https://github.com/jeremiasvargas50-netizen/solta |
| Dashboard Vercel | https://vercel.com/dashboard |
| Generar token GitHub | https://github.com/settings/tokens/new |

---

## Si algo falla

**404 en Vercel después de un deploy** → Verificá que el `vercel.json` tenga `"outputDirectory": "."` y que el `index.html` esté en la raíz del repo, no en una subcarpeta.

**La app sigue mostrando la versión vieja en el celular** → Cerrá y volvé a abrir el browser. El service worker se actualiza solo. Si sigue igual, borrá el caché del browser para ese sitio.

**Error "git no se reconoce"** → Reiniciá la PC después de instalar Git.

**Error "Permission denied (publickey)"** → La URL del remote tiene que empezar con `https://` no con `git@`. Corregilo con:
   ```
   git remote set-url origin https://github.com/jeremiasvargas50-netizen/solta.git
   ```

**Token de GitHub expirado** → Generá uno nuevo en https://github.com/settings/tokens/new (scope: `repo`, 90 días) y usalo como contraseña en el próximo push.

**Error "fatal: not a git repository"** → No estás en la carpeta correcta. Hacé el `cd` primero.

---

## Flujo de trabajo con Claude

1. Abrís un chat con Claude y describís qué querés cambiar
2. Claude te entrega el `index.html` (y otros archivos si aplica)
3. Descargás el archivo y lo subís a GitHub (Opción A o B)
4. Vercel redeploya solo
5. Chequeás en https://solta.vercel.app que todo funcione
