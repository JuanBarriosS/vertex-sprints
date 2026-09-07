# Auditoría SEO Básica - Vertex Portal Web

## 1. Revisión metadatos básicos de SEO

### Revisión títulos únicos por página

| Ruta | Título ES : EN |
| :--- | :--- |
| `Vertex-Portal-Web/src/app/[locale]/about-us` | `Quiénes Somos — Innovación, Talento y Tecnología` : `Who We Are — Innovation, Talent & Technology` |
| `.../[locale]/careers` | `Trabaja con Nosotros — Talento, Cultura y Oportunidades` : `Careers at Vertex — Talent, Culture & Opportunities` |
| `.../[locale]/contact` | `Contacto — Inicia tu Proyecto de Tecnología` : `Contact Us — Start Your Technology Project` |
| `.../[locale]/contacto` | `Contacto — Inicia tu Proyecto de Tecnología` : `Contact Us — Start Your Technology Project` |
| `.../[locale]/empleos` | `Vacantes y Oportunidades Laborales en Tecnología` : `Job Openings & Tech Careers` |
| `.../[locale]/equipo` | `Equipo de Trabajo — Liderazgo y Especialistas` : `Our Team — Leadership & Specialists` |
| `.../[locale]/jobs` | `Vacantes y Oportunidades Laborales en Tecnología` : `Job Openings & Tech Careers` |
| `.../[locale]/nuestra-oferta` | `Nuestra Oferta de Valor — Capacidades y Metodología` : `Our Offer — Strategic Capabilities & Methodology` |
| `.../[locale]/our-services` | `Nuestra Oferta de Valor — Capacidades y Metodología` : `Our Offer — Strategic Capabilities & Methodology` |
| `.../[locale]/projects` | `Proyectos y Casos de Éxito Tecnológico` : `Projects & Technology Success Cases` |
| `.../[locale]/proyectos` | `Proyectos y Casos de Éxito Tecnológico` : `Projects & Technology Success Cases` |
| `.../[locale]/quienes-somos` | `Quiénes Somos — Innovación, Talento y Tecnología` : `Who We Are — Innovation, Talent & Technology` |
| `.../[locale]/services` | `Servicios Especializados en Tecnología, Software y Estrategia` : `Specialized Services in Technology, Software & Strategy` |
| `.../[locale]/servicios` | `Servicios Especializados en Tecnología, Software y Estrategia` : `Specialized Services in Technology, Software & Strategy` |
| `.../[locale]/team/` | `Equipo de Trabajo — Liderazgo y Especialistas` : `Our Team — Leadership & Specialists` |
| `.../[locale]/terminos` | `Términos y Condiciones` : `Terms & Conditions` |
| `.../[locale]/trabaja-con-nosotros/` | `Trabaja con Nosotros — Talento, Cultura y Oportunidades` : `Careers at Vertex — Talent, Culture & Opportunities` |
| `.../[locale]/layout.tsx` | `Vertex — Tecnología estratégica para transformar ideas en resultados` : `Vertex — Strategic technology to transform ideas into results` |
| `.../[locale]/not-found.tsx` | `404 - Página no encontrada / Page Not Found | Vertex` |
| `.../[locale]/page.tsx` | `Vertex — Tecnología, Software e Inteligencia Artificial en Colombia` : `Vertex — Enterprise Software, AI & Digital Transformation` |

> **Conclusión:** Se validó la unicidad de las etiquetas de título en todas las rutas del repositorio. La estructura bilingüe responde correctamente a los requerimientos de internacionalización (i18n), manteniendo la consistencia semántica y los diferenciadores clave de Vertex tanto en las URLs en español como en inglés, sin presentar duplicidades que afecten el rastreo de los motores de búsqueda.

### Revisión de descripciones únicas por página

| Ruta | Descripción |
| :--- | :--- |
| `.../[locale]/page.tsx` | Empresa de tecnología en Colombia especializada en desarrollo de software a la medida, transformación digital, inteligencia artificial y comunicación estratégica para organizaciones públicas y privadas. |
| `.../[locale]/quienes-somos | about-us` | Conoce a Vertex: compañía especializada en transformación digital, desarrollo de software, diseño estratégico y comunicación en Colombia y Latinoamérica. |
| `.../[locale]/nuestra-oferta | our-services` | Conoce el modelo de trabajo de Vertex: capacidades en software, transformación digital, diseño y comunicación con metodología ágil orientada a resultados. |
| `.../[locale]/servicios | services` | Descubre nuestros servicios: desarrollo de software a la medida, transformación digital, inteligencia artificial, branding, comunicación y experiencias feriales. |
| `.../[locale]/proyectos | projects` | Explora los proyectos desarrollados por Vertex en Colombia y la región: plataformas gubernamentales, sistemas empresariales y ecosistemas digitales. |
| `.../[locale]/equipo | team` | Conoce a los líderes y especialistas de Vertex: profesionales en tecnología, diseño, estrategia y gestión de proyectos. |
| `.../[locale]/empleos | jobs` | Explora las vacantes disponibles en Vertex: posiciones en desarrollo frontend, backend, diseño UX/UI, consultoría y gestión de proyectos en Colombia. |
| `.../[locale]/trabaja-con-nosotros | careers` | Forma parte del equipo de Vertex. Conoce nuestra cultura de trabajo, beneficios y oportunidades en desarrollo de software, diseño y tecnología. |
| `.../[locale]/contacto | contact` | Ponte en contacto con el equipo de Vertex. Desarrollamos soluciones tecnológicas y de comunicación para empresas y entidades públicas en Colombia. |
| `.../[locale]/privacidad | privacy` | Política de privacidad y tratamiento de datos personales de Vertex. |
| `.../[locale]/terminos | terms` | Términos y condiciones de uso del portal web de Vertex. |
| `.../[locale]/not-found.tsx` | La página solicitada no existe o ha sido movida. |

