# Checklist de Implementación - Análisis de Galerías

**Proyecto:** Portfolio de Ilustrador/a  
**Fecha:** 2 de febrero de 2026  
**Basado en:** Análisis comparativo Lynn & Tonic + Active Theory  
**Objetivo:** Implementar galería responsiva, accesible, con patrones comprobados

---

## 📋 FASE 1: PREPARACIÓN (Antes de Codificar)

### Validación de Decisiones

- [ ] **Leer completamente** `docs/prompt-analisis-galerias.md` (análisis completo)
- [ ] **Revisar actualizado** `project-brief.md` (decisiones concretas)
- [ ] **Chequear tokens** en `assets/css/_variables.css`:
  - [ ] Spacing: `--space-*` definidas
  - [ ] Typography: `--font-size-*` y `--font-weight-*` completas
  - [ ] Colors: Palette consistente
  - [ ] Transitions: `--transition-*` para micro-interacciones
  - [ ] Z-index scale: Stacking definido

### Decisiones de Diseño a Confirmar

- [ ] **Paleta de colores** final (usar `--color-primary`, neutros, etc.)
- [ ] **Custom fonts:** ¿Sistema stack o Google Fonts? (recomendación: system stack por performance)
- [ ] **Estructura de navegación:** Menú superior + enlace logo
- [ ] **Resoluciones target:** Mobile (375px), Tablet (768px), Desktop (1440px)
- [ ] **Imagen de ejemplo:** Dimensión estándar (ej: 800x600, 16:9)

---

## 🛠️ FASE 2: ESTRUCTURA HTML

### Semántica de Galería

- [ ] **Crear estructura base en `index.html`:**

```html
<main class="gallery-container">
  <section class="gallery">
    <article class="gallery-item">
      <figure>
        <img 
          src="proyecto-01.jpg" 
          alt="[Descripción clara: tipo de ilustración, contexto, técnica]"
          loading="lazy"
          width="800"
          height="600"
        >
        <figcaption>
          <h3 class="project-title">Título del Proyecto</h3>
          <p class="project-meta">Ilustración • 2026 • Cliente</p>
          <p class="project-desc">Breve descripción (1-2 líneas)...</p>
        </figcaption>
      </figure>
    </article>
    <!-- Repetir para cada proyecto -->
  </section>
</main>
```

**Checklist HTML:**
- [ ] `<main>` envuelve el contenido principal
- [ ] `<section class="gallery">` agrupa elementos
- [ ] `<article>` cada proyecto individual
- [ ] `<figure>` + `<figcaption>` estructura semántica
- [ ] `alt=""` en TODAS las imágenes (específico, >20 caracteres)
- [ ] `loading="lazy"` en imágenes (performance)
- [ ] `width` + `height` en `<img>` (evita CLS)
- [ ] Heading hierarchy respetado: h1 (página) → h2 (secciones) → h3 (items)

---

## 🎨 FASE 3: CSS - LAYOUT RESPONSIVO

### Grid Base

- [ ] **Crear en `assets/css/_components.css` o `style.css`:**

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(clamp(200px, 30vw, 360px), 1fr));
  gap: clamp(1rem, 2vw, 2rem);
  padding: var(--container-padding);
}

.gallery-item {
  display: flex;
  flex-direction: column;
}

figure {
  margin: 0; /* Reset default margins */
  display: flex;
  flex-direction: column;
}

figcaption {
  padding: var(--space-lg);
  background: var(--color-bg-light);
  border: 1px solid var(--color-border-light);
  border-top: none;
}
```

**Checklist CSS:**
- [ ] Grid dinámico `auto-fit` (sin media queries para grid)
- [ ] Uso de `clamp()` para gap y sizing
- [ ] Variables de `_variables.css` en TODOS los valores
- [ ] Reset de márgenes en `figure`
- [ ] Flexbox para alineación dentro del item
- [ ] Border consistente (usar `--color-border-*`)

### Tipografía en Galería

- [ ] **Estilos de títulos y metadata:**

```css
.project-title {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-tight);
  color: var(--color-text-primary);
  margin: 0 0 var(--space-sm) 0;
}

.project-meta {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-medium);
  color: var(--color-text-secondary);
  margin: 0 0 var(--space-md) 0;
}

