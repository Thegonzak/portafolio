# 🖥️ Mi Portafolio Web

Portafolio profesional con panel de administración. Alojado en GitHub Pages.

## 📁 Estructura

```
portfolio/
├── index.html       ← Página pública (lo que todos ven)
├── admin.html       ← Panel de administración (solo tú)
├── projects.json    ← Base de datos de proyectos
└── README.md
```

---

## 🚀 Pasos para publicar en GitHub Pages

### 1. Crea el repositorio
1. Ve a [github.com/new](https://github.com/new)
2. Nómbralo `portafolio` (o como quieras)
3. Ponlo en **público**
4. Sin README (lo agregaremos ya)

### 2. Sube los archivos
```bash
git init
git add .
git commit -m "Initial portfolio"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/portafolio.git
git push -u origin main
```

### 3. Activa GitHub Pages
1. Ve a **Settings** → **Pages**
2. Source: `Deploy from a branch`
3. Branch: `main` / `/ (root)`
4. Guarda → en unos minutos tu sitio estará en:
   `https://TU_USUARIO.github.io/portafolio`

---

## 🔑 Configurar el panel de administración

### Antes de subir: cambia la contraseña
En `admin.html`, línea ~210, cambia:
```js
const ADMIN_PASSWORD = 'mipassword123'; // ← Cambia esto
```

### Crea un token de GitHub
1. Ve a [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Dale un nombre: `portafolio-admin`
3. Expiration: sin límite (o la que prefieras)
4. Selecciona el permiso: ✅ `repo`
5. Genera y copia el token (solo se muestra una vez)

### Configura el panel
1. Abre `https://TU_USUARIO.github.io/portafolio/admin.html`
2. Ingresa tu contraseña
3. Ve a la pestaña **"Configuración GitHub"**
4. Llena: usuario, nombre del repo, rama (`main`), y el token
5. Guarda

¡Listo! Ahora desde el panel puedes agregar proyectos y publicarlos con un clic.

---

## 📝 Personalización rápida

| Qué cambiar | Dónde |
|---|---|
| Tu nombre/título | `index.html` → sección `.hero h1` |
| Email de contacto | `index.html` → `<a href="mailto:...">` |
| Skills (habilidades) | `index.html` → array `SKILLS` en el script |
| Contraseña admin | `admin.html` → `ADMIN_PASSWORD` |
| Logo | Busca "Dev.Portfolio" en ambos archivos |

---

## 💡 Tips de imágenes

Para imágenes de proyectos puedes usar:
- **[Unsplash](https://unsplash.com)** — fotos gratis de alta calidad, copia la URL directa
- **[Imgur](https://imgur.com)** — sube tu screenshot y copia el link
- **[GitHub](https://github.com)** — sube la imagen a Issues de tu repo y copia la URL generada
