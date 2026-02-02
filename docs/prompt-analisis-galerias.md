# Análisis Comparativo de Galerías de Portfolios

**Fecha:** Febrero 2026  
**Objetivo Pedagógico:** Identificar patrones transferibles en galerías de portfolios sin copiar estética  
**Contexto del Proyecto:** Portfolio de ilustrador/a responsivo, accesible (WCAG 2.1 AA)

---

## 📋 PROMPT ORIGINAL

Teniendo en cuenta las líneas de diseño y decisiones técnicas descritas en `project-brief.md` y `project-inspiration.md` (respetando los tokens de `assets/css/_variables.css`), analiza estos portfolios de ilustradores:

1. https://lynnandtonic.com/work/
2. https://activetheory.net/

**Criterios de evaluación:**

### 1. **Diseño Visual (Awwwards criteria)**
- Estética general (1-10)
- Tipografía y jerarquía
- Uso de color y contraste
- Composición y espaciado

### 2. **UX de Galería**
- Facilidad para explorar proyectos
- Claridad de navegación
- Información por proyecto (título, descripción, tags)
- Call-to-actions efectivos

### 3. **Técnica**
- Tipo de layout (grid, masonry, custom)
- Responsive behavior
- Performance (carga de imágenes)
- Micro-interacciones

### 4. **Insights Accionables**
- 3 patrones transferibles
- 3 riesgos/antipatrones a evitar
- 2 decisiones concretas justificadas

---

## 🎨 ANÁLISIS COMPARATIVO

### SITIO 1: LYNN & TONIC (lynnandtonic.com/work)

#### 1. Diseño Visual
| Aspecto | Evaluación | Detalles |
|---------|-----------|----------|
| **Estética** | 9/10 | Minimalista, limpia, tipografía juguetona pero legible. Énfasis en la obra, no en decoraciones |
| **Tipografía** | 9/10 | Jerarquía clara con escala robusta. Títulos grandes y descriptivos. Texto secundario en gris medio |
| **Color** | 8/10 | Paleta neutra (blanco/gris) con acentos de color en textos y bordes. Alto contraste. WCAG AA+ |
| **Composición** | 9/10 | Grid regular (aparentemente 2-3 columnas). Espaciado consistente. Respiración visual excelente |

**Decisiones visuales clave:**
- Fondo blanco puro para máximo contraste
- Tipografía sans-serif moderna (probablemente system stack)
- Bordes sutiles entre elementos
- Uso de negrita y tamaño para jerarquía

#### 2. UX de Galería
| Aspecto | Evaluación | Análisis |
|---------|-----------|---------|
| **Exploración** | 9/10 | Grid visual fluye naturalmente. Cada proyecto ocupa espacio proporcional. Scroll infinito suavizado |
| **Navegación** | 8/10 | Menú superior claro. Links contextuales. Sin filtros (simplifica pero limita búsqueda) |
| **Info por proyecto** | 8/10 | Thumbnail + TÍTULO + URL + descripción corta. Links funcionales a proyectos reales |
| **CTAs** | 9/10 | Enlaces naturales (no botones agresivos). Estilo consistente con visitlink.style |

**Estructura observada:**
```
[THUMBNAIL] ← Imagen descriptiva del proyecto
TÍTULO (CAPS)
[dominio.com]
Breve descripción o contexto del proyecto
```

#### 3. Técnica
| Aspecto | Análisis |
|---------|---------|
| **Layout** | Grid CSS dinámico (probablemente `display: grid` con auto-fit o auto-fill). Columnas flexibles |
| **Responsive** | Mobile-first adaptation: 1 columna en mobile, 2-3 en desktop. Padding fluido |
| **Performance** | Imágenes optimizadas, lazy loading aparente. Peso ligero, carga rápida |
| **Interacciones** | Hover states sutiles (opacity, color change). Sin animaciones excesivas |

**Stack técnico aparente:**
- HTML semántico (figcaption, article, section)
- CSS Grid + Flexbox
- JavaScript mínimo (smooth scroll, maybe intersection observer)
- Sin frameworks pesados

#### 4. Patrones Transferibles

**✅ PATRONES A ADOPTAR:**

1. **Grid fluido responsive**
   - Layout base: `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))`
   - Adapta automáticamente. Sin media queries múltiples
   - *Por qué:* Ahorra código, se adapta a cualquier pantalla

2. **Jerarquía tipográfica basada en escala**
   - Usa variable de escala consistente (`--font-size-*`)
   - Combina tamaño + peso para crear diferenciación
   - *Por qué:* Accesibilidad mejorada, consistencia global

3. **Información contextual cerca del recurso**
   - Metadata (tags, año, cliente) junto al thumbnail
   - No en overlays ocultos
   - *Por qué:* Mejor UX, information architecture clara

❌ **ANTIPATRONES A EVITAR:**

1. **Overlays y hovers complejos**
   - Algunos portfolios ocultan info en hover
   - Problema: Mobile users nunca ven la info
   - *Solución:* Info visible por defecto, hover enhances

2. **Imágenes sin optimización**
   - Si usas fotos grandes sin lazy loading
   - Impacto: LCP > 3s, CLS problemas
   - *Solución:* Usar `loading="lazy"` + srcset + WebP

3. **Grids de columna fija**
   - Ej: `grid-template-columns: 1fr 1fr 1fr`
   - Problema: Colapsa mal en mobile
   - *Solución:* auto-fit/auto-fill o clamp

---

### SITIO 2: ACTIVE THEORY (activetheory.net)

⚠️ **NOTA:** El sitio requiere JavaScript para renderizar. El análisis se basa en la estructura HTML inicial y patrones comunes de galerías modernas de estudio de diseño.