.project-desc {
  font-size: var(--font-size-base);
  line-height: var(--line-height-normal);
  color: var(--color-text-secondary);
  margin: 0;
}
```

**Checklist Tipografía:**
- [ ] Escalas consistentes (`--font-size-*`)
- [ ] Jerarquía por tamaño + peso (no solo color)
- [ ] Line-height apropiado para cada nivel
- [ ] Margins reset a 0, luego setear específicamente
- [ ] Color accessibility: usar variables de `_variables.css`

### Imágenes y Responsive

- [ ] **Estilos de imagen:**

```css
img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 4 / 3; /* O tu ratio estándar */
  object-fit: cover;
  background-color: var(--color-bg-light);
}
```

**Checklist Imágenes:**
- [ ] `display: block` (elimina inline whitespace)
- [ ] `width: 100%` (fill container)
- [ ] `height: auto` (mantiene aspect ratio)
- [ ] `aspect-ratio` (evita CLS si imágenes varían)
- [ ] `object-fit: cover` (rellena el container sin distorsión)
- [ ] Background color como fallback

### Micro-interacciones (Sutiles)

- [ ] **Hover states:**

```css
.gallery-item {
  transition: transform var(--transition-base), 
              box-shadow var(--transition-base);
}

.gallery-item:hover,
.gallery-item:focus-within {
  transform: translateY(-4px);
  box-shadow: var(--shadow-md);
}

figcaption a:focus-visible {
  outline: 3px solid var(--color-primary);
  outline-offset: 2px;
}
```

**Checklist Interacciones:**
- [ ] Hover: cambio sutil (transform pequeño, sombra)
- [ ] Focus-visible: outline claro para keyboard users
- [ ] Transitions: usar variables `--transition-*`
- [ ] NO overlay complejos (info visible siempre)

---

## ♿ FASE 4: ACCESIBILIDAD (WCAG 2.1 AA)

### Checklist de Contraste

- [ ] **Validar con Wave/axe tools:**
  - [ ] Text color vs background: mínimo 4.5:1 (normal text)
  - [ ] Heading color: mínimo 3:1
  - [ ] Focus indicators: visible en todos los interactive elements
  - [ ] No hay errores WCAG AA

**Herramientas:**
- https://www.tota11y.org/ (Chrome extension)
- https://wave.webaim.org/ (web tool)
- https://www.deque.com/axe/devtools/ (DevTools extension)

### Checklist de Navegación

- [ ] **Keyboard navigation:**
  - [ ] Tab recorre todos los links en orden visual (DOM order)
  - [ ] Shift+Tab retrocede
  - [ ] Enter activa links/buttons
  - [ ] No hay trampas de keyboard
- [ ] **Skip link:** Opcionalmente, añade link "Skip to main" (escondido pero accesible)

```html
<a href="#main" class="skip-link">Skip to main content</a>
<main id="main">...</main>
```

```css
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--color-primary);
  color: white;
  padding: 8px;
  text-decoration: none;
}

.skip-link:focus {
  top: 0;
}
```

### Checklist de Imágenes

- [ ] **Cada `<img>` tiene `alt` descriptivo:**
  - [ ] NO: `alt="imagen"` o `alt="foto"`
  - [ ] SÍ: `alt="Ilustración digital en acrílico digital de montañas neblinosas, colores azul y violeta, estilo minimalista"`
  - [ ] Contexto claro en alt text
  - [ ] Longitud: 20-150 caracteres aproximadamente

### Checklist de Semántica

- [ ] **Orden de headings correcto:**
  - [ ] Solo UNA `<h1>` por página (título principal)
  - [ ] `<h2>` para secciones (Gallery, About, etc.)
  - [ ] NO saltarse niveles (h1 → h3 es incorrecto)
- [ ] **Uso de `<figure>` / `<figcaption>`** para imágenes con caption
- [ ] **Links descriptivos:** NO `[Click here]`, SÍ `[View project details]`

---

## 📊 FASE 5: PERFORMANCE

### Optimización de Imágenes

- [ ] **Antes de subir imágenes:**
  - [ ] Redimensionar a 800x600 máximo (o tu tamaño estándar)
  - [ ] Comprimir con herramienta:
    - Squoosh: https://squoosh.app/
    - ImageOptim (Mac)
    - FileOptimizer (Windows)
  - [ ] Formato: WebP > JPG (compatibilidad fallback)
  - [ ] Tamaño meta: < 100KB por imagen

**Estructura recomendada:**
```html
<picture>
  <source srcset="proyecto.webp" type="image/webp">
  <img src="proyecto.jpg" alt="...">
