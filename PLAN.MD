# PLAN.MD — Portfolio Personal

## 1. Descripción del Proyecto

Portfolio personal de desarrollador web, alojado en **GitHub Pages** como sitio estático sin backend. Incluye un panel de administración integrado directamente en el navegador que permite gestionar los proyectos y publicarlos en GitHub sin necesidad de servidores externos.

- **URL de deploy:** https://thegonzak.github.io/portafolio/
- **Tipo:** Sitio estático (GitHub Pages)
- **Autor:** Gonzalo — GitHub: [Thegonzak](https://github.com/Thegonzak)
- **Contacto:** kevinsaucedo96@hotmail.com

---

## 2. Stack Tecnológico

| Tecnología | Uso |
|---|---|
| HTML5 | Estructura del sitio |
| CSS3 | Estilos, animaciones, responsive |
| JavaScript Vanilla (ES6+) | Lógica del sitio y panel admin |
| GitHub API v3 | Deploy automático desde el navegador |
| Google Fonts | Playfair Display + DM Sans |
| LocalStorage | Borradores del formulario admin |
| SessionStorage | Sesión de autenticación admin |
| fetch API | Carga dinámica de projects.json |

**Zero dependencias externas** — sin frameworks, sin npm, sin build steps.

---

## 3. Estructura de Archivos

```
portafolio/
├── index.html        # Sitio público del portfolio
├── admin.html        # Panel de administración
├── projects.json     # Base de datos de proyectos (array JSON)
├── assets/
│   └── perfil.jpeg   # Foto de perfil del hero
├── PLAN.MD           # Este documento
└── README.md         # Instrucciones de uso
```

---

## 4. Funcionalidades Implementadas

### Sitio Público (`index.html`)

- **Navbar fija** con logo y navegación por secciones (scroll suave)
- **Hero section** con foto de perfil circular, título y subtítulo
- **Estadísticas dinámicas** — contador de proyectos calculado desde `projects.json`
- **Grid de proyectos** cargados dinámicamente via `fetch()` desde `projects.json`
- **Sección "Sobre mí"** con listado de habilidades técnicas
- **Sección de contacto** con enlace `mailto:`
- **Footer** con año actualizado dinámicamente
- **Animaciones CSS:** fade-up al hacer scroll, hover en tarjetas, pulse ring en foto de perfil
- **Diseño responsive** (mobile-first, breakpoints para tablet y desktop)

### Panel de Administración (`admin.html`)

- **Autenticación** con contraseña hasheada (SHA-256 via Web Crypto API)
- **Sesión persistente** en `sessionStorage` (se limpia al cerrar el navegador)
- **CRUD completo de proyectos:**
  - Crear nuevo proyecto
  - Ver lista de proyectos existentes
  - Editar proyecto seleccionado
  - Eliminar proyecto con confirmación
- **Formulario con campos:** título, descripción, año, link, URL de imagen, tags
- **Preview automático** de imagen al ingresar URL
- **Conversor inteligente de URLs de Imgur** (convierte links de página a URL directa de imagen)
- **Gestión de tags** — agregar con tecla Enter, eliminar con click en la X
- **Guardado de borradores** en `localStorage` (persiste entre sesiones)
- **Publicación con un clic** — push de `projects.json` a GitHub via API
- **Notificaciones toast** — mensajes de éxito, error e info con auto-dismiss

### Integración con GitHub API

- Configuración guardada localmente: usuario, repositorio, rama, token de acceso personal
- Push automático del archivo `projects.json` usando la GitHub REST API v3
- Detección automática del SHA actual del archivo para hacer updates (no crea duplicados)
- Contenido codificado en Base64 antes del envío
- Commit automático con mensaje que incluye fecha y hora

---

## 5. Diseño Visual

**Tema:** Oscuro con acentos dorados (paleta "luxury")

| Elemento | Valor |
|---|---|
| Fondo principal | Navy oscuro `#0a1628` |
| Fondo secundario | Navy medio `#0f2040` |
| Acento principal | Gold `#c8a96e` |
| Acento claro | Gold claro `#e8c98a` |
| Texto claro | Crema `#f4f1eb` |

**Efectos visuales:**
- Glassmorphism en la navbar (`backdrop-filter: blur`)
- Sombras doradas en elementos destacados
- Transiciones suaves en hover
- Animación `fade-up` al entrar en viewport (Intersection Observer)
- Efecto `pulse ring` animado en la foto de perfil del hero

**Tipografía:**
- **Playfair Display** — títulos y encabezados (serif elegante)
- **DM Sans** — cuerpo de texto y UI (sans-serif legible)

---

## 6. Estado Actual del Proyecto

| Característica | Estado |
|---|---|
| Sitio público | ✅ Completo y funcional |
| Panel de administración | ✅ Operativo |
| Integración GitHub API | ✅ Activa |
| Diseño responsive | ✅ Implementado |
| Animaciones CSS | ✅ Implementadas |
| Proyectos publicados | ✅ 1 proyecto (E-Commerce Dashboard PC Solutions) |

---

## 7. Historial de Versiones

| Commit | Descripción |
|---|---|
| v1.0 inicial | Versión base del portfolio |
| Iteraciones sucesivas | Mejoras en panel admin, funcionalidades CRUD |
| Integración GitHub API | Deploy automático desde el navegador |
| Ajustes UI/UX | Refinamiento visual y de interacciones |
| Update projects.json | Publicación del primer proyecto real (31/3/2026) |
| Cambios recientes | Ajustes y mejoras generales |

---

## 8. Decisiones Técnicas

**¿Por qué sin frameworks?**
El sitio es pequeño y su complejidad no justifica añadir React, Vue u otro framework. Mantener zero-dependencias simplifica el deploy en GitHub Pages y elimina el paso de build.

**¿Por qué GitHub API para el admin?**
Permite gestionar el contenido del portfolio directamente desde el navegador sin necesitar un CMS externo, servidor propio, ni base de datos. El token de acceso se guarda localmente en el navegador del autor.

**¿Por qué SHA-256 para la contraseña del admin?**
La página de admin es pública (cualquiera puede acceder a la URL), pero el hash de la contraseña evita que sea trivialmente visible en el código fuente. No es seguridad de producción, es una barrera razonable para un portfolio personal.

**¿Por qué projects.json como "base de datos"?**
Es la solución más simple para un sitio estático: un archivo JSON versionado en git, editable desde el admin y servido directamente por GitHub Pages. Sin costos, sin infraestructura.
