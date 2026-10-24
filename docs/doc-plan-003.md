# Documentación del Plan 003: Landing Page Nicolás Ariel Sena

## Resumen
Transformación del `index.html` básico ("Hola mundo") en una landing page profesional completa usando la identidad visual de Devlights (Bootcamp 5.0) y el contenido biográfico de Nicolás Ariel Sena.

---

## Pasos Realizados

### 1. Análisis de Requisitos
- **Diseño base**: `docs/result-scraping-002.md` - Guía UI/UX Bootcamp 5.0 Devlights
- **Contenido**: `docs/result-scraping-001.md` - Perfil profesional completo de Nicolás Ariel Sena
- **Mantener**: "Hola mundo" transformado en "Hola mundo, me presento: Nicolás Ariel Sena"

### 2. Estructura de la Landing Page
Creé las siguientes secciones en un solo archivo `index.html`:

| Sección | ID | Contenido |
|---------|-----|-----------|
| Header/Nav | `#hero` | Logo NAS, navegación responsive, menú móvil |
| Hero | `#hero` | Badge "Hola mundo, me presento...", título principal, stats, CTAs |
| Sobre Mí | `#about` | Bio completa, 4 tarjetas de enfoque (IA, Full Stack, Data, Educación) |
| Skills/Stack | `#skills` | 6 categorías con tags interactivos (IA, Backend, Frontend, DB, DevOps, Gestión) |
| Proyectos | `#projects` | 6 tarjetas de logros reales (Alura, SSI, Aikestar, SSI Labs, Hackathon, Open Source) |
| Experiencia | `#experience` | Timeline 4 roles (SSI, Alura, Aikestar/Beetrack, UNNE) con tech tags |
| Objetivos | `#objectives` | 4 cards de visión profesional |
| FAQ | `#faq` | 5 preguntas usando `<details>/<summary>` nativo |
| Contacto | `#contact` | Info de contacto + formulario funcional (Formspree) |
| Footer | `#footer` | Copyright, links, redes sociales |

### 3. Implementación Técnica

#### Stack (todo vía CDN, un solo archivo)
- **Tailwind CSS** (Play CDN) - Configuración custom con colores de marca
- **Google Fonts** - Poppins (títulos) + Inter (cuerpo)
- **FontAwesome 6.4** - Iconos
- **AOS 2.3.1** - Animaciones scroll reveal

#### Paleta de Colores (brand)
```css
brand: {
  bg: '#F4F2EC',      // Beige claro (fondo principal)
  dark: '#1C1C1C',    // Casi negro (header/footer)
  purple: '#9D4EDD',  // Acento principal
  blue: '#3B82F6',    // Acento secundario
  red: '#EF4444',     // Acento alerta
  yellow: '#FBBF24',  // Acento warning
  text: '#111827',    // Texto principal
  textLight: '#6B7280' // Texto secundario
}
```

#### Animaciones e Interacciones
- **AOS**: `fade-up`, `fade-right`, `fade-left`, `zoom-in` con delays escalonados
- **Hover states**: `translateY(-5px)`, shadow increase, color transitions
- **Skill tags**: Scale + shadow on hover
- **Project/Experience cards**: Lift + shadow on hover
- **FAQ**: Native `<details>` con flecha rotatoria CSS-only
- **Mobile menu**: Toggle hamburger
- **Active nav highlight**: IntersectionObserver
- **Form**: Fetch API con feedback visual (loading, success, error)

#### Formas Geométricas de Fondo
4 divs absolutos con `filter: blur(60px)` y opacidad baja en Hero, About, Projects, Contact

### 4. Contenido Integrado (de result-scraping-001.md)
- ✅ Bio completa (Corrientes, UNNE, SSI, Alura, YouTube)
- ✅ 4 áreas especialización (IA, Full Stack, Análisis/QA, Educación)
- ✅ 5 logros/proyectos destacados con métricas
- ✅ Stack tecnológico completo (6 categorías)
- ✅ 4 objetivos visión profesional
- ✅ Enlaces digitales (LinkedIn, Alura, YouTube, GitHub)

---

## Cómo Publicar en GitHub Pages

### Opción A: Desde la Interfaz Web (Recomendado)

1. **Subir el repositorio a GitHub**
   Como bien dijiste. Esto está cubierto por la clase del sábado. Omito

2. **Activar GitHub Pages**
   - Ve a tu repositorio en GitHub.com
   - Settings → Pages (menú lateral izquierdo)
   - Source: "Deploy from a branch"
   - Branch: `main` / `(root)`
   - Save

3. **Acceder a tu sitio**
   - URL: `https://TU_USUARIO.github.io/mi-landing/`
   - Tarda 1-3 minutos en desplegar

### Opción B: GitHub Actions (Automático)

Crea `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - uses: actions/deploy-pages@v4
```
Luego en Settings → Pages → Source: "GitHub Actions"

### Opción C: Dominio Personalizado (Opcional)

1. En Settings → Pages → Custom domain: `tudominio.com`
2. En tu proveedor DNS añade:
   - Type: `CNAME`, Name: `www`, Value: `TU_USUARIO.github.io`
   - Type: `A`, Name: `@`, Value: `185.199.108.153` (y .109, .110, .111)
3. En repositorio: `echo "tudominio.com" > CNAME` y commit

---

## Verificación Local

```bash
# Opción 1: Python
python -m http.server 8000
# Abre http://localhost:8000

# Opción 2: Node (npx serve)
npx serve .

# Opción 3: VS Code Live Server
# Click derecho en index.html → "Open with Live Server"
```

---

## Checklist de Calidad

- [x] Un solo archivo `index.html` (sin dependencias locales)
- [x] Responsive: mobile-first, breakpoints md/lg
- [x] Accesibilidad: semántica HTML5, alt text, contraste, focus states
- [x] Performance: CDN cacheados, sin build step
- [x] SEO: meta tags, title, description, estructura heading
- [x] Formulario funcional (Formspree - requiere configurar endpoint real)
- [x] Animaciones suaves (AOS + CSS transitions)
- [x] Modo oscuro solo en header/footer (diseño original)
- [x] "Hola mundo" transformado y visible en Hero

---

## Próximos Pasos Sugeridos

1. **Configurar Formspree real**: Reemplazar `your-form-id` en el action del form
2. **Añadir favicon**: `<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🚀</text></svg>">`
3. **Analytics**: Añadir Google Analytics / Plausible / Umami
4. **PWA**: Manifest + Service Worker para installability
5. **Imágenes reales**: Reemplazar placeholders por fotos reales (optimizadas WebP)

---

## Archivos Generados/Modificados

```
mi-landing/
├── index.html          ← Landing page completa (único archivo)
├── docs/
│   ├── plan-003.md     ← Plan original
│   ├── result-scraping-001.md  ← Contenido fuente
│   ├── result-scraping-002.md  ← Diseño fuente
│   └── doc-plan-003.md ← Esta documentación
```

---

**Fecha**: 2025-10-23  
**Autor**: Nicolás Ariel Sena (asistido por opencode)  
**Versión**: 1.0.0