# Soltá — Paso a paso para subir a GitHub + Vercel

**Tiempo total: 15 minutos.** No necesitás saber programar.

---

## PARTE 1 — Crear tu cuenta de GitHub (3 min)

GitHub es donde se guarda el código. Vercel lo agarra de ahí.

1. Andá a **https://github.com/signup**
2. Email, contraseña, nombre de usuario.
   - Tip: elegí un nombre simple como `jeremiasvargas` — lo vas a ver en URLs.
3. Verificá tu email
4. **Cuando te pregunte "team" o plan**, elegí siempre el plan **Free**
5. Ya estás dentro de GitHub.

---

## PARTE 2 — Instalar Git en tu computadora (3 min)

Git es el programa que envía los archivos a GitHub.

1. Andá a **https://git-scm.com/download/win**
2. El download empieza solo. Abrí el archivo `.exe`
3. **Apretá "Next" en TODAS las pantallas del instalador.** No cambies nada.
4. Cuando termina, abrí el menú Inicio de Windows y buscá **"Git Bash"** → abrilo
5. Aparece una ventana negra como una terminal. Eso es lo que vamos a usar.

**Una vez (configurar tu identidad):** copiá y pegá estos dos comandos, cambiando los datos:

```
git config --global user.name "Jeremias Vargas"
git config --global user.email "jeremiasvargas50@gmail.com"
```

(Apretá Enter después de cada uno. Si no sale ningún error, está bien.)

---

## PARTE 3 — Crear el repo vacío en GitHub (2 min)

1. En GitHub.com, arriba a la derecha, click en el **+** → **"New repository"**
2. **Repository name:** `solta`
3. **Description:** `App de PNL — Soltá lo que te pesa` (opcional)
4. **Public** o **Private** — elegí Public si querés que cualquiera vea el código, Private si querés que sea solo tuyo
5. **NO marques** ninguna de las casillas de "Add README" ni ".gitignore" ni "License" — déjalas en blanco
6. Click verde **"Create repository"**
7. Te lleva a una pantalla que dice "Quick setup". **No la cierres** — vas a copiar comandos de ahí.

---

## PARTE 4 — Subir tu app a GitHub (3 min)

1. **Abrí Git Bash** (la ventana negra)
2. Copiá y pegá este comando (te lleva a la carpeta de tu app):

```
cd "/c/Users/jerem/OneDrive/Documentos/Claude/Projects/APP Submodalidades PNL/solta-deploy"
```

(En Git Bash, las rutas usan `/c/` en vez de `C:\`. Pegá tal cual está.)

Apretá Enter.

3. Ahora corré estos comandos **uno por uno** (copiá, pegá, Enter):

```
git init
```

```
git add .
```

```
git commit -m "Soltá v1 - primera versión"
```

```
git branch -M main
```

4. Ahora el comando que conecta con tu repo de GitHub. **Volvé a la pestaña de GitHub**, copiá la línea que aparece debajo de "…or push an existing repository from the command line" (la que dice `git remote add origin https://github.com/...`). Pegala en Git Bash y Enter.

   Será algo como:
   ```
   git remote add origin https://github.com/jeremiasvargas/solta.git
   ```

5. Por último:

```
git push -u origin main
```

   - **Si te pide login**, te abre una ventanita pidiendo usuario y contraseña/token.
   - GitHub ya no acepta contraseña común. Vas a necesitar un **Personal Access Token**:
     - Andá a **https://github.com/settings/tokens/new**
     - Note: `solta-push`
     - Expiration: 90 days
     - Scope: marcá **`repo`** (la primera casilla)
     - Click **Generate token**
     - **Copiá el token** que aparece (es una sola vez, después no lo volvés a ver)
     - Pegalo donde te pide la contraseña en Git Bash.

6. Si todo salió bien, vas a ver "Branch 'main' set up to track 'origin/main'."
7. Volvé a GitHub.com → recargá la página de tu repo → ahora tenés todos los archivos ahí.

✅ **Tu código está en GitHub.**

---

## PARTE 5 — Conectar Vercel y deployar (3 min)

1. Andá a **https://vercel.com/signup**
2. Click **"Continue with GitHub"** → autorizá la conexión
3. Te lleva al dashboard de Vercel. Click el botón grande **"Add New..."** → **"Project"**
4. Vas a ver la lista de tus repos de GitHub. Buscá **`solta`** y click **"Import"**
5. En la pantalla de configuración:
   - **Project Name:** `solta` (o lo que quieras)
   - **Framework Preset:** dejá **"Other"**
   - **Root Directory:** dejá `./`
   - **Build Command:** dejalo vacío
   - **Output Directory:** dejalo vacío
   - **Install Command:** dejalo vacío
6. Click el botón grande **"Deploy"**
7. **Esperá ~30 segundos** mientras Vercel hace la magia
8. Te aparece "Congratulations!" con confeti y un preview de tu app

✅ **Tu app está online.** Vercel te da una URL como `https://solta-tres.vercel.app` o similar.

Click en ella y mirá que funcione.

---

## PARTE 6 — Conectar tu dominio (opcional, si tenés uno)

Si tenés un dominio como `solta.app` o `pnlcoaching.com.ar`:

1. En Vercel, dentro del proyecto → **Settings** → **Domains**
2. Agregá tu dominio
3. Vercel te dice qué CNAME poner en tu proveedor (Nic.ar, GoDaddy, etc.)
4. Esperás 1-24 hs hasta que propague
5. Listo, queda en tu dominio propio.

Si no tenés dominio, te queda gratis con la URL `*.vercel.app` y está perfecto para arrancar.

---

## PARTE 7 — Cómo actualizar la app después

Cada vez que quieras cambiar algo:

1. Editás `index.html` con cualquier editor (incluso el Bloc de notas sirve)
2. Abrís Git Bash
3. Vas a la carpeta:
   ```
   cd "/c/Users/jerem/OneDrive/Documentos/Claude/Projects/APP Submodalidades PNL/solta-deploy"
   ```
4. Tres comandos:
   ```
   git add .
   git commit -m "describí qué cambiaste"
   git push
   ```
5. Vercel detecta el cambio solo y re-deploya en 30 segundos. No hacés nada más.

---

## Si algo falla

**Error: "git no se reconoce como comando"** → Reiniciá la PC después de instalar Git.

**Error: "Permission denied (publickey)"** → Estás usando SSH en vez de HTTPS. Volvé al paso de `git remote add origin` y asegurate que la URL empieza con `https://` no con `git@`.

**Error: "fatal: not a git repository"** → No estás en la carpeta correcta. Volvé a hacer `cd "/c/Users/jerem/OneDrive/Documentos/Claude/Projects/APP Submodalidades PNL/solta-deploy"` antes de los otros comandos.

**Token expira en 90 días** → Cuando te falle un push, generás un token nuevo en https://github.com/settings/tokens/new y lo usás de nuevo.

**El push pide usuario/contraseña varias veces** → En Git Bash, después del primer login se queda guardado. Si no, instalá **Git Credential Manager** (viene con Git para Windows si elegiste todo "Next" en el instalador).

---

## Resumen de tus URLs cuando termines

- Tu repo de código: `https://github.com/TU_USUARIO/solta`
- Tu app online: `https://solta-XXX.vercel.app` (Vercel te la da)
- Dashboard de Vercel: `https://vercel.com/dashboard`

**Eso es todo. Si te trabás en cualquier paso, decime el error exacto y lo resolvemos.**
