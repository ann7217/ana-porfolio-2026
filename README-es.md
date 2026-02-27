https://ann7217.github.io/ana-porfolio-2026/

# Mi portafolio de ilustracion web

_Critical Coding for a Better Living._

**Construye un sitio real, accesible y multilingüe—commit cada semana.**

Este proyecto es mi portafolio web personal donde muestro mis proyectos y habilidades como ilustradora. Incluye diferentes trabajos como bocetos, ilustraciones personales, organizados para presentar mi estilo artístico. El objetivo es crear un sitio accesible, responsive y fácil de navegar. 

## Propósito y Audiencia

- **Mi objetivo:** el objetivo de este sitio es presentar mi trabajo como ilustradora y crear una presencia online donde pueda mostrar mis proyectos artísticos.

## Tecnologías Principales (Explicación Detallada)

### GitHub Pages

- Los estudiantes habilitan Pages en su repositorio para publicar el proyecto en vivo en una URL como `https://usuario.github.io/proyecto`.
- El despliegue es automático: cada commit en `main` actualiza el sitio.

### Jekyll

- No es necesario que los estudiantes lo usen directamente, pero Pages lo emplea en segundo plano.
- Se incluye un archivo `.nojekyll` para evitar conflictos, salvo que se requiera explícitamente.

### GitHub Actions

- Se incluyen flujos CI opcionales:

  - **Critical CI (Estudiante):** verifica enlaces, peso de página y accesibilidad.

- Se recomienda su uso: así los estudiantes aprenden cómo los profesionales automatizan controles de calidad.

## Tecnologías de Soporte (Resumen)

- **Markdown:** para `README.md` y `project-brief.md`.
- **YAML:** en `project.yaml` para describir metadatos (título, lema, URL, etc.).
- **Liquid:** no lo editan los estudiantes directamente, pero se usa en plantillas de curso/profesor para mostrar info del proyecto.
- **JSON-LD:** se añade automáticamente en los templates cuando los proyectos aparecen en el showroom.

## Uso de IA
Se utilizó inteligencia artificial como apoyo para:
Resolución de dudas técnicas, generar ideas, mejorar el proyecto.

## Estructura del Repositorio

```plaintext
student-project-template/
├── index.html              # Página principal (HTML semántico)
├── assets/
│   ├── css/
│   │   ├── style.css       # Entrada principal (importa parciales)
│   │   ├── _variables.css  # Tokens de diseño
│   │   ├── _reset.css      # Reset del navegador
│   │   ├── _base.css       # Tipografía, enlaces
│   │   ├── _layout.css     # Contenedores, grids
│   │   ├── _components.css # Header, footer, botones, cards
│   │   ├── _utilities.css  # Clases auxiliares
│   │   ├── _accessibility.css
│   │   ├── _responsive.css
│   │   └── _print.css
│   └── js/
│       └── main.js         # Funcionalidad JavaScript
├── images/                 # Imágenes (mantener optimizadas)
├── project.yaml            # Metadatos del proyecto (Semana 4)
├── project-brief.md        # Definición del proyecto (Semana 2)
├── project-inspiration.md  # Referencias y moodboard
├── GETTING-STARTED.md      # Guía de inicio y metodología
├── README-es.md            # Guía y registro semanal
├── .nojekyll               # Evita conflictos con Jekyll
└── .github/workflows/
    └── critical.yml        # Comprobaciones CI/CD
```

## Flujo en la Práctica

1. **Clonar Plantilla:** El estudiante crea su repo a partir de esta plantilla.
2. **Semana 1:** Configurar repo, hacer primer commit (actualizar README).
3. **Semana 2:** Completar `project-brief.md` y `project.yaml` (definición del proyecto).
4. **Commits Semanales:** Actualizar `index.html`, CSS y JS con lo aprendido. Cada clase → un commit.
5. **Semana 4:** Asegurarse de completar `project.yaml`; enviar metadatos al repo del curso (PR o formulario).
6. **Semana 5+:** Continuar mejorando el proyecto y reflexionando sobre los commits.

## Escalabilidad y Retroalimentación

- **Log de Commits:** Cada commit documenta el aprendizaje semanal.
- **Revisión entre Pares:** En la Semana 5, los compañeros exploran los proyectos a través del showroom.
- **CI:** Los checks automáticos indican rápidamente problemas (enlaces rotos, activos pesados, accesibilidad).
- **Profesorado:** Revisa commits seleccionados o evalúa el proyecto final.

## Diferencias con otros Repositorios

- `web-foundations`: contiene lecciones y metodología comunes (no editable por estudiantes).
- `professor-course-template`: organiza el curso y el showroom.
- `student-project-template`: espacio creativo individual; este repo es el que se evalúa.

## Referencias

- GitHub Pages – [https://docs.github.com/es/pages](https://docs.github.com/es/pages)
- GitHub Actions – [https://docs.github.com/es/actions](https://docs.github.com/es/actions)
- Jekyll – [https://jekyllrb.com](https://jekyllrb.com)
- Guía Markdown – [https://www.markdownguide.org](https://www.markdownguide.org)
- Introducción YAML – [https://learnxinyminutes.com/docs/yaml/](https://learnxinyminutes.com/docs/yaml/)
- Schema.org / JSON-LD – [https://schema.org](https://schema.org)

© 2025 Rubén Vega Balbás, PhD — WEB ATELIER (UDIT) · ORCID: <https://orcid.org/0000-0001-6862-9081>
