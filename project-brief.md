# Project Brief

**Student:** [ Ana]  
**Handle:** @[your-github-username]  
**Course:** Web Design 2025 · Fall  
**Date:** [Fill in date - Week 2]

---

## Project Concept

### What are you building?

<!-- Describe your project in 2-3 sentences -->

### Who is it for?

<!-- Define your target audience -->

### Why does it matter?

<!-- Explain the purpose and value of your project -->

---

## Technical Approach

### Core Technologies

- [ ] HTML5 (semantic markup)
- [ ] CSS3 (responsive design)
- [ ] JavaScript (if applicable)
- [ ] Other: ****\_\_\_****

### Accessibility Goals

- [X] Semantic HTML structure
- [X] Proper heading hierarchy
- [X] Alt text for images
- [X] Keyboard navigation support
- [X] Color contrast compliance
- [X] Screen reader compatibility

### Responsive Design Strategy

- [ ] Mobile-first approach
- [X] Flexible grid system
- [X] Scalable typography
- [ ] Optimized images
- [ ] Touch-friendly interactions

---

## Content Strategy

### Key Sections/Pages

1. **Galería Principal** - Grid de proyectos/ilustraciones con `grid-template-columns: repeat(auto-fit, minmax(clamp(200px, 30vw, 360px), 1fr))`
2. **Detalle de Proyecto** - Página individual con full-size image, descripción técnica, tools usados, y contexto
3. **Página "Sobre mí"** - Biografía, skills, y call-to-action (contacto/redes)

### Content Sources

<!-- Where will your content come from? -->

### Multilingual Considerations

- Primary language:
- Secondary language (optional):
- Translation strategy:

---

## Design Direction

### Visual Style

**Enfoque:** Minimalista limpio con énfasis en la obra (inspirado en Lynn & Tonic). Paleta neutra + acentos estratégicos de color. Tipografía clara y jerarquía robusta. NO overlays complejos; información visible siempre. Mobile-first responsivo.

### Color Palette

Usa variables definidas en `_variables.css`:
- **Primario:** `--color-primary: #1d4ed8` (destaca CTAs, accents)
- **Neutros:** `--color-text-primary`, `--color-text-secondary` para jerarquía
- **Fondo:** `--color-bg: #ffffff` (máximo contraste, accesibilidad)
- **Bordes/Separadores:** `--color-border-light` para sutileza

### Typography

**System stack (no custom fonts aún):** `--font-family-base: system-ui, -apple-system, 'Segoe UI', Roboto...`
- Escala fluida via `clamp()`: `--font-size-3xl` para h1, `--font-size-lg` para metadata
- Jerarquía por tamaño + peso: h1 (3xl + bold), h2 (2xl + semibold), metadata (sm + medium)
- Line-height: `--line-height-normal: 1.5` para body, `--line-height-tight: 1.2` para headings

### Inspiration/References

<!-- Análisis basado en estos 3 portfolios -->
- [Lynn & Tonic Work Gallery](https://lynnandtonic.com/work/) - Galería limpia, grid responsivo, info clara, WCAG AA+
- [Active Theory](https://activetheory.net/) - Tipografía premium, espaciado generoso, animations smooth
- *Tercera referencia: [Tobias Ahlin](https://tobiasahlin.com/) - Minimalist portfolio con motion design sutil*

**Decisiones Concretas:**
1. **Layout Grid:** `repeat(auto-fit, minmax(clamp(200px, 30vw, 360px), 1fr))` → responsive sin breakpoints
2. **Contenido por proyecto:** Visible siempre, estructura semántica `figure/figcaption`, alt text descriptivo, metadata clara (tipo + fecha + 1-2 tags)
---

## Success Metrics

### Week 4 Goals

- [ ] Functional homepage
- [ ] Basic responsive layout
- [ ] Core content in place
- [ ] Accessible markup

### Final Project Goals

- [ ] Fully responsive across devices
- [ ] Meets WCAG 2.1 AA standards
- [ ] Fast loading performance
- [ ] Complete content
- [ ] Polished visual design

---

## Reflection Questions

### What excites you most about this project?

### What challenges do you anticipate?

### How does this project connect to your learning goals?

---

_This brief will evolve as your project develops. Update it as needed and reference it in your weekly commits._