</picture>
```

### Checklist Lighthouse

- [ ] **Ejecutar Lighthouse en DevTools (F12 > Lighthouse):**
  - [ ] Performance: > 90
  - [ ] Accessibility: > 95
  - [ ] Best Practices: > 90
  - [ ] SEO: > 90
- [ ] **Si no alcanzas:**
  - [ ] Performance bajo: revisar LCP (images), CLS (layout)
  - [ ] Accessibility bajo: falta alt text, contraste, focus indicators
  - [ ] SEO bajo: añadir meta description, keywords, structured data

### Checklist de Métricas Core Web Vitals

- [ ] **LCP (Largest Contentful Paint):** < 2.5s
  - Impactado por: tamaño de imágenes, priorización
- [ ] **FID (First Input Delay):** < 100ms
  - Impactado por: JS heavy
- [ ] **CLS (Cumulative Layout Shift):** < 0.1
  - Impactado por: imágenes sin `aspect-ratio`, fonts sin preload

---

## 🧪 FASE 6: TESTING RESPONSIVO

### Breakpoints de Testing

- [ ] **Mobile (375px):**
  - [ ] 1 columna grid
  - [ ] Touch targets > 44px
  - [ ] No overflow horizontal
- [ ] **Tablet (768px):**
  - [ ] 2 columnas grid
  - [ ] Spacing proporcional
- [ ] **Desktop (1440px):**
  - [ ] 3-4 columnas grid
  - [ ] Max-width respetado
  - [ ] Hover states funcionan

### Navegadores

- [ ] **Chrome/Edge** (Chromium)
- [ ] **Firefox**
- [ ] **Safari** (si tienes Mac)
- [ ] **Mobile Safari (iOS)**

**Herramientas:**
- DevTools responsive design mode (F12)
- BrowserStack: https://www.browserstack.com/ (pago pero exhaustivo)

---

## 📝 FASE 7: DOCUMENTACIÓN

### Comentarios en Código

- [ ] **CSS:** Comentar secciones principales

```css
/* ===== GALLERY GRID ===== */
.gallery {
  /* ... */
}

/* ===== PROJECT ITEMS ===== */
.gallery-item {
  /* ... */
}
```

- [ ] **HTML:** Comentar estructura lógica si es compleja

```html
<!-- Gallery Section -->
<section class="gallery" role="region" aria-label="Projects gallery">
  <!-- Project Items -->
  <article class="gallery-item">
    <!-- ... -->
  </article>
</section>
```

### Actualizar README

- [ ] **Añadir a `README.md`:**
  - [ ] Decisiones de design (grid, paleta, tipografía)
  - [ ] Variables CSS usadas
  - [ ] Comandos para verificar (Lighthouse, WAVE)
  - [ ] Browser compatibility

---

## ✅ FASE 8: VALIDACIÓN FINAL

### HTML Validation

- [ ] **Validar HTML:** https://validator.w3.org/
  - [ ] Sin errores fatales
  - [ ] Warnings documentados si existen

### CSS Validation

- [ ] **Validar CSS:** https://jigsaw.w3.org/css-validator/
  - [ ] Compatibilidad con navegadores target
  - [ ] Prefixes añadidos si es necesario (ej: `-webkit-`)

### Git Commit

- [ ] **Commits descriptivos:**
  ```bash
  git add .
  git commit -m "feat: implement responsive gallery grid with auto-fit layout"
  git commit -m "style: add typography hierarchy with font-weight + size"
  git commit -m "a11y: validate WCAG AA contrast and alt text"
  git commit -m "perf: optimize images with lazy loading and aspect-ratio"
  ```

---

## 🚀 FASE 9: DESPLIEGUE

### Pre-deploy Checklist

- [ ] Todos los tests pasaron
- [ ] Lighthouse > 90 (todos los scores)
- [ ] WCAG AA validado
- [ ] Responsive probado en 3+ breakpoints
- [ ] Links funcionales
- [ ] Imágenes optimizadas

### Opciones de Hosting

- [ ] **Vercel:** https://vercel.com/ (Next.js friendly, free tier)
- [ ] **Netlify:** https://www.netlify.com/ (static sites, free tier)
- [ ] **GitHub Pages:** https://pages.github.com/ (gratuito, simple)
- [ ] **Servidor personal:** Si tienes acceso

---

## 📚 REFERENCIAS RÁPIDAS

### CSS Grid
- [MDN: CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [CSS-Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

### Accesibilidad
- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/)
- [WebAIM: Image Alt Text](https://webaim.org/articles/alttext/)
- [A11y Project Checklist](https://www.a11yproject.com/checklist/)

### Performance
- [Web.dev: Core Web Vitals](https://web.dev/vitals/)
- [Lighthouse Guide](https://developers.google.com/web/tools/lighthouse)

### Tipografía
- [Type Scale Calculator](https://typescale.com/)
- [Font Pairing Tool](https://fontjoy.com/)

---

## 📞 SOPORTE & PREGUNTAS

**Si encuentras problemas:**

1. **Layout no responde:** Verifica `grid-template-columns` y `clamp()` sintaxis
2. **Imágenes se distorsionan:** Añade `object-fit: cover` y `aspect-ratio`
3. **Focus states no visibles:** Añade `outline` + `outline-offset` en `:focus-visible`
4. **Lighthouse bajo:** Usa DevTools > Lighthouse para detalles específicos
5. **Alt text confuso:** Prueba describiendo la imagen a alguien sin verla

---

**Última actualización:** 2 febrero 2026  
**Próxima revisión:** Después de implementar Fase 3 (CSS Layout)