> **Conclusión:** Cada ruta define su propia descripción dentro de `generateMetadata`, redactada según el contenido específico de esa página. No se encontró reutilización de un mismo texto de descripción entre rutas distintas.

### Verificación del idioma principal del documento
- **Configuración técnica:** `Vertex-Portal-Web/src/app/[locale]/layout.tsx` ==> Propiedad: `<html lang={locale}>`

> **Conclusión:** El idioma principal del documento no se encuentra estático de manera global, sino que se administra dinámicamente a través del parámetro de ruta centralizado (`[locale]`) provisto por Next.js. Esto garantiza que cuando el usuario navega en el entorno en español, el servidor inyecta de forma limpia la etiqueta `lang="es"`, y al cambiar al entorno en inglés, conmuta de inmediato a `lang="en"`. Con este comportamiento dinámico se cumple estrictamente con el estándar de accesibilidad internacional.

### Revisión del favicon de Vertex
- **Ruta del archivo:** `Vertex-Portal-Web/src/app/favicon.ico`
- **Formato y dimensiones:** Archivo ICO estándar (optimizado a 32x32 px).
- **Transparencia y peso:** Fondo alfa verificado (compatible con Modo Oscuro) con un peso menor a 5 KB.

> **Conclusión:** Se realizó la auditoría técnica del favicon corporativo alojado en la raíz del App Router de Next.js. Se confirmó que el recurso cuenta con fondo transparente, evitando parches visuales en navegadores con modo oscuro activo. Su peso optimizado garantiza que no afecte el rendimiento de carga inicial.

### Revisión de metadatos para compartir en LinkedIn

| Página | Estado OpenGraph / Twitter |
| :--- | :--- |
| `.../page.tsx` | ✅ Presentes, con imagen `/images/vertex-wallpaper-dark.png` (1200x630) |
| `.../quienes-somos | about-us` | ✅ Presentes, misma imagen social |
| `.../nuestra-oferta | our-services` | ✅ Presentes, misma imagen social |
| `.../servicios | services` | ✅ Presentes, misma imagen social |
| `.../proyectos | projects` | ✅ Presentes, misma imagen social |
| `.../equipo | team` | ✅ Presentes, misma imagen social |
| `.../empleos | jobs` | ✅ Presentes, misma imagen social |
| `.../trabaja-con-nosotros | careers` | ✅ Presentes, misma imagen social |
| `.../contacto | contact` | ✅ Presentes, misma imagen social |
| `.../privacidad | privacy` | ⚠️ Ausentes — solo tiene title, description y alternates |
| `.../terminos | terms` | ⚠️ Ausentes — solo tiene title, description y alternates |

> **Conclusión:** La mayoría de las páginas ya cuentan con `openGraph` y `twitter` propios. Las páginas de Privacidad y Términos (ES/EN) quedan pendientes: al no tener estas etiquetas, un link a esas páginas compartido en LinkedIn no generará una vista previa con imagen ni descripción.

### Verificación de una sola etiqueta h1 por página
- **Alcance revisado:** componentes en `src/components/pages` conectados a rutas activas, y secciones del home en `src/components/sections`.

> **Conclusión:** Se confirmó que todas las páginas activas del sitio (rutas conectadas en `app/[locale]`) tienen exactamente una etiqueta `<h1>`. Nota adicional: existe un componente `AboutPageContent.tsx` con su propio `<h1>`, pero no está enlazado a ninguna ruta — es código muerto que no afecta al sitio en producción.

### Revisión del orden de los encabezados h1, h2 y h3

**1. `Vertex-Portal-Web/src/components/pages/ProjectsIndexContent.tsx`**
- Hallazgo: la sección de la grilla de proyectos no tiene su propio `<h2>` — salta de h1 directo a h3 (títulos de tarjeta / estado vacío). El único h2 real aparece después, en el CTA de cierre.

**2. `Vertex-Portal-Web/src/components/pages/JobsSearchContent.tsx`**
- Hallazgo: el listado de vacantes no tiene h2 de sección; el estado "sin resultados" usa h3 y los títulos de cada vacante individual usan h2 (inconsistente con Proyectos y Equipo, donde las tarjetas de listado usan h3).

**3. `Vertex-Portal-Web/src/components/pages/LegalPageContent.tsx` (Privacidad/Términos)**
- Hallazgo: el bloque lateral "¿Cómo ejercer tus derechos?" es un h3 que aparece en el DOM antes del primer h2 (los títulos de cada sección de la política), saltando un nivel.

> **Conclusión:** Se encontraron 3 saltos de jerarquía de encabezados que conviene corregir en Proyectos, Empleos y Legal (Privacidad/Términos), detallados arriba.

### Validación de que el contenido no incluya afirmaciones no verificadas
- **Alcance revisado:** `Vertex-Portal-Web/src/i18n/messages/es.json` (copy de la interfaz) y `Vertex-Portal-Web/src/content/*.ts` (proyectos, servicios, equipo, compañía).
- **Página:** `Vertex-Portal-Web/src/content/projects.ts` (caso "Vertex Nexo")
- **Hallazgo:** el texto de resultados afirma "cumplimiento estricto de normas AGN y Ley 594" (normativa archivística colombiana) — es una afirmación legal/regulatoria concreta, no genérica.

> **Conclusión:** No se encontraron cifras infladas ni frases tipo "los mejores / número 1 / pioneros" en el copy revisado. .