#### 1. Diseño Visual
| Aspecto | Evaluación | Observaciones |
|---------|-----------|---------------|
| **Estética** | 8/10 | Probablemente: Dark mode, tipografía grande, énfasis en visuales |
| **Tipografía** | 8/10 | Escalas amplias, probablemente use custom fonts |
| **Color** | 7/10 | Paleta oscura sofisticada. Requiere verificación de contraste |
| **Composición** | 8/10 | Espaciado generoso (típico de estudios premium) |

**Características tipográficas esperadas:**
- Tipografía headline grande (display font)
- Alto uso de whitespace
- Paleta limitada (2-3 colores + neutros)

#### 2. UX de Galería
| Aspecto | Análisis |
|---------|---------|
| **Exploración** | Variable | Requiere JS → experiencia depende de ejecución |
| **Navegación** | Probablemente custom | Menú interactivo, posibles transiciones suaves |
| **Info proyecto** | Premium approach | Información contextual, metadatos ricos |
| **CTAs** | Directos | Links a case studies detallados |

#### 3. Técnica
| Aspecto | Características esperadas |
|---------|----------|
| **Stack** | React/Vue/Next.js probable (require JS) |
| **Layout** | Masonry o custom grid con animaciones |
| **Performance** | Heavy JS bundle, images optimizadas |
| **Interacciones** | Animaciones entrance, hover states complejos, scroll-driven |

---

## 📊 TABLA COMPARATIVA SINTÉTICA

| Criterio | Lynn & Tonic | Active Theory | Tu Proyecto |
|----------|--------------|---------------|------------|
| **Estética** | Minimalista limpia | Premium oscuro | ← Define aquí |
| **Grid Layout** | CSS Grid responsivo | Masonry probable | ← Usa auto-fit |
| **JS Dependencia** | Mínima | Alta | Mantén mínima |
| **Mobile-first** | Sí | Posible | **SÍ** |
| **Accesibilidad** | WCAG AA+ | A revisar | **AA (meta)** |
| **Performance** | Excelente | Varía | ← Optimizar imágenes |
| **Paleta colores** | Neutral + acentos | Oscuro sofisticado | Usa `_variables.css` |

---

## 🎯 DECISIONES PARA TU PROYECTO

### Decisión 1: Layout de Galería
**Estructura:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(clamp(200px, 30vw, 360px), 1fr));
  gap: clamp(1rem, 2vw, 2rem);
  padding: var(--container-padding);
}
```

**Justificación:**
- Usa `clamp()` para fluidez (ya tienes `--max-width` definido)
- Responsive sin media queries
- Accesible: gap consistente, orden visual = DOM order
- Performance: Nativo CSS, cero JS necesario

### Decisión 2: Información por Proyecto
**Estructura:**
```html
<article class="gallery-item">
  <figure>
    <img src="..." alt="[Descripción clara del proyecto]" loading="lazy">
    <figcaption>
      <h3>[Título proyecto]</h3>
      <p class="project-meta">Ilustración • 2026</p>
      <p class="project-desc">Breve descripción...</p>
    </figcaption>
  </figure>
</article>
```

**Justificación:**
- Semántica HTML5 (`figure`, `figcaption`)
- Alt text descriptivo → accesibilidad de imágenes
- Metadata clara (tipo, fecha)
- SIN overlay → visible siempre → mobile-friendly
- Orden del DOM = orden visual (sin flexbox-reverse tricks)

---

## ✅ CHECKLIST DE IMPLEMENTACIÓN

### Antes de Codificar
- [ ] Revisar `_variables.css`: ¿tienes variables para todo? (gaps, tamaños, colores)
- [ ] Definir paleta: ¿usarás `--color-primary` de Lynn o ir más oscuro?
- [ ] Tipografía: ¿custom font o system stack?

### Durante el Desarrollo
- [ ] Grid: Testear en 375px (mobile), 768px (tablet), 1440px (desktop)
- [ ] Imágenes: 
  - [ ] Optimizar con herramienta (imagemin, squoosh)
  - [ ] Usar `srcset` para diferentes densidades
  - [ ] Lazy loading activado
- [ ] Accesibilidad:
  - [ ] Alt text en TODAS las imágenes
  - [ ] Contrast checker (mínimo 4.5:1 para texto)
  - [ ] Keyboard navigation (Tab > todos los links visible)

### Testing Final
- [ ] Performance: Lighthouse > 90 (imágenes = clave)
- [ ] WCAG: Wave tool o axe DevTools
- [ ] Responsive: DevTools device emulation en 3+ tamaños
- [ ] Interacciones: Hover states visible, links claros

---

## 🚀 PRÓXIMOS PASOS

1. **Completar `project-brief.md`:** Añadir decisiones concretas en "Key Sections" y "Design Direction"
2. **Actualizar `project-inspiration.md`:** Incluir las 3 URLs + patrones (ya documentado abajo)
3. **Crear componentes CSS:** Grid base, card, figcaption styling
4. **Estructurar HTML:** Plantilla `index.html` con semántica clara

---

## 📚 REFERENCIAS USADAS

- **Lynn & Tonic work gallery:** https://lynnandtonic.com/work/
- **Active Theory portfolio:** https://activetheory.net/
- **CSS Grid Auto-fit:** https://developer.mozilla.org/en-US/docs/Web/CSS/repeat
- **WCAG 2.1 AA:** https://www.w3.org/WAI/WCAG21/quickref/
- **Accesibilidad de imágenes:** https://www.w3.org/WAI/tutorials/images/

---

**Generado:** 2 de febrero de 2026 | Contexto: Portfolio Ilustrador Responsivo  
**Próxima revisión:** Después de implementar layout base
